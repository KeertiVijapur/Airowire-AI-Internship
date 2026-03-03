# Semantic Search on emarketer Articles (POC) - (https://www.youtube.com/watch?v=ZzUsDE1XjhE)

## Overview

Built a **proof-of-concept semantic search engine** by scraping ~7,000 articles from Insider Intelligence (emarketer archive) and enabling similarity-based retrieval + summarization.

The goal: demonstrate how semantic search outperforms traditional keyword search.

---

## What This Does

1. Scrapes archive pages (paginated URLs)
2. Extracts:

   * Article title
   * Article body text
3. Stores data as JSON/CSV
4. Enables:

   * Semantic similarity search
   * Auto-summary of results

---

## Tech Stack

* `httpx` – HTTP requests
* `lxml` – Fast HTML parsing
* `tqdm` – Progress tracking
* Custom `cached_get()` – Avoid re-downloading pages
* JSON / Pandas
* LLM (Gemini / GPT) for semantic search + summarization

---

## Key Engineering Ideas

### 1️ Caching (Critical)

```python
def cached_get(url):
    # Saves HTML locally using hashed filename
    # Prevents re-fetching pages during debugging
```

✔ Saves hours during development
✔ Allows safe interruption + resume

---

### 2️ Systematic Debugging

* Liberal `print()` usage
* Strategic `breakpoint()`
* “Rubber duck debugging”
* LLM-assisted troubleshooting

---

### 3️ Scraping Flow

```python
for page in range(1, N):
    html = cached_get(page_url)
    extract_article_links(html)

for link in links:
    html = cached_get(link)
    extract_title_and_body(html)
```

---

## Outcome

* Scraped ~7,000 articles in one day
* Built working semantic search demo
* Used as client-facing POC
* Improved proposal conversion
