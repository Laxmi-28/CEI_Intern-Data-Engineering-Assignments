# Week 1 Assignment - Data Exploration and Data Cleaning using Pandas

This assignment focuses on learning Python basics and performing data exploration and data cleaning using the Pandas library on a shopping dataset.

The objective of this assignment is to load a CSV dataset into a Pandas DataFrame, explore the dataset structure, identify and handle missing values, perform basic data operations such as selecting columns and filtering rows, check and remove duplicate records, create a derived column, and save the cleaned dataset as a new CSV file.

The dataset used for this assignment is the Combined Shopping Dataset obtained from Kaggle. Various Pandas functions were used to understand the dataset structure, analyze data types, handle missing values, perform filtering operations, and prepare the dataset for further analysis.

---

## Objective

The objectives of this assignment are:

1. Load a CSV dataset into a Pandas DataFrame.
2. Explore the dataset using functions such as `head()`, `tail()`, `shape`, `dtypes`, `info()`, and `describe()`.
3. Identify and handle missing values using appropriate techniques.
4. Perform basic operations such as selecting columns and filtering rows.
5. Check and remove duplicate records.
6. Create a derived column (`savings = initial_price - final_price`).
7. Save the cleaned dataset as a new CSV file.

---

## Dataset Information

**Dataset Name:** Shopping Dataset

**Source:** Kaggle

**Dataset Used:** `Combined_dataset.csv`

The dataset contains product information including product titles, descriptions, ratings, prices, discounts, seller details, reviews, and categories.

---

## Summary

The dataset was successfully loaded and explored using various Pandas functions. Missing values were identified and handled by filling numerical columns with appropriate statistical values and text columns with meaningful default values. Basic filtering and column selection operations were performed to analyze specific product categories, ratings, and discounts.

Duplicate records were checked and removed to ensure data quality. The `final_price` column was cleaned and converted into a numeric format to enable calculations. A new derived column named `savings` was created to calculate the difference between the initial price and final price of each product.

Finally, the cleaned dataset was exported as `cleaned_shopping_data.csv` and downloaded for further use.

---

## Files Included

- `Week1_assignment.ipynb` – Jupyter Notebook containing all code and outputs.
- `cleaned_shopping_data.csv` – Cleaned dataset after preprocessing.
- `README.md` – Project documentation.

---

## Technologies Used

- Python
- Pandas
- Google Colab

---

## Learning Outcomes

Through this assignment, I learned:

- Loading datasets using Pandas
- Exploring dataset structure and data types
- Handling missing values using `fillna()`
- Selecting and filtering data
- Working with column data types
- Checking and removing duplicate records
- Creating derived columns
- Exporting cleaned datasets to CSV files
- Performing basic data preprocessing using Pandas

---

## Conclusion

This assignment provided practical experience in data exploration and data cleaning using Python and Pandas. The dataset was successfully cleaned by handling missing values, filtering records, checking duplicates, converting data types, and creating a derived column (`savings`). The final cleaned dataset is more structured and ready for further data analysis and visualization.
