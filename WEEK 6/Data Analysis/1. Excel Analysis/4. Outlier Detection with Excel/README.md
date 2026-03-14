# Outlier Detection with Excel (https://www.youtube.com/watch?v=sUTJb0F9eBw)

Outliers are data points that **differ significantly from other observations** in a dataset. Detecting outliers is important because they can affect statistical analysis and model accuracy.

Outliers may occur due to:

* Measurement variability
* Data entry errors
* Experimental errors
* Rare but meaningful observations

While outliers sometimes need to be removed, they can also provide **important insights** into unusual patterns in the data.

---

# Dataset Example

In this example, we use a **COVID-19 dataset** and analyze the column:

```
New Cases
```

This column represents the number of **new COVID-19 cases recorded daily**.

---

# Identifying Outliers Using Quartiles

Outliers can be detected using the **Interquartile Range (IQR) method**.

Key components:

| Metric      | Meaning                          |
| ----------- | -------------------------------- |
| Q1          | First Quartile (25th percentile) |
| Q3          | Third Quartile (75th percentile) |
| IQR         | Interquartile Range = Q3 − Q1    |
| Lower Bound | Q1 − 1.5 × IQR                   |
| Upper Bound | Q3 + 1.5 × IQR                   |

Any value:

```
< Lower Bound  OR  > Upper Bound
```

is considered an **outlier**.

---

# Step 1 — Calculate Quartiles

Excel provides the `QUARTILE.EXC` function.

### First Quartile (Q1)

```id="3qg1x1"
=QUARTILE.EXC(data_range,1)
```

---

### Third Quartile (Q3)

```id="5nyg1y"
=QUARTILE.EXC(data_range,3)
```

---

# Step 2 — Calculate Interquartile Range (IQR)

```id="b1hnzq"
IQR = Q3 - Q1
```

Excel formula:

```id="qk9y39"
=Q3 - Q1
```

---

# Step 3 — Calculate Lower Bound

Formula:

```id="w8w0hm"
Lower Bound = Q1 - (1.5 * IQR)
```

Excel formula:

```id="x3v0b0"
=Q1 - 1.5 * IQR
```

In some cases (like COVID cases), negative values are impossible.
If the lower bound becomes negative, it can be set to **0**.

---

# Step 4 — Calculate Upper Bound

Formula:

```id="7u4fex"
Upper Bound = Q3 + (1.5 * IQR)
```

Excel formula:

```id="t3db2j"
=Q3 + 1.5 * IQR
```

---

# Step 5 — Detect Outliers

Use the `IF` and `OR` functions to flag outliers.

Example formula:

```id="n33r9f"
=OR(A2 > Upper_Bound, A2 < Lower_Bound)
```

If the result is:

| Result | Meaning      |
| ------ | ------------ |
| TRUE   | Outlier      |
| FALSE  | Normal value |

Apply this formula to the entire dataset.

---

# Filtering Outliers

After computing the formula:

1. Apply **Filter** to the column
2. Filter by **TRUE**

This will display all rows containing **outliers**.

---

# Visualizing Outliers with Box Plots

Excel provides **Box & Whisker plots** to visualize outliers.

### Steps

1. Select the dataset column
2. Go to **Insert**
3. Click **Recommended Charts**
4. Choose **Box and Whisker Chart**

---

# Understanding the Box Plot

A box plot displays:

| Component               | Meaning        |
| ----------------------- | -------------- |
| Lower whisker           | Lower bound    |
| Q1                      | First quartile |
| Median                  | Middle value   |
| Q3                      | Third quartile |
| Upper whisker           | Upper bound    |
| Points outside whiskers | Outliers       |

This chart helps quickly identify **extreme values**.

---

# Handling Outliers

Once detected, you have several options:

### 1. Keep the Outliers

Useful when outliers represent **important rare events**.

Example:

* sudden pandemic spikes
* rare medical events

---

### 2. Remove the Outliers

Remove if they represent:

* data entry errors
* measurement mistakes
* impossible values

Example:

```
Negative COVID cases
```

---

### 3. Transform the Data

Alternative methods include:

* normalization
* log transformation
* winsorization
which would complete your **entire Data Analysis module in the repo**.
