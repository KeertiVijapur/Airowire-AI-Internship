# Data Aggregation in Excel (https://youtu.be/NkpT0dDU8Y4)

This section covers how **Excel can be used to aggregate and visualize data** to discover trends and insights. Using a COVID-19 dataset containing daily cases and deaths across countries, Excel features such as **Pivot Tables, Color Scales, Sparklines, and Data Bars** help summarize and interpret large datasets efficiently.

---

## 1. Data Cleanup

Before performing aggregation, the dataset must be cleaned.

Steps performed:
- Removed **empty columns** that did not contain useful information.
- Removed **rows with missing values** in the `new_cases` column.
- Used **Find & Select → Go To Special → Blanks** to locate empty cells.
- Deleted rows containing blank values.

This ensures the dataset contains **complete and usable records** for analysis.

---

## 2. Data Manipulation

To enable better aggregation, additional time-based columns were created from the `date` column.

### Converting Data to Excel Table
The dataset was first converted into an **Excel Table** using:

Insert → Table

Benefits:
- Automatic filtering
- Structured references
- Formulas automatically applied to the entire column

### Extracting Time Components

Three new columns were created:

**Week**

```

=WEEKNUM([@date],1)

```

Extracts the week number from the date.

**Month**

```

=TEXT([@date],"mmm")

```

Returns the month abbreviation.

**Year**

```

=TEXT([@date],"yyyy")

```

Returns the year.

These columns allow aggregation by **week, month, or year**.

---

## 3. Visualizing Clusters with Color Scales

Excel **Conditional Formatting → Color Scales** was used to identify patterns in the `new_cases` column.

- Green = Low number of cases  
- Yellow = Medium values  
- Red = High number of cases  

By zooming out, clusters of high and low values become visible, allowing quick identification of **case surges and trends**.

---

## 4. Aggregating Data with Pivot Tables

Pivot Tables were used to summarize COVID-19 cases.

### Example Aggregation

Goal: **Total new cases per country per week**

Pivot Table configuration:

Rows → `location`  
Columns → `week`  
Values → `sum(new_cases)`  
Filters → `year`

This provides a structured view showing **weekly case totals for each country across different years**.

Pivot tables can also compute:
- Sum
- Average
- Maximum
- Minimum
- Count

---

## 5. Trend Visualization using Sparklines

Sparklines are small charts embedded inside cells that show trends.

Steps:
Insert → Sparklines → Line

Sparklines were created to show **weekly case trends for each country**.

Features used:
- Highlight **High Points**
- Highlight **Low Points**
- Increase line thickness for visibility

This quickly reveals how cases rose and fell across weeks.

---

## 6. Visualizing Values using Data Bars

**Data Bars** provide a graphical representation of numeric values within cells.

Steps:
Conditional Formatting → Data Bars

A Pivot Table was created to show:

Rows → Month  
Columns → Country  
Values → Sum of New Cases  
Filter → Year  

Data bars then displayed the **relative magnitude of cases each month**, forming a wave-like visualization that highlights peaks and declines.

---

## Key Learnings

- Data aggregation summarizes large datasets for easier analysis.
- **Pivot Tables** are powerful tools for grouping and summarizing data.
- **Color Scales** reveal clusters and value distributions.
- **Sparklines** show trends within pivot tables.
- **Data Bars** provide quick visual comparison across values.
