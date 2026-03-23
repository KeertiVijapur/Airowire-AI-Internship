# Data Visualization & Forecasting in Excel (http://youtube.com/watch?v=judFpVgfsV4 , https://www.youtube.com/watch?v=sORnCj52COw&t=1813s)

## Excel – Time Series Analysis & Visualization

Excel is a powerful tool for **exploratory data analysis (EDA)** and **time-series visualization**. It allows users to analyze trends, forecast future values, and understand relationships between variables using simple built-in features.

---

## What is this about?

This module focuses on:

* Exploring **time-series financial data**
* Visualizing trends using simple Excel tools
* Performing **forecasting and volatility analysis**
* Understanding relationships between variables

---

## Key Features Used

* Pivot Tables for structured data analysis
* Sparklines for quick trend visualization
* Forecasting using GROWTH function
* Standard deviation for volatility measurement
* Scatter plots with trendlines
* Correlation and R² analysis
* Correlation matrix using Data Analysis ToolPak

---

## Data Visualization Techniques

### 1. Sparklines (Trend Visualization)

Sparklines are small charts inside cells that show trends over time.

* Helps compare multiple variables quickly
* Shows upward/downward movement patterns

---

### 2. Pivot Tables

Used to organize and summarize time-series data.

* Convert raw data into structured format
* Enable easy visualization and calculations

---

## Forecasting

Excel provides the **GROWTH function** to predict future values.

```excel
=GROWTH(known_y_values, known_x_values, new_x)
```

Used to:

* Predict next-day values
* Estimate trends based on historical data

---

## Measuring Volatility

Volatility is measured using **standard deviation**.

```excel
=STDEV(range)
```

To make it more meaningful:

```excel
Volatility = Standard Deviation / Mean
```

* Helps compare fluctuations across variables
* Identifies stable vs highly volatile data

---

## Scatter Plots & Trendlines

Scatter plots help visualize relationships between two variables.

Steps:

1. Select two data columns
2. Insert → Scatter Plot
3. Add Trendline

---

## R² (Coefficient of Determination)

R² shows how well one variable explains another.

* Value ranges from 0 to 1
* Higher value = stronger relationship

---

## Correlation Analysis

Using Excel:

```excel
=CORREL(range1, range2)
```

* Measures relationship between variables
* Values range from -1 to +1

---

## Correlation Matrix

Created using **Data Analysis ToolPak**:

Steps:

1. Go to **Data → Data Analysis**
2. Select **Correlation**
3. Choose input range
4. Generate matrix

---

### Insights from Correlation Matrix

* Strong positive correlation → variables move together
* Negative correlation → opposite movement
* Weak correlation → little or no relationship

---

## Use Cases

* Financial data analysis
* Stock & currency trend analysis
* Forecasting future values
* Identifying relationships between variables
* Exploratory data analysis (EDA)
