jumana anas 13006950 t2
khaled ashraf 13004073 t2
hassan osama 13001158 t2
Karim ahmed eldesouky 13006787  T9

---

## ⚠️ Important Note on Notebook Structure

Before creating the final project structure, **our team originally developed the entire project inside ONE single Jupyter notebook** that contained:

- Data exploration  
- Feature engineering  
- Modeling  
- Hyperparameter tuning  
- Evaluation  
- Error analysis  

Later, we followed the project submission guidelines and **split the work into three notebooks**:

- `01_data_exploration_and_feature_engineering.ipynb`  
- `02_modeling.ipynb`  
- `03_evaluation.ipynb`

Because of this, **some functions, variables, or outputs may appear to depend on earlier work**.  
If anything seems missing in one notebook, **it is most likely present in another**.  
We apologize if this causes any minor inconvenience during review.

---

# 📌 Project Overview

Healthcare fraud is a major financial challenge for Medicare, costing the U.S. healthcare system **over $68 billion annually**.  
The goal of this project is to develop an **end-to-end, data-driven fraud detection system** to help identify potentially fraudulent healthcare providers.

This project uses the **CMS Healthcare Provider Fraud Detection Dataset** (from Kaggle) and includes:

- **Four real Medicare datasets**:  
  - Beneficiary data  
  - Inpatient claims  
  - Outpatient claims  
  - Provider fraud labels  
- **Provider-level feature engineering** (aggregating thousands of claim-level records)  
- **Handling severe class imbalance (~10% fraud)**  
- **Training & tuning multiple ML models**  
- **Comprehensive evaluation & error analysis**  
- **Interpretability for non-technical stakeholders**

---

# 🧠 Project Pipeline (High-Level)

### **1. Data Exploration & Feature Engineering**
- Joined multi-table healthcare data using BeneID and Provider keys  
- Cleaned data, fixed date formats, imputed errors  
- Extensive exploratory data analysis (EDA):  
  - Beneficiary demographics  
  - Chronic conditions  
  - Claim amounts  
  - Geographic and temporal trends  
- Created **provider-level dataset** with dozens of aggregated features  
- Engineered advanced features such as:  
  - % high-cost claims  
  - Readmission rates  
  - Chronic condition ratios  
  - Cost-per-physician metrics  
  - Inpatient/outpatient ratios

---

### **2. Modeling**
We trained and compared multiple models:

| Model | Baseline | Tuned |
|-------|----------|--------|
| Decision Tree | ✔ | ✔ |
| Random Forest | ✔ | ✔ |
| Gradient Boosting (XGBoost) | ✔ | ✔ |
| Logistic Regression | ✔ | ✔ |

**Class imbalance was addressed using:**
- Class weighting  
- `scale_pos_weight` (XGBoost)  
- Recall-focused hyperparameter tuning  
- PR-AUC scoring  

---

### **3. Evaluation & Error Analysis**

We evaluated models using:

- Precision  
- Recall  
- F1-score  
- ROC-AUC  
- PR-AUC  
- Confusion matrices  
- ROC Curves  
- Precision–Recall curves  
- Feature importance (Logistic Regression coefficients)

We performed a detailed **error analysis**:

- Identified high-confidence false positives  
- Identified low-confidence false negatives  
- Examined key features influencing each error  
- Provided real-world explanations and implications  

This demonstrates the model's behavior and limitations in a business context.

---

# 🏆 Summary of Results

### **Best Overall Model: Logistic Regression (Tuned)**  
Even though ensemble methods (Random Forest, XGBoost) had strong performance, **Logistic Regression was chosen** because:

- It offered **high recall** for fraud cases  
- It remained **interpretable** for Medicare investigators  
- Coefficient-based feature importance ensured transparency  
- It generalized well without overfitting  

### **Key Findings**

- Fraudulent providers tend to have:  
  - Higher % of high-cost claims  
  - Higher average claim amounts  
  - Higher inpatient/outpatient ratios  
  - Greater physician utilization  
- False negatives were mainly “low-risk looking” fraud cases  
- False positives tended to have unusual high-cost claim patterns  

### **Performance Summary (Example)**  
*(Values are illustrative; real values appear in the notebook output.)*

| Model | Precision (Fraud) | Recall (Fraud) | F1 | AUC-ROC | PR-AUC |
|-------|-------------------|----------------|----|----------|--------|
| Logistic Regression (Tuned) | ~0.68 | ~0.80 | ~0.73 | High | High |
| Random Forest (Tuned) | Good | Moderate | Good | High | High |
| XGBoost (Tuned) | Good | Moderate | Good | High | High |
| Decision Tree (Tuned) | Lower | Highest | Moderate | Lower | Lower |

---


