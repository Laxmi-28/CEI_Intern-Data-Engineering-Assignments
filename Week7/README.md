# Delta Lake Assignment – Incremental Data Processing

## Objective

The objective of this assignment is to perform **incremental data processing using Delta Lake** in Databricks. The project demonstrates how to load customer data into a Delta table, clean the data, apply incremental updates using the **MERGE** operation, and validate the final results.

---

## Technologies Used

- Databricks Community/Free Edition
- Apache Spark (PySpark)
- Delta Lake
- Unity Catalog
- Python

---

## Project Structure

```
Week7_Assignment/
│   ├── customer_master.csv
│   └── customer_incremental.csv
│   └── Week7_assignment.ipynb
|   └── README.md
```

---

## Dataset Description

### customer_master.csv
Contains the existing customer records.

Columns:

- customer_id
- first_name
- last_name
- email
- city
- state
- signup_date
- loyalty_points
- status
- last_updated

### customer_incremental.csv

Contains new customer records along with updates to existing customers.

---

## Assignment Workflow

### Step 1 – Load Customer Master Dataset

- Upload the CSV file to a Unity Catalog Volume.
- Read the dataset using `spark.read.csv()`.
- Display the dataset.
- Verify the total number of records.

---

### Step 2 – Data Cleaning

Performed the following cleaning operations:

- Removed duplicate records using `dropDuplicates()`
- Filled missing values using `fillna()`
- Verified null values in each column

---

### Step 3 – Create Delta Table

The cleaned customer dataset was saved as a Delta table using:

```python
saveAsTable("customer_master")
```

---

### Step 4 – Read Incremental Dataset

Loaded the incremental customer dataset containing:

- Existing customers (to be updated)
- New customers (to be inserted)

---

### Step 5 – Apply MERGE Operation

Used Delta Lake's `MERGE` command to perform incremental processing.

The merge operation:

- Updates existing customers based on `customer_id`
- Inserts new customers if they do not already exist

```python
target.customer_id = source.customer_id
```

This demonstrates **Slowly Changing Dimension (SCD Type 1)** behavior, where existing records are overwritten with the latest values.

---

### Step 6 – Validation

Validated the results by:

- Checking the final row count
- Checking duplicate customer IDs
- Displaying the final dataset

---

## Results

- Customer data successfully loaded into a Delta table.
- Duplicate records removed.
- Missing values handled.
- Incremental updates applied using Delta Lake MERGE.
- Existing customer records updated.
- New customer records inserted.
- Validation confirmed successful processing.

---

## Learning Outcomes

Through this assignment, I learned:

- Reading CSV files using PySpark
- Data cleaning using Spark DataFrames
- Creating Delta tables
- Using Delta Lake MERGE for incremental processing
- Updating existing records
- Inserting new records
- Validating processed data
- Working with Unity Catalog in Databricks

---

## Author

**Kothapally Laxmi Prasanna**

B.Tech – Data Science  
CVR College of Engineering

---
