# Diabetes Prediction: From Raw Data to Evaluation

**Student:** Awadh Mohammed Alhajri  
**Training Context:** SDAIA Academy training project  
**Academy:** [SDAIA Academy](https://github.com/SDAIAAcademy)  
**Tag:** #SDAIAAcademy

## Project Overview

This project demonstrates a complete educational machine-learning workflow for binary diabetes classification, starting from raw-data inspection and cleaning and continuing through model training, evaluation, comparison, and explainability.

The workflow includes:

- Exploratory data analysis
- Missing-value handling and data cleaning
- Categorical encoding
- Feature correlation analysis
- Stratified train/test splitting
- Feature standardization
- XGBoost classification
- LightGBM classification
- Confusion-matrix analysis
- Accuracy, Precision, Recall, F1, ROC-AUC, and PR-AUC
- ROC and Precision-Recall curves
- SHAP global and local explanations

> **Important:** The dataset used in this project is synthetic and educational. It does not contain real patient records and is not intended for clinical diagnosis or medical decision-making.

## Dataset

The notebook generates the synthetic dataset deterministically using a fixed random seed.

- Raw rows: **1,545**
- Raw columns: **11**
- Duplicate rows removed: **45**
- Final cleaned rows: **1,500**
- Missing values after imputation: **0**
- Training rows: **1,200**
- Test rows: **300**

## Model Results

| Model | Accuracy | Precision | Recall | F1 | ROC-AUC | PR-AUC |
|---|---:|---:|---:|---:|---:|---:|
| XGBoost | 0.767 | 0.679 | 0.541 | 0.602 | 0.805 | 0.713 |
| LightGBM | 0.763 | 0.667 | 0.551 | 0.603 | 0.803 | 0.700 |

The repository also includes the exported model metrics and the worked 20-patient classification-metrics exercise.

## Repository Contents

- `Awadh_Mohammed_Alhajri_Diabetes_Classification.ipynb` — complete executed notebook
- `diabetes_raw.csv` — synthetic dataset used in the notebook
- `TECHNICAL_DOCUMENTATION.md` — technical methodology and implementation notes
- `model_metrics.csv` — model evaluation results
- `exercise_metrics.csv` — worked classification-metrics exercise
- `requirements.txt` — Python dependencies
- `.gitignore` — excludes local environments and temporary files

## How to Run

1. Clone the repository:

```bash
git clone https://github.com/mohamedguesmi1992-gif/diabetes-classification-awadh-alhajri.git
cd diabetes-classification-awadh-alhajri
```

2. Create and activate a Python virtual environment.

3. Install the required packages:

```bash
python -m pip install -r requirements.txt
```

4. Start Jupyter:

```bash
jupyter notebook
```

5. Open:

```text
Awadh_Mohammed_Alhajri_Diabetes_Classification.ipynb
```

## Technical Documentation

See [TECHNICAL_DOCUMENTATION.md](TECHNICAL_DOCUMENTATION.md) for the preprocessing decisions, model settings, evaluation methodology, explainability workflow, reproducibility notes, and project limitations.

## Version Control

The project is maintained in Git with meaningful commits so that changes to code, documentation, data, and results can be tracked clearly.

## References

- [scikit-learn](https://scikit-learn.org/stable/)
- [XGBoost](https://xgboost.readthedocs.io/en/stable/)
- [LightGBM](https://lightgbm.readthedocs.io/en/latest/)
- [SHAP](https://shap.readthedocs.io/en/latest/)
- [SDAIA Academy on GitHub](https://github.com/SDAIAAcademy)

## Acknowledgement

This project was prepared in the context of SDAIA Academy training activities.

#SDAIAAcademy
