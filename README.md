# CSV to MySQL ETL Pipeline

## Overview

This project implements a simple ETL (Extract, Transform, Load) pipeline using Python. The pipeline reads sales data from a CSV file, performs data cleaning and transformation, and loads the processed data into a MySQL database.

## Technologies Used

- Python
- Pandas
- NumPy
- SQLAlchemy
- PyMySQL
- MySQL

## ETL Process

### 1. Extract

- Read sales data from a CSV file using Pandas.
- Validate successful file loading.
- Display sample records for verification.

### 2. Transform

The following transformations are applied:

- Standardize column names:
  - Convert to lowercase
  - Replace spaces with underscores
  - Convert camel case to snake case

- Convert `order_date` to datetime format.

- Convert `sales_amount` to numeric format.

- Create derived fields:
  - `unit_price`

- Categorize sales transactions:
  - High Value (≥ 500)
  - Medium Value (≥ 100)
  - Low Value (< 100)

- Remove invalid records with non-positive sales values.

- Add ETL load timestamp for audit tracking.

### 3. Load

- Connect to MySQL using SQLAlchemy.
- Insert transformed records into the target table.
- Load data in batches for improved performance.

## Project Structure

```text
etl_csv_to_mysql/
│
├── data/
│   └── sales.csv
│
├── etl.py
├── requirements.txt
└── README.md
