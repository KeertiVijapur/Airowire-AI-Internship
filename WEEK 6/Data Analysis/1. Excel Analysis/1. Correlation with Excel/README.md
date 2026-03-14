# Correlation Analysis with Excel (https://www.youtube.com/watch?v=lXHCyhO7DmY)

Correlation analysis helps us understand the **relationship between two variables**. It measures how strongly two variables are linearly related.

The **correlation coefficient** ranges from:

| Value  | Meaning                      |
| ------ | ---------------------------- |
| **+1** | Perfect positive correlation |
| **0**  | No correlation               |
| **-1** | Perfect negative correlation |

In this tutorial we analyze relationships between COVID-19 variables:

* **New Cases**
* **New Deaths**
* **New Vaccinations**

---

# Enabling the Excel Data Analysis ToolPak

Before performing correlation analysis, enable the **Data Analysis ToolPak**.

### Steps

1. Go to **File → Options**
2. Click **Add-ins**
3. At the bottom select **Excel Add-ins**
4. Click **Go**
5. Enable **Analysis ToolPak**
6. Click **OK**

After enabling it, you will see **Data Analysis** in the **Data tab**.

---

# Creating a Correlation Matrix

A **correlation matrix** shows correlation coefficients between multiple variables.

### Steps

1. Go to **Data → Data Analysis**
2. Select **Correlation**
3. Click **OK**

Configure:

* **Input Range** → select the variables
* **Labels in first row** → check if headers exist
* **Output Range** → choose where results appear

Example variables selected:

```
New Cases
New Deaths
New Vaccinations
```

---

# Example Correlation Results

Example correlation matrix:

| Variable         | New Cases | New Deaths | New Vaccinations |
| ---------------- | --------- | ---------- | ---------------- |
| New Cases        | 1         | **0.84**   | 0.20             |
| New Deaths       | 0.84      | 1          | **0.23**         |
| New Vaccinations | 0.20      | 0.23       | 1                |

### Interpretation

**New Cases vs New Deaths**

* Correlation ≈ **0.84**
* Strong positive correlation
* Higher cases are associated with higher deaths

**New Vaccinations vs New Deaths**

* Correlation ≈ **0.23**
* Weak positive correlation
* Relationship exists but is much weaker

---

# Visualizing Correlation with Scatterplots

Scatterplots help visualize relationships between variables.

### Creating a Scatterplot

1. Select the two variables
2. Go to **Insert → Recommended Charts**
3. Choose **Scatter Plot (XY Chart)**

Example:

```
X-axis → New Cases
Y-axis → New Deaths
```

---

# Adding a Trendline

A **trendline** helps visualize the relationship between variables.

Steps:

1. Click the chart
2. Go to **Chart Elements (+)**
3. Enable **Trendline**
4. Format the line (color, thickness)

Example:

* Red trendline
* Solid dashed style

---

# Example Insights

### New Cases vs New Deaths

* Strong upward trend
* Indicates strong positive correlation
* Higher infection rates are associated with higher deaths

### New Vaccinations vs New Deaths

* Much flatter trendline
* Weak positive correlation
* Indicates vaccinations may influence deaths, but further analysis is required

---

# Important Note

Correlation **does not imply causation**.

Although vaccination increases may coincide with decreasing deaths, additional statistical methods are needed to confirm causal relationships.

Further analysis may include:

* Regression analysis
* Time series forecasting
* Outlier detection
* Hypothesis testing
