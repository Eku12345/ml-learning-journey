Q. Why is business understanding important before building a machine learning model?

Answer:

Business understanding helps define the problem clearly, identify the target variable, understand the impact of predictions, and choose appropriate evaluation metrics. A technically correct model may still fail if it does not solve the actual business problem.

Q1. Is this a classification or regression problem?

Answer:
Classification, because the target variable (Attrition) has two categories: Yes and No.

Q2. Is the dataset balanced?

Answer:
No. The IBM Attrition dataset is imbalanced, with approximately:

No → 84%
Yes → 16%

This means accuracy alone can be misleading, so we'll also evaluate Precision, Recall, F1-score, and ROC-AUC later.

Q3. Are there missing values?

Answer:
No. This dataset has no missing values, which simplifies preprocessing.

Q4. Why did we use df.nunique()?

Answer:
It helps identify:

Constant columns (only one unique value).
High-cardinality columns.
Columns that may not provide useful information.
Q5. What should we look for before modeling?

Answer:

Missing values
Target distribution
Constant features
Data types
Potential data leakage
Features requiring encoding

Q2. Why should constant columns be removed?

Answer:

Constant columns contain the same value for every observation. Since they have no variance, they do not help the model distinguish between classes and should be removed.

Q3. Why should EmployeeNumber be removed?

Answer:

EmployeeNumber is a unique identifier. It does not contain meaningful predictive information and may lead the model to memorize specific records instead of learning general patterns.

Q4. Should numerical columns with many unique values be removed?

Answer:No. High-cardinality numerical columns like MonthlyIncome or DailyRate often contain valuable information. High cardinality is only a concern for identifier-like columns or categorical features with many unique categories.

Q5. What is Univariate Analysis?

Answer:

Univariate Analysis is the process of analyzing one variable at a time to understand its distribution, central tendency, spread, and presence of outliers or unusual values.

Q6. Why doesn't Random Forest require Feature Scaling?

Answer:

Random Forest is built using Decision Trees, which split data based on feature thresholds rather than distances. Since scaling does not change the order of feature values, it does not affect how the trees split the data.

Q. Why does Random Forest often allow deep trees while Decision Tree needs pruning?

Answer

A Decision Tree consists of a single tree, so deep trees easily overfit. Random Forest averages predictions from many independently trained trees, reducing variance. Therefore, deeper trees are often acceptable.

Q. Why did you use scoring='f1' instead of accuracy?

Answer

The dataset is imbalanced, and accuracy alone can be misleading because correctly predicting the majority class dominates the score. F1-score balances precision and recall, making it more appropriate for evaluating employee attrition predictions.

Q. What if GridSearchCV does not improve performance?
Answer

This does not mean GridSearchCV failed. It indicates that, within the tested hyperparameter combinations, the baseline model was already close to optimal. Performance may instead be limited by the dataset, feature quality, or class imbalance.

Another Important Interview Question
Q. Is it acceptable if the tuned model performs the same as the baseline?
Answer

Yes. Hyperparameter tuning is an optimization process, not a guarantee of improvement. If the tuned model performs similarly, it suggests that the default configuration is already effective for the given dataset and search space.

Q. Why would you optimize Recall instead of Accuracy in an employee attrition model?

Answer

Because the business goal is to identify employees at risk of leaving. Missing a resigning employee (False Negative) is more costly than incorrectly flagging an employee who ultimately stays (False Positive). Therefore, Recall is the more appropriate optimization metric.

Q. 

| Business Problem     | Most Important Metric           | Why?                                          |
| -------------------- | ------------------------------- | --------------------------------------------- |
| Employee Attrition   | **Recall**                      | Missing someone likely to resign is costly.   |
| Cancer Detection     | **Recall**                      | Missing a patient with cancer is dangerous.   |
| Spam Detection       | **Precision**                   | You don't want genuine emails marked as spam. |
| Credit Card Fraud    | **Recall**                      | Missing fraud is expensive.                   |
| Movie Recommendation | **Accuracy** or Ranking Metrics | Overall prediction quality matters more.      |

Q. Why did you use scoring='recall' in GridSearchCV instead of accuracy?

Answer

Because the objective of the employee attrition model is to identify employees who are likely to resign. Missing a resigning employee (a False Negative) is more costly than incorrectly flagging an employee who ultimately stays (a False Positive). Therefore, optimizing Recall aligns better with the business goal.

Q. Does predict() directly predict classes?
✅ Answer

No.

predict() first calculates class probabilities using predict_proba(). It then converts those probabilities into class labels using a default threshold of 0.5.

Q. Why do we use predict_proba()[:,1]?
✅ Answer

predict_proba() returns probabilities for all classes. Since class 1 represents employees who leave, [:,1] extracts only the probability of attrition.

Q. Does threshold tuning retrain the Random Forest?
✅ Answer

No.

Threshold tuning does not change the trained model.

It only changes the probability cutoff used to convert predicted probabilities into class labels.

Q1. Why did lowering the threshold improve Recall?
Answer

Lowering the decision threshold causes the model to classify more observations as the positive class. This increases the number of true positives, improving Recall, but it may also increase false positives, reducing Precision.

Q2. Why did Accuracy decrease?
Answer

Lowering the threshold causes more employees to be predicted as "Leave." While this identifies more true resignations, it also incorrectly flags more employees who would stay, increasing false positives and reducing overall accuracy.

Q. What is ROC Curve?
Answer

ROC (Receiver Operating Characteristic) Curve shows the trade-off between:

True Positive Rate (Recall)
False Positive Rate

at different classification thresholds.

Instead of checking only one threshold (0.5),

ROC evaluates every possible threshold.

Q. What is AUC?
Answer

AUC (Area Under the ROC Curve) measures how well a model distinguishes between classes.

Higher AUC indicates better class separation.

Q. What does an AUC of 0.75 mean?
Answer

An AUC of 0.75 means that if we randomly choose one positive and one negative observation, the model will rank the positive observation higher than the negative one about 75% of the time.

Q. Why is ROC-AUC useful when Accuracy is already available?
Answer

Accuracy evaluates the model at one decision threshold (usually 0.5).

ROC-AUC evaluates the model across all possible thresholds, providing a more complete measure of its ability to distinguish between classes.

1. What is Random Forest?

Answer

Random Forest is an ensemble machine learning algorithm that combines multiple Decision Trees using Bagging (Bootstrap Aggregating). It reduces overfitting and improves generalization by averaging the predictions of many trees.

2. Why is it called Random Forest?

Answer

It builds many Decision Trees using random subsets of:

Training samples (Bootstrap Sampling)
Features (Random Feature Selection)

The collection of these random trees forms a "Random Forest."

3. Difference between Decision Tree and Random Forest?
Decision Tree	Random Forest
Single Tree	Multiple Trees
High Variance	Low Variance
Easily Overfits	Less Overfitting
Fast	Slightly Slower
Easy to Interpret	Less Interpretable
4. What is Ensemble Learning?

Answer

Ensemble Learning combines predictions from multiple models to improve performance compared to using a single model.

5. What is Bagging?

Answer

Bagging (Bootstrap Aggregating) trains multiple models on different bootstrap samples and combines their predictions.

6. What is Bootstrap Sampling?

Answer

Bootstrap Sampling randomly selects observations with replacement, meaning the same observation can appear multiple times in one sample.

7. What is Out-of-Bag (OOB) Data?

Answer

Observations not selected during bootstrap sampling are called Out-of-Bag samples. They can be used to estimate model performance without a separate validation set.

8. Why does Random Forest reduce overfitting?

Answer

Each tree is trained on different samples and different features. Averaging many diverse trees reduces variance and improves generalization.

9. What is Feature Randomness?

Answer

At every split, Random Forest considers only a random subset of features instead of all features.

10. What is Feature Importance?

Answer

Feature Importance measures how much each feature contributes to reducing impurity across all trees.

11. What does feature_importances_ return?

Answer

It returns the normalized importance score of every feature used by the Random Forest.

12. Why is Random Forest more robust than Decision Trees?

Answer

Because prediction is based on the collective decision of many trees instead of relying on a single tree.

13. Does Random Forest require Feature Scaling?

Answer

No.

Tree-based algorithms are scale-independent.

14. Does Random Forest require Normal Distribution?

Answer

No.

Random Forest makes no assumption about data distribution.

15. Can Random Forest handle Outliers?

Answer

Yes.

It is generally robust to outliers because tree splits are not significantly affected by extreme values.

16. Can Random Forest handle Non-linear relationships?

Answer

Yes.

Decision Trees naturally capture non-linear relationships.

17. Important Hyperparameters?
n_estimators
max_depth
max_features
min_samples_split
min_samples_leaf
random_state
18. What does n_estimators mean?

Answer

Number of Decision Trees in the forest.

19. What does max_depth control?

Answer

Maximum depth of each Decision Tree.

20. What happens if max_depth increases?

Answer

Training accuracy increases.

Risk of overfitting also increases.

21. What is min_samples_split?

Answer

Minimum number of samples required to split a node.

22. What is min_samples_leaf?

Answer

Minimum number of samples required in a leaf node.

23. What is max_features?

Answer

Number of random features considered at every split.

24. Why use GridSearchCV?

Answer

To find the best combination of hyperparameters using cross-validation.

25. What is Cross Validation?

Answer

It splits the training data into multiple folds and evaluates the model on each fold to estimate generalization performance.

26. Why didn't GridSearchCV improve your model?

Answer

Because the best hyperparameter combination was already close to the default settings, indicating hyperparameters were not the main limitation.

27. Why was Training Accuracy 100%?

Answer

Random Forest can perfectly memorize the training data when trees are deep enough, leading to overfitting.

28. What is Recall?

Answer

Recall measures how many actual positive cases were correctly identified.

Recall=
TP+FN
TP
	​

29. Why optimize Recall for Employee Attrition?

Answer

Missing an employee who will resign is more costly than incorrectly flagging an employee who stays.

30. Why isn't Accuracy sufficient?

Answer

Accuracy can be misleading on imbalanced datasets because the model can achieve high accuracy while failing to detect the minority class.

31. What is Threshold Tuning?

Answer

Threshold tuning changes the probability cutoff used to convert predicted probabilities into class labels.

32. Does Threshold Tuning retrain the model?

Answer

No.

It only changes the decision threshold.

33. What is predict_proba()?

Answer

It returns the probability of each class instead of the predicted label.

34. Why use predict_proba()[:,1]?

Answer

Because class 1 represents employees leaving the company.

35. What happens when threshold decreases?

Answer

Recall increases
Precision decreases
False Positives increase
36. What is ROC Curve?

Answer

ROC Curve shows the relationship between True Positive Rate and False Positive Rate across different thresholds.

37. What is AUC?

Answer

AUC measures how well the model separates the two classes.

38. What does AUC = 0.75 mean?

Answer

The model ranks a randomly selected positive instance higher than a randomly selected negative instance approximately 75% of the time.

39. Why use ROC-AUC?

Answer

Because it evaluates model performance across all thresholds instead of only one threshold.

40. Why did you recommend threshold = 0.30?

Answer

It improved Recall substantially while maintaining a reasonable Accuracy, making it more suitable for the HR business objective.

