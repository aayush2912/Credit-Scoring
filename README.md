# Credit Risk Scoring

This project aims to build an effective **Credit Risk Scoring** system using machine learning. The goal is to predict the creditworthiness of individuals based on their financial information. The project is structured into two major parts:

1. **Model Comparisons**: Evaluating different machine learning models to determine the best performer for predicting credit risk.
2. **Feature Engineering**: Enhancing the model's performance by creating additional meaningful features from raw data.

---

## Table of Contents
- [Overview](#overview)
- [Part 1: Model Comparisons](#part-1-model-comparisons)
  - [Steps Involved](#steps-involved)
  - [Model Comparison and Selection](#model-comparison-and-selection)
  - [Conclusion](#conclusion)
- [Part 2: Feature Engineering](#part-2-feature-engineering)
  - [Financial Ratios](#financial-ratios)
  - [Age-based Features](#age-based-features)
  - [Interaction Features](#interaction-features)
  - [Flag Features](#flag-features)
  - [Model Training](#model-training)
  - [Feature Importance](#feature-importance)
- [Conclusion](#conclusion)

---

## Overview

In this project, we use machine learning algorithms to predict the credit risk of individuals. We begin by comparing different models to choose the best one and then enhance it using engineered features that help the model make better predictions. This work is aimed at classifying individuals into different risk categories (low, medium, high) based on their financial profile.

---

## Part 1: Model Comparisons

### Steps Involved:
1. **Data Loading**: The first step is to load the credit data, which includes information such as income, debt, loan amount, and other personal financial details.
2. **Exploratory Data Analysis (EDA)**: This step helps us understand the data by checking for patterns, missing values, and distribution of key features. EDA helps us identify any imbalances or anomalies that may need to be addressed before training the model.
3. **Train/Validation/Test Split (60/20/20)**: We divide the data into three sets:
    - **60%** for training the model,
    - **20%** for validation (tuning the model's parameters),
    - **20%** for testing the final model’s performance.
4. **Model Development**: We train multiple machine learning models on the training dataset and evaluate their performance on the validation and test sets. Models considered include:
    - **Decision Tree**
    - **Random Forest**
    - **XGBoost**
5. **Hyperparameter Tuning**: For each model, we optimize its parameters to improve performance. This is done through techniques such as grid search or random search.

### Model Comparison and Selection

Several machine learning models were tested and compared using their **ROC AUC scores**, a metric for evaluating the quality of predictions:
- **Decision Tree**: A basic model for quick evaluation, with and without tuning.
- **Random Forest**: A more complex model that uses an ensemble of decision trees for better accuracy.
- **XGBoost**: A highly efficient and powerful boosting model that was tuned to achieve the best results.

The performance of these models was compared based on **ROC AUC scores** on the validation and test datasets. After evaluation, the **Tuned XGBoost** model was selected as the best performer, with the highest ROC AUC scores.

### Conclusion:
The best-performing model in this comparison is **Tuned XGBoost**, with the highest **Validation ROC AUC** of 0.864 and strong **Test ROC AUC** of 0.839. This model was chosen for further work in **Part 2**, where we apply feature engineering to improve its performance.

---

## Part 2: Feature Engineering

Feature engineering is a crucial step to improve the model's predictive capabilities. In this part, we enhance the **XGBoost** model by creating new features from the existing financial data. These engineered features provide deeper insights into an individual’s financial health, enabling the model to make more accurate predictions about credit risk.

### Financial Ratios:
Financial ratios capture important aspects of an individual's financial health and repayment ability. The following ratios were created:
- **Debt-to-Income Ratio**: Measures the proportion of income that goes toward debt payments.
- **Loan-to-Income Ratio**: Indicates the proportion of income requested as a loan.
- **Expense Ratio**: Reflects how much of the income is spent on living expenses.
- **Asset-to-Debt Ratio**: Indicates the ratio of assets to debt, providing insight into financial stability.
- **Payment-to-Income Ratio**: Shows how much of the income is used to pay off the loan over time.

These ratios help the model better understand an individual's financial situation and predict their ability to repay loans.

### Age-based Features:
Age can significantly impact creditworthiness. Therefore, age transformations were introduced:
- **Age Squared**: Captures non-linear effects of age, acknowledging that the impact of age on credit risk might not be linear.
- **Age Group**: Categorizes individuals into different age groups (e.g., Young, Adult, Senior, etc.), which can help the model understand age-related patterns in financial behavior.

### Interaction Features:
Interaction features allow the model to capture relationships between multiple factors. For example:
- **Income per Age**: The relationship between income and age can help identify if older individuals with lower income are riskier.
- **Debt per Age**: Similarly, analyzing debt relative to age can highlight financial struggles in different age groups.
- **Assets per Age**: This shows how individuals' assets compare to their age, helping the model detect financial maturity.

### Flag Features:
Flag features are binary indicators that highlight specific conditions, helping the model quickly identify high-risk cases. These flags include:
- **High Debt Flag**: Indicates if an individual has a debt-to-income ratio above the median.
- **Low Income Flag**: Flags individuals with income below the median.
- **High Loan Request Flag**: Flags individuals requesting loan amounts above the median.

### Model Training:
Once the engineered features were created, the **XGBoost** model was retrained using the new dataset, which now contains the original and engineered features. The goal was to improve the model's predictive accuracy by giving it more relevant data.

### Feature Importance:
After training the model, we evaluated the importance of each feature in predicting credit risk. The most important features were selected based on their contribution to the model’s decisions:
- **Top 9 Features**: These explain 50% of the model's decisions.
- **Top 16 Features**: These explain 70% of the model's decisions.
- **Top 20 Features**: These explain 80% of the model's decisions.
- **Top 25 Features**: These explain 90% of the model's decisions.

This feature importance analysis provides insight into which features are most influential in determining credit risk, and can be used to design a **scoring system** for individuals.

---

## Conclusion

### Part 1: Model Comparison
In **Part 1**, different machine learning models were evaluated. The **Tuned XGBoost** model was selected as the best performer, achieving the highest **Validation ROC AUC** of **0.864** and a **Test ROC AUC** of **0.839**.

### Part 2: Feature Engineering
In **Part 2**, the performance of the **XGBoost** model was enhanced through feature engineering. We created new features such as **financial ratios**, **age-based features**, **interaction features**, and **flag features** to improve the model's predictive power. By retraining the model with these new features, we expect it to have a better understanding of the financial behavior of individuals.

This project aims to create a robust, interpretable, and effective credit risk scoring system for financial institutions and lenders. It can be expanded to incorporate more advanced techniques such as **ensemble methods**, **model interpretability**, and **deployment** for real-world applications.
