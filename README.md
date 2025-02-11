# Credit Risk Scoring Model  

## Project Overview  
This project implements a machine learning solution for predicting credit risk, helping banks make informed decisions about loan approvals. The model predicts whether a client is likely to default on a loan based on various personal and financial features.  

## Dataset  
The dataset contains **4,455 records** with **14 features**, including:  
- **Personal Information:** Age, marital status, employment details  
- **Financial Metrics:** Income, assets, debt  
- **Historical Data:** Credit records  
- **Loan-Specific Information:** Loan amount requested, time period  

## Project Structure  
1. **Data Preparation**  
   - Categorical variable encoding  
   - Missing value treatment  
   - Feature preprocessing  
   - Train/validation/test split  

2. **Model Development**  
   - Implemented and compared multiple models:  

### Decision Tree  
- **Baseline Model (Default Parameters)**  
  - Validation ROC AUC: **0.665**  
- **Tuned Model**  
  - Parameters: `max_depth=6`, `min_samples_leaf=100`  
  - Validation ROC AUC: **0.816**  

### Random Forest  
- **Tuned Parameters:**  
  - `n_estimators=200`, `max_depth=3`, `min_samples_leaf=10`  
- **Performance:**  
  - Train ROC AUC: **0.829**  
  - Validation ROC AUC: **0.841**  
  - Test ROC AUC: **0.820**  

### XGBoost  
- **Tuned Parameters:**  
  - `eta=0.1`, `max_depth=3`, `min_child_weight=5`, `subsample=0.8`, `colsample_bytree=1.0`  
- **Performance:**  
  - Train ROC AUC: **0.926**  
  - Validation ROC AUC: **0.864**  
  - Test ROC AUC: **0.839**  

## Key Findings  
✔ **XGBoost performed best**, achieving the highest validation (0.864) and test (0.839) scores.   
✔ **Parameter tuning** significantly improved model performance.  
✔ **Ensemble methods outperformed single decision trees**, demonstrating the advantage of using multiple learners.  

## Requirements  
To run this project, install the following dependencies:  

```bash
pip install pandas numpy scikit-learn xgboost seaborn matplotlib