# Data Preparation in DuckDB (https://www.youtube.com/watch?v=Fg8n-O0dhrI&list=PLw2SS5iImhEThtiGNPiNenOr2tVvLj6H7&index=3)

DuckDB is a high-performance analytical SQL database designed for fast data analysis.  
It can process large datasets efficiently and is commonly used for **data cleaning, transformation, and exploratory analysis** directly using SQL.

In this section, we explore how DuckDB can be used for **practical data preparation tasks** such as handling messy datasets, converting formats, managing missing values, and performing exploratory data analysis.

---

## Creating a Sample Dataset

To simulate a real-world business scenario, we create a dataset representing customer orders with fields such as customer name, order date, product type, order amount, and region.

```sql
CREATE OR REPLACE TABLE orders AS
SELECT
    seq AS order_id,
    CASE WHEN seq % 5 = 0 THEN NULL ELSE 'Customer ' || seq END AS customer,
    DATE '2025-01-01' + CAST(seq % 15 AS INTEGER) AS order_date,
    CASE WHEN seq % 3 = 0 THEN 'Widget'
         WHEN seq % 3 = 1 THEN 'Gadget'
         ELSE 'Thing' END AS product,
    CASE WHEN seq % 4 = 0 THEN NULL ELSE seq * 10 END AS amount,
    CASE WHEN seq % 4 = 0 THEN 'EU' ELSE 'US' END AS region
FROM range(1, 50);
````

This dataset intentionally contains **missing values and mixed data types** to demonstrate realistic data preparation challenges.

---

## Creating a Messy CSV

Messy CSV files often occur in real-world datasets due to inconsistent formatting, missing values, or extra delimiters.

Example CSV structure:

```
order_id,customer,order_date,product,amount,region
1,Customer 1,2025-01-01,Widget,100,US
2,,2025-01-02,Gadget,,EU
3,Customer 3,2025-01-03,Thing,300,US
```

DuckDB can handle such files efficiently without requiring heavy preprocessing.

---

## Creating a Large Dataset

DuckDB allows creation and processing of large datasets quickly using SQL functions.

```sql
COPY (
    SELECT seq AS id, random() AS value
    FROM range(1000000)
) TO 'big.csv';
```

This generates a **large CSV dataset** useful for testing performance and analysis workflows.

---

## Exploratory Data Analysis (EDA)

Before cleaning data, it is useful to understand the dataset through quick exploratory queries.

```sql
SELECT * FROM orders LIMIT 5;

SELECT COUNT(*) AS total_orders,
       AVG(amount) AS avg_amount
FROM orders;
```

EDA helps identify **missing values, unusual patterns, and data inconsistencies**.

---

## Converting Data to Different Formats

DuckDB can export data into multiple formats such as **JSON and Parquet**.

```sql
COPY (SELECT * FROM orders) TO 'orders.json';
COPY (SELECT * FROM orders) TO 'orders.parquet' (FORMAT PARQUET);
```

These formats are widely used in **data pipelines and analytics workflows**.

---

## Reading Messy CSV Files

DuckDB can load messy CSV files while ignoring problematic rows.

```sql
SELECT *
FROM read_csv_auto('messy_orders.csv', ignore_errors=true);
```

This allows analysts to **inspect and clean problematic records later**.

---

## Handling Missing Values

Missing data can affect analysis results. DuckDB provides functions such as `COALESCE` to replace null values.

```sql
SELECT
    order_id,
    COALESCE(customer, 'Unknown') AS customer
FROM orders;
```

This replaces missing customer names with `"Unknown"`.

---

## String Operations

String functions help standardize inconsistent text values.

```sql
SELECT
    order_id,
    UPPER(product) AS product_name
FROM orders;
```

This converts product names to uppercase for consistent formatting.

---

## Date Parsing and Conversion

Dates from different formats can be standardized using SQL functions.

```sql
SELECT
    order_id,
    STRFTIME(order_date, '%Y-%m') AS order_month
FROM orders;
```

This extracts the **year and month** for time-based analysis.

---

## Conditional Logic

Conditional expressions help categorize data.

```sql
SELECT
    order_id,
    CASE
        WHEN amount > 200 THEN 'High Value'
        ELSE 'Standard'
    END AS order_type
FROM orders;
```

---

## Working with Multiple Formats

DuckDB can read and combine multiple file formats in a single query.

```sql
CREATE VIEW combined_data AS
SELECT * FROM 'orders.parquet'
UNION ALL
SELECT * FROM 'orders.json';
```

---

## Processing Data in Chunks

Large datasets can be processed efficiently using chunked operations.

```sql
SELECT *
FROM read_csv_auto('large_dataset.csv')
LIMIT 100;
```

---

## Filtering Rows and Dropping Columns

Unnecessary columns and rows can be removed to simplify analysis.

```sql
SELECT
    order_id,
    amount
FROM orders
WHERE region = 'US';
```

---

## Creating Derived Columns

New metrics can be calculated from existing data.

```sql
SELECT
    order_id,
    amount,
    amount * 0.1 AS tax_estimate
FROM orders;
```

---

## Summary and Pivot Analysis

Aggregations help summarize data and generate insights.

```sql
SELECT
    region,
    COUNT(*) AS total_orders,
    SUM(amount) AS total_revenue
FROM orders
GROUP BY region;
```

This provides a **summary of orders and revenue by region**.

---

## Key Takeaways

* DuckDB enables **fast SQL-based data preparation**
* Supports **large datasets efficiently**
* Handles **messy CSV files and missing data**
* Allows **data transformation and aggregation using SQL**
* Supports exporting to formats like **JSON and Parquet**

DuckDB is especially useful for **analytical workloads and data preprocessing pipelines**.
