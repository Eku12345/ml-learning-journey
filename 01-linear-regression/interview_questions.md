# Linear Regression - Interview Questions & Answers

## 1. What is Linear Regression?

Linear Regression is a supervised machine learning algorithm used to predict a continuous numerical target variable by modeling a linear relationship between input features and the target.

---

## 2. What is the equation of Linear Regression?

y = β0 + β1x1 + β2x2 + ... + βnxn

Where:

* y = predicted value
* β0 = intercept
* β1...βn = coefficients
* x1...xn = features

---

## 3. What does the intercept represent?

The intercept is the predicted value of the target when all feature values are zero.

---

## 4. What does a coefficient represent?

A coefficient represents the expected change in the target variable for a one-unit increase in the feature, keeping all other variables constant.

---

## 5. What is Ordinary Least Squares (OLS)?

OLS is the method used to find the best-fit line by minimizing the sum of squared residuals.

---

## 6. Why do we square residuals?

* Prevent positive and negative errors from canceling out
* Penalize large errors more heavily
* Makes optimization mathematically convenient

---

## 7. What is a residual?

Residual = Actual Value − Predicted Value

A residual represents the prediction error.

---

## 8. What are the assumptions of Linear Regression?

1. Linear relationship between features and target
2. Independence of observations
3. Homoscedasticity
4. Normality of residuals
5. No severe multicollinearity

---

## 9. What is homoscedasticity?

The variance of residuals remains constant across all predicted values.

---

## 10. What is heteroscedasticity?

The variance of residuals changes across predictions.

This can make coefficient estimates unreliable.

---

## 11. What is multicollinearity?

Multicollinearity occurs when independent variables are highly correlated with each other.

---

## 12. Why is multicollinearity a problem?

* Unstable coefficients
* Difficult interpretation
* Inflated variance of estimates

---

## 13. How do you detect multicollinearity?

Using:

* Correlation Matrix
* VIF (Variance Inflation Factor)

---

## 14. What is VIF?

Variance Inflation Factor measures how much a feature is correlated with other features.

General rule:

* VIF < 5 → acceptable
* VIF > 10 → problematic

---

## 15. What is R²?

R² measures the proportion of variance in the target explained by the model.

---

## 16. What is Adjusted R²?

Adjusted R² penalizes unnecessary features and adjusts for model complexity.

---

## 17. Difference between R² and Adjusted R²?

R² always increases or remains the same when features are added.

Adjusted R² can decrease if added features do not provide useful information.

---

## 18. Can R² be negative?

Yes.

When the model performs worse than simply predicting the mean of the target.

---

## 19. What is MAE?

Mean Absolute Error is the average absolute difference between actual and predicted values.

---

## 20. What is MSE?

Mean Squared Error is the average squared difference between actual and predicted values.

---

## 21. What is RMSE?

Root Mean Squared Error is the square root of MSE.

RMSE is in the same units as the target variable.

---

## 22. Difference between MAE and RMSE?

MAE:

* Less sensitive to outliers

RMSE:

* Penalizes large errors more heavily
* More sensitive to outliers

---

## 23. How do outliers affect Linear Regression?

Outliers can significantly influence the regression line and coefficient estimates.

---

## 24. How do you detect outliers?

* Boxplots
* IQR method
* Z-score
* Residual analysis

---

## 25. What happens if the relationship is not linear?

Linear Regression may underfit and perform poorly.

Alternatives:

* Polynomial Regression
* Decision Trees
* Random Forest
* Gradient Boosting

---

## 26. What is underfitting?

The model is too simple and cannot capture patterns in the data.

Characteristics:

* Low train performance
* Low test performance

---

## 27. What is overfitting?

The model memorizes training data and fails to generalize.

Characteristics:

* High train performance
* Low test performance

---

## 28. How do you detect overfitting?

Compare train and test performance.

Large performance gap indicates overfitting.

---

## 29. How can overfitting be reduced?

* More data
* Feature selection
* Regularization
* Cross-validation

---

## 30. What is train-test split?

Train-test split separates data into training and testing sets to evaluate model generalization.

---

## 31. Why not train on the entire dataset?

Without a test set, model performance cannot be evaluated on unseen data.

---

## 32. Why is feature scaling generally not required for Linear Regression?

Linear Regression coefficients adjust according to feature scale.

However, scaling may help when using regularized models like Ridge or Lasso.

---

## 33. What is Ridge Regression?

Ridge Regression adds an L2 penalty to reduce large coefficients and combat overfitting.

---

## 34. What is Lasso Regression?

Lasso Regression adds an L1 penalty and can drive some coefficients to zero, performing feature selection.

---

## 35. When would you choose Linear Regression?

* Target is continuous
* Relationship is approximately linear
* Interpretability is important
* Business users need coefficient explanations
