# Week 4 – Data Sourcing

## Scraping with Google Sheets (https://www.youtube.com/watch?v=eYQEk7XJM7s)

### Overview

This session demonstrated how to import structured web data directly into **Google Sheets** using built-in import functions — primarily the `IMPORTHTML()` formula.

Unlike traditional scraping with Python, Google Sheets allows web data extraction using simple spreadsheet formulas.

The example used in the session involved importing tables from Wikipedia pages such as:

* Demographics of India
* List of highest-grossing Indian films

---

## Core Function: IMPORTHTML()

### Syntax

```excel
=IMPORTHTML(url, query, index)
```

### Parameters

| Parameter | Description                         |
| --------- | ----------------------------------- |
| `url`     | Web page URL containing the data    |
| `query`   | `"table"` or `"list"`               |
| `index`   | Table/list number (starting from 1) |

### Example

```excel
=IMPORTHTML("https://en.wikipedia.org/wiki/Demographics_of_India","table",4)
```

This imports the 4th table from the given Wikipedia page.

---

## Workflow Demonstrated

| Step | Action                      | Purpose                 |
| ---- | --------------------------- | ----------------------- |
| 1    | Enter IMPORTHTML formula    | Connect to webpage      |
| 2    | Allow external data access  | Enable live data import |
| 3    | Verify table matches source | Validate correctness    |
| 4    | Copy → Paste as Values      | Enable sorting          |
| 5    | Sort by column (e.g., Year) | Analyze data            |
| 6    | Refresh sheet               | Get updated web data    |

---

## Important Observations

### 1️ Permission Handling

Google Sheets prompts for permission when importing from a new URL. Access must be granted.

### 2️ Dynamic Data

* Imported data updates automatically when the source webpage changes.
* Suitable for live dashboards and tracking.

### 3️ Sorting Limitation

* Formula-generated data cannot be directly sorted.
* Workaround: Copy → Paste as Values → Then sort.

---

## Other Import Functions Introduced

| Function        | Purpose                                                          |
| --------------- | ---------------------------------------------------------------- |
| `IMPORTXML()`   | Extract specific elements using XPath (more advanced & powerful) |
| `IMPORTFEED()`  | Import RSS/Atom feeds                                            |
| `IMPORTRANGE()` | Import data from another Google Sheet                            |
| `IMPORTDATA()`  | Import CSV/TSV data via URL                                      |

Among these, **IMPORTXML** is considered the most powerful because it allows precise extraction from complex pages.

---

## Key Learnings

* Google Sheets can function as a lightweight web scraping tool.
* IMPORTHTML is ideal for structured tables and lists.
* Index parameter is critical when pages contain multiple tables.
* Dynamic imports are useful for real-time monitoring.
* Converting formula output to static values enables deeper analysis.

---

## Practical Applications

* Monitoring Wikipedia statistics
* Financial tracking tables
* Population data tracking
* Box office trend analysis
* Live data dashboards

---

## Excel vs Google Sheets (Quick Comparison)

| Feature           | Excel       | Google Sheets      |
| ----------------- | ----------- | ------------------ |
| Web Import Method | Power Query | IMPORTHTML Formula |
| Requires Formula  | No          | Yes                |
| Live Refresh      | Yes         | Yes                |
| Code Required     | No          | No                 |
| XPath Support     | Limited     | Yes (IMPORTXML)    |

---

## Conclusion

This session reinforced that **data sourcing does not always require programming**.

Google Sheets provides a powerful, no-code way to extract and monitor web data using simple formulas. While limited compared to Python-based scraping, it is highly effective for structured data extraction and quick analytics workflows.
