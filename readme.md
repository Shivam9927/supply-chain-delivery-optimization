# Supply Chain Delivery Optimization & Late Delivery Risk Prediction

> **End-to-end supply chain analytics project identifying operational bottlenecks, quantifying business impact, and building predictive models to reduce $2.1M profit at risk from late deliveries**

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## 📋 Table of Contents

- [Business Problem](#-business-problem)
- [Project Overview](#-project-overview)
- [Key Findings](#-key-findings)
- [Methodology](#-methodology)
- [Tech Stack](#️-tech-stack)
- [Business Report](#-executive-business-report)
- [Results & Visualizations](#-results--visualizations)
- [Strategic Recommendations](#-strategic-recommendations)
- [Installation & Usage](#-installation--usage)
- [Project Structure](#-project-structure)
- [Key Learnings](#-key-learnings)
- [Author](#-author)

---

## 🎯 Business Problem

A global e-commerce company managing end-to-end order fulfillment across multiple regions faces critical delivery performance issues:

- **54.71% late delivery rate** — more than half of orders fail to meet promised delivery windows
- **$2.1M profit at risk** from delayed orders (out of $7.5M total profit)
- **100% delay rate** on First Class shipping mode
- **Eroded customer trust** and inability to make reliable delivery commitments

**Core Challenge:** Actual shipping times frequently deviate from scheduled timelines, creating operational inefficiencies and financial losses.

---

## 🔍 Project Overview

This project delivers a comprehensive supply chain analytics solution to:

1. **Identify operational bottlenecks** causing late deliveries across 6 dimensions
2. **Quantify business impact** of delays on profitability
3. **Build predictive models** to flag high-risk orders before shipment
4. **Provide executive-ready recommendations** with prioritized action plans

**Dataset:** 172,765 e-commerce orders (Jan 2015 - Jan 2018)  
**Source:** [DataCo Supply Chain Dataset](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis) (Kaggle)

---

## 📊 Key Findings

### Business KPIs

| Metric | Value |
|--------|-------|
| **Total Orders Analyzed** | 172,765 |
| **Late Delivery Rate** | 54.71% |
| **On-Time Delivery Rate** | 45.29% |
| **Total Profit (profitable orders)** | $7.5M |
| **Profit at Risk (delayed orders)** | $2.1M |
| **90th Percentile Delay** | 3 days |
| **Average Order Profit** | $22.03 |

### Critical Bottlenecks Identified

**🚨 Shipping Mode = #1 Failure Point**
- **First Class:** 100% delay rate
- **Second Class:** 79.8% delay rate  
- **Standard Class:** 39.8% delay rate ✅ (best performer)
- **Same Day:** 0% delay rate ✅

**💳 Payment Processing Bottlenecks**
- **Payment Review status:** 55.3% delay rate (80% in Central Africa)
- **Pending Payment:** 55% delay rate

**🌍 Geographic Patterns**
- All regions cluster between 55-59% delay rate (systemic, not regional issue)
- Central Africa: 58.7% (highest)
- Customer segments nearly identical (54.5-55.4%) — no preferential service

**📦 Department-Level Issues**
- Health & Beauty: 56.9% delay rate
- Pet Shop: 56.6% delay rate
- Outdoors (Central Africa): 61.3% delay rate

**📅 Seasonal Patterns**
- **Peak delay months:** August & September (55.4%), December (55.2%)
- **Intra-day peaks:** Hour 21 (57.1% — late evening orders miss cutoff windows)

---

## 🛠️ Methodology

### 1. Data Preparation & Cleaning
- Loaded 180K+ raw orders, removed 25+ redundant/sensitive columns
- Filtered out cancelled orders (not relevant for delivery analysis)
- Converted date fields, handled missing values
- Feature engineering: order processing time, delay calculation, time-based features

### 2. Exploratory Data Analysis
- Profitability distribution (80.7% profit, 18.7% loss, 0.6% break-even)
- Delay distribution analysis (31% of orders exactly 1 day late)
- Profit vs. delay correlation (mean profit stable at $20-23 across all delay levels)

### 3. Bottleneck Detection
Analyzed delay rates across 6 operational dimensions:
- **Order Region** (10 regions)
- **Customer Segment** (Consumer, Corporate, Home Office)
- **Shipping Mode** (First Class, Second Class, Standard, Same Day)
- **Order Status** (Complete, Processing, Pending, etc.)
- **Payment Type** (Payment, Transfer, Debit, Cash)
- **Department Name** (15 product categories)

### 4. Root Cause Analysis
Deep-dive into **Central Africa** (highest-delay region):
- Ranked top 10 driver factors by delay percentage
- Identified **Shipping Mode: First Class (100%)** and **Payment Review (80%)** as root causes
- Cross-referenced with department and customer segment data

### 5. Time-Based Pattern Analysis
- **Monthly trends:** August, September, December peak delay months
- **Day of week:** Minimal variance (Monday 55.5% vs. Friday 54.8%)
- **Hourly patterns:** Late evening (hour 21) and midday (hours 11-12) show peaks

### 6. Machine Learning Predictive Modeling

**Algorithm:** Random Forest Classifier

**Features:**
- Scheduled shipment days
- Product category & department (frequency encoded)
- Customer segment
- Order region
- Shipping mode
- Order timing (month, hour)
- Payment type

**Class Imbalance Handling:** SMOTE oversampling (balanced 79,182:79,182)

**Model Performance (Test Set):**

| Metric | Class 0 (On-Time) | Class 1 (Late) | Overall |
|--------|-------------------|----------------|---------|
| **Precision** | 0.68 | 0.78 | 0.74 |
| **Recall** | 0.72 | 0.75 | 0.74 |
| **F1-Score** | 0.70 | 0.77 | 0.74 |
| **Accuracy** | — | — | **74%** |

**Business Impact:** 78% precision on late predictions means the model can reliably flag high-risk orders for proactive intervention.

---

## 🖥️ Tech Stack

**Data Engineering & Analysis**
- Python (Pandas, NumPy) — data cleaning, feature engineering
- SQL-ready data structure for multi-table joins

**Machine Learning**
- Scikit-learn — Random Forest, train/test split, classification metrics
- Imbalanced-learn (SMOTE) — class imbalance handling
- Frequency encoding for high-cardinality categoricals

**Visualization & Reporting**
- Matplotlib, Seaborn — professional business visualizations
- Custom color palettes (Viridis) for executive readability
- Annotated charts with business insights

**Statistical Analysis**
- Delay distribution analysis
- Root cause detection by category
- Profitability impact quantification

---

## 📄 Executive Business Report

A comprehensive **10-page executive report** was prepared for business stakeholders:

### Report Sections
1. **Executive Summary** — Headline metrics and key findings
2. **Business Context & Objectives** — Problem statement and analytical goals
3. **Key Performance Indicators (KPIs)** — Baseline performance metrics
4. **Profitability Analysis** — Distribution and delay impact on profit
5. **Bottleneck Detection** — 6-dimensional operational analysis
6. **Root Cause Analysis** — Central Africa deep-dive
7. **Time-Based Delay Patterns** — Seasonal, weekly, hourly trends
8. **Machine Learning Model Results** — Random Forest performance
9. **Strategic Recommendations** — Prioritized action plan (CRITICAL/HIGH/MEDIUM/LOW)
10. **Conclusion** — Target state metrics and implementation roadmap

**[📥 Download Full Report (PDF)](Supply_Chain_Performance_Report.pdf)**

### Report Highlights

<img width="1202" height="291" alt="image" src="https://github.com/user-attachments/assets/a30825d6-b40f-4ed5-82c6-993c333253d0" />


---

## 📈 Results & Visualizations

### Profitability Distribution

<img width="621" height="787" alt="Profitability Distribution " src="https://github.com/user-attachments/assets/3fa7bbb0-1445-4fc8-a0d3-def604221410" />


*80.7% of orders are profitable, but 18.7% loss-making share is disproportionately concentrated among delayed shipments*

---

### Delay Distribution & Profit Impact

<img width="1308" height="477" alt="delayed distribution" src="https://github.com/user-attachments/assets/2b6209dd-9f84-4f0b-b547-71ff89e72459" />


*31% of orders arrive exactly 1 day late; mean profit remains stable at $20-23 across all delay levels*

---

### Bottleneck Detection (6 Dimensions)

<img width="1532" height="832" alt="Bottleneck Detection " src="https://github.com/user-attachments/assets/d3f28a77-865b-405a-804c-8d4db63bee2b" />


*Shipping Mode is the #1 operational failure point: First Class 100% delay, Second Class 79.8%, Standard Class 39.8%*

---

### Root Cause Analysis — Central Africa
<img width="1346" height="713" alt="Root Cause Analysis " src="https://github.com/user-attachments/assets/6f03b064-5a3b-48df-a65a-3c3abc8b7e6f" />


*Top 10 delay drivers in highest-risk region: First Class Shipping (100%), Payment Review (80%)*

---

### Time-Based Delay Patterns
<img width="1566" height="500" alt="Time-Based Delay Patterns " src="https://github.com/user-attachments/assets/578c9d99-9a07-41ba-9890-ee66a470abe0" />


*Seasonal peaks: Aug/Sep/Dec; Intra-day peak: Hour 21 (late evening orders)*

---

### Machine Learning Model Performance
<img width="1567" height="452" alt="Model accuracy" src="https://github.com/user-attachments/assets/3cb08508-a131-40f7-b0c1-42c5747f0cb2" />


*Random Forest achieves 74% accuracy, 78% precision on late delivery predictions*

---

## 💡 Strategic Recommendations

### CRITICAL Priority

**1. Immediately Audit First Class & Second Class Shipping**
- **Finding:** First Class = 100% delay rate, Second Class = 79.8%
- **Action:** Conduct carrier SLA audit; consider suspending First Class until resolved
- **Expected Impact:** 15-20% reduction in late deliveries

---

### HIGH Priority

**2. Deploy Predictive Alert System**
- **Finding:** Random Forest model ready for production (74% accuracy, 78% precision)
- **Action:** Integrate into order management system to flag high-risk orders
- **Expected Impact:** Proactive intervention on $2.1M profit at risk

**3. Resolve Payment Processing Bottlenecks**
- **Finding:** Payment Review (80% delay in Central Africa), Pending Payment (55%)
- **Action:** Automated escalation for reviews exceeding 2 hours
- **Expected Impact:** 10-15% faster order processing

---

### MEDIUM Priority

**4. Seasonal Surge Capacity Planning**
- **Finding:** Aug/Sep/Dec show 55.2-55.4% delay rates
- **Action:** Pre-position inventory, add temp logistics partnerships
- **Expected Impact:** Maintain <10% delay rate during peak vs. current 50%+

**5. Default to Standard Class**
- **Finding:** Standard Class achieves 39.8% delay (best non-premium mode)
- **Action:** Re-evaluate shipping mode assignment logic
- **Expected Impact:** 20% improvement in overall on-time delivery

**6. Investigate High-Delay Departments in Africa**
- **Finding:** Outdoors (61.3%), Golf (60.8%) in Central Africa
- **Action:** Warehouse audit of stock availability and carrier assignment
- **Expected Impact:** 15% improvement in department-specific delays

---

### LOW Priority

**7. Reduce Loss-Making Order Share (18.7%)**
- **Action:** Pricing and discount review; identify if discounted orders are disproportionately late
- **Expected Impact:** Improve margin and reduce compounded profitability problem

**8. Continuously Retrain Predictive Model**
- **Action:** Quarterly retraining; add carrier-level data, weather, warehouse utilization
- **Target:** Improve recall to >80% within 6 months

---

## 🚀 Installation & Usage

### Prerequisites
```bash
Python 3.8+
Jupyter Notebook
```

### Clone Repository
```bash
git clone https://github.com/[your-username]/supply-chain-delivery-optimization.git
cd supply-chain-delivery-optimization
```

### Install Dependencies
```bash
pip install -r requirements.txt
```

### Download Dataset
1. Download [DataCo Supply Chain Dataset](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis) from Kaggle
2. Place `DataCoSupplyChainDataset.csv` in project root directory

### Run Analysis
```bash
jupyter notebook "Supply Chain Analysis.ipynb"
```

Run all cells to reproduce:
- Data cleaning and feature engineering
- Exploratory data analysis
- Bottleneck detection across 6 dimensions
- Root cause analysis
- Time-based pattern analysis
- Random Forest model training and evaluation

---

## 📁 Project Structure
supply-chain-delivery-optimization/
├── README.md                                    # This file
├── Supply Chain Analysis.ipynb                  # Main analysis notebook
├── Supply_Chain_Performance_Report.pdf          # Executive business report
├── DataCoSupplyChainDataset.csv                 # Dataset (download separately)
├── DescriptionDataCoSupplyChain.csv             # Data dictionary
├── visualizations/                              # Generated charts
│   ├── profitability_distribution.png
│   ├── delay_profit_analysis.png
│   ├── bottleneck_analysis.png
│   ├── root_cause_central_africa.png
│   ├── time_based_analysis.png
│   └── confusion_matrix.png
├── requirements.txt                             # Python dependencies
└── LICENSE                                      # MIT License

---

## 🎓 Key Learnings

This project demonstrates:

✅ **End-to-end supply chain analytics** from data extraction to executive recommendations  
✅ **Operations research methodology** for bottleneck detection and root cause analysis  
✅ **Predictive modeling for operational risk** with class imbalance handling (SMOTE)  
✅ **Business impact quantification** ($2.1M profit at risk, delay costs by dimension)  
✅ **Stakeholder communication** via executive-ready reports and visualizations  
✅ **Strategic prioritization** of recommendations (CRITICAL/HIGH/MEDIUM/LOW tiers)  

### Directly Applicable To:
- Retail supply chain optimization (warehouse fulfillment, last-mile delivery)
- Inventory planning and demand forecasting
- Shipping partner performance management
- Operational KPI development and monitoring
- Order lifecycle analytics
- E-commerce logistics optimization

### Methodology Transferability:
This analytical framework—bottleneck detection across operational dimensions, root cause analysis by geography, predictive risk modeling, and quantified business impact—is directly applicable to retail supply chain challenges including warehouse fulfillment optimization, last-mile delivery performance, order lifecycle analytics, and inventory allocation. The same techniques used to identify First Class shipping failures can surface warehouse picking inefficiencies, carrier performance gaps, or regional capacity constraints in any omnichannel retail operation.

---

## 👤 Author

**Shivam Pawar**  
MS Data Science & Analytics, California State University, Chico (GPA: 3.9)  
Graduating May 2026

📧 Email: [shivampawars@gmail.com](mailto:shivampawars@gmail.com)  
💼 LinkedIn: [linkedin.com/in/shivam-pawar09](https://linkedin.com/in/shivam-pawar09/)  
🐙 GitHub: [github.com/Shivam9927](https://github.com/Shivam9927)

---

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- Dataset: [DataCo Smart Supply Chain for Big Data Analysis](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis) (Kaggle)
- Analysis Period: January 2015 - January 2018
- Tools: Python, Jupyter, Scikit-learn, Pandas, Matplotlib, Seaborn

---

## 📌 Citation

If you use this project for research or educational purposes, please cite:
Pawar, S. (2026). Supply Chain Delivery Optimization & Late Delivery Risk Prediction.
GitHub repository: https://github.com/Shivam9927/supply-chain-delivery-optimization

---

<div align="center">

**⭐ If you found this project helpful, please consider giving it a star!**

Made with ❤️ for supply chain analytics and operational excellence

</div>
