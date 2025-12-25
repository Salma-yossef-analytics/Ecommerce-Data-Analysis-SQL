# 🛒 Ecommerce Data Analysis: Resolving SQL Data Quality Issues

This project demonstrates how to handle **Data Quality Issues** in SQL databases, specifically focusing on inconsistent date formats that lead to incorrect chronological sorting.

## 📌 Problem Description
When importing data from CSV files to SQLite, dates are often stored as `TEXT` (Strings). If the date format is inconsistent (e.g., `D/M/YYYY`), standard SQL aggregation functions like `MIN()` and `MAX()` sort the values **alphabetically** instead of **chronologically**.

* **Example of the Issue:** SQL identifies `1/10/2011` as the minimum date because it starts with "1", while `9/9/2011` is identified as the maximum because it starts with "9".

## 🚀 Solutions Implemented

In this notebook (`sql_data_quality_issue.ipynb`), I implemented two professional approaches to resolve this:

### 1. Pre-processing Transformation (Recommended)
* **Method:** Convert the `InvoiceDate` column to a standard Python `datetime` object using Pandas **before** loading it into the SQLite database.
* **Result:** SQL now recognizes the column as a valid timestamp, enabling accurate time-series analysis.
* **Accuracy:** 100% correct chronological sorting.

### 2. Post-processing Transformation
* **Method:** Fetch the raw string data from SQL and perform the transformation within the Pandas environment.
* **Use Case:** Ideal when working with "Read-Only" databases where the schema cannot be modified.

## 📊 Results Comparison

| Feature | Raw SQL (String) | Cleaned Data (Datetime) |
| :--- | :--- | :--- |
| **Oldest Invoice** | 1/10/2011 (Incorrect) | 2010-12-01 (Correct) |
| **Latest Invoice** | 9/9/2011 (Incorrect) | 2011-12-09 (Correct) |

## 🛠️ Tools Used
* **Python** (Core Logic)
* **Pandas** (Data Cleaning & Transformation)
* **SQLite3** (Database Management)
* **Jupyter Notebook** (Documentation & Execution)

---
**Author:** Salma Yossef
