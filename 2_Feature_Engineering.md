# Credit Risk Scoring - Part 2: Feature Engineering

This section of the project focuses on enhancing the Credit Risk model through feature engineering. We create various financial ratios, age-based features, interaction features, and flag features that will help improve the model's ability to predict credit risk.

## Table of Contents
- [Overview](#overview)
- [Feature Engineering](#feature-engineering)
  - [Financial Ratios](#financial-ratios)
  - [Age-based Features](#age-based-features)
  - [Interaction Features](#interaction-features)
  - [Flag Features](#flag-features)
- [Model Training](#model-training)
- [Feature Importance](#feature-importance)
- [Conclusion](#conclusion)

## Overview
Feature engineering is a crucial step in improving the performance of predictive models. In this part of the project, we create new features derived from the original dataset, such as:
- **Financial Ratios** to assess the borrower's financial health.
- **Age-based Features** to categorize individuals by age and study the non-linear effects.
- **Interaction Features** to explore relationships between key variables.
- **Flag Features** to capture specific risk indicators.

These features are then used to train our XGBoost model.

## Feature Engineering

### Financial Ratios
We calculate the following important financial ratios to assess an individual's financial condition:
```python
# Create important financial ratios
df['debt_to_income'] = df['debt'] / df['income']
df['loan_to_income'] = df['amount'] / df['income']
df['expense_ratio'] = df['expenses'] / df['income']
df['asset_to_debt'] = df['assets'] / df['debt']
df['payment_to_income'] = (df['amount'] / df['time']) / df['income']
```

### Age-based Features
These features capture the effect of age on the credit risk scoring. We create non-linear transformations and categorize age groups:
```python
# Age categories and transformations
df['age_squared'] = df['age'] ** 2  # Non-linear age effects
df['age_group'] = pd.cut(df['age'], 
                        bins=[0, 25, 35, 45, 55, 100],
                        labels=['Young', 'Young_Adult', 'Adult', 'Senior', 'Elder'])

```

### Flag Features
Flag features are binary indicators that highlight specific risk factors:
```python
# Create binary flags for risk indicators
df['high_debt_flag'] = (df['debt_to_income'] > df['debt_to_income'].median()).astype(int)
df['low_income_flag'] = (df['income'] < df['income'].median()).astype(int)
df['high_loan_request_flag'] = (df['amount'] > df['amount'].median()).astype(int)
```

## Model Training
After creating the new features, we proceed to train the XGBoost model using these additional features. The model is trained on the updated dataset with the engineered features included.
```python
# Train the XGBoost model using the new features
xgboost_model = XGBClassifier()
xgboost_model.fit(X_train, y_train)
```

## Feature Importance
Once the model is trained, we analyze the feature importances to identify which features contribute most to the model's predictions. Based on the XGBoost feature importance output, we summarize the top features:

- Top 9 Features: These features explain 50% of the model's decisions.
- Top 16 Features: These features explain 70% of the model's decisions.
- Top 20 Features: These features explain 80% of the model's decisions.
- Top 25 Features: These features explain 90% of the model's decisions.
The next step is to use the Top 16 Features to create a dynamic scoring system.

## Conclusion
We engineered new features that enhanced the model's predictive capabilities. We created financial ratios, age-based features, interaction features, and flag features to better capture the factors influencing credit risk. After training the XGBoost model with these features, we analyzed the feature importances and identified the top features that drive model decisions.