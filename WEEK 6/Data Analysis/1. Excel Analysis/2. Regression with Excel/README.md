# Regression Analysis with Excel (https://www.youtube.com/watch?v=AERQBMIHwXA)

Regression analysis helps us understand the **relationship between a dependent variable and one or more independent variables**. It allows us to model how changes in independent variables influence a target variable.

In this tutorial, we perform **Multiple Linear Regression using Excel** on a COVID-19 dataset.

---

# Dataset Variables

The dataset contains several variables related to COVID-19 trends.

For this analysis:

### Dependent Variable (Y)

* **New Deaths**

### Independent Variables (X)

* **New Cases per 1000**
* **New Tests per 1000**
* **New Vaccinations per 1000**
* **Stringency Index**

The variables for cases, tests, and vaccinations were **scaled per 1000** to simplify interpretation of regression coefficients.

---

# Types of Regression

### Simple Linear Regression

Uses **one independent variable**.

Example:

```
Y = β0 + β1X
```

---

### Multiple Linear Regression

Uses **multiple independent variables**.

Example:

```
Y = β0 + β1X1 + β2X2 + β3X3 + ... + βnXn
```

In our case:

```
New Deaths =
β0 + β1(New Cases per 1000)
   + β2(New Tests per 1000)
   + β3(New Vaccinations per 1000)
   + β4(Stringency Index)
```

---

# Enabling Excel Data Analysis ToolPak

Regression analysis requires the **Excel Data Analysis ToolPak**.

Steps:

1. Go to **File → Options**
2. Select **Add-ins**
3. At the bottom choose **Excel Add-ins**
4. Click **Go**
5. Enable **Analysis ToolPak**
6. Click **OK**

Once enabled:

```
Data Tab → Data Analysis
```

---

# Running Regression in Excel

### Step 1 — Open Regression Tool

```
Data → Data Analysis → Regression
```

---

### Step 2 — Configure Inputs

**Input Y Range**

```
New Deaths
```

**Input X Range**

```
New Cases per 1000
New Tests per 1000
New Vaccinations per 1000
Stringency Index
```

Check:

```
Labels in first row
```

Choose output location:

* New worksheet
* New workbook
* Same worksheet

Then click **OK**.

---

# Regression Output Interpretation

Excel produces a regression summary including:

* R Square
* Adjusted R Square
* ANOVA table
* Coefficients
* P-values

---

# Adjusted R² (Model Fit)

For **multiple regression**, we use **Adjusted R²** instead of R².

Example result:

```
Adjusted R² = 0.816
```

Interpretation:

**81.6% of the variation in new deaths is explained by the independent variables.**

This indicates a **strong model fit**.

---

# Model Significance (F-Test)

Check the **Significance F value**.

Rule:

```
If Significance F < 0.05
→ Model is statistically significant
```

In our analysis:

```
Significance F << 0.05
```

This means the regression model is statistically valid.

---

# Interpreting Coefficients

Each coefficient represents the expected change in the dependent variable when the independent variable increases by one unit (holding other variables constant).

### New Cases per 1000

Coefficient ≈ **7**

Interpretation:

```
For every 1000 additional new cases,
new deaths increase by about 7.
```

---

### New Tests per 1000

Coefficient ≈ **0.69**

Interpretation:

```
For every 1000 additional tests,
new deaths increase by about 0.69.
```

---

### New Vaccinations per 1000

Coefficient ≈ **-0.07**

Interpretation:

```
For every 1000 additional vaccinations,
new deaths decrease by about 0.07.
```

The negative coefficient suggests a **potential reduction in deaths with increased vaccinations**, but the effect is small.

---

### Stringency Index

Coefficient ≈ **2.71**

Interpretation:

```
Higher policy stringency appears associated with higher deaths.
```

However, this result may seem counterintuitive.

---

# Checking Variable Significance (P-values)

To determine if variables are meaningful in the model, examine **P-values**.

Rule:

```
P-value < 0.05 → statistically significant
```

Results:

| Variable         | P-value | Interpretation  |
| ---------------- | ------- | --------------- |
| New Cases        | <0.05   | Significant     |
| New Tests        | <0.05   | Significant     |
| New Vaccinations | <0.05   | Significant     |
| Stringency Index | 0.11    | Not Significant |

Therefore:

* **Stringency Index should not be included in the final model.**

---

# Important Insight

Even though regression shows relationships between variables:

⚠ **Regression does not prove causation.**

Further statistical analysis may be required such as:

* Time series analysis
* Policy evaluation
* Controlled statistical studies
