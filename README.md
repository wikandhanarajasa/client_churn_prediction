# Client Churn Prediction

## Introduction
This project aims to create a machine learning model to predict whether the client of Beta Bank will remain or leave.

## Goal
To develop a machine learning model to predict client churn with an F1 score exceeding 0.59.

## Stages
The stages of this project are as follows:
1. Load the data and study the general information.
2. Prepare the data if anomalies are found & check the class balance.
3. Create and train the machine learning model.
4. Draw conclusions.

## Data Content
The dataset consists of the following columns:

### Features
- **RowNumber:** Index of string data
- **CustomerId:** Customer ID
- **Surname:** Last name
- **CreditScore:** Credit score
- **Geography:** Country of residence
- **Gender:** Gender
- **Age:** Age
- **Tenure:** Duration of tenure for fixed-term customer deposits (in years)
- **Balance:** Account balance
- **NumOfProducts:** Number of bank products used by the customer
- **HasCrCard:** Whether the customer has a credit card (1 - yes; 0 - no)
- **IsActiveMember:** Customer's level of activity (1 - yes; 0 - no)
- **EstimatedSalary:** Estimated salary

### Target
- **Exited:** Whether the customer has exited (1 - yes; 0 - no)

## Conclusion
The goal of this project is to develop a machine learning model capable of achieving an F1 score greater than 0.59. The data has undergone several preprocessing steps as follows:
- Filled the missing value in the `tenure` column with 0.
- Dropped unnecessary columns to run the machine learning model: `RowNumber`, `CustomerId`, and `Surname`.
- Applied one-hot encoding to convert categorical data into numerical format.
- Data split: 80% for the training set, 10% for the test set, and 10% for the validation set.

Various machine learning models were tested, including Logistic Regression and Random Forest. The Random Forest model was found to be the most suitable for the project objective, achieving an F1 score exceeding 0.59.

### Hyperparameters:
- Training: `max_depth=10`
- Validation: `max_depth=11`

### Results
#### Training:
- **Confusion Matrix:** [[6326, 73], [731, 870]]
- **Accuracy:** 90.0%
- **ROC AUC:** 76.6%
- **Precision Class 0:** 89.6%
- **Precision Class 1:** 92.3%
- **Recall Class 0:** 98.9%
- **Recall Class 1:** 54.3%
- **F1 Score Class 0:** 94.0%
- **F1 Score Class 1:** 68.4%

#### Testing:
- **Confusion Matrix:** [[777, 17], [112, 94]]
- **Accuracy:** 87.1%
- **ROC AUC:** 71.7%
- **Precision Class 0:** 87.4%
- **Precision Class 1:** 84.7%
- **Recall Class 0:** 97.9%
- **Recall Class 1:** 45.6%
- **F1 Score Class 0:** 92.3%
- **F1 Score Class 1:** 59.3%

#### Validation:
- **F1 Score:** 96.0%

### Addressing Imbalance:
Given the imbalance in the target column, both upscaling and downscaling methods were tested:
- **Upscaling Method:** Using Random Forest with `max_depth=11`, the F1 score was 62%, exceeding the requirement.
- **Downscaling Method:** Using Random Forest with `n_estimators=500` and `max_depth=11`, the F1 score was 53%.

### Summary:
The recommended machine learning model for this project is Random Forest with `max_depth=10` for testing and `max_depth=11` for validation, achieving an F1 score of more than 59% for testing and 96% for validation. After addressing the imbalance, the recommended model remains Random Forest with `max_depth=10` using upscaling, resulting in an F1 score of 62%, exceeding the requirement of 59%.
