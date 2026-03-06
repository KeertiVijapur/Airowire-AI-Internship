# Data Transformation in Excel

This module demonstrates how **Microsoft Excel** can be used to transform and analyze cleaned datasets.
Using a **city population dataset**, we perform ratio calculations, aggregation, and visualization to derive meaningful insights.

---

## Techniques Covered

### 1. Calculating Ratios

Computed ratios between dataset columns to understand relationships.

Examples:

* **Metro Area / City Area**
* **Metro Population / City Population**

Example formula:

```
=G2/D2
```

---

### 2. Density Comparison

Compared:

```
(Metro Population / City Population) ÷ (Metro Area / City Area)
```

to estimate **relative crowding levels between metro and city areas**.

---

### 3. Pivot Tables

Used **Pivot Tables** to:

* Aggregate data
* Count frequency of records
* Identify duplicates
* Summarize values by categories

Example:

* Rows → Country
* Values → Count of cities

---

### 4. Aggregations

Pivot tables were used to compute:

* Count of cities per country
* Sum of city populations
* Grouped summaries across countries

---

### 5. Charts from Pivot Tables

Created **bar charts** to visualize:

* Population distribution across cities
* Density comparisons
* Identification of **outliers**

Example insight:
Cities with significantly higher population or density can be quickly identified from the chart.

---

## Key Learnings

* Excel enables quick **data transformation and exploration**.
* **Ratios help reveal hidden relationships in datasets**.
* **Pivot tables provide powerful aggregation and summary capabilities**.
* Charts help visualize **patterns and outliers** in the data.

---

## Dataset

City population dataset containing:

* City name
* Country
* City population
* Metro population
* City area
* Metro area
