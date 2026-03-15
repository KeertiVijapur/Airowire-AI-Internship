# Data Analysis with SQL (https://www.youtube.com/watch?v=Xn3QkYrThbI)

SQL is widely used for **analyzing structured data stored in databases**. It allows analysts to efficiently query, filter, aggregate, and analyze large datasets directly inside the database.

In many modern workflows, SQL is often combined with **Python libraries like Pandas and SQLAlchemy** to perform deeper analysis and visualization.

This section demonstrates how to perform **data analysis using SQL (via Python)**.

---

# Connecting to a Database

To query a database from Python, we can use **SQLAlchemy** together with **Pandas**.

Example:

```python
from sqlalchemy import create_engine
import pandas as pd

engine = create_engine("mysql+pymysql://user:password@localhost/database")

query = "SELECT * FROM posts LIMIT 10"

df = pd.read_sql(query, engine)
```

This loads the SQL query result directly into a **Pandas DataFrame**.

---

# Counting Rows in a Table

SQL can quickly compute statistics such as the number of rows.

```sql
SELECT COUNT(*) 
FROM posts;
```

This query returns the **total number of records** in the table.

---

# User Activity Analysis

We can identify the **most active users** by counting their posts.

```sql
SELECT owner_user_id, COUNT(*) AS post_count
FROM posts
GROUP BY owner_user_id
ORDER BY post_count DESC;
```

This helps identify **top contributors** in a community.

---

# Post Concentration Analysis

Often a **small percentage of users produce most of the content**.

Example SQL:

```sql
SELECT owner_user_id, COUNT(*) AS posts
FROM posts
GROUP BY owner_user_id
ORDER BY posts DESC
LIMIT 10;
```

This helps analyze:

* user engagement
* contribution inequality
* community dynamics

---

# Correlation Analysis

SQL can also compute **statistical relationships between variables**.

Example: Correlation between **user reputation and views**.

```sql
SELECT CORR(reputation, views) AS correlation_value
FROM users;
```

Interpretation:

| Value | Meaning                      |
| ----- | ---------------------------- |
| 1     | Perfect positive correlation |
| 0     | No relationship              |
| -1    | Perfect negative correlation |

---

# Regression Analysis

SQL can estimate the **regression slope between two variables**.

Example:

```sql
SELECT REGR_SLOPE(views, reputation) AS regression_slope
FROM users;
```

This helps measure how **reputation influences post views**.

---

# Working with Large Datasets

A key advantage of SQL is that **large datasets can be analyzed directly in the database** without loading everything into memory.

Example workflow:

1. Run SQL aggregations inside the database
2. Retrieve summarized results
3. Analyze further using Python

Example:

```python
query = """
SELECT region, COUNT(*) as total_transactions
FROM transactions
GROUP BY region
"""

df = pd.read_sql(query, engine)
```

---

# SQL for Statistical Analysis

SQL can perform several statistical operations including:

* Aggregations (`SUM`, `AVG`, `COUNT`)
* Correlations
* Regression
* Percentile calculations
* Window functions

Example:

```sql
SELECT 
    AVG(amount) AS average_transaction,
    MAX(amount) AS highest_transaction,
    MIN(amount) AS lowest_transaction
FROM transactions;
```

---

# Using AI to Generate SQL Queries

Modern workflows often combine **SQL with AI tools** like ChatGPT.

AI can help with:

* generating SQL queries
* debugging query errors
* suggesting analysis ideas
* translating business questions into queries

Example prompt:

```
Generate SQL to calculate the average transaction amount by region.
```

---

# Example Data Analysis Workflow

A typical workflow might look like:

1. Connect to database
2. Extract relevant data using SQL
3. Load data into Pandas
4. Perform statistical analysis
5. Visualize insights

Example:

```python
query = """
SELECT region, AVG(amount) as avg_transaction
FROM transactions
GROUP BY region
"""

df = pd.read_sql(query, engine)
```

This structure can turn your repo into a **very strong portfolio project for internships and research roles.**
