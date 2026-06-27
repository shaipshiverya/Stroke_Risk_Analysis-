# 🏥 Stroke Risk Analysis

A beginner-level healthcare data analytics project exploring stroke risk factors using patient data.

---

## 📌 Project Overview

Stroke is the 2nd leading cause of death globally[cite: 1]. This project analyzes a dataset of 5,110 patients to identify key risk factors and build a simple prediction model — helping hospital teams understand who is most at risk[cite: 1].

**Domain:** Healthcare[cite: 1]  
**Tools:** Python, pandas, matplotlib, seaborn, scikit-learn[cite: 1]  
**Dataset:** [Stroke Prediction Dataset — Kaggle (fedesoriano)](https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset)[cite: 1]

---

## 📂 Dataset

| Feature | Description |
| :--- | :--- |
| age | Patient age[cite: 1] |
| gender | Male / Female[cite: 1] |
| hypertension | 0 = No, 1 = Yes[cite: 1] |
| heart_disease | 0 = No, 1 = Yes[cite: 1] |
| ever_married | Yes / No[cite: 1] |
| work_type | Type of employment[cite: 1] |
| Residence_type | Urban / Rural[cite: 1] |
| avg_glucose_level | Average blood glucose (mg/dL)[cite: 1] |
| bmi | Body Mass Index[cite: 1] |
| smoking_status | Never / Formerly / Smokes / Unknown[cite: 1] |
| stroke | 0 = No Stroke, 1 = Stroke (Target)[cite: 1] |

---

## 🚧 Challenges Faced

*   **Dataset column confusion** — Some column names were unclear at first (`Residence_type` capitalization, `smoking_status` categories)[cite: 1]. Had to carefully check `df.info()` and `df.unique()` outputs before building any plots[cite: 1].
*   **Class imbalance** — Only ~4.9% of patients had a stroke[cite: 1]. A naive model would just predict "no stroke" every time and still look accurate[cite: 1]. Used `class_weight='balanced'` in Random Forest to handle this[cite: 1].
*   **BMI missing values** — 201 records had missing BMI[cite: 1]. Filled with median instead of mean since BMI has outliers[cite: 1].
*   **Wrong analysis approach** — Initial version was too ML-heavy (XGBoost, SHAP, feature engineering)[cite: 1]. Rebuilt from scratch with a focus on EDA and simple storytelling[cite: 1].

---

## 📊 Key Findings

1. Patients **60+** have a 10x higher stroke rate than those under 40[cite: 1].
2. **Hypertension** patients experience a 3x higher stroke rate[cite: 1].
3. **Heart disease** patients experience a 4x higher stroke rate[cite: 1].
4. **High glucose** (>125 mg/dL) is strongly linked to stroke risk[cite: 1].
5. **Formerly smoking** patients carry the highest stroke rate among smoking categories[cite: 1].

---

## 🧠 Model

| Detail | Value |
| :--- | :--- |
| **Algorithm** | Random Forest Classifier[cite: 1] |
| **Train/Test Split** | 80% / 20%[cite: 1] |
| **Class Handling** | class_weight='balanced'[cite: 1] |

---

## 📁 Project Structure

```text
Stroke_Risk_Analysis/
│
├── Stroke_Risk_Analysis_v4.ipynb   # Main notebook
├── healthcare-dataset-stroke-data.csv
└── README.md
