# Data Analysis with Python (Pandas) - (https://www.youtube.com/watch?v=ZPfZH14FK90)

Python has become one of the most widely used languages for **data analysis**, primarily due to the powerful **Pandas library**. Pandas provides efficient tools for working with structured data and performing statistical analysis.

Common tasks performed with Pandas include:

* Data loading and preprocessing
* Data inspection and exploration
* Pivot tables and aggregations
* Correlation and statistical testing
* Time series analysis
* Data visualization

---

# Dataset Overview

In this example, we analyze a **credit card transaction dataset** stored in **Parquet format**.

Each row represents a **credit card transaction** and includes information such as:

* Transaction ID
* Transaction date and time
* Transaction amount
* Decision (Approved / Declined)
* Dispute type
* Jurisdiction (Domestic / Cross-border)
* Issuer region
* Acquirer region

---

# Why Use Parquet Files?

Parquet is a columnar storage format designed for efficient data processing.

Advantages:

| Feature            | Benefit                           |
| ------------------ | --------------------------------- |
| Faster reading     | Optimized for analytics workloads |
| Smaller file size  | Highly compressed                 |
| Efficient querying | Column-based storage              |

Compared to CSV files, Parquet files are typically **5–10× smaller and faster to process**.

---

# Reading a Parquet File with Pandas

First import the Pandas library.

```python
import pandas as pd
```

Load the dataset:

```python
df = pd.read_parquet("transactions.parquet")
```

Preview the dataset:

```python
df.head()
```

View all column names:

```python
df.columns
```

---

# Understanding the Dataset

Each record represents a **single credit card transaction**.

Important columns include:

| Column           | Description                       |
| ---------------- | --------------------------------- |
| transaction_id   | Unique transaction identifier     |
| transaction_date | Date of the transaction           |
| transaction_time | Time of the transaction           |
| amount           | Transaction amount                |
| decision         | Approved or Declined              |
| dispute_type     | Fraud or non-fraud dispute        |
| jurisdiction     | Domestic or cross-border          |
| issuer_region    | Card issuing region               |
| acquirer_region  | Region where transaction occurred |

---

# Exploratory Data Analysis

Before performing analysis, it is useful to explore the dataset:

```python
df.info()
df.describe()
df.head()
```

These functions provide insights into:

* data types
* summary statistics
* missing values
* column structure

---

# Pivot Table Analysis

Pivot tables summarize data by grouping and aggregation.

Example: Analyze **disputes by region**.

```python
df.pivot_table(
    values="transaction_id",
    index="acquirer_region",
    columns="dispute_type",
    aggfunc="count"
)
```

This produces a table showing the **number of disputes per region**.

---

# Converting Counts to Percentages

Sometimes percentages provide better insight than raw counts.

Example:

```python
pivot = df.pivot_table(
    values="transaction_id",
    index="acquirer_region",
    columns="dispute_type",
    aggfunc="count"
)

pivot_percent = pivot.div(pivot.sum(axis=1), axis=0) * 100
```

This shows the **percentage distribution of dispute types by region**.

---

# Correlation Analysis

Correlation measures the **relationship between two variables**.

Example: Check whether **transaction amount affects approval**.

First convert categorical values into numeric form.

```python
df["approved"] = (df["decision"] == "Approved").astype(int)
```

Calculate correlation:

```python
df[["amount", "approved"]].corr()
```

Example result:

```text
Correlation = -0.009
```

Interpretation:

* Very weak negative relationship
* Larger transactions may be slightly more likely to be declined
* Relationship is extremely weak

---

# Testing Statistical Significance

To determine if the correlation is meaningful, perform a **Pearson correlation test**.

```python
from scipy.stats import pearsonr

corr, p_value = pearsonr(df["amount"], df["approved"])
```

Interpretation:

| Value          | Meaning                    |
| -------------- | -------------------------- |
| p-value < 0.05 | Significant relationship   |
| p-value > 0.05 | Relationship may be random |

Example result:

```text
p-value = 0.77
```

Conclusion:
The relationship between **amount and approval is not statistically significant**.

---

# Jurisdiction Analysis

We can also test whether **domestic vs cross-border transactions** affect approval rates.

Convert the jurisdiction column:

```python
df["domestic"] = (df["jurisdiction"] == "Domestic").astype(int)
```

Then compute correlation with approval:

```python
df[["approved", "domestic"]].corr()
```

If correlation is weak and p-value is high, jurisdiction may **not significantly affect approval rates**.

---

# Time-Based Analysis

To analyze patterns over time, combine the date and time columns.

```python
df["timestamp"] = pd.to_datetime(df["transaction_date"] + " " + df["transaction_time"])
```

Extract time features:

```python
df["hour"] = df["timestamp"].dt.hour
df["day"] = df["timestamp"].dt.day_name()
```

---

# Approval Rate by Hour and Day

Create a pivot table showing **approval percentage by hour and day**.

```python
pivot = df.pivot_table(
    values="approved",
    index="hour",
    columns="day",
    aggfunc="mean"
) * 100
```

---

# Heatmap Visualization

Visualizing approval rates as a heatmap makes patterns easier to identify.

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.heatmap(pivot, cmap="RdYlGn", annot=True)
plt.title("Approval Rate by Hour and Day")
plt.show()
```

Color interpretation:

* **Green** → Higher approval rates
* **Red** → Lower approval rates

---

# Key Insights

From the analysis:

* Fraud disputes vary slightly across regions.
* Transaction amount does **not strongly influence approval rates**.
* Jurisdiction (domestic vs cross-border) shows **weak correlation with approvals**.
* No strong hourly or daily pattern in approvals.

In real-world datasets, such analyses often reveal important patterns used by financial institutions.

---

# Role of AI in Data Analysis

Modern workflows often combine **Python tools with AI assistance**.

Large Language Models (LLMs) like ChatGPT can help with:

* generating Pandas code
* debugging errors
* suggesting analytical methods
* interpreting results

This approach significantly reduces the time required to move from **idea → analysis → insights**.
which can become a **very strong GitHub portfolio project.**
