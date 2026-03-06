# Splitting Text in Excel (https://youtu.be/fQeADnqiOAg)

This module demonstrates how to use Excel’s **Text to Columns** feature to split a single column containing multiple pieces of information into separate columns. This technique is commonly used when working with scraped data or text copied from websites where several attributes are stored in one column.

## Objective
The goal is to transform unstructured text data into a structured table that is easier to analyze and export as a CSV file.

## Example Dataset
The data was taken from the **US Senate voting records** website. When copied into Excel, each row appears in a single column like this:

Baldwin (D-WI), Yea  
Barrasso (R-WY), No  
Bennet (D-CO), Yea  

Each row contains multiple fields:
- Senator Name
- Party
- State
- Vote

## Method Used

Excel provides a feature located at:

Data → Text to Columns

This tool allows splitting text using **delimiters** such as commas, hyphens, or parentheses.

### Step 1 – Split by "("
Separate the **Senator name** from the rest of the information.

Example:
Baldwin | D-WI), Yea

### Step 2 – Split by "-"
Separate **Party** from **State**.

Example:
D | WI), Yea

### Step 3 – Split by ")"
Extract the **State code**.

Example:
WI | , Yea

### Step 4 – Split by ","
Separate the **Vote result**.

## Final Structured Data

After splitting, the dataset becomes:

| Senator  | Party | State | Vote |
|---------|------|------|------|
| Baldwin | D    | WI   | Yea  |
| Barrasso| R    | WY   | No   |
| Bennet  | D    | CO   | Yea  |

## Key Learnings

- The **Text to Columns** feature helps convert messy text data into structured columns.
- Delimiters like **parentheses, hyphens, and commas** can be used to split data step-by-step.
- This method is useful when preparing **scraped or copied web data** for analysis.
- Structured data enables easier filtering, sorting, and exporting to CSV format.
