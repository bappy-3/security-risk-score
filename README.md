# security-risk-score

> **Security Risk Scoring Framework for Financial Audit Systems**  
> *An ML-Based Dynamic Risk Scoring Engine for Behavioral Audit Log Analysis*

---

## Overview

**Security Risk Score** is a machine learning-based framework that analyzes financial audit logs and assigns a **dynamic security risk score** to every audit event. Rather than producing a simple binary fraud prediction, the framework estimates a continuous probability of risk, enabling auditors and security analysts to prioritize investigations based on the severity of suspicious activities.

The project integrates traditional fraud detection with behavioral analytics, contextual audit information, explainable AI, and incremental learning to demonstrate how AI can support intelligent financial auditing and continuous security monitoring.

---

## Key Features

- Dynamic security risk scoring using machine learning
- Behavioral audit log analysis
- Context-aware feature engineering
- Synthetic enterprise audit log generation
- Random Forest-based risk prediction
- Incremental (online) learning with `SGDClassifier`
- Explainable AI using SHAP
- High-risk event identification
- Interactive Streamlit dashboard
- Continuous model adaptation through new audit logs

---

## Motivation

Traditional fraud detection systems generally classify transactions as either fraudulent or legitimate. However, real-world financial auditing requires understanding **how risky** an activity is rather than making a simple yes/no decision.

This framework addresses that limitation by generating continuous risk scores while incorporating behavioral patterns such as:

- User activity frequency
- Transaction amount
- Event type
- Off-hours activity
- Device information
- Administrative actions
- IP-based contextual information

---

## Architecture

```text
                    Public Fraud Datasets
                            +
                  Synthetic Audit Logs
                            │
                            ▼
                Data Preprocessing & Cleaning
                            │
                            ▼
              Behavioral Feature Engineering
                            │
                            ▼
             Random Forest Risk Prediction
                            │
                            ▼
                 Continuous Risk Scoring
                            │
                            ▼
              High-Risk Event Identification
                            │
                            ▼
                 Explainability (SHAP)
                            │
                            ▼
                 Interactive Dashboard
                            │
                            ▼
                 Incremental Learning
                 (Online Model Updates)
                            │
                            ▼
              Continuously Updated Risk Scores
```

---

## Project Pipeline

### 1. Data Collection

The framework utilizes multiple data sources:

- BankSim simulated banking dataset
- Credit Card Fraud Detection dataset
- Synthetic enterprise audit logs

---

### 2. Data Preprocessing

The collected datasets undergo preprocessing including:

- Missing value handling
- Feature encoding
- Numerical scaling
- Timestamp processing
- Behavioral feature extraction

---

### 3. Behavioral Feature Engineering

The framework generates security-oriented features such as:

- Transaction amount
- Event type
- User activity frequency
- Off-hours indicator
- Device type
- Administrative access events
- IP-related contextual information

---

### 4. Machine Learning

A Random Forest classifier is trained to estimate the probability that an audit event represents suspicious behavior.

Instead of returning only binary classifications, the model outputs:

```text
Risk Score ∈ [0,1]
```

where higher values indicate higher security risk.

---

### 5. High-Risk Detection

Audit events exceeding a configurable threshold are automatically flagged as high-risk events for further investigation.

Example:

| User | Event | Risk Score |
|------|------|-----------:|
| User_102 | ADMIN_ACCESS | 0.93 |
| User_217 | TRANSFER | 0.86 |
| User_431 | LOGIN | 0.78 |

---

### 6. Explainable AI

The framework uses **SHAP (SHapley Additive Explanations)** to explain why the model assigned a high risk score.

This improves transparency and assists auditors in understanding model decisions.

---

### 7. Incremental Learning

Unlike conventional fraud detection systems, the framework supports **online learning**.

As new audit logs arrive:

- New events are processed
- The model updates using `partial_fit()`
- Risk scores are continuously refreshed

This enables adaptation without retraining the entire model.

---

## Technologies

- Python
- Pandas
- NumPy
- Scikit-learn
- Random Forest
- SGDClassifier
- SHAP
- Streamlit
- Matplotlib
- Seaborn
- Faker

---

## Repository Structure

```text
security-risk-score/
│
├── security_risk.ipynb
├── requirements.txt
├── high_risk_audit_events.csv
├── streamlit_dashboard.py
├── README.md
└── data/
    ├── banksim.csv
    ├── creditcard.csv
    └── synthetic_audit_logs.csv
```

---

## Future Improvements

Future development may include:

- Real-time audit log ingestion
- Apache Kafka integration
- Graph-based anomaly detection
- Deep learning architectures (LSTM, Transformer)
- User behavioral profiling
- Adaptive risk thresholds
- Graph Neural Networks (GNN)
- SIEM integration
- Enterprise authentication and authorization
- Multi-organization deployment

---

## Research Contribution

This project demonstrates a proof-of-concept framework for **AI-assisted security risk scoring in financial audit systems**. By integrating machine learning, behavioral analytics, explainable AI, and incremental learning, it illustrates how intelligent audit analysis can move beyond static fraud detection toward continuous, adaptive security monitoring.

---

## License

This project is intended for academic research and educational purposes.
