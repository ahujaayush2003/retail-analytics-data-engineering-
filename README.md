# retail-analytics-data-engineering-
End to End Azure Data Engineering project using ADF, Databricks, ADLS, and Power BI
End-to-End Azure Data Engineering Project

📌 Project Overview

This project demonstrates a production-style retail analytics data platform built using Azure Data Factory, Azure Data Lake Storage (ADLS), Databricks, and Power BI following the Medallion Architecture (Bronze → Silver → Gold).

The goal was to ingest raw retail transaction data, clean and transform it into analytics-ready datasets, and finally visualize business KPIs through an interactive Power BI dashboard.


🎯 Problem Statement

Retail organizations generate large volumes of transactional data that is often:
	•	Fragmented
	•	Unclean
	•	Difficult to analyze in real time

The challenge was to:
	•	Build a scalable ingestion pipeline
	•	Ensure data quality & reliability
	•	Enable business-friendly dashboards for decision-making


🏗️ Solution Architecture

The solution follows a layered data platform design:

🔹 Architecture Flow

Source → ADLS (Bronze) → ADF → Databricks (Silver & Gold) → Power BI

🔹 Medallion Architecture
	•	Bronze (Raw Layer)
Raw, immutable data ingestion using Azure Data Factory into ADLS.
	•	Silver (Cleaned Layer)
Data cleansing, deduplication, null handling, return logic, and standardization using Databricks (PySpark).
	•	Gold (Business Layer)
Aggregated KPIs and analytics-ready tables optimized for reporting.
	•	Consumption Layer
Power BI dashboards connected directly to Gold tables.

📌 (Architecture diagram included in this repository)


🧰 Tech Stack
	•	Azure Data Factory (ADF) – Ingestion & orchestration
	•	Azure Data Lake Storage Gen2 (ADLS) – Data storage
	•	Azure Databricks (PySpark + Delta Lake) – Processing & transformations
	•	Power BI Desktop – Data visualization & dashboards
	•	Delta Lake – ACID-compliant storage for analytics


🔄 Data Pipeline Breakdown

1️⃣ Bronze Layer – Raw Ingestion
	•	Raw retail CSV data ingested via ADF Copy Activity
	•	Stored in ADLS Bronze container
	•	Schema-on-read approach
	•	Data remains unchanged & immutable

📂 Notebook: Bronze_Ingestion.ipynb

2️⃣ Silver Layer – Data Cleaning & Transformation

Performed using Databricks (PySpark):
	•	Removed duplicates
	•	Handled null customer IDs
	•	Identified returns using negative quantities
	•	Standardized date & time columns
	•	Created derived fields:
	•	is_return
	•	line_total
	•	Time-based attributes (Year, Month, Hour, DayOfWeek)

📂 Notebook: Silver_Transformation.ipynb

3️⃣ Gold Layer – Business Aggregations

Created analytics-ready tables such as:
	•	Revenue by product
	•	Revenue by country
	•	Customer-level KPIs
	•	Monthly & yearly revenue trends
	•	Return rate analysis
	•	Time-based sales density
	•	Pareto (80/20) product analysis

All outputs stored as Delta tables for BI consumption.

📂 Notebook: Gold.ipynb

📊 Power BI Dashboard

An interactive Retail Analytics Dashboard built using Gold tables.


Key KPIs Visualized:
	•	💰 Total Revenue
	•	🧾 Total Orders
	•	📦 Units Sold
	•	⏰ Sales Density by Hour
	•	📈 Monthly Revenue Trends
	•	🌍 Sales by Country
	•	🔁 Return Rate by Product
	•	📆 Sales by Day / Month / Year

📸 (Dashboard screenshot included in this repository)


🚧 Challenges Faced
	•	Handling negative quantities for return transactions
	•	Managing null customer identifiers
	•	Designing reusable transformations
	•	Ensuring schema consistency across layers
	•	Optimizing data for BI performance


📌 Key Learnings
	•	Designing scalable ETL pipelines
	•	Implementing Medallion Architecture
	•	Delta Lake best practices
	•	Data modeling for BI
	•	End-to-end cloud data engineering workflow


🚀 Future Enhancements
	•	Incremental data loading
	•	Streaming ingestion
	•	Row-level security
	•	Power BI Service deployment
	•	Automated refresh scheduling
