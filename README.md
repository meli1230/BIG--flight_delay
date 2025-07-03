# Binary Prediction of Flight Delays – San Jose Airport (SJC)
This project aims to predict whether flights departing from San Jose International Airport (SJC), California are delayed or not, using binary classification models trained on a cleaned subset of the Flight Delay Dataset 2018–2024 from Kaggle.

## Resources
The notebook containing the code was provided within the source files. However, if you wish to see the Google Collab version, you can find it [here](https://colab.research.google.com/drive/18goYM5GGeQgMENW6jTGsoLAh27j9pQDC?usp=sharing). 

## Objective
Predict whether a flight will be delayed by 15 minutes or more (DepDel15 = 1) or not (DepDel15 = 0), using historical flight data.

## Dataset Overview

- Source: [Kaggle Dataset](https://www.kaggle.com/datasets/shubhamsingh42/flight-delay-dataset-2018-2024)
- Scope: Only January 2018 data used.
- Initial shape: ~500,000 instances, 119 features
- Filtered to: San Jose (SJC) departures only
- Final cleaned dataset: 3,880 rows, 67 features

## Data Preprocessing

- Missing values: Dropped mostly null columns and imputed logical defaults (e.g. `CancellationCode` → 0 if N/A).
- Constant columns: Removed features like `Month` that had the same value across all instances.
- Standardization: Scaled numerical features to mean 0, std 1.
- Encoding: Label encoded string categories and applied dummy variables for categorical columns.
- Feature selection: Removed features strongly correlated with the target (e.g., `DepDelay`, `ArrDel15`) to prevent data leakage.
- Outlier removal: IQR and Z-score methods applied.

## Train-Test Split

- 80% Train, 20% Test
- Validation inside train split: 70% Train, 30% Validation
- Applied 5-fold cross-validation during training

## Models Used

1. Logistic Regression
2. Random Forest
3. Gradient Boosting
4. XGBoost

## Model Parameters

| Model               | Parameters Highlights                                                  |
|--------------------|--------------------------------------------------------------------------|
| Logistic Regression| C, penalty = l2, solver = liblinear                                      |
| Random Forest       | n_estimators, max_depth, max_features                                    |
| Gradient Boosting   | n_estimators, max_depth, learning_rate                                   |
| XGBoost             | n_estimators, max_depth, learning_rate, subsample = 0.8, eval_metric     |

## Evaluation Metrics

- Accuracy  
- Precision  
- Recall  
- F1-score  
- Specificity  
- ROC-AUC Curve
- Confusion Matrix

## Results Summary

| Model             | Accuracy | Precision | Recall | F1-score | AUC  |
|------------------|----------|-----------|--------|----------|------|
| Logistic Regression | ~90%     | 1.00      | 38%    | —        | 0.92 |
| Random Forest     | 87%      | 83%       | 24.6%  | —        | —    |
| Gradient Boosting | 92.2%  | —         | 59.6%| 0.72   | 0.94 |
| XGBoost           | 90.5%    | 93.4%     | 43.8%  | —        | 0.918|

Best performing model: Gradient Boosting
- Balanced precision and recall
- Highest AUC and F1-score
- Chosen as the final production model

## Final Model Performance

- Accuracy: 81%
- Recall: 56.5%
- Precision: High
- AUC: High
- Slightly conservative behavior: tends to avoid false positives

## Key Insights

- Gradient Boosting provides the best balance between sensitivity and specificity.
- Logistic Regression is overly conservative (high precision, low recall).
- XGBoost performs well but is slightly less sensitive.
- Data preprocessing (especially removing correlated columns) was critical to avoid data leakage and overfitting.
