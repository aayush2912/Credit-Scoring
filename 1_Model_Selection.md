# Credit Risk Scoring - Part 1: Model Comparison and Selection

This project focuses on evaluating different machine learning models to predict credit risk. Part 1 involves the comparison of several models with a focus on their ability to predict credit risk based on training, validation, and test datasets. The models are evaluated using ROC AUC scores to determine their performance.

## Table of Contents
- [Overview](#overview)
- [Data Preparation](#data-preparation)
- [Models](#models)
  - [Decision Tree](#decision-tree)
  - [Random Forest](#random-forest)
  - [XGBoost](#xgboost)
- [Model Evaluation](#model-evaluation)
- [Conclusion](#conclusion)

## Overview
In this section of the project, we perform a comprehensive comparison of various machine learning models to predict credit risk. The following models are implemented:
- Decision Tree (Default and Tuned Parameters)
- Random Forest (Tuned Parameters)
- XGBoost (Tuned Parameters)

The primary metric used for evaluation is the ROC AUC score, which is calculated on the train, validation, and test datasets.

## Data Preparation
- **Data Loading**: The dataset is loaded from a CSV file containing credit-related features for each individual (e.g., debt, income, loan amount).
- **Exploratory Data Analysis (EDA)**: Basic summary statistics and visualizations are generated to understand the distributions of important features.
- **Train/Validation/Test Split**: The dataset is split into three parts:
  - Training: 60% of the data
  - Validation: 20% of the data
  - Test: 20% of the data

## Models

### Decision Tree (Default Parameters)
- **Model**: Decision Tree with default parameters.
- **ROC AUC Score**: 0.665 (Validation)

### Decision Tree (Tuned Parameters)
- **Model**: Decision Tree with hyperparameter tuning (max_depth=6, min_samples_leaf=100).
- **Best ROC AUC Score**: 0.816 (Validation)

### Random Forest (Tuned Parameters)
- **Model**: Random Forest with hyperparameter tuning (n_estimators=200, max_depth=3, min_samples_leaf=10).
- **ROC AUC Scores**:
  - Train: 0.829
  - Validation: 0.841
  - Test: 0.820

### XGBoost (Tuned Parameters)
- **Model**: XGBoost with hyperparameter tuning (eta=0.1, max_depth=3, min_child_weight=5, subsample=0.8, colsample_bytree=1.0).
- **ROC AUC Scores**:
  - Train: 0.926
  - Validation: 0.864
  - Test: 0.839

## Model Evaluation
The models were evaluated using the ROC AUC score, which is a standard metric for binary classification problems. Higher ROC AUC scores indicate better model performance.

### ROC AUC Comparison
| Model                           | Train ROC AUC | Validation ROC AUC | Test ROC AUC |
|----------------------------------|---------------|--------------------|--------------|
| Decision Tree (Default)          | 0.665         | 0.665              | -            |
| Decision Tree (Tuned)            | 0.816         | 0.816              | -            |
| Random Forest (Tuned)            | 0.829         | 0.841              | 0.820        |
| XGBoost (Tuned)                  | 0.926         | 0.864              | 0.839        |

## Conclusion
- **Tuned XGBoost** achieved the best results, with the highest **Validation ROC AUC** (0.864) and strong **Test ROC AUC** performance (0.839).
- XGBoost outperformed the Decision Tree and Random Forest models, demonstrating its ability to capture complex patterns in the data.
- Based on these results, **XGBoost** is the chosen model for further steps in the credit risk scoring system.
