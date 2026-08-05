# Support Vector Machine (SVM) - Breast Cancer Classification

## Project Overview

This project demonstrates the implementation of a **Support Vector Machine (SVM)** classifier using the **Breast Cancer Wisconsin Dataset** from Scikit-learn.

The objective is to classify breast tumors as **Malignant** or **Benign** based on 30 numerical features extracted from digitized images of breast cell nuclei.

The project covers the complete machine learning workflow, including data preprocessing, feature scaling, model training, evaluation, and hyperparameter tuning.

---

## Dataset Information

- **Dataset:** Breast Cancer Wisconsin Dataset
- **Source:** Scikit-learn (`load_breast_cancer`)
- **Samples:** 569
- **Features:** 30 Numerical Features
- **Target Variable:**
  - 0 → Malignant
  - 1 → Benign

---

## Project Workflow

- Import Libraries
- Load Dataset
- Exploratory Data Analysis (EDA)
- Missing Value Analysis
- Train-Test Split
- Feature Scaling using StandardScaler
- Baseline SVM Model
- Model Evaluation
- Hyperparameter Tuning using GridSearchCV
- Model Comparison
- Conclusion

---

## Model Used

**Support Vector Classifier (SVC)**

Baseline Parameters:

- Kernel = RBF
- C = 1.0
- Gamma = scale

Best Parameters (GridSearchCV):

- Kernel = RBF
- C = 10
- Gamma = 0.01

---

## Model Performance

### Baseline Model

- Accuracy: **98.25%**

### Tuned Model

- Accuracy: **98.25%**

The tuned model selected different hyperparameters but produced similar performance on the test dataset, indicating that the baseline model was already close to optimal.

---

## Evaluation Metrics

The model was evaluated using:

- Accuracy
- Precision
- Recall
- F1 Score
- Confusion Matrix
- Classification Report

---

## Key Learnings

- Understanding Support Vector Machines
- Hyperplanes and Maximum Margin
- Support Vectors
- Hard Margin vs Soft Margin
- Kernel Trick
- Linear and RBF Kernels
- Importance of Feature Scaling
- Hyperparameter Tuning using GridSearchCV
- Cross Validation
- Model Evaluation

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

## Repository Structure

```text
06-support-vector-machine/
│
├── dataset/
├── notebooks/
│   └── svm_breast_cancer.ipynb
├── interview_questions.md
├── README.md
├── requirements.txt
└── .gitignore
```

---

## Future Improvements

- Compare SVM with Logistic Regression and Random Forest
- Explore additional kernels
- Perform advanced hyperparameter optimization
- Deploy the model using Flask or FastAPI

---

## Author

**Ekta Kumari**

Machine Learning Learning Journey