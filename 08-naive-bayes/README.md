# SMS Spam Detection using Multinomial Naive Bayes

## Project Overview

This project builds a Machine Learning model to classify SMS messages as **Spam** or **Ham (Not Spam)** using the **Multinomial Naive Bayes** algorithm.

Since machine learning models cannot understand raw text, the messages were first converted into numerical feature vectors using **CountVectorizer**. The model was then trained, evaluated, and optimized using GridSearchCV.

This project demonstrates one of the most common real-world applications of Naive Bayes: **text classification**.

---

## Problem Statement

The objective is to automatically classify incoming SMS messages into:

- Ham (Legitimate Message)
- Spam (Unwanted Message)

Such systems are commonly used in:

- Email Spam Detection
- SMS Filtering
- Customer Support Ticket Classification
- News Categorization
- Sentiment Analysis

---

## Dataset

**Dataset:** SMS Spam Collection Dataset

- Total Messages: 5,574
- Features:
  - `message`
- Target:
  - `label`
    - 0 → Ham
    - 1 → Spam

The dataset contains no missing values and is moderately imbalanced.

---

## Project Workflow

1. Load the dataset
2. Perform Exploratory Data Analysis (EDA)
3. Encode target labels
4. Split data into training and testing sets
5. Convert text into numerical features using CountVectorizer
6. Train a Multinomial Naive Bayes classifier
7. Evaluate model performance
8. Perform hyperparameter tuning using GridSearchCV
9. Test the model on custom SMS messages

---

## Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

---

## Model Performance

### Baseline Model

- Accuracy: **98.74%**
- Precision (Spam): **0.99**
- Recall (Spam): **0.92**
- F1-score (Spam): **0.95**

### Hyperparameter Tuning

GridSearchCV was used to tune the Laplace smoothing parameter (`alpha`).

Best Parameters:

```python
{'alpha': 1.0}
```

The tuned model achieved performance comparable to the baseline model, confirming that the default smoothing parameter was already optimal for this dataset.

---

## Key Learnings

- Understood the intuition behind Bayes' Theorem.
- Learned why Naive Bayes is called "Naive".
- Learned how CountVectorizer converts text into numerical feature vectors.
- Understood sparse matrices and why they are memory efficient.
- Learned why CountVectorizer is fitted only on training data.
- Understood the Zero Frequency Problem.
- Learned how Laplace Smoothing prevents zero probabilities.
- Learned the role of the `alpha` hyperparameter.
- Learned why F1-score is preferred over accuracy for imbalanced datasets.
- Learned how GridSearchCV validates hyperparameters.

---

## Future Improvements

Possible improvements include:

- TF-IDF Vectorization
- Stopword Removal
- Lemmatization
- Stemming
- N-gram Features
- Comparing with Logistic Regression
- Comparing different Naive Bayes variants

---

## Project Structure

```
08-naive-bayes/
│
├── dataset/
│   └── SMSSpamCollection
│
├── notebooks/
│   └── naive_bayes_sms_spam.ipynb
│
├── README.md
├── interview_questions.md
├── requirements.txt
└── .gitignore
```

---

## Conclusion

This project demonstrates how the Multinomial Naive Bayes algorithm efficiently performs text classification by learning word probabilities from training data. Using CountVectorizer and Laplace Smoothing, the model achieved excellent performance in detecting spam messages while maintaining high precision and recall.