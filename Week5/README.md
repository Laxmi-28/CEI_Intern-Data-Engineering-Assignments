# Week 5 Assignment — Apache Spark Basics
**Subject:** Big Data Processing with Apache Spark  
**Platform:** Databricks Community Edition  
**Language:** PySpark (Python)  
**Dataset:** Retail Sales Data — 510 rows, 10 columns

---

## 📁 Repository Structure

```
week5-spark-assignment/
│   └── sales_data.csv           ← Retail sales dataset (510 rows)
│   └── Week5-Assignment.ipynb   ← Main Databricks notebook
│   └── Week5-Answers.docx       ← Question and Answers document
│── README.md
```

---

## 🎯 Objective

Understand Apache Spark fundamentals and apply them to perform data cleaning, transformation, and aggregation using PySpark DataFrames on a retail sales dataset.

---

## 📊 Dataset Description

| Column | Type | Description |
|---|---|---|
| customer_id | Long | Unique customer ID |
| customer_name | String | Customer full name |
| age | Long | Customer age |
| gender | String | Male / Female / Other |
| city | String | City of purchase |
| region | String | North / South / East / West / Central |
| category | String | Product category |
| quantity | Long | Units purchased |
| unit_price | Double | Price per unit (₹) |
| revenue | Double | Total revenue (quantity × price) |

> Dataset intentionally contains ~10 duplicate rows and null values in `age` and `revenue` columns for cleaning practice.

---

## ✅ Steps Performed

| Step | Description |
|---|---|
| Step 2 | Created and verified Spark Session (Spark 4.1.0) |
| Step 3 | Loaded data from Unity Catalog table — 510 rows, 10 columns |
| Step 4 | Cleaned data: removed duplicates, filled null ages, dropped null revenue |
| Step 5 | Filtered data by age, category, and region |
| Step 6 | Transformed: renamed columns, added derived columns |
| Step 7 | Basic aggregations: avg, min, max, describe |
| Step 8 | GroupBy analysis: by region, category, age group, city |
| Step 9 | Understood narrow vs wide transformations, shuffle, lazy evaluation |
| Step 10 | Built full end-to-end pipeline |

---

## ❓ Assignment Questions Answered (Q1–Q15)

### Q1 — Limitations of MapReduce vs Spark
MapReduce reads from disk at every step, making multi-step jobs very slow. Spark keeps data in memory (RAM) between operations — up to 100x faster for iterative jobs. Spark also provides a simpler API (DataFrames, Python) vs MapReduce's verbose Java code.

### Q2 — In-Memory Computing for ML
In ML, algorithms iterate over the same dataset many times. MapReduce writes results to disk after every iteration. Spark caches the dataset in RAM using `.cache()` or `.persist()`, so each iteration reads from memory — dramatically reducing I/O time.

### Q3 — Remove Duplicates on Specific Columns
```python
df_clean = df.dropDuplicates(["user_id", "transaction_date"])
```

### Q4 — Filter West Region + GroupBy Category
```python
df_sales.filter(F.col("region") == "West") \
        .groupBy("product_category") \
        .agg(F.avg("sale_amount").alias("avg_sale_amount")) \
        .show()
```

### Q5 — .na.drop() vs .na.fill()
- `.na.drop()` removes rows that contain null values
- `.na.fill()` replaces null values with a specified value

```python
# Fill null values in status column with 'Unknown'
df = df.na.fill({"status": "Unknown"})
```

### Q6 — City Count Greater Than 100
```python
df.groupBy("city") \
  .agg(F.count("*").alias("record_count")) \
  .filter(F.col("record_count") > 100) \
  .show()
```

### Q7 — Immutability and Data Cleaning
Spark DataFrames are immutable — you cannot modify them in place. Every cleaning operation (drop, rename, cast) creates a new DataFrame. You must reassign: `df = df.drop("col")`. This ensures a full audit trail of transformations and makes pipelines reproducible.

### Q8 — Filter Age 18–30 and Premium Subscription
```python
df.filter(
    (F.col("age").between(18, 30)) &
    (F.col("subscription") == "Premium")
).show()
```

### Q9 — Handle Nulls Before Aggregations
Null values are silently ignored by `sum()` and `avg()`, which can produce misleading results. Filling or dropping nulls beforehand ensures calculations reflect the true data distribution and avoids unexpected None outputs.

### Q10 — Cast and Rename Timestamp Column
```python
from pyspark.sql.types import TimestampType

df = df.withColumn("event_time", F.col("raw_timestamp").cast(TimestampType())) \
       .drop("raw_timestamp")
```

### Q11 — Shuffle and Wide Transformations
A **shuffle** moves data across partitions (and machines) so rows with the same key end up together. `groupBy()` is a wide transformation because it requires data from multiple partitions to be combined — Spark must redistribute the data across the cluster, which involves disk I/O and network transfer, making it slower than narrow transformations like `filter()`.

### Q12 — Remove Null Email or Empty Username
```python
df_clean = df.filter(
    F.col("email").isNotNull() &
    (F.col("username") != "")
)
```

### Q13 — Multiple Statistics with .agg()
```python
df.agg(
    F.min("price").alias("min_price"),
    F.max("price").alias("max_price"),
    F.avg("price").alias("mean_price")
).show()
```

### Q14 — Risk of inferSchema with Messy Dates
`inferSchema=True` samples the data and guesses types. If date columns contain inconsistent formats (e.g., `2024-01-15` mixed with `15/01/2024`), Spark may infer the column as `String` instead of `Date`, silently breaking downstream date operations without throwing an error.

### Q15 — Final Processing Pipeline
```python
from pyspark.sql import functions as F

df = spark.read.table("sales_data")
df = df.dropDuplicates()
df = df.na.fill({"unit_price": 0})
result = df.groupBy("store_id") \
           .agg(F.sum("revenue").alias("total_revenue"))
display(result)
```

---

## 🔑 Key Spark Concepts Covered

| Concept | Description |
|---|---|
| SparkSession | Entry point to all Spark functionality |
| DataFrame | Distributed table — like pandas but scalable |
| Lazy Evaluation | Transformations build a plan; actions (show, count) execute it |
| Narrow Transformation | filter(), withColumn() — no data movement |
| Wide Transformation | groupBy(), join() — causes shuffle across partitions |
| Shuffle | Data redistribution across partitions (expensive) |
| Immutability | Every transformation returns a new DataFrame |

---

## 📤 Pipeline Output (Top Results)

| Region | Category | Orders | Total Revenue | Avg Revenue |
|---|---|---|---|---|
| North | Sports | 18 | ₹5,64,081 | ₹31,338 |
| East | Electronics | 16 | ₹4,81,563 | ₹30,098 |
| West | Sports | 16 | ₹4,26,054 | ₹26,628 |
| East | Sports | 21 | ₹4,05,814 | ₹19,324 |
| Central | Sports | 15 | ₹3,97,742 | ₹26,516 |

---

## 🚀 How to Run

1. Sign up at [community.cloud.databricks.com](https://community.cloud.databricks.com/)
2. Create a new notebook
3. Upload `sales_data.csv` via **Catalog → Add data → Create or modify table**
4. Import `Week5-Assignment.ipynb` via **Workspace → Import**
5. Attach cluster and click **Run All**
