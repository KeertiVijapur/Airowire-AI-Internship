# Data Analysis with Datasette (https://www.youtube.com/watch?v=7kDFBnXaw-c)

## Overview

Datasette is an **open-source tool for exploring, analyzing, and publishing datasets** using SQLite databases. It provides a powerful web interface that allows users to query, filter, visualize, and export data without writing complex code.

Datasette transforms any **SQLite database into an interactive data exploration platform** with built-in features such as filtering, faceting, visualization plugins, and API access.

This tool is particularly useful for:

* Data journalism
* Data exploration
* Publishing datasets
* Lightweight analytics platforms
* Sharing datasets with non-technical users

---

# Installation

Datasette can be installed using **pip** or **Homebrew**.

### Using pip

```bash
pip install datasette
```

### Using Homebrew

```bash
brew install datasette
```

---

# Running Datasette

To start exploring a SQLite database:

```bash
datasette mydatabase.db
```

This launches a local server:

```
http://localhost:8001
```

You can now explore your dataset using the Datasette interface.

---

# Creating a Sample Dataset

Example SQL schema for an **e-commerce dataset**:

```sql
CREATE TABLE customers (
    customer_id INTEGER PRIMARY KEY,
    name TEXT,
    email TEXT,
    region TEXT,
    signup_date TEXT
);

CREATE TABLE products (
    product_id INTEGER PRIMARY KEY,
    name TEXT,
    category TEXT,
    price REAL,
    cost REAL
);

CREATE TABLE orders (
    order_id INTEGER PRIMARY KEY,
    customer_id INTEGER,
    product_id INTEGER,
    order_date TEXT,
    quantity INTEGER,
    status TEXT,
    FOREIGN KEY(customer_id) REFERENCES customers(customer_id),
    FOREIGN KEY(product_id) REFERENCES products(product_id)
);
```

This dataset allows analysis of:

* customer behavior
* product sales
* regional trends
* order status patterns

---

# Key Datasette Features

## Filtering Data

Datasette allows filtering using query parameters.

Example:

```
?region=North
```

Example filter:

```
/orders?_where=quantity>2
```

---

# Faceting

Faceting helps summarize categorical data.

Example:

* Orders by region
* Orders by product category
* Orders by status

This allows quick insight into dataset distributions.

---

# Running SQL Queries

Datasette allows direct SQL queries from the interface.

Example:

```sql
SELECT
    region,
    COUNT(*) as total_orders
FROM orders
GROUP BY region
ORDER BY total_orders DESC;
```

This query shows **which region generates the most orders**.

---

# Exporting Data

Datasette supports exporting data in multiple formats:

* CSV
* JSON
* newline-delimited JSON

Example API call:

```bash
curl "http://localhost:8001/orders.json"
```

This enables easy integration with other tools.

---

# Creating Canned Queries

Datasette allows predefined SQL queries stored in metadata.

Example:

```json
{
  "databases": {
    "ecommerce": {
      "queries": {
        "top_customers": "SELECT customer_id, SUM(quantity * price) AS total FROM orders GROUP BY customer_id ORDER BY total DESC LIMIT 10"
      }
    }
  }
}
```

This creates a **Top Customers dashboard query**.

---

# Publishing Datasette

Datasette supports easy deployment to cloud platforms.

Example:

```bash
datasette publish cloudrun ecommerce.db --project my-analysis
```

This deploys the dataset as a **public interactive data explorer**.

---

# Example Use Cases

Datasette is used for:

* Publishing government datasets
* Data journalism projects
* Interactive research datasets
* Public data dashboards
* Lightweight analytics platforms

---

# Key Advantages

* Works directly with **SQLite databases**
* No heavy backend required
* Built-in **JSON API**
* Easy **data publishing**
* Plugin ecosystem for maps, charts, and dashboards
