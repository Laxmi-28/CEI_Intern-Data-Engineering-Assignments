# SQL Sales Data Analysis – Superstore Dataset

## Project Overview

This project demonstrates SQL-based exploratory data analysis on the Superstore dataset using Databricks SQL. The objective was to analyze sales performance, customer behavior, product profitability, and data quality through filtering, aggregation, sorting, and business-driven queries.

## Dataset Information

The dataset contains **9,994 sales transactions** with details about orders, customers, products, sales, profit, shipping, and geographical regions from **2016–2019**.

## Analysis Performed

### 1. Data Exploration

* Examined table schema and column data types.
* Retrieved sample records.
* Identified unique product categories.
* Extracted customer names and locations.

### 2. Data Filtering

Applied SQL WHERE clauses to:

* Filter records by region and category.
* Analyze high-value sales transactions.
* Retrieve date-specific orders.
* Identify loss-making orders.

### 3. Aggregation Analysis

Used GROUP BY to calculate:

* Total sales by region.
* Total profit by region.
* Average sales by category.
* Total quantity sold by category.
* Category-wise sales and profit.

### 4. Sorting and Ranking

Generated business insights by:

* Identifying top sales orders.
* Finding top revenue-generating products.
* Determining the most profitable categories and sub-categories.

### 5. Business Use Cases

Performed real-world business analysis including:

* Monthly sales trend analysis.
* Year-wise order distribution.
* Top customers by sales.
* Duplicate order identification.

### 6. Data Validation & Quality Checks

Validated data integrity by:

* Verifying total row count (9,994 records).
* Checking unique Row IDs.
* Detecting null values.
* Validating shipping dates.
* Identifying zero-sales transactions.

## Key Insights

* Sales show strong growth during year-end months, especially November and December.
* A small group of customers contributes significantly to total revenue.
* Technology and Office Supplies categories are major contributors to sales and profit.
* Some orders generate negative profit, indicating the impact of discounts and operational costs.
* Data quality checks confirmed the dataset is suitable for analysis.

## Tools & Technologies

* SQL
* Databricks
* Superstore Dataset

## Outcome

This project demonstrates practical SQL skills including data retrieval, filtering, aggregation, sorting, business reporting, and data validation, providing actionable insights from retail sales data.
