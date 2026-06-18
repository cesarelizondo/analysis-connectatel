# 📡 ConnectaTel Customer Analysis

> End-to-end exploratory data analysis (EDA), data cleaning, statistical analysis, and customer segmentation for a Latin American telecommunications company, using Python and Pandas.

---

## 📌 Project Overview

ConnectaTel is a telecommunications company operating across Latin America. This project analyzes customer behavior using data recorded through 2024, combining three datasets — **plan details**, **customer information**, and **real usage records** — to build a statistical customer profile, detect anomalous usage patterns, and segment customers for retention and pricing strategy purposes.

The analysis was developed as a complete, reproducible data analyst workflow: from raw, messy data to business-ready insights.

## 🗂️ Datasets

| File | Description |
|------|-------------|
| `plans.csv` | Current plan details: monthly price, included minutes, included GB, and per-unit overage costs (Básico / Premium). |
| `users_latam.csv` | Customer information: age, city, registration date, contracted plan, and churn date. |
| `usage.csv` | Detailed log of real service usage: individual call and text message records. |

## Project Preview

| Data Cleaning | Distribution & Outliers |
|---------------|--------------------------|
| Sentinel values (`-999`, `"?"`) and impossible future dates detected and corrected | Boxplots and histograms used to identify right-skewed usage and high-consumption outliers |

| Usage Segmentation | Age Segmentation |
|---------------------|-------------------|
| Customers classified into Bajo uso / Uso medio / Alto uso | Customers classified into Joven / Adulto / Adulto Mayor |

## 🔍 Key Insights

After cleaning and analyzing the dataset, several relevant findings were identified:

- `age` contained a `-999` sentinel value that distorted the mean and standard deviation; it was corrected using median imputation.
- `city` had both a `"?"` sentinel (2.4% of rows) and genuine missing values (11.7%), both treated as nulls due to lack of reliable imputation criteria.
- `reg_date` included 40 records with an impossible future year (2026), which were marked as null.
- `churn_date` is missing in 88.35% of rows, but this is not a data quality issue — it represents customers who are still active and have not churned.
- `duration` and `length` in the usage table showed high null rates (55% and 45%), confirmed to be **Missing At Random (MAR)**: `duration` only applies to calls and `length` only applies to text messages, by design.
- Outliers were detected in the upper tail of `cant_mensajes`, `cant_llamadas`, and `cant_minutos_llamada`; these were **kept** in the analysis, since they represent real high-consumption customer behavior rather than data errors.
- The contracted plan (Básico/Premium) shows **no meaningful correlation** with actual usage volume — customers in both plans message, call, and consume minutes at nearly identical rates.
- The **Alto uso** segment shows the highest churn rate (~14%) compared to Uso medio and Bajo uso (~11.4% each), suggesting usage intensity is linked to dissatisfaction or cancellation risk.
- Age groups (Joven, Adulto, Adulto Mayor) show very similar usage behavior; age alone is not a strong predictor of plan choice or consumption.

## 💡 Business Recommendations

Based on the analysis, the following recommendations could improve decision-making:

- Create an intermediate or "Plus" plan targeted at the Alto uso segment, with more included minutes/messages at a more competitive overage rate, to reduce the friction likely driving churn in that group.
- Implement automated alerts or plan-upgrade recommendations when Básico customers consistently approach their included limits.
- Design a proactive retention campaign focused on Alto uso customers, given their elevated churn rate.
- Reassess Premium plan pricing and value communication, since real usage does not differ significantly from Básico customers.
- Strengthen data validation at the point of capture to prevent sentinel values and impossible dates from entering the system.

```
Raw Data (plans, users, usage)
    │
    ▼
Data Loading & Structural Exploration
    │
    ▼
Data Quality Assessment (nulls, sentinels, invalid dates)
    │
    ▼
Data Cleaning (imputation, sentinel correction, date fixes)
    │
    ▼
Usage Aggregation per Customer
    │
    ▼
Statistical Summary
    │
    ▼
Distribution Analysis & Outlier Detection (IQR)
    │
    ▼
Customer Segmentation (by usage and age)
    │
    ▼
Executive Business Insights
```

## 🧩 Analysis Steps

1. **Load & Explore** — Import datasets, inspect shape, dtypes, and structure.
2. **Data Quality Assessment** — Detect nulls, sentinel values, and invalid/future dates.
3. **Data Cleaning** — Impute `age` with the median, convert sentinels to nulls, fix impossible dates, validate MAR patterns in `usage`.
4. **Usage Aggregation** — Summarize calls, messages, and call minutes per customer; merge with customer profile.
5. **Distribution & Outlier Analysis** — Histograms by plan, boxplots, and IQR-based outlier detection.
6. **Customer Segmentation** — Rule-based segmentation by usage level (Bajo / Uso medio / Alto) and age group (Joven / Adulto / Adulto Mayor).
7. **Executive Insights** — Translate findings into business-ready conclusions and recommendations.

## 🎯 Skills Demonstrated

✔ Data Cleaning

✔ Data Validation

✔ Exploratory Data Analysis (EDA)

✔ Descriptive Statistics

✔ Missing Value Treatment (MCAR/MAR diagnosis)

✔ Feature Engineering

✔ Outlier Detection

✔ Customer Segmentation

✔ Business Analytics

✔ Python Programming

✔ Pandas

✔ NumPy

✔ Data Visualization (Seaborn / Matplotlib)

## 📚 Statistical Concepts Applied

- Mean vs Median
- Descriptive Statistics
- Frequency & Categorical Analysis
- Missing Data Mechanisms (MAR)
- Sentinel Value Detection
- Outlier Detection (IQR method)
- Rule-Based Conditional Segmentation
- Date/Time Validation
- Data Pipelines

## 🛠️ How to Run This Notebook

1. Clone this repository:
   ```bash
   git clone https://github.com/<your-username>/<your-repo>.git
   ```
2. Open `Analysis-ConnectaTel.ipynb` in Jupyter Notebook, JupyterLab, or Google Colab.
3. Make sure `plans.csv`, `users_latam.csv`, and `usage.csv` are placed in a `/datasets` folder relative to the notebook (or update the file paths in the loading cell accordingly).
4. Install dependencies if needed:
   ```bash
   pip install pandas numpy seaborn matplotlib
   ```
5. Run all cells from top to bottom.

## Why This Project Matters

This project demonstrates the complete workflow expected from a Data Analyst:

- Inspecting raw, multi-source datasets
- Diagnosing and cleaning inconsistent data (sentinels, invalid dates, MAR nulls)
- Validating data quality decisions with evidence, not assumptions
- Exploring customer behavior across usage and demographic dimensions
- Applying statistical techniques (IQR outlier detection, distribution analysis)
- Producing segmentation and business-oriented insights tied to retention and pricing strategy

Rather than focusing only on code, the notebook emphasizes analytical thinking and decision-making using data — connecting each cleaning and segmentation decision back to its business implication.

## 👋 About Me

I'm an aspiring Data Analyst with a background in BFSI (Banking, Financial Services & Insurance) enterprise support, transitioning into data analytics with experience in:

- Python
- SQL
- Data Visualization
- Statistical Analysis
- Business Intelligence

I'm currently building a portfolio of end-to-end analytics projects focused on transforming raw, messy data into actionable business insights.
