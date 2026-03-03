# Scheduled Web Scraping with GitHub Actions (https://www.youtube.com/watch?v=eJG86J200nM)

## Overview

This project demonstrates how to automate a web scraper using **GitHub Actions** and run it on a schedule (cron job).

Instead of running scripts manually, we configure a workflow that:

* Runs daily (or at any scheduled time)
* Installs dependencies
* Executes a scraping script
* Saves scraped data as JSON
* Commits updated data back to the repository

This enables **automated data collection pipelines**.

---

# Why Use Scheduled Scraping?

In real-world applications, data needs to be:

* Updated daily
* Monitored for changes
* Logged historically
* Collected without manual intervention

GitHub Actions provides a free, serverless way to automate this.

---

# Tech Stack

* Python
* `httpx` (async HTTP client)
* `lxml` (HTML parsing)
* GitHub Actions
* Cron scheduling

---

# Project Structure

```
.
├── scrape.py
├── imdb-top250-YYYY-MM-DD.json
└── .github/
    └── workflows/
        └── imdb-top250.yml
```

---

# Scraper Script (scrape.py)

This script:

* Fetches IMDb Top 250 movies
* Extracts:

  * Title
  * Year
  * Rating
* Saves results as timestamped JSON

### Key Concepts Used:

* Custom User-Agent header
* CSS selectors
* Error handling (`raise_for_status()`)
* Timestamp logging (UTC)

---

# GitHub Actions Workflow

Located at:

```
.github/workflows/imdb-top250.yml
```

---

## Workflow Triggers

```yaml
on:
  schedule:
    - cron: "0 0 * * *"  # Runs daily at 00:00 UTC
  workflow_dispatch:     # Allows manual trigger
```

### Cron Format

```
* * * * *
│ │ │ │ │
│ │ │ │ └── Day of week
│ │ │ └──── Month
│ │ └────── Day of month
│ └──────── Hour (UTC)
└────────── Minute
```

GitHub uses **UTC time**, not local time.

---

## Workflow Steps

1. Checkout repository
2. Install Python & dependencies
3. Run scraper
4. Commit updated JSON
5. Push changes

Example:

```yaml
- name: Run scraper
  run: |
    uv run --with httpx,lxml,cssselect python scrape.py
```

---

# Automation Flow

1. GitHub scheduler triggers workflow
2. Ubuntu runner starts
3. Script executes
4. New JSON file created
5. Data committed automatically
6. Repository updated

Fully automated pipeline.

---

# Important Notes

## 1️ Schedule Delay

GitHub does NOT guarantee exact cron timing.
It may delay execution by several minutes.

This is normal behavior.

---

## 2️ Rate Limiting

To avoid overwhelming servers:

* Add delays between requests
* Use proper headers
* Respect website ToS

---

## 3️ Best Practices

* Cache dependencies
* Log errors clearly
* Validate data before saving
* Monitor workflow failures
* Use meaningful commit messages

---

# Real-World Applications

* Price monitoring
* Stock tracking
* News aggregation
* Competitor analysis
* Job listing aggregation
* Vulnerability scanning

---

# Key Learning

Scheduled scraping moves you from:

> Manual script execution
> to
> Production-ready automated data pipelines

This is closer to how data engineering systems work in real companies.

---

# What This Demonstrates

* Automation via CI/CD tools
* Cron scheduling
* Data versioning
* Headless execution
* Continuous data ingestion

---

# Final Insight

GitHub Actions is not just for CI testing —
it can be used as a lightweight cloud automation engine for data pipelines.

This bridges scraping with DevOps principles.
