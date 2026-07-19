# E-Commerce Order Analytics System - Mini Project

## What this is

This is my intern mini project. The task was to build a small analytics
system on top of fake e-commerce data (orders, order items, products,
customers), clean it up, and then answer some business questions using SQL.

Everything is done in one notebook: `project.ipynb`.

## How to run

1. Make sure you have `pandas` installed (`pip install pandas`).
   `sqlite3` comes built-in with Python, no need to install it separately.
2. Open `project.ipynb` in Jupyter Notebook / Jupyter Lab / VS Code.
3. Run all cells from top to bottom (Run All). It will:
   - generate the 4 csv files with some intentional bad data
   - clean the data and save cleaned versions + a small report
   - create a SQLite database (`shop.db`) and run all the SQL questions
   - run a sample report using the small report tool
   - run the edge case tests at the end

Running the whole notebook takes a few seconds, no internet needed.

## Files generated when you run the notebook

- `customers.csv`, `products.csv`, `orders.csv`, `order_items.csv` - raw generated data (has issues on purpose)
- `customers_clean.csv`, `products_clean.csv`, `orders_clean.csv`, `order_items_clean.csv` - cleaned data
- `cleaning_report.txt` - short summary of issues found while cleaning
- `shop.db` - SQLite database used for all the SQL queries

## What's inside the notebook

- **Part 1** - generates the 4 csv files (with some issues like missing
  customer_id, wrong date format, negative quantity for returns, messy
  product names, some bad emails)
- **Part 2** - cleaning functions: `clean_orders()`, `clean_products()`,
  `validate_emails()`, `check_referential_integrity()`
- **Part 3** - all the SQL questions (revenue per category, top customers,
  running totals, dense rank, lag/lead, CTEs, ntile, cohort analysis, self
  join, etc.) run on SQLite
- **Part 4** - a simple `generate_report()` function that shows total
  orders/revenue/customers for a date range, top 3 products, and % change
  vs the previous period
- **Part 5** - some basic test functions for the edge cases mentioned in
  the assignment (bad order_id, discount > 100, quantity = 0, future dates)

## Notes / things I'd do differently with more time

- Right now `generate_report()` is just called with hardcoded sample dates
  instead of using `input()`, so the notebook can run start to finish
  without needing anyone to type anything.
- Data is randomly generated with `random.seed(42)`, so results will be the
  same every time it's run.
- Didn't add proper error handling everywhere, kept it simple since this is
  just a learning project.

