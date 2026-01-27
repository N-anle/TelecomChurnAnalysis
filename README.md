# Telco Customer Churn & Retention Strategy

## Overview
Customer churn represents a **direct and recurring revenue loss**.  
This project analyzes customer behavior to **identify high-risk churn segments**, understand **why they churn**, and translate those insights into **actionable retention strategies**.

The analysis focuses on a Telco dataset where a specific customer segment (Fiber Optic, Month-to-Month users) exposes **>$70,000 in monthly recurring revenue at risk**.

---

## Business Objective
Move beyond churn prediction as a classification task and instead:
- Identify **who is most at risk**
- Understand **why churn occurs**
- Quantify **which interventions are financially justified**

The goal is to support **proactive retention decisions**, not automated cancellations or alerts.

---

##  Data Preparation
- Cleaned and standardized customer-level data
- Handled missing and inconsistent values
- Encoded categorical variables and scaled numerical features
- Preserved class balance awareness (≈26% churn rate)

The final dataset contains **7,043 customers** and **20 behavioral, contractual, and billing features**.

---

## Exploratory Data Analysis (EDA)

### Key Dimensions Analyzed
- **Customer tenure**
- **Contract type**
- **Service subscriptions**
- **Payment methods**
- **Monthly charges**

EDA was structured around **business questions**, not just correlations.

---

## Key Insights

### 1️⃣ The “Month-1 Cliff”
- ~60% of Month-to-Month customers churn within the **first 30 days**
- Indicates **onboarding or setup failure**, not price sensitivity

### 2️⃣ The “Protection Gap”
- High-value Fiber customers are the **least protected**
- ~73% lack retention anchors (Online Security or Tech Support)
- Customers with these services are **~50% less likely to churn**

### 3️⃣ Payment Method as a Proxy Risk Signal
- Electronic Check users show significantly higher churn
- Further analysis revealed this is a **proxy** for:
  - Fiber subscription
  - Month-to-Month contracts
  - Low service stickiness

---

## Modeling Approach

- **Model:** Logistic Regression  
- **Objective:** Maximize Recall on churners while retaining interpretability  
- **Class Handling:** `class_weight='balanced'` to reflect financial asymmetry  

### Why Logistic Regression?
- Strong linear churn drivers (pricing, tenure, contract structure)
- Stable performance under class imbalance
- Transparent coefficients for stakeholder trust

---

## Model Performance (Test Set)
- **Recall:** ~72%  
- **Precision:** ~54% (>2× lift over baseline churn rate of 26%)  
- **ROC-AUC:** 0.84  

Metrics were selected based on **business cost trade-offs**, not raw accuracy.

---

## Retention Strategy Simulation

Two counterfactual simulations were conducted to estimate real-world impact.

### Scenario A — Contract Migration
- Incentivize high-risk Month-to-Month users to 1-Year contracts
- **Projected churn reduction:** ~34%
- **Revenue upside:** ~$12,600 per month (test cohort)

### Scenario B — Targeted Retention Campaign
- Estimated intervention cost: $30 per customer
- Payback period: ~2.5 months
- **12-month ROI:** ~380%

---

## Outcome
This project delivers a **data-driven retention framework** that:
- Prioritizes high-risk customers
- Identifies structural churn drivers
- Demonstrates why **retention is financially superior to acquisition**

---

## Key Takeaway
Churn is not random — it is **structural, predictable, and preventable** when customer behavior, product design, and financial incentives are aligned.

---

## 🛠 Tools & Technologies
- Python
- Pandas, NumPy
- Scikit-Learn
- Matplotlib / Seaborn
