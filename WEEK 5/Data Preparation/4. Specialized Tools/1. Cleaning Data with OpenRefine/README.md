# Cleaning Data with OpenRefine (https://www.youtube.com/watch?v=zxEtfHseE84)

This module covers the use of **OpenRefine** for data cleaning, especially for resolving **entity discrepancies** where multiple text variants actually refer to the same real-world entity.

## What is OpenRefine?

**OpenRefine** is an open-source data cleaning and transformation tool. It was originally a Google project and is now freely available for Windows, macOS, and Linux. After installation, it runs in the browser, similar to Jupyter Notebook.

It is especially useful when datasets contain **inconsistent naming, formatting differences, punctuation issues, abbreviations, or duplicate-looking entities** that should actually be treated as one.

## Problem it Solves

A common real-world issue in data systems is that the **same entity appears in multiple forms**.

Example:

* `XYZ Limited`
* `XYZ Ltd`

To a human, both clearly refer to the same organization.
But from a system’s point of view, they are treated as **different values**, which creates problems in:

* aggregation
* grouping
* reporting
* analysis
* duplicate detection

This is common in finance, e-commerce, customer records, legal data, and many other real-world datasets.

## Dataset Used

The exercise uses a dataset downloaded from the **US Department of Justice**, containing fields such as:

* Case ID
* Trade Name
* Legal Name
* Address

The dataset contains multiple address entries that are essentially the same, but differ slightly due to punctuation or formatting.

Example:

* `9227 Haven Avenue Suite 330`
* `9227 Haven Avenue Suite 330.,`

These are the same address in reality, but appear as separate values in raw data.

## Steps Performed in OpenRefine

### 1. Upload Data and Create Project

The input file is selected and uploaded into OpenRefine.
After previewing the file, a new project is created.

### 2. Inspect Entity Variations

The address column is examined to identify entries that look similar but are treated as different due to formatting differences.

### 3. Apply Text Facet

Using:

* column dropdown
* **Facet**
* **Text facet**

OpenRefine groups identical or repeated text values and displays their frequency.

This helps identify which address fragments or entity names occur multiple times.

### 4. Use Clustering

OpenRefine’s **Cluster and Edit** feature is used to group similar text values using built-in clustering algorithms.

This identifies entries that differ only by:

* punctuation
* commas
* dots
* abbreviations
* minor formatting changes

### 5. Merge Similar Entities

The user can either:

* review and merge clusters manually, or
* trust the clustering output and merge all selected clusters at once

This converts multiple versions of the same entity into a single clean standardized value.

## Example Outcome

Before cleaning:

* `9227 Haven Avenue Suite 330`
* `9227 Haven Avenue Suite 330.,`

After clustering and merging:

* `9227 Haven Avenue Suite 330`

This improves consistency and ensures proper grouping during analysis.

## Key Learning

The main concept demonstrated in this exercise is **entity resolution** — the process of identifying and merging multiple textual variants that refer to the same real-world object.

OpenRefine makes this process much easier by combining:

* faceting
* clustering
* interactive cleaning
* manual review options

## Why It Matters

Without entity resolution:

* duplicate entities remain split
* counts become inaccurate
* aggregations become misleading
* reports contain inconsistent results

With OpenRefine:

* similar entities can be standardized
* analysis becomes more accurate
* cleaned data becomes easier to use in downstream workflows

## Conclusion

OpenRefine is a powerful tool for **interactive data cleaning** and is especially useful for **resolving inconsistent text entries** in real-world datasets. In this exercise, it was used to identify and merge multiple address variants into clean, consistent entities using faceting and clustering features.
