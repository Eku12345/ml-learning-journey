--Why did you create the DataFrame manually instead of using data.frame?

I created the DataFrame explicitly using data.data and data.feature_names because it's the most widely used and portable approach. Not all scikit-learn datasets provide a frame attribute, and the explicit construction makes it clear how the features and target are assembled.

--Why do we use fit_transform() on the training set but only transform() on the test set?

The scaler should learn its parameters, such as the mean and standard deviation, only from the training data. The same learned parameters are then applied to the test data using transform(). This prevents data leakage and ensures that the model is evaluated on truly unseen data.

--Why is StandardScaler commonly used with KNN instead of MinMaxScaler?


Both StandardScaler and MinMaxScaler can work with KNN. StandardScaler is commonly used because it centers features around zero with unit variance and performs well when features approximately follow a normal distribution. MinMaxScaler is useful when features have known minimum and maximum bounds. The choice depends on the data rather than KNN itself.


--How do you choose the value of K?

We typically start with a reasonable baseline such as K = 5. Then we use cross-validation techniques like GridSearchCV to evaluate multiple values of K and select the one that gives the best validation performance. The optimal K depends on the dataset.

--Why is KNN training fast but prediction slow?

KNN performs almost no computation during training because it simply stores the training data. During prediction, it computes the distance between the new sample and all training samples, making inference computationally expensive.

--What's the difference between predict() and predict_proba()?

Answer:

predict() returns the final predicted class label (e.g., 0 or 1).
predict_proba() returns the probability of each class, which can help assess the model's confidence in its prediction.

Q. Why do we evaluate on the test set instead of the training set?

The purpose of the test set is to evaluate how well the model generalizes to unseen data. Since the model has already learned from the training data, evaluating on it can give an overly optimistic estimate of performance. The test set provides a more realistic assessment of how the model is likely to perform in production.



