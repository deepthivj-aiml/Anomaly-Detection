Domain-Driven Anomaly Detection for Streaming Behavior (Open-Source)
📖 Project Overview

This project implements a Netflix-inspired anomaly detection system using open-source credit card data to simulate streaming behavior.

In production systems like Netflix, anomaly detection is not just about models. It starts with domain knowledge:

Expert rules define what “unexpected behavior” looks like

Semi-supervised models correct and refine these rules

Supervised models are trained as confidence grows

This project mirrors that philosophy using publicly available data.

🎯 Objectives

Simulate streaming fraud detection with open-source data.

Create domain-driven heuristics to bootstrap labels.

Engineer behavioral features instead of raw statistics.

Train a semi-supervised Autoencoder for anomaly scoring.

Combine Autoencoder scores with features in a supervised XGBoost model.

Evaluate the system on precision, recall, and anomaly detection effectiveness.

🗂️ Dataset

Credit Card Fraud Detection dataset from OpenML

Used fetch_openml("creditcard") to ensure Colab-friendly, reliable download

Subset of 50,000 rows for demonstration purposes

Features used: Amount, V1–V6 (numeric features)

Heuristic pseudo-labels simulate “unexpected streaming behavior,” e.g., unusually high transaction amount or abnormal feature combinations.

⚙️ Project Pipeline

Data Loading

Load open-source dataset directly via OpenML

Heuristic Pseudo-Labels

Create labels based on domain-inspired rules

Feature Engineering

Scale numeric features

Autoencoder (Semi-Supervised)

Train to reconstruct normal behavior

Compute reconstruction error as anomaly score

Supervised Model (XGBoost)

Combine features + Autoencoder scores

Train XGBoost classifier to detect anomalies

Evaluation

Classification metrics: precision, recall, F1-score

Visualize reconstruction error distribution

💻 Tech Stack

Python 3

Libraries: pandas, numpy, scikit-learn, xgboost, torch, matplotlib, seaborn, openml

Colab-compatible

📊 Key Results

Semi-supervised Autoencoder detects anomalies from pseudo-labels

XGBoost improves detection by combining heuristics and anomaly scores

False positives are reduced compared to heuristics alone

Histogram of Autoencoder reconstruction errors visualizes anomalous sessions

🛠️ How to Run

Open the Colab notebook or clone the repo

Install required packages:

pip install scikit-learn xgboost pandas numpy matplotlib seaborn torch openml


Run the single-cell pipeline or full notebook

Evaluate and visualize anomalies

📌 Resume Bullet / Project Description

Developed a domain-driven anomaly detection system for streaming-like behavior using open-source datasets; combined heuristic rules, Autoencoder anomaly scores, and XGBoost classification, reducing false positives while maintaining high recall on simulated fraudulent sessions.

🔮 Next Steps / Extensions

Add time-series session features (start/end times, device sequences)

Implement streaming detection (online anomaly scoring)

Explore top-K anomaly alerts for operational monitoring

Integrate more sophisticated semi-supervised models (VAE, LSTM Autoencoders)
