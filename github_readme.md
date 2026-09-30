# 🫀 UCI Heart Disease Dataset - Data Gathering, Cleaning & Preprocessing

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Cleaning-150458?style=for-the-badge&logo=pandas)
![Status](https://img.shields.io/badge/Task-Completed-success?style=for-the-badge)
![Internship](https://img.shields.io/badge/YuvaIntern-Data%20Science-orange?style=for-the-badge)

## 📌 Executive Summary

This repository contains the official submission for **Week 1 Task: Data Gathering, Cleaning, and Preprocessing** as part of the **YuvaIntern Data Science Internship Program**. 

The goal of this project is to raw clinical diagnostic patient records from the **UCI Heart Disease Dataset**, identify structural anomalies, clean impossible biological values, treat extreme outliers, and transform features into a standardized format ready for predictive machine learning workflows.

---

## 📂 Repository Structure

```text
├── README.md                                  <- Project overview and setup instructions
├── heart.csv                                  <- Raw dataset downloaded from UCI / Kaggle
├── cleaned_heart_disease_dataset.csv          <- Final processed dataset ready for ML
├── Heart_Disease_Data_Cleaning.ipynb         <- Jupyter / Google Colab Notebook with executable code
└── Data_Cleaning_Report_YuvaIntern.pdf        <- Comprehensive 3-page Executive PDF Report
```

---

## 📊 Dataset Metadata

- **Dataset Name:** UCI Heart Disease Prediction Dataset
- **Source:** [Kaggle / UCI Machine Learning Repository](https://www.kaggle.com/datasets/redwansorowar/uci-heart-disease-data)
- **Original Dimensions:** 303 rows × 14 columns
- **Final Dimensions:** 302 rows × 14 columns *(1 duplicate removed)*

### Primary Attributes:
1. `age`: Patient age in years
2. `sex`: Gender (1 = Male, 0 = Female)
3. `cp`: Chest pain type (0 = Typical Angina, 1 = Atypical Angina, 2 = Non-anginal, 3 = Asymptomatic)
4. `trestbps`: Resting blood pressure (in mm Hg)
5. `chol`: Serum cholesterol (in mg/dl)
6. `fbs`: Fasting blood sugar (> 120 mg/dl; 1 = True, 0 = False)
7. `restecg`: Resting electrocardiographic results
8. `thalach`: Maximum heart rate achieved
9. `exang`: Exercise-induced angina (1 = Yes, 0 = No)
10. `oldpeak`: ST depression induced by exercise relative to rest
11. `slope`: Slope of peak exercise ST segment
12. `ca`: Number of major vessels (0–3) colored by fluoroscopy
13. `thal`: Thalassemia classification
14. `target`: Diagnostic status (0 = Absence of Heart Disease, 1 = Presence)

---

## 🛠️ Data Cleaning Methodology

| Anomaly Identified | Affected Column(s) | Action Taken | Rationale |
| :--- | :--- | :--- | :--- |
| **Duplicate Entries** | Entire Row | Dropped 1 duplicate row | Prevents data leakage during model training. |
| **Impossible Zeroes** | `chol`, `trestbps` | Replaced 0s with Median | $0\text{ mg/dl}$ cholesterol is medically impossible; median imputation avoids outlier skew. |
| **Missing Categories**| `ca`, `thal` | Mode Imputation | Assigns the most frequent valid categorical diagnostic state. |
| **Extreme Outliers** | `chol`, `trestbps`, `thalach` | $1.5 \times \text{IQR}$ Winsorization Capping | Restricts boundary extremes without losing data points. |
| **Type Alignment** | `sex`, `cp`, `target` | Explicit cast to `int64` | Standardizes categorical discrete variables. |
| **Feature Scaling** | Continuous Features | `StandardScaler` ($\mu=0, \sigma=1$) | Equalizes feature variance for distance-based ML models. |

---

## 🚀 How to Run the Code

### Option 1: Google Colab (Recommended)
1. Open [Google Colab](https://colab.research.google.com).
2. Upload `Heart_Disease_Data_Cleaning.ipynb`.
3. Upload `heart.csv` into Colab's session storage folder (left menu 📁).
4. Click **Runtime > Run All**.

### Option 2: Local Jupyter Notebook
1. Clone this repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/YuvaIntern-Task1-Data-Cleaning.git
   cd YuvaIntern-Task1-Data-Cleaning
   ```
2. Install dependencies:
   ```bash
   pip install pandas numpy scikit-learn
   ```
3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook Heart_Disease_Data_Cleaning.ipynb
   ```

---

## 📈 Key Findings & Comparison

| Metric | Raw Dataset | Cleaned Dataset |
| :--- | :--- | :--- |
| **Total Rows** | 303 | 302 |
| **Missing / Invalid Values** | 2 Biological Zeroes | 0 |
| **Outlier Values (>1.5 IQR)** | 15 Extreme Values | 0 (Capped) |
| **Data Format** | Unscaled / Mixed | Standardized & Scaled |

---

## 👤 Author Information

- **Author:** [Your Name]
- **Role:** Data Science Intern
- **Organization:** YuvaIntern
- **Task:** Deliverable 1 - Data Gathering, Cleaning & Preprocessing