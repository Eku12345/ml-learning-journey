# Naive Bayes Interview Questions

---

## 1. What is Naive Bayes?

Naive Bayes is a probabilistic machine learning algorithm based on Bayes' Theorem. It predicts the class with the highest posterior probability while assuming that all input features are conditionally independent given the target class.

---

## 2. Why is it called "Naive"?

It assumes that all input features are conditionally independent of each other given the class. This assumption is rarely true in real-world datasets, which is why it is called "Naive."

---

## 3. What is Bayes' Theorem?

Bayes' Theorem updates the probability of an event after observing new evidence.

---

## 4. What is Prior Probability?

The probability of a class before observing any evidence.

Example:
Probability that an SMS is spam before reading its content.

---

## 5. What is Posterior Probability?

The updated probability of a class after considering the observed features.

---

## 6. What is the likelihood in Naive Bayes?

Likelihood is the probability of observing a feature given a class.

Example:

P(Free | Spam)

---

## 7. Why is Naive Bayes popular for text classification?

Because it is:
- Fast
- Memory efficient
- Works well with high-dimensional sparse data
- Performs well even with relatively small datasets

---

## 8. What does CountVectorizer do?

CountVectorizer converts text documents into numerical feature vectors by creating a vocabulary of unique words and counting how many times each word appears in each document.

---

## 9. What does CountVectorizer learn during fit()?

It learns the vocabulary (unique words) from the training data and assigns each word a column index.

---

## 10. Why do we use fit_transform() on the training data and transform() on the test data?

fit() learns the vocabulary from the training data.

The same vocabulary is then used to transform the test data.

This prevents data leakage.

---

## 11. What is data leakage in this project?

If CountVectorizer is fitted on the entire dataset before train-test split, it learns words from the test set, resulting in data leakage.

---

## 12. Why does CountVectorizer return a sparse matrix?

Most documents contain only a small subset of the total vocabulary.

Instead of storing thousands of zeros, a sparse matrix stores only non-zero values, making it memory efficient.

---

## 13. What does Multinomial Naive Bayes learn during fit()?

It learns:
- Prior probability of each class
- Probability of each word given each class

---

## 14. What is the Zero Frequency Problem?

If a word never appears in a class during training, its probability becomes zero.

Since Naive Bayes multiplies probabilities, one zero causes the entire class probability to become zero.

---

## 15. What is Laplace Smoothing?

Laplace smoothing adds a small value to every word count so that unseen words receive a non-zero probability.

This prevents the Zero Frequency Problem.

---

## 16. What does the alpha parameter control?

Alpha controls the amount of Laplace smoothing.

- Small alpha → Less smoothing
- Large alpha → More smoothing

---

## 17. Why can both very small and very large alpha values be problematic?

Alpha = 0 results in zero probabilities for unseen words.

A very large alpha over-smooths the probabilities, making informative and uninformative words appear too similar.

---

## 18. Why did we use MultinomialNB instead of GaussianNB?

Because CountVectorizer produces word-count features.

Multinomial Naive Bayes is designed for count-based data, whereas Gaussian Naive Bayes assumes continuous numerical features.

---

## 19. Why did we use map() instead of LabelEncoder?

Since the target had only two known categories (ham and spam), map() is simpler, more readable, and gives explicit control over the mapping.

---

## 20. Why was F1-score used in GridSearchCV instead of Accuracy?

The dataset is imbalanced.

F1-score balances Precision and Recall, making it more suitable than Accuracy for evaluating performance.

---

## 21. Why didn't GridSearchCV improve the model?

GridSearchCV confirmed that the default parameter (alpha = 1.0) was already the optimal choice for this dataset.

Validation is valuable even when performance does not improve.

---

## 22. What is the difference between predict() and predict_proba()?

predict() returns the predicted class labels.

predict_proba() returns the probability of each class.

---

## 23. When would you prioritize Recall over Precision?

Examples:
- Spam Detection
- Fraud Detection
- Disease Detection

Missing positive cases is more costly than generating false alarms.

---

## 24. What are the advantages of Naive Bayes?

- Simple
- Fast
- Works well with text data
- Performs well on high-dimensional datasets
- Easy to implement

---

## 25. What are the limitations of Naive Bayes?

- Assumes feature independence
- Performance decreases when features are highly correlated
- Simpler than modern ensemble and deep learning models

---

## 26. What are the three common variants of Naive Bayes?

- Gaussian Naive Bayes → Continuous numerical features
- Multinomial Naive Bayes → Word counts / text classification
- Bernoulli Naive Bayes → Binary features (0/1)

---

## 27. Explain the complete workflow of your project.

1. Loaded the SMS Spam dataset.
2. Performed exploratory data analysis.
3. Encoded target labels.
4. Split the dataset into train and test sets.
5. Converted text into numerical features using CountVectorizer.
6. Trained a Multinomial Naive Bayes classifier.
7. Evaluated the model using Accuracy, Precision, Recall, F1-score, and Confusion Matrix.
8. Tuned the alpha parameter using GridSearchCV.
9. Tested the model on custom SMS messages.
"Why is Naive Bayes called 'Naive'?"

SOME MORE QUESTIONS-----

Naive Bayes assumes that all i
nput features are conditionally independent given the target class. Although this assumption is rarely true in real-world data, the algorithm often performs surprisingly well in practice.

How does Naive Bayes know which words indicate spam?

It does not rely on predefined spam keywords. During training, it learns the probability of each word occurring in each class (spam or not spam). During prediction, it combines these learned probabilities to estimate the most likely class.

Why are we using MultinomialNB instead of GaussianNB?

Answer:

Because after applying CountVectorizer, the features represent the frequency (counts) of words in each document. Multinomial Naive Bayes is specifically designed for count-based features, making it well-suited for text classification tasks.

Q. If your dataset is imbalanced, what's the first thing you should do?

I would first evaluate the baseline model using metrics such as Precision, Recall, F1-score, and the Confusion Matrix. If the minority class performance is poor, I would then consider techniques such as class weighting, oversampling, or undersampling.

Why did you use map() instead of LabelEncoder?


Since the target variable contains only two known categories (ham and spam), map() is simpler, more readable, and gives explicit control over the mapping. LabelEncoder is more useful when there are many categories or the mappings are not known beforehand.

What does CountVectorizer do?

CountVectorizer converts text documents into numerical feature vectors by creating a vocabulary of unique words and counting how many times each word appears in each document.

We should fit the CountVectorizer only on the training data because it learns the vocabulary from the text. If we fit it on the entire dataset before splitting, the vocabulary will include words from the test set, introducing data leakage and leading to an overly optimistic evaluation.

Why do we use fit_transform() on the training set but only transform() on the test set when using CountVectorizer?

Answer:

fit() learns the vocabulary from the training data. The same vocabulary is then used to transform the test data. This prevents the preprocessing step from learning information from unseen test data and avoids data leakage.

What does the shape (4459, 7700) represent after applying CountVectorizer?

Answer:

It means there are 4,459 training documents (SMS messages) and 7,700 unique words in the learned vocabulary. Each row represents one document, each column represents one word, and each cell contains the count of that word in the document.

Why does CountVectorizer return a sparse matrix instead of a NumPy array?

Answer:

Most documents contain only a small fraction of the total vocabulary, resulting in many zero values. A sparse matrix stores only the non-zero entries, making it significantly more memory-efficient.

Why are most values in the CountVectorizer output zero?

A strong answer:

Because each document contains only a small subset of the total vocabulary. Since most words do not appear in a given document, their counts are zero, resulting in a sparse feature matrix.

What does MultinomialNB.fit() learn?

A strong answer:

During training, Multinomial Naive Bayes learns the prior probability of each class and the probability of each word occurring within each class. These learned probabilities are then used to classify new documents.

Q. What is the difference between predict() and predict_proba()?

Answer:

predict() returns the final predicted class labels.
predict_proba() returns the probability of each class, allowing us to understand the model's confidence.

Why isn't accuracy a good metric for imbalanced datasets?

Accuracy can be misleading because a model may achieve a high accuracy simply by predicting the majority class. Therefore, for imbalanced datasets, we also evaluate Precision, Recall, F1-score, and the Confusion Matrix to understand the model's performance on the minority class.

Why do we use Laplace smoothing in Naive Bayes?

A strong answer:

Laplace smoothing prevents zero probabilities for unseen words. Without smoothing, if a word has never appeared in a particular class during training, its probability becomes zero, causing the entire posterior probability for that class to become zero. Laplace smoothing adds a small value (controlled by alpha) to every word count so that every word has a non-zero probability.

| Alpha            | Effect                                               |
| ---------------- | ---------------------------------------------------- |
| 0                | No smoothing                                         |
| 0.1              | Very little smoothing                                |
| 1                | Standard Laplace smoothing                           |
| Large (e.g., 10) | Heavy smoothing, probabilities become overly uniform |

Why can't we simply leave unseen words with probability zero?

Strong Answer:

Because Naive Bayes multiplies the probabilities of all features. If even one feature has a probability of zero for a class, the entire probability for that class becomes zero, regardless of the evidence from the other features. Laplace smoothing assigns a small non-zero probability to unseen words, allowing the model to make more robust predictions.

Q. Why can both very small and very large alpha values be problematic?


An alpha of 0 means no smoothing, so unseen words receive zero probability, which can make the entire class probability zero. A very large alpha applies excessive smoothing, making the word probabilities overly similar and reducing the model's ability to distinguish between informative and uninformative words. Therefore, we choose a moderate alpha value, often using GridSearchCV to find the best one.

Q. Scoring="f1" is a better choice than scoring="accuracy" for the moderately imbalanced dataset?

Since the dataset is imbalanced, accuracy can be misleading because a model may achieve high accuracy by correctly predicting the majority class while performing poorly on the minority class. F1-score combines both Precision and Recall, making it a more reliable evaluation metric for imbalanced classification problems.

Q. Why not optimize Recall instead of F1?


Because our objective is still to balance Precision and Recall. If we optimize only Recall, the model may classify too many legitimate messages as spam, increasing false positives. F1-score provides a balanced evaluation unless the business explicitly prioritizes one metric over the other.

-----> Even if the tuned model performs similarly to the baseline model, GridSearchCV is still valuable because it validates that the chosen hyperparameters perform consistently across multiple cross-validation folds. This gives greater confidence that the model will generalize well rather than relying on a single train-test split.

