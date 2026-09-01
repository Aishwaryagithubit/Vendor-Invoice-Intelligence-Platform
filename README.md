# Vendor Invoice Intelligence Platform

> An AI-powered analytics system that predicts freight costs and identifies risky vendor invoices using machine learning.

This project helps businesses detect invoice anomalies, reduce cost leakage, and improve audit efficiency by combining data engineering, statistical analysis, and machine learning.

---

## Overview

The Vendor Invoice Intelligence Platform is an end-to-end machine learning solution designed to support finance and procurement teams in analyzing vendor invoices.

The platform provides two core capabilities:

- **Freight Cost Prediction** — estimates expected freight costs from invoice and purchasing data.
- **Invoice Risk Detection** — identifies potentially risky invoices that may require manual review.

The system combines SQL-based feature engineering, data preprocessing, exploratory analysis, machine learning, model evaluation, and real-time inference through a Streamlit application.

---

## Key Features

- Freight cost prediction using machine learning
- Vendor invoice risk detection
- SQL-based feature engineering
- Invoice and purchasing data analysis
- Data preprocessing and feature scaling
- Random Forest regression and classification
- Saved models for real-time inference
- Interactive Streamlit dashboard
- Risk-based manual approval workflow

---

## Machine Learning Models

| Task | Model | Purpose |
|---|---|---|
| Freight Cost Prediction | Random Forest Regressor | Estimate expected freight cost |
| Invoice Risk Detection | Random Forest Classifier | Identify invoices requiring review |

### Freight Cost Prediction

The regression model uses invoice, purchasing, vendor, and item-level features to estimate expected freight costs.

**Performance**

- **R²:** 96.59%
- **MAE:** 27.64

### Invoice Risk Detection

The classification model evaluates invoice-level financial and operational signals to identify potentially risky invoices.

Risk signals include:

- Invoice and item-value discrepancies
- High freight-to-invoice ratios
- Extended payment terms
- Receiving delays

---

## Data & Feature Engineering

The project uses relational data stored in SQLite and creates analytical features through SQL aggregation.

Key features include:

| Feature | Description |
|---|---|
| `invoice_dollars` | Total invoice value |
| `Freight` | Freight cost |
| `days_po_to_invoice` | Days between PO and invoice |
| `days_to_pay` | Payment duration |
| `total_brands` | Number of brands on the purchase order |
| `total_item_quantity` | Total quantity purchased |
| `total_item_dollars` | Total value of purchased items |
| `avg_receiving_delay` | Average receiving delay |

---

## Machine Learning Workflow

```text
Raw Data
   ↓
SQLite Database
   ↓
SQL Feature Engineering
   ↓
Data Preprocessing
   ↓
Feature Scaling
   ↓
Model Training
   ↓
Model Evaluation
   ↓
Model Serialization
   ↓
Streamlit Application
   ↓
Real-Time Prediction

---
Project Structure
Vendor-Invoice-Intelligence-Platform/
│
├── app.py
├── requirements.txt
├── README.md
│
├── data/
│   └── inventory.db
│
├── models/
│   ├── predict_freight_cost.pkl
│   ├── freight_scaler.pkl
│   ├── predict_flag_invoice.pkl
│   └── scaler.pkl
│
├── Inference/
│   ├── predict_freight.py
│   └── predict_invoice_flag.py
│
├── freight_cost_prediction/
│   ├── data_preprocessing.py
│   ├── model_evaluation.py
│   └── train.py
│
├── invoice_flagging/
│   ├── data_preprocessing.py
│   ├── modeling_evaluation.py
│   └── train.py
│
├── notebooks/
│
└── Project images/

---
Technology Stack
Python
Pandas
NumPy
SQL / SQLite
Scikit-learn
Random Forest
Joblib
Streamlit
Installation

Clone the repository and install the required dependencies:

git clone <your-repository-url>
cd Vendor-Invoice-Intelligence-Platform
pip install -r requirements.txt
Run the Application

Launch the Streamlit application:

streamlit run app.py

The application provides an interactive interface for:

Freight cost prediction
Invoice risk detection
Business Value

The platform is designed to help organizations:

Identify potentially risky invoices earlier
Detect unusual invoice and freight patterns
Reduce financial cost leakage
Prioritize invoices for manual review
Improve audit efficiency
Support faster finance operations
Enable data-driven vendor invoice decisions
Limitations

This system is designed as a decision-support tool.

A risk prediction does not independently establish that an invoice is fraudulent. Flagged invoices should be reviewed using appropriate financial and business controls.

Model performance may also vary when applied to data that differs significantly from the training dataset.

Future Improvements
Add SHAP-based model explanations
Compare additional machine learning algorithms
Add batch invoice scoring through CSV upload
Introduce model and data-drift monitoring
Integrate with live enterprise databases
Containerize the application with Docker
Deploy the platform to cloud infrastructure
Live Demo

Streamlit Application:
<your-streamlit-app-url>

Author

Aishwarya Sah

AI / Machine Learning Engineer

Building machine learning systems and data driven applications.
