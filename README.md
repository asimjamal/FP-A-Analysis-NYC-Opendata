# 🧾 Public Finance FP&A Analysis – Budget vs Actuals & Anomaly Detection  
**Dataset:** [Revenue Budget & Financial Plan – City of New York (Open Data Portal)](https://data.cityofnewyork.us/City-Government/Revenue-Budget-Financial-Plan-Exec-Adpt-Prel/ugzk-a6x4)  

---

## 📘 Project Overview  

This project analyzes **New York City’s historical revenue budgets and actual receipts** to understand budget accuracy, detect anomalies, and visualize fiscal trends.  

The goal was to simulate the kind of **Financial Planning & Analysis (FP&A)** work done in enterprise finance — turning raw financial data into actionable insights through metrics, visualizations, and automation.

---

## 🎯 Objectives  

1. **Compare Budget vs Actuals** across revenue categories and fiscal years.  
2. **Quantify variance and forecast accuracy** by revenue stream.  
3. **Detect anomalies** — large deviations between planned and actual revenues.  
4. **Visualize fiscal performance** via an interactive Power BI dashboard.  
5. **Summarize insights** that inform financial decision-making and planning.

---

## 🧩 Dataset Details  

**Source:** NYC Open Data – *Revenue Budget & Financial Plan (Exec/Adpt/Prel)*  
**Scope:** Fiscal revenue projections and actual receipts for multiple years.  

The NYC Financial Plan dataset (51k records, FY2017–2025) captures multi-year budget and revenue actuals across ~70 revenue classes. The data is clean, with minimal nulls and strong fiscal coverage. Tax-related and intergovernmental revenue dominate, giving a robust base for FP&A-style KPI analysis — focusing on forecast accuracy, variance attribution, and anomaly detection.

**Key Columns Used:**
| Column | Description |
|---------|--------------|
| `Fiscal_Year` | City fiscal year |
| `Revenue_Class` | Main category (e.g., Taxes, Federal Aid, Misc Revenue) |
| `Revenue_Category` | Subcategory of revenue |
| `Adopted_Budget` | Final approved budget |
| `Executive_Budget` | Mid-year adjusted budget |
| `Actual_Receipts` | Actual realized revenue |
| `Revenue_Code` | Unique identifier for each source |

---

## 🧮 Analytical Approach  

### 1. Data Cleaning & Preparation  
- Imported and cleaned dataset using Python (`pandas`)  
- Standardized column names and numeric formatting  
- Filtered fiscal years for consistency and relevance  

### 2. KPI Calculations  
| KPI | Formula | Purpose |
|-----|----------|----------|
| **Variance ($)** | `Actual_Receipts - Adopted_Budget` | Dollar difference |
| **Variance %** | `(Variance / Adopted_Budget) * 100` | Relative deviation |
| **Forecast Accuracy** | `1 - abs(Variance %) / 100` | Measure of budget reliability |

### 3. Anomaly Detection  
Implemented rule-based and statistical checks:
- Flagged any revenue category with **Variance % > ±15%**
- Calculated Z-scores to highlight outliers beyond ±2 std dev  
- Summarized flagged items by year and revenue class  

### 4. Visualization  
Built an **interactive Power BI dashboard** featuring:
- Budget vs Actual trends by year  
- Variance waterfall chart  
- Forecast accuracy heatmap  
- Anomaly flags by revenue category  
- Drill-down filters for fiscal year and revenue class  

---

## 📊 Key Insights (Sample Findings)  

- **Federal Categorical Aid** consistently underperformed vs budget in multiple fiscal years.  
- **Property Tax Revenue** overperformed post-2018, driving strong actual results.  
- **2020–2021** showed major anomalies in multiple revenue sources, aligning with COVID-related impacts.  
- Average **budget forecast accuracy** across all categories was **~86%**, suggesting relatively conservative forecasting.

---

## 🛠 Tech Stack  

| Tool | Purpose |
|------|----------|
| **Python (pandas, numpy)** | Data cleaning & anomaly detection |
| **SQL** | Data exploration and summarization |
| **Power BI** | Dashboard design & visualization |
| **GitHub** | Version control & project documentation |
| **NYC Open Data API** | Data source ingestion |

---

## 🚀 How to Reproduce  

1. **Clone Repository**  
   ```bash
   git clone https://github.com/asimjamal/nyc-fpa-revenue-analysis.git
   cd nyc-fpa-revenue-analysis
