# Web Scraping with Playwright (Python) - (https://www.youtube.com/watch?v=biFzRHk4xpY)

## What I Learned

In this session, I learned how to scrape **JavaScript-rendered websites** using **Playwright in Python**.

Unlike `requests`, Playwright launches a real browser and executes JavaScript before extracting content.

This is useful when:

* Data is loaded dynamically
* HTML source doesn’t contain actual data
* Websites block basic HTTP scraping

---

## Why Playwright?

Modern websites load content using JavaScript APIs.
Using `requests.get()` only returns the initial HTML shell.

Playwright:

* Runs JavaScript
* Waits for content to load
* Extracts fully rendered HTML

---

## Installation

```bash
pip install playwright
playwright install
```

---

## Basic Example

```python
from playwright.sync_api import sync_playwright

def scrape_quotes():
    with sync_playwright() as p:
        browser = p.chromium.launch(headless=True)
        page = browser.new_page()
        page.goto("https://quotes.toscrape.com/js/")

        quotes = page.query_selector_all(".quote")

        for q in quotes:
            text = q.query_selector(".text").inner_text()
            author = q.query_selector(".author").inner_text()
            print(f"{text} - {author}")

        browser.close()

scrape_quotes()
```

---

## Key Concepts Used

* `sync_playwright()` → Start browser session
* `browser.new_page()` → Open page
* `page.goto()` → Navigate to URL
* `query_selector()` / `query_selector_all()` → Select elements
* `inner_text()` → Extract text
* Headless mode → Run browser without UI

---

## Extra Features

* Take screenshots:

```python
page.screenshot(path="page.png", full_page=True)
```

* Wait for page load:

```python
page.wait_for_timeout(2000)
```

---

## Key Takeaways

* Playwright is better than `requests` for JS-heavy websites.
* It behaves like a real browser.
* Useful for:

  * Dynamic dashboards
  * Stock data sites
  * Login-required scraping
* More powerful and modern than Selenium for Python users.
