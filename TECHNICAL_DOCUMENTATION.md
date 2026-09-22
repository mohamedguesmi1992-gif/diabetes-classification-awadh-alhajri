# Technical Documentation

## 1. Problem definition

The notebook implements a binary classification task:

- Target `Diabetes = 1`: diabetes class
- Target `Diabetes = 0`: non-diabetes class

The project is educational and uses synthetic data. It is not a clinical diagnostic system.

## 2. Raw features

The raw dataset contains:

- `PatientID`
- `Age`
- `Gender`
- `BMI`
- `Glucose`
- `BloodPressure`
- `Insulin`
- `FamilyHistory`
- `SmokingStatus`
- `ActivityLevel`
- `Diabetes`

`PatientID` is removed before model training because it is an identifier rather than a predictive clinical feature.

## 3. Data-quality handling

The executed notebook records:

- 1,545 raw rows
- 45 duplicated rows
- 1,500 rows after duplicate removal
- Missing values in BMI, Insulin, and SmokingStatus
- Hidden missing values represented by zero in Glucose and BloodPressure
- Inconsistent Gender values such as `Male`, `male`, `M`, `Female`, `female`, `F`, and trailing whitespace

Processing steps:

1. Replace zero values in Glucose and BloodPressure with `NaN`.
2. Impute BMI, Glucose, BloodPressure, and Insulin with each column's median.
3. Impute SmokingStatus with its mode.
4. Remove duplicate rows.
5. Strip whitespace and normalize Gender labels.
6. Drop PatientID.

After imputation, the notebook reports zero remaining missing values.

## 4. Encoding

- Gender: binary mapping
- FamilyHistory: binary mapping
- ActivityLevel: ordinal mapping (`Low=0`, `Medium=1`, `High=2`)
- SmokingStatus: one-hot encoding

## 5. Train/test methodology

The cleaned dataset is separated into features and target.

A stratified split is used:

- 80% training: 1,200 rows
- 20% testing: 300 rows
- `random_state=42`
- `stratify=y`

Continuous numerical variables are standardized with `StandardScaler`. The scaler is fit on the training set only and then applied to both training and test sets.

## 6. Models

### XGBoost

Configuration used in the notebook:

- `n_estimators=300`
- `learning_rate=0.05`
- `max_depth=4`
- `subsample=0.8`
- `colsample_bytree=0.8`
- `random_state=42`

### LightGBM

Configuration used in the notebook:

- `n_estimators=300`
- `learning_rate=0.05`
- `num_leaves=15`
- `min_child_samples=20`
- `subsample=0.8`
- `subsample_freq=1`
- `colsample_bytree=0.8`
- `random_state=42`

## 7. Evaluation

The project evaluates both classifiers using:

- Confusion matrix
- Accuracy
- Precision
- Recall
- F1 Score
- ROC-AUC
- PR-AUC
- ROC curve
- Precision-Recall curve

Observed test-set results:

| Model | Accuracy | Precision | Recall | F1 | ROC-AUC | PR-AUC |
|---|---:|---:|---:|---:|---:|---:|
| XGBoost | 0.767 | 0.679 | 0.541 | 0.602 | 0.805 | 0.713 |
| LightGBM | 0.763 | 0.667 | 0.551 | 0.603 | 0.803 | 0.700 |

These are the notebook's observed educational results, not external clinical validation.

## 8. Explainability

The notebook uses `shap.TreeExplainer` on the fitted XGBoost model.

It includes:

- Global feature-importance bar plot
- SHAP beeswarm plot showing direction and magnitude
- Local waterfall plot for one high-risk test example

The explainer is configured to explain model output in probability space using a 200-row training background sample.

## 9. Reproducibility

Important deterministic settings include:

- Synthetic data generator seed: `7`
- Train/test split seed: `42`
- XGBoost seed: `42`
- LightGBM seed: `42`
- Exercise sample seed: `119`
- SHAP background sample seed: `0`

## 10. Limitations

- The data is synthetic and created inside the notebook.
- The project is a classroom demonstration, not a medically validated model.
- No external hospital dataset or prospective clinical evaluation is used.
- Model performance is based on one fixed synthetic data-generation process and one held-out split.
- The two models use fixed hyperparameters rather than a documented hyperparameter-search procedure.
- Metrics should therefore be interpreted only in the context of this educational exercise.

## 11. Main implementation references

- scikit-learn: https://scikit-learn.org/stable/
- XGBoost: https://xgboost.readthedocs.io/en/stable/python/
- LightGBM: https://lightgbm.readthedocs.io/en/latest/Python-API.html
- SHAP: https://shap.readthedocs.io/en/latest/
