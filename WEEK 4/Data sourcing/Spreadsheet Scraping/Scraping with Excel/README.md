# Week 4 – Data Sourcing

## Scraping with Excel (Web Import Using Query) - (https://www.youtube.com/watch?v=OCl6UdpmzRQ)

### Overview

This session demonstrated how Microsoft Excel can be used to import live web data directly into a spreadsheet using the **Web Query (Power Query) feature**.

Instead of writing code, Excel provides a built-in way to connect to web pages, extract structured tables, transform them, and refresh them automatically.

The example used in the session was importing a **two-week weather forecast for Chennai** from timeanddate.com.

---

## Core Concept

Excel’s **“From Web” Query Feature** allows:

* Connecting to a webpage using a URL
* Detecting structured HTML tables
* Importing selected tables
* Cleaning and transforming data
* Refreshing data dynamically

This essentially acts as a no-code scraping tool for structured tables.

---

## Step-by-Step Workflow

| Step | Action                     | Purpose                         |
| ---- | -------------------------- | ------------------------------- |
| 1    | Open weather webpage       | Identify structured data source |
| 2    | Copy webpage URL           | Required for Excel connection   |
| 3    | Excel → Data Tab           | Access import tools             |
| 4    | New Query → From Web       | Establish web connection        |
| 5    | Paste URL                  | Connect to webpage              |
| 6    | Open Query Editor          | View detected tables            |
| 7    | Select Table 0             | Choose required weather table   |
| 8    | Remove unnecessary columns | Clean dataset                   |
| 9    | Close & Load               | Import into worksheet           |
| 10   | Refresh Data               | Pull latest updates             |

---

## Transformations Performed

Columns removed:

* Conditions
* Comfort
* Humidity
* Precipitation Chance
* Sun UV
* Sunrise
* Sunset

These were removed to keep only essential forecast information.

---

## Important Features Observed

### 1️ Applied Steps Panel

* Tracks every transformation action
* Makes the process transparent
* Steps can be modified or reversed

### 2️ Live Data Refresh

* Data can be refreshed anytime
* Automatically pulls latest forecast
* No need to repeat scraping process

### 3️ Flexible Data Cleaning

* Transform before loading
* Or clean after loading
* Both options supported

---

## Key Learnings

* Excel can function as a basic web scraping tool.
* Structured HTML tables can be directly imported without coding.
* Data pipelines can be built even in spreadsheet environments.
* Refresh capability makes it suitable for live dashboards.
* Understanding table structure on websites is important before import.

---

## Practical Significance

This technique is useful for:

* Business reporting dashboards
* Financial market data
* Weather monitoring
* Periodic data collection
* Non-programmer data workflows

It reduces dependency on programming when dealing with structured web tables.

---

## Conclusion

This session showed that **data sourcing does not always require programming**.
Excel’s Web Query feature provides a simple yet powerful way to connect to external live data sources, clean them, and maintain dynamic updates.

It reinforced the idea that understanding data structure is more important than the tool used.
