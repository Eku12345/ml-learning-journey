

# Decision Tree Classifier - Bank Marketing Campaign Prediction

## Objective

Build a Decision Tree classifier to predict customer subscribe to a term deposit and understand how tree-based models make decisions.

---

## Skills Demonstrated

* Exploratory Data Analysis (EDA)
* Missing Value Handling
* Feature Selection
* Encoding Categorical Variables
* Decision Tree Classification
* Tree Visualization
* Feature Importance
* Hyperparameter Tuning
* Cross Validation
* Model Evaluation

---

## Dataset

Bank Marketing


## Initial Observations

- Dataset contains 11,162 records and 17 features.
- Target variable (deposit) is reasonably balanced.
- No missing (NaN) values are present.
- Some categorical features contain "unknown" values that may represent missing information.
- The `balance` feature contains noticeable outliers.
- `poutcome` has a large number of "unknown" values and requires further investigation.
- Several binary categorical variables (housing, loan, default) are suitable for encoding.

## Algorithm

* Decision Tree Classifier
- Baseline model
- Predictions
- Confusion Matrix
- Classification Report
- Feature Importance
- Tree Visualization
---

## Evaluation Metrics

* Accuracy

* Confusion Matrix


---

## Key Learnings

* How Decision Trees split data
* Gini Index vs Entropy
* Information Gain
* Overfitting and Underfitting
* Tree Pruning
* Feature Importance
* Why Decision Trees do not require feature scaling
