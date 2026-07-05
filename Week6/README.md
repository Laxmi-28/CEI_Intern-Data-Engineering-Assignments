# Spark Architecture & Data Processing Assignment

## Overview

This project demonstrates the fundamentals of **Apache Spark** using **PySpark**. It covers Spark architecture, lazy evaluation, DataFrame transformations, schema handling, null value processing, aggregation, Parquet optimization, predicate pushdown, and an end-to-end data processing pipeline.

The assignment uses a sample **Bookstore Sales** dataset to perform data cleaning, transformation, analysis, and storage in different file formats.

---

## Objectives

- Understand Apache Spark Architecture
- Learn Driver, Cluster Manager, and Executors
- Understand Local Mode vs Cluster Mode
- Learn Lazy Evaluation and DAG Execution
- Read CSV files using an explicit schema
- Perform DataFrame transformations
- Filter and select required columns
- Rename columns and change data types
- Create new calculated columns
- Handle missing values
- Perform aggregation using `groupBy`
- Compare CSV and Parquet formats
- Understand Predicate Pushdown optimization
- Build an end-to-end Spark data processing pipeline

---

## Technologies Used

- Python
- PySpark 4.x
- Pandas
- Apache Spark

---

## Project Structure

```
Spark-Architecture-Assignment/
│
├── bookstore_sales.csv
├── output_csv/
├── output_parquet/
├── final_output/
├── Spark_Architecture_Assignment.ipynb
└── README.md
```

---

## Dataset

The sample dataset contains bookstore sales information.

### Columns

| Column | Description |
|---------|-------------|
| order_id | Unique order ID |
| customer_name | Customer Name |
| genre | Book Category |
| price | Price of the book |
| quantity | Quantity purchased |
| city | Customer City |
| rating | Customer Rating |

---

## Steps Performed

### 1. Spark Architecture

- Created SparkSession
- Understood:
  - Driver
  - Cluster Manager
  - Executors
  - Local Mode
  - Cluster Mode

---

### 2. Read CSV with Schema

Used an explicit schema instead of schema inference for faster and more reliable data loading.

```python
spark.read.csv(..., schema=schema)
```

---

### 3. Lazy Evaluation

Created transformations without immediate execution.

Execution starts only after actions like:

- show()
- count()
- write()

Used

```python
explain(True)
```

to visualize the execution plan.

---

### 4. Data Filtering

Filtered Fiction books.

Selected only required columns.

---

### 5. Data Transformation

Performed:

- Rename column
- Cast price to Double
- Created Total Amount

Formula:

```
Total Amount = Price × Quantity
```

---

### 6. Null Handling

Checked missing values.

Filled

- Rating → 4.0
- Quantity → 1

using

```python
na.fill()
```

---

### 7. Aggregation

Grouped data by Genre.

Calculated total sales using

```python
groupBy().sum()
```

This demonstrates a **Wide Transformation** involving shuffle.

---

### 8. CSV vs Parquet

Saved data into

- CSV
- Parquet

Compared both formats.

### Why Parquet?

- Columnar storage
- Better compression
- Faster queries
- Predicate Pushdown support

---

### 9. Predicate Pushdown

Filtered Parquet data

```python
total_amount > 500
```

Verified optimization using

```python
explain(True)
```

Spark pushed filters directly to the storage layer.

---

### 10. End-to-End Pipeline

Created a reusable pipeline that

- Reads CSV
- Casts data types
- Creates total_amount
- Handles null values
- Filters records
- Writes output as Parquet

---

## Output

The final pipeline produces cleaned data with

- Correct schema
- Calculated Total Amount
- Missing ratings handled
- Filtered records
- Parquet output

---

## Spark Concepts Covered

- Spark Architecture
- Driver
- Executors
- Cluster Manager
- Local Mode
- Lazy Evaluation
- DAG
- Transformations
- Actions
- DataFrame API
- Schema Handling
- Null Handling
- Aggregation
- Shuffle
- CSV
- Parquet
- Predicate Pushdown
- Reusable Pipeline

---

## Learning Outcomes

After completing this assignment, I learned how to

- Create Spark sessions
- Load structured datasets
- Work with Spark DataFrames
- Build transformations
- Understand Spark execution plans
- Handle missing values
- Perform aggregations
- Save data efficiently in Parquet
- Build reusable Spark pipelines
- Understand Spark performance optimizations

---

## How to Run

1. Install dependencies

```bash
pip install pyspark pandas
```

2. Open the notebook

```
Spark_Architecture_Assignment.ipynb
```

3. Run all cells sequentially.

---

## Author

**Laxmi Prasanna**

Apache Spark & PySpark Assignment
