# 💳 FraudGuard

## Credit Card Transaction Anomaly Detection

*AICA x DataCamp Capstone Project*

---

## 📌 Project Overview

Modern fraud detection systems must strike a delicate balance: **catch as much fraud as possible** while **minimizing false alarms** that frustrate legitimate customers.

In this project, I act as a **Machine Learning Scientist at a fintech startup** tasked with improving an outdated rule-based fraud detection system. Using real-world transaction data, I build and evaluate machine learning models designed to detect **fraudulent credit card transactions**, with a strong emphasis on **Recall**.

---

## 🎯 Business Objective

* **Maximize Recall** → catch as many fraudulent transactions as possible
* **Maintain acceptable Precision** → avoid excessive false positives
* Reduce customer friction while improving fraud coverage

---

## 📂 Dataset

**Source:** Kaggle – Credit Card Fraud Detection Dataset
**Link:** [https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)

### 📊 Dataset Details

* **Transactions:** 284,807
* **Fraud cases:** Highly imbalanced (~0.17%)
* **Timeframe:** September 2013 (European cardholders)

### 🧾 Feature Description

* `V1` – `V28`: PCA-transformed features (anonymized)
* `Amount`: Transaction amount
* `Time`: Seconds elapsed between transactions
* `Class`: Target variable

  * `0` → Legitimate transaction
  * `1` → Fraudulent transaction

📌 *Note:* PCA transformation preserves confidentiality but removes feature interpretability.

---

## 🛠️ Methodology

### 1️⃣ Data Exploration

* Verified dataset cleanliness (no missing values)
* Identified **extreme class imbalance**
* Dropped `Time` due to limited predictive value

### 2️⃣ Data Preprocessing

* Stratified train–test split to preserve class distribution
* Standardized `Amount` feature using **StandardScaler**
* Retained PCA features as-is

### 3️⃣ Baseline Modeling

Trained and evaluated:

* **Logistic Regression** (baseline)
* **Random Forest**
* **XGBoost**

Metrics used:

* Recall (primary)
* Precision
* F1 Score
* Accuracy (secondary)

---

## 📈 Models & Results

### 🔹 Baseline Models

| Model               | Precision | Recall | F1 Score |
| ------------------- | --------- | ------ | -------- |
| Logistic Regression | 0.872     | 0.694  | 0.773    |
| Random Forest       | 0.965     | 0.847  | 0.902    |
| XGBoost             | 0.895     | 0.867  | 0.881    |

---

### 🔧 Hyperparameter Tuning

Used **RandomizedSearchCV** with **Recall** as the scoring metric for:

* Random Forest
* XGBoost

Class imbalance handled using:

* `class_weight='balanced'` (Random Forest)
* `scale_pos_weight` (XGBoost)

---

### 🏆 Best Model: Tuned XGBoost

| Metric     | Score     |
| ---------- | --------- |
| **Recall** | **0.898** |
| Precision  | 0.854     |
| F1 Score   | 0.876     |
| Accuracy   | 0.9996    |

✅ **Best trade-off between high fraud detection and manageable false positives**

---

## 🧠 Key Insights

* Accuracy alone is misleading in highly imbalanced datasets.
* Random Forest achieved extremely high recall but at the cost of poor precision when tuned aggressively.
* **XGBoost provided the best balance**, aligning with real-world fraud detection priorities.
* Metric-driven model selection is critical in production ML systems.

---

## ⚙️ Tech Stack

* **Python 3**
* **pandas**, **NumPy**
* **scikit-learn**
* **XGBoost**
* **Matplotlib**, **Seaborn**
