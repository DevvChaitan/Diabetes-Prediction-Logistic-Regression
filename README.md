# Diabetes Prediction using Logistic Regression
**Unlox AI & ML Cohort — Minor Project 3**  
**Author:** Chaitanya Rao Solapurkar  
**Student ID:** 20522493  
**Date:** October 2026  

---

## Project Overview
This repository contains an end-to-end binary classification project predicting diabetes status (`Outcome: 0 = No diabetes, 1 = Diabetes`) using the Pima Indians Diabetes Database from Kaggle (`diabetes.csv`).

Because this model functions as a diagnostic screening tool, **Recall (Sensitivity)** was prioritized alongside **ROC-AUC** to minimize dangerous False Negatives (missed diabetic cases).

---

## Repository Contents
- **`Chaitanya_Rao_Solapurkar_Diabetes_Prediction.ipynb`**: Complete Jupyter Notebook containing data loading, data hygiene auditing, train-test splitting, median imputation, standardization, balanced Logistic Regression training, test evaluation, and coefficient/odds-ratio interpretation. Fully executed with all outputs and plots visible.
- **`Chaitanya_Rao_Solapurkar_Logistic_Regression_Report.pdf`**: 4-page formal project report formatted with the official Unlox template, complete evaluation metrics, confusion matrix, embedded diagnostic charts, and clinical conclusions.

---

## Workflow Summary
1. **Data Inspection & Hygiene:** Identified physiologically impossible zero values in clinical variables (`Glucose`, `BloodPressure`, `SkinThickness`, `Insulin`, `BMI`) and converted them to `NaN`.
2. **Leakage-Free Splitting:** Partitioned the dataset into 80% train (614 samples) and 20% test (154 samples) with stratification prior to preprocessing.
3. **Preprocessing:** Learned median imputation and standard scaling solely on the training data and transformed the test set.
4. **Model Training:** Trained a Logistic Regression classifier with `class_weight='balanced'` to offset class imbalance.
5. **Evaluation:** Assessed discrimination and classification performance on the test set.

---

## Key Results

### Evaluation Metrics (Test Set, N = 154)
| Metric | Score | Clinical Meaning |
| :--- | :---: | :--- |
| **Accuracy** | **0.734** | Overall correct classifications |
| **Precision** | **0.603** | Reliability of positive predictions |
| **Recall (Sensitivity)** | **0.704** | Detection rate of actual diabetic patients (38 / 54 detected) |
| **F1-Score** | **0.650** | Harmonic balance between precision and recall |
| **ROC-AUC** | **0.813** | Overall class-separation capability |

### Confusion Matrix
| | Predicted: No Diabetes (0) | Predicted: Diabetes (1) |
| :--- | :---: | :---: |
| **Actual: No Diabetes (0)** | **TN = 75** (48.7%) | **FP = 25** (16.2%) |
| **Actual: Diabetes (1)** | **FN = 16** (10.4%) | **TP = 38** (24.7%) |

### Top Risk Factors (Odds Ratios)
- **Glucose ($\beta = +1.183$, $\text{OR} = 3.27\times$):** Dominant predictor; odds of diabetes more than triple per 1-SD increase.
- **BMI ($\beta = +0.710$, $\text{OR} = 2.03\times$):** Second strongest risk factor; odds double per 1-SD increase.
- **Pregnancies ($\text{OR} = 1.45\times$) & Pedigree Function ($\text{OR} = 1.33\times$):** Noticeable positive contributors.

---

## How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/DevvChaitan/Diabetes-Prediction-Logistic-Regression.git
   cd Diabetes-Prediction-Logistic-Regression
   ```
2. Install dependencies:
   ```bash
   pip install numpy pandas scikit-learn matplotlib seaborn
   ```
3. Open and run the notebook:
   ```bash
   jupyter notebook Chaitanya_Rao_Solapurkar_Diabetes_Prediction.ipynb
   ```
