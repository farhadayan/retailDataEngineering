# Retail Data Engineering Project — Azure Databricks, ADF, and Python

This project demonstrates a **complete end-to-end Data Engineering pipeline** built with **Azure Databricks**, **Azure Data Factory**, and **Azure SQL Database** (or local SQLite for demo).  
It showcases how to design and orchestrate a **medallion architecture (Bronze → Silver → Gold)** pipeline, suitable for portfolio or interview demonstrations.

---

## Project Overview

### Objective
To build a simple yet realistic retail data pipeline:
1. Ingest raw data (CSV / JSON) into a data lake (Bronze layer)
2. Clean, transform, and standardize into the Silver layer using **Databricks (PySpark)**
3. Enrich and aggregate into business-ready Gold tables
4. Load curated data into **Azure SQL Database** for analytics consumption
5. Orchestrate all steps using **Azure Data Factory (ADF)**


Transformation Logic
Bronze → Silver

Read raw data (sales.csv, products.csv, customers.json)

Clean missing values
Convert data types
Write standardized data to /processed/ as Parquet

Silver → Gold

Join Customers, Products, and Sales
Compute derived columns (e.g. TotalAmount = Quantity * Price)
Create dimension and fact tables
Store in /curated/ for analytics

Gold → Azure SQL

Write curated tables to Azure SQL Database (or export as CSV for demo)
Ready for Power BI or other visualization tools

