# Data Visualization with Seaborn (https://www.youtube.com/watch?v=6GUZXDef2U0)

## Seaborn – Python Data Visualization Library

Seaborn is a **data visualization library for Python** built on top of Matplotlib. It simplifies creating **statistical and attractive visualizations** with minimal code.

---

## What is Seaborn?

Seaborn is a library that:

* Provides **high-level visualization tools**
* Works seamlessly with **Pandas DataFrames**
* Generates complex plots with **less code**
* Focuses on **statistical data visualization**

---

## Key Features

* Built on top of Matplotlib
* Easy-to-use API for complex plots
* Built-in datasets for practice
* Attractive default styles
* Supports statistical plotting
* Works well with Pandas and NumPy
* Customizable themes and color palettes

---

## Installation

### Using pip

```bash
pip install seaborn
```

### Using conda

```bash
conda install seaborn
```

---

## Basic Setup

```python
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd
```

---

## Types of Plots

### 1. Distribution Plots

Used to analyze distribution of a single variable.

```python
sns.histplot(data['column'])
```

* Histogram
* KDE (Kernel Density Estimation)

---

### 2. Joint Plot

Used to compare two variables.

```python
sns.jointplot(x='x_col', y='y_col', data=df, kind='reg')
```

* Scatter + Regression
* KDE plots

---

### 3. Pair Plot

Shows relationships across all numerical variables.

```python
sns.pairplot(df)
```

---

### 4. Rug Plot

Shows distribution using small ticks.

```python
sns.rugplot(data['column'])
```

---

## Categorical Plots

### 1. Bar Plot

```python
sns.barplot(x='category', y='value', data=df)
```

---

### 2. Count Plot

```python
sns.countplot(x='category', data=df)
```

---

### 3. Box Plot

```python
sns.boxplot(x='category', y='value', data=df)
```

* Shows median, quartiles, and outliers

---

### 4. Violin Plot

```python
sns.violinplot(x='category', y='value', data=df)
```

* Combines box plot + distribution

---

### 5. Strip Plot

```python
sns.stripplot(x='category', y='value', data=df, jitter=True)
```

---

### 6. Swarm Plot

```python
sns.swarmplot(x='category', y='value', data=df)
```

---

## Matrix Plots

### Heatmap

```python
sns.heatmap(df.corr(), annot=True)
```

* Used for correlation visualization

---

### Cluster Map

```python
sns.clustermap(data)
```

* Groups similar data points

---

## Styling & Customization

### Set Style

```python
sns.set_style("darkgrid")
```

---

### Set Context

```python
sns.set_context("talk")
```

---

### Color Palettes

```python
sns.set_palette("magma")
```

---

## Regression Plots

```python
sns.lmplot(x='x_col', y='y_col', data=df)
```

* Shows relationship between variables
* Adds regression line

---

## Working with Data

Load built-in datasets:

```python
sns.load_dataset("tips")
```

Or use Pandas:

```python
pd.read_csv("file.csv")
```

---

## Use Cases

* Exploratory Data Analysis (EDA)
* Statistical data visualization
* Correlation analysis
* Trend analysis
* Data storytelling
