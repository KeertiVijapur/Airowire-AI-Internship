# Week 4 – Data Sourcing

## Get the Data – Introduction (https://www.youtube.com/watch?v=1LyblMkJzOo)

### Overview

Before performing any data analysis, visualization, or deployment, the first step in any data science workflow is acquiring data. This module introduced three fundamental approaches to obtaining data depending on availability and access constraints.

Understanding these approaches helps in choosing the correct method based on the situation.

---

## Three Core Methods of Data Acquisition

### 1️ Downloading Data (Bulk Access)

The simplest method is directly downloading datasets if they are publicly available.

Examples discussed:

* IMDb dataset (available as gzipped TSV files)
* Public datasets from platforms like Kaggle

Key observations:

* Bulk downloads allow complete control over analysis.
* Data is usually structured (CSV/TSV).
* Enables building recommendation systems, trend analysis, and rating studies.

Example Insight:
IMDb data includes:

* Actor/Director IDs
* Names
* Birth/Death years
* Movie titles
* Ratings and votes

This type of dataset supports large-scale movie analytics and personalization systems.

---

### 2️ Querying Data via APIs

When full downloads are not available, data can be queried selectively using APIs or databases.

Example discussed:

* Google Search autocomplete (undocumented API)
* Region-based “how to” query suggestions

Key learnings:

* APIs allow dynamic, real-time data collection.
* Even undocumented APIs can be explored using browser developer tools.
* This method avoids downloading unnecessary bulk data.

Insight:
Different countries show different query patterns, revealing regional interests.

This method is especially useful for:

* Trend analysis
* Market research
* Real-time dashboards

---

### 3️ Scraping Data from Web Pages

When no dataset or API is available, web scraping becomes necessary.

Example:

* Scraping cricket statistics from howstat.com
* Extracting player IDs, strike rates, runs, and performance metrics

Tools used:

* Python
* Beautiful Soup
* CSV export

Key insight:
Scraping requires understanding webpage structure and extracting structured data from semi-structured HTML.

Observation from example:

* Older players generally have slower strike rates.
* Modern players show faster scoring patterns.

---

## Comparative Understanding

| Method    | When to Use                 | Difficulty | Control Level |
| --------- | --------------------------- | ---------- | ------------- |
| Download  | Public dataset available    | Easy       | High          |
| API Query | Partial / live data needed  | Moderate   | Medium        |
| Scraping  | No API or dataset available | Advanced   | High          |

---

## My Key Learnings

* Data acquisition strategy depends on accessibility.
* APIs provide cleaner and more maintainable workflows than scraping.
* Scraping is powerful but fragile (webpage structure changes).
* Bulk datasets enable deep offline analysis.
* Combining all three methods provides flexibility in real-world projects.

---

## Practical Importance

These techniques are foundational for:

* Building recommendation engines
* Trend analysis systems
* Market intelligence tools
* Sports analytics
* Content strategy analysis

---

## Conclusion

This module strengthened my understanding that **data sourcing is the backbone of data science**.
Without reliable data acquisition methods — download, query, or scrape — analysis and AI modeling cannot begin.

Mastering these three approaches ensures adaptability across different real-world scenarios.
