# 🚨 Financial Transaction Fraud Detection System

## 📌 Project Overview
With the rapid growth of online financial transactions, fraudulent activities such as unauthorized transfers, balance draining, and suspicious merchant payments have increased significantly. These frauds lead to financial losses and reduce user trust in digital payment systems.

This project focuses on detecting fraudulent transactions using machine learning by applying effective data preprocessing, feature engineering, and predictive modeling techniques while handling highly imbalanced data.

---

## 🎯 Objectives
- Identify patterns that distinguish fraudulent and non-fraudulent transactions  
- Apply robust data preprocessing and feature engineering  
- Build and evaluate machine learning models for fraud detection  
- Interpret important features contributing to fraud  
- Propose real-world fraud prevention and monitoring strategies  

---

## 📂 Dataset Description
Each row in the dataset represents a **single financial transaction**.

### 🎯 Target Variable
- **`isFraud`**
  - `1` → Fraudulent transaction  
  - `0` → Legitimate transaction  

### 📊 Features
| Feature | Description |
|------|-----------|
| `step` | Time of transaction (1 step = 1 hour, 30-day simulation) |
| `type` | Transaction type (CASH-IN, CASH-OUT, TRANSFER, PAYMENT, DEBIT) |
| `amount` | Transaction amount |
| `oldbalanceOrg` | Sender balance before transaction |
| `newbalanceOrig` | Sender balance after transaction |
| `oldbalanceDest` | Receiver balance before transaction |
| `newbalanceDest` | Receiver balance after transaction |
| `nameOrig`, `nameDest` | Sender and receiver identifiers |
| `isFlaggedFraud` | Rule-based fraud indicator (not used for training) |

---

## ⚙️ Data Preprocessing
- No missing values detected  
- No duplicate records  
- Severe class imbalance:
  - Fraud: **0.13%**
  - Non-fraud: **99.87%**
- Used `class_weight = 'balanced'`
- Outlier analysis across transaction types
- Multicollinearity detected using **VIF**

---

## 🧠 Feature Engineering

### 🔹 Balance-Based Features
- **Balance Spent Ratio**
- **Balance Drained Indicator** (more than 50% balance removed)

### 🔹 Time-Based Features
- Hour of day  
- Day of month  
- Night transaction indicator  

### 🔹 Risk-Based Features
- Transaction type risk encoding  
- Merchant destination indicator  

⚠️ Highly collinear balance features were dropped and replaced with engineered features for better stability and interpretability.

---

## 🤖 Models Used

### 1️⃣ Logistic Regression
- Feature scaling using **StandardScaler**
- High recall for fraud detection
- ROC-AUC: **0.97**
- Optimized classification threshold for business use

---

### 2️⃣ Random Forest (Best Performing Model)
- No feature scaling required
- Handles non-linear relationships effectively

**Performance Metrics**
- Accuracy: ~100%
- Precision: 99.88%
- Recall: 99.31%
- ROC-AUC: 0.998
- PR-AUC: 0.996

---

## 🔍 Key Fraud Indicators
1. Transaction Type (TRANSFER & CASH-OUT)
2. Balance Spent Ratio
3. Balance Drained Indicator
4. Transaction Amount
5. Merchant Destination
6. Night-Time Transactions

These indicators strongly align with real-world fraud behavior.

---

## 🛡️ Fraud Prevention Strategy
A multi-layer detection framework:
1. **Rule-Based Controls**
2. **Machine Learning Probability Scoring**
3. **Behavioral Anomaly Detection**
4. **Cross-Transaction Pattern Analysis**

---

## 📊 Evaluation & Monitoring
- Fraud detection rate
- False positive rate
- Fraud loss prevented
- Customer friction metrics
- ROC-AUC and PR-AUC tracking
- Model drift detection
- ROI measurement

---

## 🧪 Technologies Used
- Python  
- Pandas, NumPy  
- Scikit-learn  
- Matplotlib, Seaborn  
- Jupyter Notebook  

---


## 🚀 Future Improvements
- XGBoost / LightGBM integration  
- SHAP-based explainability  
- Real-time fraud detection API  
- Graph-based fraud ring detection  
- Streaming transaction analysis  

---
