# Forecasting with Excel (https://www.youtube.com/watch?v=QrTimmxwZw4)

Forecasting is the process of **predicting future values based on historical data**. Excel provides built-in forecasting functions that use **linear regression and time-series models** to estimate unknown values.

Common Excel forecasting functions include:

* `FORECAST`
* `FORECAST.LINEAR`
* `TREND`
* `FORECAST.ETS`

---

# FORECAST and FORECAST.LINEAR

The `FORECAST` function predicts a value using **linear regression**.
`FORECAST.LINEAR` is simply another name for the same function.

### Formula

```
FORECAST(x, known_y's, known_x's)
```

Where:

| Parameter   | Meaning                                |
| ----------- | -------------------------------------- |
| `x`         | Value for which prediction is required |
| `known_y's` | Dependent variable values              |
| `known_x's` | Independent variable values            |

---

# Example Dataset

We use a **Height vs Weight dataset**.

| Height (cm) | Weight (kg) |
| ----------- | ----------- |
| 167         | 51.3        |
| 170         | 55          |
| 175         | 60          |
| 180         | 63          |

Before analysis, the dataset was converted from:

* **Inches → Centimeters**
* **Pounds → Kilograms**

### Conversion formulas

Height conversion:

```
Height_cm = Height_inches × 2.54
```

Weight conversion:

```
Weight_kg = Weight_pounds / 2.204
```

---

# Visualizing Data

A **scatter plot** helps visualize the relationship between variables.

Steps:

1. Select Height and Weight columns
2. Go to **Insert → Scatter Plot**

Observation:

* As height increases, weight tends to increase
* The relationship appears approximately **linear**

---

# Using FORECAST Function

Example: Predict weight for a person **170 cm tall**.

```
=FORECAST(170, weight_range, height_range)
```

Example result:

```
170 cm → ~56 kg
```

This estimate is calculated using **linear regression between height and weight**.

---

# Reverse Prediction

We can also predict height from weight.

Example:

```
=FORECAST(75, height_range, weight_range)
```

Result:

```
75 kg → ~180 cm
```

---

# Predicting Multiple Values with TREND

When forecasting **multiple values**, the `TREND` function is more efficient.

### Formula

```
TREND(known_y's, known_x's, new_x's)
```

Example:

```
=TREND(weight_range, height_range, new_height_range)
```

Advantages:

* Computes regression **once**
* Predicts values for **multiple X inputs**
* Faster than repeating `FORECAST` many times

---

# Forecasting Time Series Data

Linear regression works well for **linear relationships**, but not for **cyclical data** such as:

* traffic patterns
* sales data
* seasonal trends

Example dataset:

| Time   | Vehicles |
| ------ | -------- |
| Hour 1 | 12       |
| Hour 2 | 18       |
| Hour 3 | 25       |
| Hour 4 | 14       |

Traffic data typically shows:

* daily peaks
* weekly patterns
* seasonal fluctuations

Linear regression cannot capture these patterns.

---

# Using FORECAST.ETS

Excel provides `FORECAST.ETS` for **seasonal time-series forecasting**.

ETS stands for:

```
Error
Trend
Seasonality
```

### Formula

```
FORECAST.ETS(target_date, values, timeline)
```

Optional parameters:

| Parameter       | Purpose                      |
| --------------- | ---------------------------- |
| seasonality     | length of repeating cycle    |
| data_completion | handle missing values        |
| aggregation     | combine duplicate timestamps |

---

# Example: Traffic Forecast

```
=FORECAST.ETS(A2, vehicle_values, timeline)
```

Where:

* `A2` → time we want prediction for
* `vehicle_values` → past traffic data
* `timeline` → timestamps

Excel automatically detects **seasonality** (e.g., 24-hour cycles).

---

# Linear vs ETS Forecast

| Method           | Best For                  |
| ---------------- | ------------------------- |
| FORECAST / TREND | Linear relationships      |
| FORECAST.ETS     | Seasonal time-series data |

Example:

* **Linear forecast** → straight upward line
* **ETS forecast** → captures daily traffic peaks

---

# Visualization Comparison

When plotting:

* **Actual Data**
* **Linear Prediction**
* **ETS Prediction**

Observations:

* Linear prediction produces a **smooth line**
* ETS prediction **follows seasonal patterns more closely**
