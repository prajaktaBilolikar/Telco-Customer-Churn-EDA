# 📊 Telecom Customer Churn — Exploratory Data Analysis (EDA)

![Python](https://shields.io)
![Pandas](https://shields.io)
![Seaborn](https://shields.io)
![Matplotlib](https://shields.io)

## 📌 Project Overview
Customer churn is a critical metric in the telecommunications industry, where acquiring new customers is significantly more expensive than retaining existing ones. This project performs an end-to-end **Exploratory Data Analysis (EDA)** on **7,043 telecom customer records** to uncover the primary drivers behind customer attrition and provide actionable, data-backed retention strategies.

---

## 🎯 Executive Summary
* **Overall Churn Rate:** **26.54%** (1,869 out of 7,043 customers churned).
* **Customer Baseline:** Average customer tenure is **32.37 months** (median: 29 months), with an average monthly bill of **\$64.76** (median: \$70.35) and an average lifetime value of **\$2,279.73**.
* **Primary Churn Drivers:** Month-to-month contracts, early-tenure friction (first 12 months), Fiber Optic internet service, lack of technical/security add-ons, and manual electronic check payments.

---

## 🛠️ Data Cleaning & Preparation
Before conducting visual and statistical analysis, the raw dataset (`churn.csv`) underwent the following preprocessing steps:
1. **Handling Missing/Blank Values:** Replaced blank spaces (`" "`) in the `TotalCharges` column with `0` and converted the data type from `object` to `float64`.
2. **Duplicate Verification:** Verified `0` duplicate rows and `0` duplicate `customerID` entries across all 7,043 records.
3. **Feature Transformation & Binning:**
   * Converted `SeniorCitizen` binary values (`0` / `1`) into readable categorical labels (`No` / `Yes`).
   * Engineered a `TenureGroup` feature by binning continuous `tenure` months into 7 lifecycle intervals (`0-6`, `7-12`, `13-24`, `25-36`, `37-48`, `49-60`, and `61-72` months).

---

## 🔍 Key Business & Statistical Insights

### 1. Contract Type is the Strongest Predictor of Churn
Month-to-month customers account for **88.55% (1,655 of 1,869)** of all churned users. Longer commitments dramatically reduce attrition:

| Contract Type | Retained | Churned | Total Customers | Churn Rate |
| :--- | :---: | :---: | :---: | :---: |
| **Month-to-Month** | 2,220 | 1,655 | 3,875 | **42.71%** |
| **One Year** | 1,307 | 166 | 1,473 | **11.27%** |
| **Two Year** | 1,647 | 48 | 1,695 | **2.83%** |

### 2. Critical First-Year Attrition Window
Customer churn is heavily concentrated during onboarding and stabilizes sharply after the first year:
* **0–6 Months:** **52.9%** churn rate (47.1% retained)
* **7–12 Months:** **35.9%** churn rate (64.1% retained)
* **13–24 Months:** Drops to **28.7%**
* **61–72 Months:** Drops to **6.6%**

### 3. Payment Friction in Electronic Checks
Manual payment methods experience nearly **3x** the churn rate of automated billing:
* **Electronic Check:** **45.29%** churn rate (1,071 churned vs. 1,294 retained) — representing **57.30%** of all churned customers.
* **Mailed Check:** **19.11%** churn rate (308 of 1,612)
* **Bank Transfer (Automatic):** **16.71%** churn rate (258 of 1,544)
* **Credit Card (Automatic):** **15.24%** churn rate (232 of 1,522)

### 4. Service Ecosystem & Fiber Optic Vulnerability
* **Fiber Optic Risk:** Fiber optic subscribers churn at **41.9%**, more than double the rate of DSL users (**19.0%**) and customers without internet (**7.4%**).
* **Sticky Support & Security Add-Ons:** Customers without protective or support services churn at **2x to 3x** the rate of subscribed users:
  * *Online Security:* **41.8%** churn without vs. **14.6%** with
  * *Tech Support:* **41.6%** churn without vs. **15.2%** with
  * *Online Backup:* **39.9%** churn without vs. **21.5%** with
  * *Device Protection:* **39.1%** churn without vs. **22.5%** with
* **Low-Impact Features:** Gender, basic phone service, multiple lines, and streaming add-ons (TV/Movies) show minimal variance in churn rates.

### 5. Demographic Insights
* **Senior Citizens:** Seniors make up **16.21% (1,142)** of the customer base but churn at **41.7%**, compared to **23.6%** for non-seniors.

---

## 💡 Actionable Business Recommendations

1. **Launch a "First-Year Lock-In" Campaign:** Target month-to-month subscribers in their **0–12 month** window with a discounted rate or free 3-month upgrade when switching to a 1-year contract.
2. **Bundle Tech Support & Security with Fiber Optic Plans:** Include free **Tech Support** and **Online Security** for the first 6 months of new Fiber Optic subscriptions to address the **41.9%** churn rate.
3. **Incentivize Auto-Pay Migration:** Offer a one-time **\$5–\$10 bill credit** to Electronic Check users (**45.29%** churn) who switch to automatic credit card or bank transfer payments.
4. **Create a Senior Citizen Onboarding Track:** Provide simplified billing statements and proactive 90-day support check-ins for senior customers (**41.7%** churn).

---

## 📁 Repository Structure

```text
├── Customer_Churn_EDA.ipynb   # Jupyter Notebook containing code, visualizations, and analysis
├── churn.csv                  # Raw telecom customer dataset (7,043 rows, 21 columns)
└── README.md                  # Project documentation, findings, and recommendations
```

---

## 🚀 How to Run Locally

1. **Clone the repository:**
   ```bash
   git clone https://github.com
   cd Telecom-Customer-Churn-EDA
   ```
2. **Install required libraries:**
   ```bash
   pip install pandas numpy seaborn matplotlib jupyter
   ```
3. **Launch Jupyter Notebook:**
   ```bash
   jupyter notebook Customer_Churn_EDA.ipynb
   ```
