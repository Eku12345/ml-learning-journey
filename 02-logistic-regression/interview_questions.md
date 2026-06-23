### 1. What is Logistic Regression?

Logistic Regression is a supervised machine learning algorithm used for classification problems where the target variable is categorical.

### 2. Why is it called Logistic Regression?

It uses a regression equation internally but applies a sigmoid function to convert outputs into probabilities for classification.

### 3. What type of problems does Logistic Regression solve?
Binary Classification
Multi-class Classification
Probability Estimation

Examples:

Fraud Detection
Customer Churn
Disease Prediction
Spam Detection
### 4. What is the Sigmoid Function?

It converts any real number into a probability between 0 and 1.

### 5. Why not use Linear Regression for classification?

Problems:

Predictions can be less than 0 or greater than 1
Not suitable for probabilities
Sensitive to outliers
### 6. What does Logistic Regression actually predict?

It predicts probabilities first.

Example:

Probability = 0.82

Then applies a threshold to classify.

### 7. What is the default threshold?
0.5

If probability ≥ 0.5:

Class = 1

Otherwise:

Class = 0
### 8. Can threshold be changed?

Yes.

Threshold depends on business requirements.

### 9. What happens if threshold is lowered?
Recall ↑
Precision ↓

More positives are predicted.

### 10. What happens if threshold is increased?
Precision ↑
Recall ↓

Fewer positives are predicted.

### 11. What are odds?
Odds = P / (1-P)

Example:

Probability = 0.8

Odds = 0.8/0.2 = 4

Meaning:

4 to 1 in favor.

### 12. What are log odds?

The logarithm of odds.

Logistic Regression models log odds as a linear function of features.

### 13. What is the cost function in Logistic Regression?

Binary Cross Entropy (Log Loss)

Not Mean Squared Error.

### 14. Why not use MSE?

MSE creates a non-convex optimization problem.

Log Loss provides better optimization properties.

### 15. What is Log Loss?

Measures how well predicted probabilities match actual outcomes.

Lower is better.

### 16. What is a confusion matrix?
	Predicted 0	Predicted 1
Actual 0	TN	FP
Actual 1	FN	TP
### 17. What is Accuracy?
(TP + TN) / Total

Percentage of correct predictions.

### 18. When is Accuracy misleading?

For imbalanced datasets.

Example:

99% normal
1% fraud

Predicting everything as normal gives:

99% accuracy

but zero business value.

### 19. What is Precision?

Out of all positive predictions:

How many were actually positive?

### 20. What is Recall?

Out of all actual positives:

How many did we correctly identify?

### 21. What is F1 Score?

Harmonic mean of Precision and Recall.

Useful when both matter.

### 22. Precision vs Recall?

Fraud Detection:

Usually prioritize Recall.

Spam Detection:

Usually prioritize Precision.

### 23. What is ROC Curve?

ROC plots:

True Positive Rate
vs
False Positive Rate

for multiple thresholds.

### 24. What is AUC?

Area Under ROC Curve.

Measures ranking ability.

### 25. What does AUC = 0.86 mean?

The model ranks a randomly selected positive observation above a randomly selected negative observation 86% of the time.

### 26. What is Cross Validation?

Evaluates model performance using multiple train-test splits.

### 27. Why use Cross Validation?

Provides a more stable estimate of model performance.

### 28. What is K-Fold Cross Validation?

Dataset is split into K folds.

Each fold acts as test data once.

### 29. Why does Logistic Regression require scaling?

Optimization converges faster and more reliably when features are on similar scales.

### 30. Why don't trees require scaling?

Trees split using thresholds rather than distances.

### 31. What is Regularization?

A technique used to reduce overfitting.

### 32. What is L1 Regularization?

Adds absolute values of coefficients.

Can shrink coefficients to zero.

Feature selection capability.

### 33. What is L2 Regularization?

Adds squared coefficients.

Shrinks coefficients but rarely makes them exactly zero.

### 34. What is C in Logistic Regression?

Inverse of regularization strength.

Small C:

Strong Regularization

Large C:

Weak Regularization
### 35. What happens when C is too small?

Possible underfitting.

### 36. What happens when C is too large?

Possible overfitting.

### 37. What is Data Leakage?

Information from the target leaks into features.

Example:

alive

in Titanic dataset.

### 38. Why use One Hot Encoding?

Avoids artificial ordering of categories.

### 39. Why not use Label Encoding?

May incorrectly imply:

Red > Blue > Green

which has no meaning.

### 40. What is Class Imbalance?

One class heavily outnumbers another.

Example:

99% non-fraud
1% fraud
### 41. How do you handle Class Imbalance?
Class Weights
SMOTE
Oversampling
Undersampling
Threshold Tuning
### 42. What are class weights?

Increase importance of minority class during training.

### 43. How do you explain coefficients in Logistic Regression?

Coefficient indicates change in log odds for a one-unit increase in the feature.

### 44. What is Multiclass Logistic Regression?

Extension of Logistic Regression for more than two classes.

### 45. What is Softmax?

Generalization of sigmoid used for multiclass classification.