# LLM-Powered Website Scraping

## Objective

Use Large Language Models (LLMs) to:

* Extract structured data from websites
* Handle authentication
* Deal with JavaScript-heavy sites
* Adapt to layout changes automatically
* Build repeatable, production-ready scrapers

This shifts scraping from:

> Writing rigid CSS selectors
> to
> Describing what data you want

---

# Why LLM Scraping?

Traditional scraping problems:

* Selectors break when layout changes
* JS-rendered content doesn’t load via requests
* Authentication barriers
* Dynamic content (hover, infinite scroll)
* Maintenance overhead

LLMs solve this by:

* Understanding semantic structure
* Trying multiple extraction strategies
* Using browser automation when needed
* Adapting automatically when selectors fail

---

# Core Principle

> Describe the data you want.
> Let the LLM choose the best extraction method.

---

# Scraping Strategies

## Strategy 1 – HTML Parsing (Fastest)

```python
import requests
from bs4 import BeautifulSoup

response = requests.get(url)
soup = BeautifulSoup(response.content, "html.parser")
```

✔ Fast
✖ Fails on JS-rendered content

---

## Strategy 2 – API Discovery (Most Reliable)

* Inspect Network tab
* Find hidden JSON API
* Call API directly

✔ Stable
✔ Structured
✖ May require authentication

---

## Strategy 3 – Browser Automation (Most Powerful)

```python
from playwright.sync_api import sync_playwright

with sync_playwright() as p:
    browser = p.chromium.launch()
    page = browser.new_page()
    page.goto(url)
```

✔ Handles JS
✔ Handles login
✔ Handles hover/infinite scroll
✖ Slower

---

# Chrome Remote Debugging (Authenticated Scraping)

Instead of automating login:

1. Launch Chrome in debug mode:

```bash
google-chrome --remote-debugging-port=9222 --user-data-dir=/tmp/profile
```

2. Log in manually
3. Let LLM connect to running Chrome

LLM can then:

* Access logged-in session
* Extract data behind login walls
* Avoid CAPTCHA solving

---

# Handling Dynamic Content

## 1️ Hover-triggered content

LLM:

* Identifies hoverable elements
* Triggers JS events
* Waits for content
* Extracts revealed data

---

## 2️ Infinite Scroll

LLM generates logic like:

```python
while True:
    page.evaluate("window.scrollTo(0, document.body.scrollHeight)")
```

Until no new content loads.

---

## 3️ Lazy-loaded images

LLM:

* Scrolls to trigger load
* Waits for `src` to populate
* Extracts real URLs

---

# Extracting Structured Data

Traditional:

```python
products = soup.find_all("div", class_="product-card")
```

LLM approach:

> Extract all products. For each include:
>
> * Name
> * Price
> * Rating
> * Reviews
> * Availability

LLM:

* Understands semantics
* Normalizes fields
* Validates output schema
* Outputs JSON

---

# Making Scrapers Repeatable

## Step 1 – Successful prompt

```
Scrape all job listings from this page:
- Title
- Company
- Location
- Salary
- Posted date
```

## Step 2 – Convert to script

Create:

```
scrape_jobs.py
```

With:

* Error handling
* Retry logic
* Logging
* CSV export

## Step 3 – Schedule

* GitHub Actions
* Cron jobs
* Email alerts on failure

---

# Handling Failures

## Scenario: Selector broken

Instead of:

```python
.product-card
```

LLM:

* Re-analyzes HTML
* Identifies product blocks semantically
* Updates extraction logic

---

## Scenario: 429 Rate Limit

LLM adds:

* Delay between requests
* User-agent rotation
* Exponential backoff

---

# Legal & Ethical Considerations

Allowed:

* Public research
* Data journalism
* Personal analysis
* APIs with permission

Avoid:

* Violating ToS
* Bypassing paywalls
* Aggressive scraping
* Overloading servers

Best practice:

```python
headers = {
    "User-Agent": "ResearchBot/1.0 (contact@example.com)"
}
```

---

# Production-Level Workflow

Example: Job Aggregator

1. Scrape:

   * Indeed
   * LinkedIn (via logged-in Chrome)
   * Glassdoor

2. Extract:

   * Title
   * Company
   * Salary
   * Skills

3. Deduplicate

4. Store in SQLite

5. Daily schedule

6. Send Slack/email alerts

---

# Real-World Use Cases

## Data Journalism

* Scrape city council minutes
* Extract voting patterns
* Analyze trends

## Competitive Intelligence

* Monitor competitor pricing
* Alert on price drops
* Track inventory

## Real Estate Analysis

* Track property prices
* Calculate median price per sq ft

## Academic Research

* Scrape publications
* Track citations
* Analyze topic trends
