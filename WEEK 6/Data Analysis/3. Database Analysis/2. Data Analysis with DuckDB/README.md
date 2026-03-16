# Data Analysis with DuckDB (https://www.youtube.com/watch?v=4U0GqYrET5s)

## Overview

DuckDB is a **high-performance analytical database designed for fast data analysis**. It is optimized for **OLAP workloads** and works extremely well with **Pandas, Parquet files, and Jupyter notebooks**.

DuckDB enables analysts to run **SQL queries directly on files such as Parquet, CSV, or Pandas DataFrames** without needing a separate database server.

It is particularly useful for:

* Large-scale data analysis
* Fast analytical queries
* Working with Parquet datasets
* Combining SQL with Python data workflows

---

# Why DuckDB?

DuckDB offers several advantages over traditional data analysis workflows.

### 1. Parallel Processing

DuckDB uses **parallel query execution**, making it significantly faster than many Python-based operations.

### 2. Columnar Storage

DuckDB processes data using **columnar storage**, which improves analytical query performance.

### 3. On-Disk Operations

Unlike Pandas which loads all data into memory, DuckDB can **query data directly from disk**.

### 4. SQL-Based Analysis

DuckDB supports **standard SQL**, allowing analysts to run complex queries efficiently.

---

# Parquet File Format

DuckDB works especially well with **Parquet**, a columnar storage format designed for analytics.

Benefits of Parquet:

* Smaller file size
* Faster read/write operations
* Built-in compression
* Strong typing

Example comparison:

| Format  | Size       | Read Speed |
| ------- | ---------- | ---------- |
| CSV     | Large      | Slower     |
| JSON    | Very Large | Slow       |
| SQLite  | Medium     | Moderate   |
| Parquet | Small      | Very Fast  |

Parquet is commonly used in **big data analytics pipelines**.

---

# Installing DuckDB

Install DuckDB using pip:

```bash
pip install duckdb
```

---

# Basic Usage with Python

Example of running a SQL query using DuckDB:

```python
import duckdb

result = duckdb.sql("""
SELECT departure_delay,
       COUNT(DISTINCT distance) AS routes
FROM '2015_flights.parquet'
GROUP BY departure_delay
ORDER BY departure_delay
""").df()

print(result)
```

This query directly reads the **Parquet file without loading it into memory first**.

---

# Querying Pandas DataFrames

DuckDB can directly query Pandas DataFrames using SQL.

```python
import pandas as pd
import duckdb

df = pd.read_parquet("2015_flights.parquet")

result = duckdb.sql("""
SELECT departure_delay,
       COUNT(DISTINCT distance)
FROM df
GROUP BY departure_delay
""").df()
```

This allows analysts to **mix Pandas and SQL workflows seamlessly**.

---

# Performance Comparison

Example task:
Counting unique routes by delay bucket.

### Pandas

```python
df.groupby("departure_delay")["distance"].nunique()
```

Execution time: ~10 seconds

### DuckDB

```python
duckdb.sql("""
SELECT departure_delay,
       COUNT(DISTINCT distance)
FROM df
GROUP BY departure_delay
""")
```

Execution time: ~0.4 seconds

DuckDB can be **20× faster** for analytical queries.

---

# Ranking Data Example

Example SQL query to rank arrival delays:

```sql
SELECT *,
       RANK() OVER (
           PARTITION BY distance
           ORDER BY arrival_delay
       ) AS delay_rank
FROM flights
```

This calculates the **rank of arrival delay for each flight route**.

---

# Joining Datasets

DuckDB supports SQL joins for combining datasets.

Example:

```sql
SELECT f.arrival_delay,
       COUNT(*) * c.cost AS total_cost
FROM flights f
JOIN delay_cost c
ON f.arrival_delay = c.delay
GROUP BY f.arrival_delay
```

This query calculates the **total cost of flight delays**.

---

# Mixing DuckDB and Pandas

DuckDB integrates smoothly with Python workflows.

Example:

```python
distance_segments = duckdb.sql("""
SELECT *,
CASE
    WHEN distance < 1000 THEN 'short'
    WHEN distance < 2000 THEN 'medium'
    ELSE 'long'
END AS category
FROM df
""").df()
```

You can then continue analysis in **Pandas**.

---

# Key Advantages

* Extremely fast analytical queries
* Works directly with **Parquet files**
* Supports **SQL + Python workflows**
* Handles **large datasets efficiently**
* No database server required

If you want, I can also help you **turn your entire repo into a professional “Data Engineering & Data Science Toolkit” GitHub project**, which would make it **very strong for internships or research applications.**
