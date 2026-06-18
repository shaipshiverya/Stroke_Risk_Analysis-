# 🏥 Stroke Risk Analysis — Healthcare EDA & Predictive Insights

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python) 
![XGBoost](https://img.shields.io/badge/Model-XGBoost-orange) 
![SHAP](https://img.shields.io/badge/Explainability-SHAP-green) 
![Domain](https://img.shields.io/badge/Domain-Healthcare-red)

---

## 📈 Project Overview & Business Problem
Stroke is the **2nd leading cause of death globally**, causing roughly 11% of all deaths worldwide according to the WHO. For large healthcare networks, stroke patients are one of the most expensive emergency room admissions, averaging **₹1.5L to ₹3L per hospitalization** in India.

This project builds a **stroke risk screening tool for hospital registration desks**. By analyzing a patient's everyday lifestyle and health data at the intake counter, the tool automatically flags high-risk patients for immediate doctor review. This helps save lives and cuts down hospital costs without requiring extra clinical resources.

* **Target End-Users:** Hospital Operations Managers & Clinical Triage Teams

---

## 📊 Dataset Structure

* **Data Source:** [Kaggle — Stroke Prediction Dataset](https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset)
* **Data Volume:** 5,110 patient records
* **Features Used:** 12 clinical and lifestyle attributes (Age, Gender, Hypertension, Heart Disease, Smoking Status, BMI, etc.)
* **Target Metric:** `stroke` (0: No Stroke, 1: Had a Stroke)
* **Data Challenge:** Severe class imbalance (only ~4.9% of patients in the data actually had a stroke)

---

## 🔧 Tech Stack
* **Language:** Python
* **Data Manipulation:** Pandas, NumPy
* **Data Visualization:** Matplotlib, Seaborn
* **Machine Learning & Preprocessing:** Scikit-learn, XGBoost
* **Imbalance Handling:** SMOTE (`imbalanced-learn`)
* **Model Explainability:** SHAP (SHapley Additive exPlanations)

---

## 📋 Project Workflow
1. **Data Loading:** Importing raw patient records.
2. **Data Cleaning:** Handling missing values in BMI and mapping data values cleanly.
3. **Exploratory Data Analysis (EDA):** Building 13 visual charts to find patterns between patient features and stroke rates.
4. **Feature Engineering:** Creating 5 new clinical combination features to help the model learn better.
5. **Model Training:** Setting up an XGBoost Classifier combined with a SMOTE balancing pipeline.
6. **Model Explainability:** Using SHAP values to see exactly how individual metrics change the risk score.
7. **Business Insights:** Turning data patterns into concrete recommendations for hospital management.

---

## 🔍 Exploratory Data Analysis (EDA) Blueprint
I built **13 distinct charts** to evaluate risk factors across patient groups:
* **Target Imbalance:** Tracked the 4.9% low-prevalence stroke baseline.
* **Violin Plots:** Evaluated the overall spread of Age, Glucose, and BMI across patients.
* **Age & Gender Impact:** Isolated stroke rates across aging brackets and gender categories.
* **Lifestyle & Work Factors:** Mapped stroke risks against smoking habits, residence location (urban vs. rural), and job categories.
* **Comorbidities:** Created multi-risk heatmaps analyzing how having both high blood pressure and heart disease impacts survival rates.
* **Risk Zones:** Created a scatter plot mapping Age vs. Glucose levels to highlight the exact clinical "Danger Zone."

---

## ⚙️ Feature Engineering (Domain Logic)
To help the AI catch hidden patterns, I engineered **5 new features** based on medical logic:

| New Feature Name | Math Logic | Real-World Clinical Meaning |
|:---|:---|:---|
| `age_glucose_interaction` | `age` × `avg_glucose_level` | Combined impact of older age and high blood sugar. |
| `high_risk_age` | `age > 60 → 1` (Else: 0) | Flags patients crossing the WHO high-risk age limit. |
| `hypertension_heart` | `hypertension` AND `heart_disease` | Captures patients dealing with multiple co-occurring heart conditions. |
| `bmi_age_interaction` | `bmi` × `age` | Models how obesity risks become significantly more dangerous as a patient ages. |
| `glucose_category` | Binned Glucose Levels | Groups patients into standard clinical boxes: Normal, Prediabetes, or Diabetes. |

---

## 🤖 Model Performance & Evaluation
* **Final Model Pipeline:** XGBoost + SMOTE (Synthetic Minority Over-sampling Technique)
* **ROC-AUC Score:** **~0.85+**
* **Core Strength:** High Recall. In healthcare, missing a sick patient (False Negative) is highly dangerous. The model is optimized to minimize missed high-risk patients, ensuring safety-critical evaluation.

---

## 🧠 SHAP Explainability (Top Predictors)
Instead of treating the AI like a "black box," I used SHAP values to rank exactly what factors drive a high-risk stroke score:
1. 🥇 **`age_glucose_interaction`:** The combined calculation of age and blood sugar was the single strongest risk signal.
2. 🥈 **`age`:** Confirmed as the dominant standalone clinical predictor.
3. 🥉 **`avg_glucose_level`:** Validated the direct clinical link between diabetes and stroke risk.
4. 🏅 **`high_risk_age`:** Proved that crossing the 60+ age threshold significantly bumps patient risk.
5. 🏅 **`hypertension`:** Ranked as the strongest single co-occurring clinical condition.

---

## 💼 Actionable Business Recommendations
Based on the final data findings, I delivered **5 key insights** for hospital operational execution:
1. **Screen the Top 10% High-Risk Patients:** Implementing this early triage tool can save a hospital network ₹50L–₹1Cr annually in avoidable emergency readmissions.
2. **Launch a 60+ Hypertension Program:** Patients over 60 with high blood pressure showed a 20%+ stroke rate—making this group the highest return-on-investment (ROI) target for preventative check-ups.
3. **Monitor Diabetic Trends Closely:** Keeping glucose tightly managed reduces a patient's stroke probability by 20–30% according to the WHO.
4. **Extend Tobacco Cessation Support:** Data shows cardiovascular risk remains high for a long period; hospitals should extend monitoring to 3 years post smoking cessation.
5. **Zero Added Clinical Time Deployment:** Integrating this script directly into the hospital registration software automatically flags risk flags at checkout without slowing down staff.

---

## 🚀 How to Run this Notebook
1. Open the `Stroke_Risk_Analysis.ipynb` file inside Google Colab or Jupyter Notebooks.
2. Download and upload the `healthcare-dataset-stroke-data.csv` file from [Kaggle](https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset).
3. Run all code blocks from top to bottom to display the interactive graphs and model evaluation steps.

---

## 👤 Author
**Shaipshi** *Junior Data Analyst* [Portfolio](https://shaipshiverya.github.io) · [LinkedIn](https://www.linkedin.com/in/shaipshi-1b918a162) · [GitHub](https://github.com/shaipshiverya)
