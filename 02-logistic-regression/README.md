# Logistic Regression - Titanic Survival Prediction

## Objective

Predict whether a passenger survived the Titanic disaster.

## Skills Covered

- Missing Value Handling
- Feature Engineering
- One Hot Encoding
- Scaling
- Pipelines
- Logistic Regression
- Classification Metrics

## observations

ROC-AUC Score: 0.868

The ROC curve indicates strong class separation capability. The model has an 86.8% probability of ranking a randomly selected survivor higher than a randomly selected non-survivor.

Confusion Matrix:
TN = 98
FP = 12
FN = 17
TP = 52

The model achieved 83.8% accuracy with balanced precision (81%) and recall (75%), making it a strong baseline classifier.

Final Model Performance

Accuracy: 83.8%
Precision: 81%
Recall: 75%
F1 Score: 78%
ROC-AUC: 0.868

5-Fold Cross Validation ROC-AUC:
Mean Score: 0.862

Hyperparameter Tuning:
Best C = 0.01
Mean ROC-AUC = 0.8635