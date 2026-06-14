# Superstore Sales Analysis using SQL

## Project Overview

This project demonstrates the use of advanced SQL concepts on the Superstore dataset. The raw dataset was loaded into a staging table (`superstore_raw`) and transformed into a structured relational model consisting of **Customers**, **Products**, and **Orders** tables. The project focuses on applying **Subqueries**, **Common Table Expressions (CTEs)**, **Window Functions**, and **Joins** to generate meaningful business insights.

## Database Design

### Customers Table

Contains unique customer information:

* Customer ID
* Customer Name
* Segment
* Country
* City
* State
* Postal Code
* Region

### Products Table

Contains unique product information:

* Product ID
* Product Name
* Category
* Sub-Category

### Orders Table

Contains transactional order data:

* Order ID
* Order Date
* Ship Date
* Ship Mode
* Customer ID
* Product ID
* Sales
* Quantity
* Discount
* Profit

## SQL Concepts Implemented

### Subqueries

* Identified orders with sales greater than the overall average sales.
* Retrieved the highest-value order for each customer.

### Common Table Expressions (CTEs)

* Calculated total sales for each customer.
* Identified customers whose sales exceeded the average customer sales.

### Window Functions

* Ranked customers based on total sales using `RANK()`.
* Assigned row numbers to orders within each customer using `ROW_NUMBER()`.
* Generated customer rankings using `DENSE_RANK()`.

### Joins

* Combined customer and order data to create customer-level sales reports and rankings.

## Business Insights Generated

### Customer Performance Analysis

* Top 5 customers by total sales.
* Bottom 5 customers by total sales.
* Customers who placed only one order.
* Customers with above-average total sales.
* Highest order value achieved by each customer.

## Key Learnings

* Data normalization from a single raw dataset into multiple related tables.
* Practical use of Subqueries, CTEs, and Window Functions.
* Customer segmentation and ranking techniques.
* Generating business-focused insights from transactional sales data.
* Writing efficient analytical SQL queries for reporting and decision-making.

## Technologies Used

* Databricks SQL
* SQL
* Superstore Dataset

## Outcome

This project showcases the ability to transform raw business data into actionable insights using SQL. It demonstrates strong understanding of database design, data analysis, query optimization, and advanced SQL techniques commonly used in real-world data analytics and data engineering projects.

