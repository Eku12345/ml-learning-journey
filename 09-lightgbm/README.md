# LightGBM — Adult Income Classification

## Project Overview

This project uses **LightGBM** to predict whether an individual's annual income exceeds $50,000 using demographic and employment-related features from the UCI Adult Census Income dataset.

The project covers data inspection, preprocessing, categorical feature handling, model training, hyperparameter tuning, early stopping, feature importance, and error analysis.

## Dataset

- **Source:** UCI Adult / Census Income dataset
- **Training file:** `dataset/adult.data`
- **Task:** Binary classification
- **Target:** `income`
  - `<=50K`
  - `>50K`

The dataset contains demographic, education, employment, and financial-related attributes.

## Project Structure

```text
09-lightgbm/
├── dataset/
├── notebooks/
│   └── lightgbm_adult_income.ipynb
├── .gitignore
├── README.md
├── interview_questions.md
└── requirements.txt
```

## Data Preprocessing

The following steps were performed after inspecting the raw data:

1. Assigned descriptive column names.
2. Checked missing values, duplicates, unique values, target distribution, and numerical ranges.
3. Removed leading and trailing whitespace from categorical values.
4. Replaced `?` missing-value markers with `NaN`, then filled missing categorical values with `Unknown`.
5. Removed 24 duplicate rows.
6. Dropped `education` because it mapped one-to-one to `education-num`; retained the numerical education level.
7. Converted categorical predictors to pandas `category` dtype for LightGBM's categorical feature handling.
8. Separated features and target.
9. Split the data into training and test sets using an 80:20 split, `random_state=42`, and stratification.

The resulting dataset contained 32,537 rows and 13 predictor features.

## Model

The baseline used `LGBMClassifier` with:

- `random_state=42`
- `n_jobs=-1`
- Default LightGBM boosting and tree parameters

No feature scaling was applied because tree-based models generally do not require it.

## Baseline Results

| Metric | `<=50K` | `>50K` |
|---|---:|---:|
| Precision | 0.90 | 0.79 |
| Recall | 0.94 | 0.68 |
| F1-score | 0.92 | 0.73 |

- **Accuracy:** 87.88%
- **Confusion matrix:**

```text
[[4651  289]
 [ 500 1068]]
```

The model performed better on the `<=50K` class than on the `>50K` class. Recall for the higher-income class was 0.68, indicating that some individuals earning above $50K were incorrectly classified.

## Hyperparameter Tuning

`GridSearchCV` was used with five-fold cross-validation and F1-score for the `>50K` class as the scoring metric.

Parameters tested:

- `num_leaves`: 15, 31, 63
- `learning_rate`: 0.05, 0.1
- `n_estimators`: 100, 200

The best configuration within this grid was:

```python
{
    "learning_rate": 0.1,
    "n_estimators": 100,
    "num_leaves": 31
}
```

Best cross-validation F1-score: approximately **0.7114**.

The tuned model produced the same test metrics as the baseline, so the tested grid did not improve test performance.

## Early Stopping Experiment

An additional experiment used a validation set, a learning rate of 0.05, and a maximum of 500 estimators. Early stopping selected iteration 168.

This experiment achieved approximately 87.48% test accuracy and an F1-score of approximately 0.72 for `>50K`. It did not outperform the baseline. Because other hyperparameters also changed, this experiment does not isolate the effect of early stopping alone.

## Feature Importance

The model's split-based feature importance ranked `age`, `fnlwgt`, `hours-per-week`, `capital-gain`, and `capital-loss` among the leading features.

These values measure how often features were used for splits in the model. They do not establish causation or prove that a feature has a real-world effect on income.

## Error Analysis

The baseline test predictions produced:

- **False negatives:** 500
- **False positives:** 289

The mean predicted probability of `>50K` was approximately:

- False negatives: 0.286
- False positives: 0.647

This indicates that some errors were made with substantial model confidence, rather than all errors being cases close to the 0.50 decision threshold.

## Key Learnings

- How LightGBM's leaf-wise tree growth differs from level-wise growth.
- How native categorical feature handling works.
- How to tune `num_leaves`, `learning_rate`, and `n_estimators` with cross-validation.
- Why accuracy alone is insufficient for imbalanced classification.
- How confusion matrices, class-specific metrics, predicted probabilities, and feature importance help interpret model behavior.
- Why tuning and early stopping must be evaluated on held-out data.

## How to Run

1. Create and activate a Python environment.
2. Install the dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Start Jupyter:

   ```bash
   jupyter notebook
   ```

4. Open `notebooks/lightgbm_adult_income.ipynb` and run the notebook cells in order.

The notebook was developed and tested with Python 3.11 and LightGBM 3.3.5.