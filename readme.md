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
Bronze - Silver (Bronze_Silver-datatransformation)
Read raw data (sales.csv, products.csv, customers.json)

Clean missing values
Convert data types
Write standardized data to /processed/ as Parquet

Silver - Gold - build_table (Silver_Gold-transformation-build_table)

Join Customers, Products, and Sales
Compute derived columns (e.g. TotalAmount = Quantity * Price)
Create dimension and fact tables
Store in /curated/ for analytics
Write curated tables to Azure SQL Database (or export as CSV for demo)
Ready for Power BI or other visualization tools


Databricks Notebooks

Bronze_Silver-datatransformation.py	              Cleans and standardizes raw data	                            Raw CSV/JSON	                      Silver Parquet
Silver_Gold-transformation-build_table.py	        Joins, aggregates data and	Loads data to SQL                 Silver Parquet-Load data to Table	  Gold Parquet

Each notebook is written in PySpark and can be executed manually or triggered from ADF.

Azure Data Factory (ADF) Orchestration
Pipeline: p_ingest_transform_load
Web Activity 1 → Run bronze_to_silver Databricks notebook
Web Activity 2 → Run silver_to_gold_table notebook (depends on previous success) load to table (final stage)

(Optional) Copy Data Activity to ingest raw files from Blob/HTTP



Author

Mohammad Farhad Ahmed
Data Engineering Enthusiast
farhadayan@gmail.com
https://www.linkedin.com/in/farhad-ahmed/
https://github.com/farhadayan/retailDataEngineering
