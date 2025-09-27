# Medical-Insurance-Cost-Prediction-Project
Predicting Cost of Medical Insurance

## Project Overview

This project aims to predict medical insurance costs for individuals based on their personal attributes such as age, BMI, smoking status, and number of children. A Linear Regression model is developed after a thorough process of Exploratory Data Analysis (EDA), data cleaning, feature engineering, and feature selection.

## Dataset

The dataset used is `insurance.csv`, which contains 1,338 records with the following attributes:

* **age**: Age of the primary beneficiary.
* **sex**: Gender of the beneficiary (male/female).
* **bmi**: Body Mass Index.
* **children**: Number of children covered by health insurance.
* **smoker**: Whether the beneficiary is a smoker (yes/no).
* **region**: The beneficiary's residential area in the US (northeast, southeast, southwest, northwest).
* **charges**: Individual medical costs billed by health insurance (target variable).

## Analysis and Preprocessing Steps

1.  **Exploratory Data Analysis (EDA)**:
    * Visualized the distributions of numerical features (`age`, `bmi`, `charges`) which revealed that `charges` is right-skewed.
    * Analyzed the correlation between features. Key findings include a strong positive correlation between `smoker` status and `charges`, and moderate positive correlations for `age` and `bmi` with `charges`.
    * Checked for missing values (none found) and identified one duplicate row.

2.  **Data Cleaning & Preprocessing**:
    * The single duplicate row was removed.
    * **Label Encoding**: Binary categorical features `sex` and `smoker` were converted to `0` and `1`.
    * **One-Hot Encoding**: The `region` feature was converted into numerical format to avoid creating an ordinal relationship between the areas.

3.  **Feature Engineering & Selection**:
    * **Feature Creation**: A new categorical feature, `bmi_category` (Underweight, Normal, Overweight, Obese), was created by binning the continuous `bmi` values. This was then one-hot encoded.
    * **Feature Scaling**: Key numerical predictors (`age`, `bmi`, `children`) were standardized using `StandardScaler` to ensure they are on a comparable scale.
    * **Feature Selection**: Pearson Correlation and Chi-Square tests were performed to identify the features with the most significant impact on insurance charges. The final features selected for the model were `age`, `is_female`, `bmi`, `children`, `is_smoker`, `region_southeast`, and `bmi_category_Obese`.

## Model and Results

A **Linear Regression** model was trained on the preprocessed data.

* **R-squared Score**: **0.804**
* **Adjusted R-squared Score**: **0.799**

The results indicate that approximately 80% of the variance in medical charges can be explained by the selected features in our model, demonstrating a strong predictive capability.
