# FinRetention-AI: Customer Churn Prediction & Retention Optimization

This project leverages Machine Learning to predict customer churn and optimize retention strategies in the financial services sector. By analyzing transaction patterns, credit usage, and customer engagement, the system evaluates the impact of targeted retention campaigns (e.g., cashback programs) across distinct customer segments. It provides an end-to-end pipeline from data preprocessing to A/B testing simulation and ROI analysis.

---

## 🚀 Project Overview

Customer retention is critical in fintech. This project focuses on:

- **Churn Prediction** – Logistic Regression and XGBoost to identify at-risk customers  
- **Profitability Modeling** – Customer Lifetime Value (CLV) and profit proxy creation  
- **Customer Segmentation** – High Spenders, Revolvers, Transactors  
- **Intervention Simulation** – Cashback campaign reducing churn probability by 10% for high-value users  
- **A/B Testing Framework** – Control vs treatment randomization with statistical testing  
- **Engagement Metrics** – Funnel analysis, DAU/MAU stickiness, cohort retention  
- **ROI Analysis** – Incremental RAPS and profitability evaluation  
- **Model Interpretability** – SHAP-based explanation of churn drivers  

---

## 📊 Dataset

**BankChurners.csv (synthetic banking dataset)**

| Category | Features |
|----------|----------|
| Demographics | Gender, Education, Marital Status, Income |
| Credit Usage | Credit Limit, Revolving Balance, Transaction Amount, Transaction Count |
| Behavior | Months on book, Inactivity, Contacts |
| Target | Attrited Customer (churn) |

---

## 🛠️ Feature Engineering

### Profit Proxy
```python
df['Avg_Utilization_Ratio'] = df['Total_Revolving_Bal'] / df['Credit_Limit']
df['Profit_Proxy'] = (df['Credit_Limit'] * df['Avg_Utilization_Ratio']) - (0.02 * df['Total_Trans_Amt'])

📈 Methodology
Data Preprocessing
Encoding categorical variables
Train-test split (80/20)
Predictive Modeling
Model	Target	Performance
Logistic Regression	Churn	ROC-AUC = 0.99997
XGBoost Regressor	Profit Proxy	R² = 0.9998, RMSE = 11.11
Intervention Simulation
Cashback incentive applied to treatment group
10% churn reduction simulated for high-value users
Targeted using top RAPS quartile
A/B Testing
Stratified random sampling
Control vs Treatment groups
Statistical tests:
z-test (churn difference)
Welch’s t-test (profit difference)

Key result:

Churn reduction: 3.10% (p < 0.001)
Profit uplift: not significant (p ≈ 0.84)
Funnel Analysis

Stages:

Active
Transacted
Repeat
Loyal

Metrics:

DAU/MAU: 0.03–0.04
Cohort retention analysis performed
ROI Analysis
roi = (total_incremental - cost) / cost
Cost per user: 50 units
Result: Negative ROI due to high intervention cost
SHAP Interpretability

Top churn drivers:

Transaction count
Months inactive
Contact frequency
🔑 Key Results
Metric	Value
Churn Reduction	3.10%
Incremental RAPS	1,578.52
ROI	-0.79
Avg RAPS uplift	10.55
Best Segment	Revolvers (+0.27 RAPS)
Segment Insights
High Spender: +0.03 RAPS
Revolver: +0.27 RAPS
Transactor: +0.16 RAPS
📌 Business Insights
Revolvers are the most responsive segment to cashback
Broad-based cashback campaigns are not profitable
Targeted retention improves ROI significantly
Cost efficiency is the primary constraint in scaling interventions
📁 Repository Structure
FinRetention-AI/
├── FinRetention_AI.ipynb
├── data/
└── README.md
🧰 Dependencies
Python 3.8+
pandas, numpy
scikit-learn
xgboost
shap
scipy, statsmodels
matplotlib, seaborn, plotly
