# Retail Vendor Performance & Procurement Analytics

An end-to-end data analytics project evaluating vendor profitability, procurement efficiency, and inventory turnover across multi-table retail datasets. This repository demonstrates automated ETL scripting in Python, relational database modeling in SQLite, exploratory data analysis, and an executive business intelligence dashboard in Power BI.

---

## 📌 Project Overview

Retail and wholesale businesses frequently face hidden margin losses due to supplier dependency, high holding costs from slow-moving stock, and inefficient pricing tiers. 

This project establishes a complete data pipeline to solve these challenges:
1. **Automated ETL & Database Ingestion:** Python scripts with built-in logging and execution benchmarking to ingest multi-table CSV datasets (over 2 GB) into a structured SQLite database.
2. **SQL Query Optimization & Data Aggregation:** Addressing memory bottlenecks caused by large transactional datasets (~10M+ sales records) using modular SQL aggregations and CTEs to build a clean `vendor_sales_summary` table.
3. **Exploratory Data Analysis (EDA):** Preprocessing, handling missing values/white spaces, outlier diagnosis, feature engineering (Gross Profit, Profit Margin, Stock Turnover), and correlation analysis.
4. **Interactive Power BI Dashboard:** Translating derived metrics into visual business intelligence using custom DAX measures, summary tables, KPI cards, and cross-filtering visuals.

---

## 🛠️ Tech Stack & Skills

- **Languages:** Python (Pandas, NumPy, Matplotlib, Seaborn)
- **Database:** SQLite, SQLAlchemy
- **Data Engineering / Pipeline:** Python Scripting, File I/O, Automated Logging (`logging` module), Query Optimization
- **Business Intelligence:** Microsoft Power BI, DAX (Data Analysis Expressions), Power Query
- **Analytical Concepts:** Inventory Turnover, Procurement Concentration (Pareto Analysis), Unit Cost Elasticity, Gross Margin Optimization

---

## 🏗️ Architecture & Pipeline Flow

```text
Raw CSV Files (2GB+)
  ├── Begin/End Inventory
  ├── Purchases & Purchase Prices
  ├── Vendor Invoices
  └── Sales (10M+ rows)
         │
         ▼ (ingestion_db.py - Python & SQLAlchemy with Logging)
SQLite Database (`inventory.db`)
         │
         ▼ (get_vendor_summary.py - Optimized Multi-Table SQL Joins & Cleaning)
Pre-Aggregated Analytical Table (`vendor_sales_summary`)
         │
         ├───► Python Jupyter Notebook (EDA, Correlation, Margin & Turnover Analysis)
         └───► Microsoft Power BI (.pbix) (DAX Modeling & Interactive Dashboard)
