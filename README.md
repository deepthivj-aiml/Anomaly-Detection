# Domain-Driven Anomaly Detection for Streaming Behavior (Open-Source)

![Python](https://img.shields.io/badge/python-3.10-blue) ![PyTorch](https://img.shields.io/badge/pytorch-2.0-orange) ![XGBoost](https://img.shields.io/badge/xgboost-1.7-red)

## 📖 Project Overview
This project implements a **Netflix-inspired anomaly detection system** using open-source credit card data to simulate streaming behavior.

In production systems like Netflix, **anomaly detection is not just about models**. It starts with **domain knowledge**:
- Expert rules define what “unexpected behavior” looks like  
- Semi-supervised models correct and refine these rules  
- Supervised models are trained as confidence grows  

This repo demonstrates that approach using publicly available datasets.

---

## 🎯 Objectives
1. Simulate **streaming fraud detection** with open-source data.  
2. Create **domain-driven heuristics** to bootstrap labels.  
3. Engineer **behavioral features** instead of raw statistics.  
4. Train a **semi-supervised Autoencoder** for anomaly scoring.  
5. Combine Autoencoder scores with features in a **supervised XGBoost model**.  
6. Evaluate the system on **precision, recall, and anomaly detection effectiveness**.

---

## 🗂️ Dataset
- **Credit Card Fraud Detection** dataset from OpenML (`fetch_openml("creditcard")`)  
- Subset of 50,000 rows for demonstration purposes  
- Features used: `Amount`, `V1`–`V6` (numeric features)  
- **Heuristic pseudo-labels** simulate “unexpected streaming behavior” (e.g., unusually high amounts or abnormal feature combinations)

---

## ⚙️ Project Pipeline

1. **Data Loading**  
   Load open-source dataset directly via OpenML.
2. **Heuristic Pseudo-Labels**  
   Create labels based on domain-inspired rules.
3. **Feature Engineering**  
   Scale numeric features.
4. **Autoencoder (Semi-Supervised)**  
   Train to reconstruct normal behavior; compute reconstruction error as anomaly score.
5. **Supervised Model (XGBoost)**  
   Combine features + Autoencoder scores; train classifier to detect anomalies.
6. **Evaluation**  
   Classification metrics: precision, recall, F1-score; visualize reconstruction error distribution.

---

## 💻 Tech Stack
- Python 3  
- Libraries: `pandas`, `numpy`, `scikit-learn`, `xgboost`, `torch`, `matplotlib`, `seaborn`, `openml`  
- Colab-compatible  

---

## 📊 Key Results
- Semi-supervised Autoencoder detects anomalies from pseudo-labels  
- XGBoost improves detection by combining heuristics and anomaly scores  
- False positives are reduced compared to heuristics alone  
- Histogram of Autoencoder reconstruction errors visualizes anomalous sessions  

---

## 🛠️ How to Run
1. Clone the repository:
```bash
git clone <your-repo-url>
cd <repo-name>
