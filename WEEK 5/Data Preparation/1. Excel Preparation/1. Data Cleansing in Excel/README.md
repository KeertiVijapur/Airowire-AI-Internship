# Data Cleansing in Excel (https://youtu.be/7du7xkqeu4s)

This module demonstrates basic **data cleaning techniques using Microsoft Excel** on a dataset containing **city-wise population information** sourced from Wikipedia.

The goal is to prepare raw data for analysis by removing inconsistencies, formatting issues, and duplicate entries.

---

## Techniques Covered

### 1. Find and Replace

Used **Ctrl + H** to locate and remove unwanted text (e.g., `[more]` from country names).

### 2. Changing Data Format

Converted columns from **General format to Number format** for population and area columns.

### 3. Removing Extra Spaces

Used the **TRIM() function** to clean unnecessary spaces within text fields.

Example:

```
=TRIM(D2)
```

### 4. Identifying and Removing Blank Rows

Used:

```
Find & Select → Go To Special → Blanks
```

to locate empty cells and delete entire rows.

### 5. Removing Duplicate Values

Used:

```
Data → Remove Duplicates
```

to eliminate repeated entries and retain unique values.

---

## Key Learnings

* Excel can effectively clean small datasets quickly.
* Functions like **TRIM**, **Find & Replace**, and **Remove Duplicates** simplify preprocessing tasks.
* Proper data formatting ensures accurate analysis.

---

## Dataset Used

City population dataset from **Wikipedia** containing:

* City Name
* Country
* Population Estimates
* City Type
* Population Area
