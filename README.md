# Project_ASB

readme_content = """
# 🛡️ Fraud Detection in Banking Transactions using Machine Learning

This project presents a complete fraud detection pipeline built using R and machine learning to support ASB Bank's effort to combat financial fraud. Leveraging a synthetically generated dataset of 500,000 transaction records, we used advanced modeling, statistical validation, and business insights to identify patterns of fraudulent activity and recommend operational changes.

---

## 📊 Project Overview

ASB Bank is facing a growing challenge in adapting to evolving fraudulent behaviors. Our team analyzed transaction records from May to July 2024 and developed a predictive model capable of detecting fraud with a strong balance between accuracy and recall, focusing on minimizing false negatives.

---

## 📁 Dataset Description

- **Size**: 500,000 transactions
- **Period**: May–July 2024
- **Source**: Synthetic banking data (simulated ASB transactions)
- **Target Variable**: `FraudLabel` (1 = Fraud, 0 = Not Fraud)
- **Raw Attributes**: Transaction date, amount, type, location, balance, joint flag, device/agent, merchant class, and customer age.

---

## 🧱 Feature Engineering

We created additional features to capture behavioral and temporal fraud patterns:
- `hour`, `weekday`, `weekend_flag`, `time_flag`, `Time_of_Day`
- `agent_cat` (browser/device)
- `balance_cat`, `joint_cat`
- `age_group`
- `trans_cat`: Combined transaction type and channel
- One-hot encoding was applied for categorical features.

---

## 🧪 Feature Selection (Statistical Validation)

We conducted **Chi-square and t-tests** to validate variable importance before modeling:

- Categorical Variables (Chi-square): `agent_cat`, `joint_flag`, `trans_cat`, `hour`, `weekday`, `TransactionType`, etc. (all significant)
- Continuous Variables (t-test): `transaction amount`, `balance`, `age` (all highly significant, p < 0.05)

---

## 🤖 Modeling Approach

### Models Compared:
- LightGBM ✅ *(Best Performer)*
- XGBoost
- Random Forest
- Logistic Regression
- KNN

### Evaluation Metrics:
- Accuracy
- Sensitivity (Recall)
- AUC (Area Under ROC Curve)
- Precision (PPV)
- Specificity

**LightGBM** outperformed others with:
- Accuracy: 78.4%
- AUC: **87.1%**
- Sensitivity: **75.9%**
- PPV: 8.3% (affected by class imbalance)

---

## 📉 Confusion Matrix (LightGBM)

|                | Predicted Fraud | Predicted Non-Fraud |
|----------------|------------------|----------------------|
| Actual Fraud   | **680**          | 2,627                |
| Actual Non-Fraud | 2,137          | 95,909               |

> While PPV was low due to data imbalance, LightGBM captured the highest number of fraud cases with the lowest false negative rate.

---

## 🌟 Feature Importance (Top Predictors)

1. `TransactionAmount`
2. `Time_of_Day`
3. `Agent`
4. `Weekday`
5. `Age`

These confirm that fraud detection is highly influenced by **when**, **how**, and **by whom** the transaction is conducted.

---

## 🧠 Business Recommendations

1. **Enhanced Protection for Elderly Customers**
   - Implement OTPs and limit late-night access for customers 65+

2. **Customer Education & Fraud Alerts**
   - Share summary fraud reports mid-week, especially on Wednesdays

3. **Geo-Fencing & Device Profiling**
   - Use location + agent history to detect anomaly patterns

4. **Smart Flagging Instead of Blocking**
   - Flag transactions for review instead of blanket declines due to low PPV

---

## 📂 Files Included

- `704_Group_26_R_Code.qmd` – Full analysis with reproducible code
- `Poster_Final_Group26.pdf` – A2 academic poster for stakeholder communication
- `README.md` – Project documentation

---

## 👥 Contributors

- **Md Rajib Hossain** (mhos144)
- Dicky Samudra (dsam041)
- Jiawei Xu (jxu987)
- Taha Sameer (tsam755)

---

## 📌 Notes

- All models were built in **R** using `tidymodels`, `xgboost`, `lightgbm`, and `bonsai`.
- Class imbalance was handled using **SMOTE** via the `themis` package.
- Results are based on **10-fold cross-validation** for robustness.

---

## 📄 License

This project is for academic use only. Data used is synthetic and does not contain any real banking information.

"""

# Save to file
readme_path = "/mnt/data/README.md"
Path(readme_path).write_text(readme_content)

readme_path
