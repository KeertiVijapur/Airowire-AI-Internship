# Geospatial Analysis with Excel (https://www.youtube.com/watch?v=49LjxNvxyVs)

Geospatial analysis helps us understand how location impacts data. It allows us to analyze **distance, coverage, and spatial relationships** between entities such as stores, customers, and regions.

In this tutorial, we analyze **coffee shop competition in Manhattan** to determine which brand has better coverage and profitability.

---

## Problem Statement

Manhattan has multiple coffee chains competing:

* Starbucks (≈230 stores)
* McDonald's (≈16 stores)

The key question:

👉 *Which coffee chain serves more people effectively based on location?*

---

## Key Concept: Coverage Area

Each coffee shop has a **coverage area**, meaning:

* People within this area will go to the **nearest shop**
* Customers choose based on **distance (walking convenience)**

---

## Data Used

We analyze:

Variable	Description
Coffee Shop Locations	Starbucks and McDonald's store coordinates
Population Data	Number of people living in each area
Distance	Closest shop for each population cluster

---

## Steps in Geospatial Analysis

### 1. Data Collection

* Gather coffee shop locations (latitude & longitude)
* Collect population data for Manhattan

---

### 2. Data Processing

* Calculate distance between:

  * Population points
  * Coffee shop locations
* Assign each population group to the **nearest coffee shop**

---

### 3. Coverage Mapping

Each shop is assigned:

* Number of people closest to it
* Its effective service area

---

## Example Insights

### Coverage Comparison

* Starbucks covers **~2/3 of Manhattan population**
* McDonald's covers **~1/3 of population**

👉 Starbucks has **better geographic coverage**

---

### Profitability Insight

Profitability depends on:

👉 Number of people near each shop

Findings:

* McDonald's stores serve **more customers per store**
* Starbucks has **many stores but lower density per store**

---

### High & Low Performing Stores

#### Starbucks

* Least profitable store:

  * 383 Madison Avenue
  * Serves ~11 customers

#### McDonald's

* Most profitable store:

  * 213 Madison Avenue
  * High customer density

---

## Visualization

Geospatial visualization helps show:

* Coverage areas
* Population density
* Store performance

Example:

* Tall bars → High population coverage
* Short bars → Low coverage

---

## Strategic Insights

### For Starbucks

* Too many stores in crowded regions
* Needs optimization

👉 Recommendation:

* Relocate underperforming stores
* Focus on high-density regions

---

### For McDonald's

* Fewer stores but better efficiency

👉 Recommendation:

* Expand into underserved regions
