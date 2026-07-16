                                    Employee Attrition Prediction using Random Forest

Project Overview

This project predicts whether an employee is likely to leave the organization using a Random Forest Classifier.

The project demonstrates the complete machine learning workflow including data preprocessing, exploratory data analysis, model building, hyperparameter tuning, threshold tuning, ROC analysis, and business interpretation.

Dataset

IBM HR Analytics Employee Attrition Dataset

Rows: 1470

Target Variable:

Attrition

Yes
No
Technologies Used
Python
Pandas
NumPy
Matplotlib
Seaborn
Scikit-Learn
Jupyter Notebook
Workflow
Data Cleaning
Removed constant columns
Checked missing values
Checked duplicates
Exploratory Data Analysis
Numerical distributions
Categorical distributions
Boxplots
Attrition analysis
Feature Engineering
Label Encoding
One-Hot Encoding
Model Building

Random Forest Classifier

Model Evaluation
Accuracy
Confusion Matrix
Classification Report
Feature Importance
ROC Curve
Hyperparameter Tuning

GridSearchCV

Optimized parameters:

n_estimators
max_depth
max_features
min_samples_split
min_samples_leaf
Threshold Tuning

Compared thresholds:

0.50
0.40
0.30
0.20

Selected threshold:

0.30

Reason:

Improved Recall while maintaining reasonable overall model performance.

ROC-AUC

ROC-AUC Score:

0.757

Key Learnings
Random Forest reduces overfitting through bagging.
Hyperparameter tuning does not always improve performance.
Threshold tuning can significantly improve Recall without retraining the model.
Model evaluation should align with business objectives rather than relying solely on Accuracy.
Results Summary
Model	Accuracy	Recall	ROC-AUC
Baseline Random Forest	87.76%	0.10	0.757
Threshold = 0.30	83.00%	0.33	0.757
Threshold = 0.20	73.00%	0.64	0.757
Future Improvements
SMOTE for handling class imbalance
RandomizedSearchCV
XGBoost
LightGBM