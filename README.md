# ShopSpectra-BigData-Fraud-Analysis
"Scalable transaction analytics and fraud detection using PySpark on large datasets."
# ShopSpectra: Scalable Fraud and Revenue Analysis Using PySpark

This project presents a scalable data analysis pipeline applied to a transactional dataset using Apache Spark (PySpark). 
It demonstrates fraud detection, revenue aggregation, performance benchmarking under data scaling, and the application of a simple machine learning model for classification.

## Overview

The analysis covers:

- Parsing and preprocessing raw transaction data
- Revenue and fraud statistics by time (hour/day), transaction status, and merchant category
- Simulated scaling of the dataset to test Spark’s distributed processing efficiency
- Benchmarking groupBy operations at 1×, 2×, and 4× data volumes
- Persisting data using the Parquet format with partitioning
- Training a logistic regression classifier to predict fraud

## Objectives

- Perform scalable aggregation and analysis on transactional data
- Evaluate Spark performance at increasing data volumes
- Utilize partitioned storage for efficient big data querying
- Apply machine learning to detect fraudulent transactions

## Technologies Used

- **Apache Spark (PySpark)** – Big data processing
- **Pandas** – Local data manipulation
- **Matplotlib** – Visualization
- **Scikit-learn** – Logistic Regression model for fraud detection
- **Parquet** – Columnar storage format optimized for analytics

## Key Analysis Steps

1. **Data Ingestion**  
   Load CSV using PySpark with schema inference and permissive mode.

2. **Feature Engineering**  
   Normalize transaction statuses, extract timestamp features (`Hour`, `WeekDay`), and trim string fields.

3. **Data Aggregation**  
   Compute revenue, transaction counts, and fraud rates by:
   - Time of day and day of week
   - Transaction status
   - Merchant category

4. **Scalability Simulation**  
   Use `unionByName()` to create 2× and 4× scaled datasets from the base data and evaluate performance.

5. **Benchmarking**  
   Measure runtime of groupBy + aggregation at different scales to observe Spark's efficiency.

6. **Parquet Output**  
   Persist the 4× dataset to Parquet format, partitioned by merchant category for future re-aggregation.

7. **Machine Learning**  
   Train a logistic regression model on sampled Spark output to classify fraudulent transactions. Evaluate with ROC-AUC.

## Files

| File Name | Description |
|-----------|-------------|
| `ShopSpectra_Scalable_Fraud_Analysis.ipynb` | Full Jupyter notebook with PySpark code and outputs |
| `fraud_analysis.py` | Python script version of the notebook |
| `README.md` | Project documentation |

## How to Run

### Option 1: Google Colab (Recommended)

1. Upload the notebook and the CSV file
2. Run all cells (the notebook installs all required packages)

### Option 2: Local Environment

```bash
pip install pyspark pandas matplotlib scikit-learn
python fraud_analysis.py
