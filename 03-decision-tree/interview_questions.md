Decision Tree Interview Questions (Part 1)
1. What is a Decision Tree?

Answer:

A Decision Tree is a supervised machine learning algorithm used for both classification and regression tasks. It recursively splits the dataset into smaller subsets based on the feature that best separates the target variable. The final model resembles a tree structure consisting of root nodes, decision nodes, branches, and leaf nodes.

2. Why is it called a Decision Tree?

Answer:

It is called a Decision Tree because the model makes predictions by asking a sequence of decision-based questions, similar to how humans make decisions. Each internal node represents a decision, and each leaf node represents the final prediction.

3. Can Decision Trees be used for both Classification and Regression?

Answer:

Yes.

DecisionTreeClassifier is used for classification problems.
DecisionTreeRegressor is used for regression problems.
4. What is the objective of a Decision Tree?

Answer:

The objective of a Decision Tree is to split the dataset into increasingly pure subsets by selecting the feature that best separates the target classes at each node.

5. What is a Root Node?

Answer:

The Root Node is the topmost node of the tree. It contains the entire dataset before any splitting occurs.

6. What is a Decision Node?

Answer:

A Decision Node is an internal node where the data is split based on a feature and a condition.

Example:

Balance > 5000
7. What is a Leaf Node?

Answer:

A Leaf Node is the final node of the Decision Tree where no further splitting occurs. It represents the final prediction or output class.

8. What is a Branch?

Answer:

A Branch represents the outcome of a decision. It connects one node to another based on a condition being True or False.

9. What is Impurity?

Answer:

Impurity measures how mixed the classes are within a node.

Pure node → only one class
Impure node → multiple classes

Decision Trees try to minimize impurity.

10. What is a Pure Node?

Answer:

A Pure Node contains observations belonging to only one target class.

Example:

10 Yes
0 No

This is a perfectly pure node.

11. What is an Impure Node?

Answer:

An Impure Node contains observations from multiple classes.

Example:

5 Yes
5 No

This is a highly impure node.

12. Why does a Decision Tree split the data?

Answer:

The Decision Tree splits the data to reduce impurity and create child nodes that are more homogeneous than the parent node.

13. What is Gini Index?

Answer:

Gini Index is a measure of impurity used to evaluate the quality of a split in a Decision Tree. Lower Gini values indicate purer nodes.

14. What does a Gini Index of 0 mean?

Answer:

A Gini Index of 0 means the node is perfectly pure and contains observations from only one class.

15. What does a high Gini Index indicate?

Answer:

A high Gini Index indicates that the node contains a mixture of classes and is therefore more impure.

16. What is the goal of Gini Index?

Answer:

The goal is to minimize impurity after every split so that each child node becomes as pure as possible.

17. Why is duration removed from the Bank Marketing dataset?

Answer:

The duration feature is removed because it is only known after the marketing call has been completed. Using it during training introduces data leakage and results in unrealistic model performance.

18. What is Data Leakage?

Answer:

Data leakage occurs when information that would not be available at prediction time is used while training the model. This causes overly optimistic performance during training and poor generalization to real-world data.

19. Why did we create the previously_contacted feature?

Answer:

The pdays column uses -1 to indicate that a customer has never been contacted before. Since -1 is a special business code rather than a true numeric value, creating a binary feature (previously_contacted) preserves this business meaning and makes it easier for the model to use.

20. Why did we keep both pdays and previously_contacted?

Answer:

Keeping both features allows the model to determine whether the exact number of days (pdays) or the binary information (previously_contacted) is more useful. Feature importance can later help decide whether one of them should be removed.

21. Why do Decision Trees not require Feature Scaling?

Answer:

Decision Trees split data based on threshold values (for example, Balance > 5000). Since scaling does not change the order of feature values, it does not affect the splits. Therefore, feature scaling is generally unnecessary.

22. Why can't scikit-learn Decision Trees work directly with categorical strings?

Answer:

Scikit-learn Decision Trees require numerical input. Therefore, categorical variables must be converted into numeric form before training.

23. Why did we use One-Hot Encoding instead of Label Encoding?

Answer:

Most categorical variables in the Bank Marketing dataset are nominal and have no natural order. One-Hot Encoding prevents introducing a false ordinal relationship that Label Encoding would create.

24. When is Label Encoding appropriate?

Answer:

Label Encoding is appropriate for ordinal categorical variables where the categories have a meaningful order, such as:

Low
Medium
High
25. Doesn't One-Hot Encoding create too many features?

Answer:

Yes, One-Hot Encoding increases the number of features. However, Decision Trees naturally select the most informative features during splitting and ignore irrelevant ones. Therefore, One-Hot Encoding usually works well when the number of categories is moderate.

26. Why did we use drop_first=True?

Answer:

Using drop_first=True removes one redundant category from each encoded feature. While this is especially important for linear models to avoid multicollinearity, it also helps reduce unnecessary features in Decision Trees.

27. Why do we split the data into Training and Testing sets?

Answer:

The training set is used to learn the model, while the testing set is used to evaluate how well the model performs on unseen data.

28. Why do we use random_state=42?

Answer:

Setting random_state=42 ensures that the train-test split is reproducible. Running the code multiple times will produce the same split.

29. What happens during the fit() method?

Answer:

During training, the Decision Tree:

Evaluates all features.
Finds the best split using the selected criterion (Gini by default).
Splits the data into child nodes.
Repeats the process recursively until a stopping condition is met.

31. What is Gini Index?

Answer:

Gini Index is a measure of impurity used by Decision Trees to evaluate the quality of a split. Lower Gini values indicate purer nodes, while higher values indicate more mixed classes.

32. What is the formula for Gini Index?

Answer:

For multiple classes:

Gini=1−
i=1
∑
n
	​

p
i
2
	​


For binary classification:

Gini=1−(p
1
2
	​

+p
2
2
	​

)

where p
i
	​

 is the probability of each class.

33. What is the range of Gini Index?

Answer:

For binary classification:

0 → Perfectly pure node
0.5 → Maximum impurity

The Decision Tree aims to minimize the Gini Index at every split.

34. What does Gini Index = 0 mean?

Answer:

It means the node is perfectly pure, containing observations from only one class.

35. Why does a Decision Tree minimize Gini Index?

Answer:

Because lower Gini values indicate purer child nodes. A split with lower impurity generally leads to better classification performance.

36. What is Entropy?

Answer:

Entropy is a measure of uncertainty or impurity in a node. Higher entropy indicates more mixed classes, while lower entropy indicates purer nodes.

37. What is the formula for Entropy?

Answer:

Entropy=−
i=1
∑
n
	​

p
i
	​

log
2
	​

(p
i
	​

)

where p
i
	​

 is the probability of each class.

38. What is the range of Entropy?

Answer:

For binary classification:

0 → Perfectly pure node
1 → Maximum uncertainty
39. Which criterion is used by default in scikit-learn?

Answer:

DecisionTreeClassifier uses:

criterion='gini'

by default.

40. Which is faster: Gini or Entropy?

Answer:

Gini is slightly faster because it only requires multiplication, whereas Entropy involves logarithmic calculations.

41. What is Information Gain?

Answer:

Information Gain measures the reduction in impurity after splitting a node. The feature with the highest Information Gain is selected for splitting.

42. What is the formula for Information Gain?

Answer:

Information Gain=Parent Impurity−Weighted Child Impurity

When Entropy is used:

IG=H(Parent)−∑
N
N
i
	​

	​

H(Child
i
	​

)
43. Which feature becomes the root node?

Answer:

The feature that provides the highest reduction in impurity (highest Information Gain) becomes the root node.

44. Does the Decision Tree evaluate all features?

Answer:

Yes. At each node, the Decision Tree evaluates all candidate features (and possible split values for numerical features) and selects the best split.

45. What is Overfitting?

Answer:

Overfitting occurs when the model memorizes the training data instead of learning general patterns. It performs very well on the training data but poorly on unseen data.

46. How can you identify Overfitting?

Answer:

A large difference between training accuracy and testing accuracy usually indicates overfitting.

Example:

Training Accuracy = 100%
Testing Accuracy = 63%
47. What is Underfitting?

Answer:

Underfitting occurs when the model is too simple to capture the underlying patterns in the data, resulting in poor performance on both training and testing datasets.

48. What is Pruning?

Answer:

Pruning is the process of limiting the growth of a Decision Tree to reduce overfitting and improve generalization.

49. What does max_depth control?

Answer:

max_depth specifies the maximum depth of the Decision Tree. Limiting the depth helps prevent overfitting.

50. What is min_samples_split?

Answer:

min_samples_split specifies the minimum number of samples required before a node can be split into child nodes.

51. What is min_samples_leaf?

Answer:

min_samples_leaf specifies the minimum number of samples that must be present in every leaf node.

52. Why did we remove the duration column from the Bank Marketing dataset?

Answer:

The duration feature is only known after the marketing call has ended. Using it during training introduces data leakage because the information would not be available when making real-time predictions.

53. Why did we create the previously_contacted feature?

Answer:

The pdays column uses -1 to indicate that a customer has never been contacted before. Creating the binary feature previously_contacted preserves this business meaning and provides a more interpretable feature for the model.

54. What is GridSearchCV?

Answer:

GridSearchCV is a hyperparameter tuning technique that exhaustively searches through all specified parameter combinations using cross-validation to identify the best-performing model.

55. What is the difference between best_score_ and Test Accuracy?

Answer:

best_score_ is the average cross-validation score obtained during GridSearchCV on the training data.
Test Accuracy is the performance of the final model on the unseen test dataset.

Both are useful because best_score_ measures generalization during tuning, while Test Accuracy measures real-world performance on new data.