# K-Nearest Neighbors (KNN) - Breast Cancer Classification

## Project Overview

This project demonstrates the implementation of the K-Nearest Neighbors (KNN) algorithm using the Breast Cancer Wisconsin dataset from Scikit-learn. The objective is to classify tumors as **Malignant** or **Benign** and understand how different hyperparameters affect model performance.

---

## Dataset

- **Dataset:** Breast Cancer Wisconsin Dataset
- **Source:** Scikit-learn
- **Total Samples:** 569
- **Features:** 30 numerical features
- **Target Classes:**
  - Malignant (0)
  - Benign (1)

---

## Project Workflow

1. Load the dataset
2. Perform basic exploratory data analysis
3. Split the dataset into training and testing sets
4. Apply feature scaling using StandardScaler
5. Train a baseline KNN classifier
6. Evaluate model performance
7. Perform hyperparameter tuning using GridSearchCV
8. Compare baseline and tuned models

---

## Best Hyperparameters

| Parameter | Value |
|-----------|-------|
| n_neighbors | 3 |
| weights | uniform |
| metric | euclidean |

---

## Results

| Model | Accuracy |
|--------|----------|
| Baseline KNN | 95.61% |
| Tuned KNN | 98.25% |

---

## Key Learnings

- KNN is a distance-based supervised learning algorithm.
- Feature scaling is essential for KNN.
- The choice of K significantly impacts model performance.
- GridSearchCV helps identify optimal hyperparameters using cross-validation.
- Evaluation should include Precision, Recall, F1-score, and the Confusion Matrix instead of relying solely on Accuracy.

---

## Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn

---

## Author

Ekta Kumari