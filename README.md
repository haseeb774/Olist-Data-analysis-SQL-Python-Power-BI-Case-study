# 🛒 Brazilian E-Commerce Intelligence — Olist Case Study

<div align="center">

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Pandas](https://img.shields.io/badge/Pandas-EDA-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-28a745?style=for-the-badge)

**End-to-end business analytics case study on 100,000+ real e-commerce orders**  
*Revenue · Logistics · Customer Segmentation · Satisfaction*

[📊 View Dashboards](#dashboards) · [🔍 Key Findings](#key-findings) · [💡 Recommendations](#recommendations) · [⚙️ Run the Analysis](#setup--usage)

</div>

---

## 📌 Project Overview

This case study answers three real business questions using the **Olist Brazilian E-Commerce dataset** (~100K orders, 2016–2018):

| # | Business Question |
|---|---|
| 1 | What is driving revenue growth — and what's holding it back? |
| 2 | How does delivery performance affect customer satisfaction and retention? |
| 3 | Which customer segments represent the highest risk and opportunity? |

The analysis spans the full data pipeline: **SQL extraction → Python EDA → Power BI dashboards → business recommendations**.

---

## 🛠️ Tech Stack

| Layer | Tools |
|---|---|
| Data Extraction | SQL (joins, aggregations, window functions) |
| Analysis & EDA | Python — pandas, NumPy, matplotlib, seaborn |
| Modeling | scikit-learn (customer segmentation, RFM) |
| Visualization | Power BI (3-page interactive dashboard) |
| Environment | Jupyter Notebook |

---

## 📊 Dashboards

### Page 1 — Revenue & Sales Overview

![Revenue Dashboard](Olist_dashboard%201.png)

> **R$ 9.19M** total revenue · **45K** orders · **44K** customers · **R$ 206** avg order value  
> Credit card dominates at 73.6% of transactions. Bed & Bath leads all categories by revenue.

---

### Page 2 — Customer Segmentation & Retention

![Customer Dashboard](Olist_dashboard%202.png)

> **77.23%** satisfaction rate · **57.78%** 5-star reviews · **672** repeat customers  
> Champions hold the highest lifetime value. At-risk segment (39.9%) is the single largest — and most actionable — cohort.

---

### Page 3 — Delivery Performance & Operations

![Delivery Dashboard](Olist_dashboard%203.png)

> **12.02 days** avg delivery · **7.24%** late rate · **92.76%** on-time  
> State PA averages 22.6 days. State SP averages just 8.3 days — a 2.7× gap.

---

## 🔍 Key Findings

### 1. Revenue & Seasonality

![Revenue Trend](outputs/visualizations/01_revenue_trend.png)

- Revenue grew from near-zero in late 2016 to **~R$ 700K/month** by mid-2018
- **Spring and summer** consistently outperform autumn and winter by 35–55%
- November 2017 spike (likely Black Friday) is the single highest order volume month
- Low seasons (Sep–Feb) present a targeting opportunity, not an inevitable dip

![Seasonal Revenue](outputs/visualizations/12_seasonal_revenue_analysis.png)

---

### 2. Category Performance

![Top Categories](outputs/visualizations/02_top_categories.png)

- **Bed, Bath & Table** leads revenue at R$ 796K — driven by high order volume
- **Health & Beauty** and **Computers & Accessories** follow closely
- High-margin opportunity sits in **Watches & Gifts** — strong revenue relative to volume

---

### 3. Delivery Performance

![Delivery Distribution](outputs/visualizations/06_delivery_time_distribution.png)

- Median delivery: **10 days** · Average: **12 days** (right-skewed — outliers up to 209 days exist)
- Delivery time improved dramatically from **54 days avg in Aug 2016** to **under 8 days by late 2018**

![Monthly Delivery Trend](outputs/visualizations/10_monthly_avg_delivery_time.png)

- **Winter deliveries average 14.7 days** vs. **9.2 days in summer** — logistics strain is seasonal

![Seasonal Delivery](outputs/visualizations/11_seasonal_delivery_time_analysis.png)

---

### 4. Geographic Delivery Gaps

![Worst States](outputs/visualizations/11_worst_performing_states.png)
![Delivery Heatmap](outputs/visualizations/03_delivery_heatmap.png)

| State | Avg Delivery (days) | Late Rate | Avg Rating |
|---|---|---|---|
| SP | 8.3 | 5% | 4.2 ⭐ |
| PA | 22.6 | 11% | 3.9 ⭐ |
| MA | 21.3 | 18% | 3.7 ⭐ |
| CE | 20.4 | 14% | 3.9 ⭐ |
| AL | 24.5 | 26% | — |

**AL has a 26% late delivery rate** — more than 1 in 4 orders arrives late.

---

### 5. Delivery → Satisfaction Correlation

![Review by Delivery](outputs/visualizations/06_review_by_delivery_time.png)
![Review Score Comparison](outputs/visualizations/12_review_score_comparison.png)

| Delivery Speed | Avg Review Score |
|---|---|
| Fastest (<5 days) | 4.3 ⭐ |
| Fast (5–10 days) | 4.2 ⭐ |
| Normal (10–15 days) | 3.9 ⭐ |
| Slow (15–25 days) | 2.9 ⭐ |
| Ultra-Slow (25+ days) | 2.1 ⭐ |

**Late deliveries drop avg review score from 4.22 → 2.48** — a 41% collapse.

---

### 6. Correlation Matrix

![Correlation Matrix](outputs/visualizations/05_correlation_matrix.png)

Key relationships:
- `delivery_time` ↔ `review_score`: **-0.30** (moderate negative — faster = happier)
- `delivery_delay` ↔ `review_score`: **-0.22**
- `freight_value` ↔ `product_weight`: **0.60** (heavier items cost more to ship — expected)
- `price` ↔ `payment_value`: **0.71** (strong — minimal discount distortion)

---

### 7. Customer Segmentation

| Segment | Count | Behavior |
|---|---|---|
| At-Risk | ~17,500 (39.9%) | One-time buyers who never returned |
| Loyal | ~12,500 (28.5%) | Repeat buyers — tolerant of delays |
| New Customers | ~7,200 (16.4%) | 2–3 orders, then dropped |
| Champions | ~7,000 (15.9%) | High-value, frequent, satisfied |

> **The At-Risk segment is the biggest opportunity.** Winning back even 15% of them would add ~2,600 repeat customers.

---

### 8. Day-of-Week Effect

![Day of Week](outputs/visualizations/13_avg_delivery_time_by_dayofweek.png)

Orders placed on **Thursday–Friday** take ~1.5 days longer than Monday orders — likely due to weekend warehouse closures delaying dispatch.

---

## 💡 Recommendations

### Logistics
- **Immediate**: Target logistics contracts in AL, MA, PI, CE — these 4 states alone account for the majority of late deliveries
- **Automate** outlier detection — 209-day deliveries are data and operations failures
- **Incentivize Thursday/Friday early dispatch** to eliminate weekend lag

### Revenue
- **Don't accept low seasons** — targeted promotions in Sep–Feb can close the ~40% seasonal gap
- **Double down on Bed & Bath + Health & Beauty** — highest volume, proven demand

### Customer Retention
- **At-risk re-engagement**: Email + discount campaign within 60 days of last purchase
- **Champion rewards**: Free priority shipping for top 10% LTV customers
- **New customer nurture**: 2nd purchase discount within 30 days of first order

### Operations
- **Freight tier model**: Offer standard/express options — data shows customers will pay for speed
- **Regional warehouse expansion** signals from the data: northern Brazil is consistently underserved

---

## 📁 Repository Structure

```
Olist-Data-analysis-SQL-Python-Power-BI-Case-study/
│
├── sql analysis/               # SQL scripts — extraction, joins, aggregations
├── python_analysis/            # Jupyter notebooks — EDA, segmentation, modeling
│   └── outputs/
│       └── visualizations/     # All 19 Python-generated charts
│
├── Olist_Dashboard.pbix        # Power BI source file (3-page dashboard)
├── Olist_dashboard 1.png       # Revenue & Sales overview
├── Olist_dashboard 2.png       # Customer segmentation
├── Olist_dashboard 3.png       # Delivery performance
├── requirements.txt
└── README.md
```

---

## ⚙️ Setup & Usage

```bash
# Clone the repo
git clone https://github.com/haseeb774/Olist-Data-analysis-SQL-Python-Power-BI-Case-study.git
cd Olist-Data-analysis-SQL-Python-Power-BI-Case-study

# Install dependencies
pip install -r requirements.txt

# Run the analysis
cd python_analysis
jupyter notebook
```

**Dataset**: [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) — available free on Kaggle.

**Power BI Dashboard**: Open `Olist_Dashboard.pbix` in Power BI Desktop (free download from Microsoft).

---

## 📈 Results Summary

| Metric | Value |
|---|---|
| Total Revenue Analyzed | R$ 9.19M |
| Orders Analyzed | 45,000+ |
| On-Time Delivery Rate | 92.76% |
| Customer Satisfaction Rate | 77.23% |
| 5-Star Review Rate | 57.78% |
| At-Risk Customer Segment | 39.9% of base |
| Delivery Time Improvement (2016→2018) | 54 days → 7 days |

---

## 👤 Author

**Haseeb ur Rehman**  
Data Analyst · Python · SQL · Power BI

[![GitHub](https://img.shields.io/badge/GitHub-haseeb774-181717?style=flat&logo=github)](https://github.com/haseeb774)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat&logo=linkedin)](https://linkedin.com/in/haseeb-u-rehman-4822bb369)

---

<div align="center">
<i>If this project helped you or gave you ideas, consider leaving a ⭐</i>
</div>