# Wikipedia Data with Python - (https://www.youtube.com/watch?v=b6puvm-QEY0)

## What I Learned

In this session, I learned how to extract structured data from Wikipedia using the **`wikipedia` Python library**, instead of manually scraping HTML using BeautifulSoup.

This library simplifies:

* Searching pages
* Getting summaries
* Fetching full content
* Extracting references and images
* Parsing tables

---

## Installation

```python
pip install wikipedia
```

---

## Basic Usage

```python
import wikipedia as wk

# Search for a keyword
wk.search("IIT Madras", results=3)

# Get summary
wk.summary("IIT Madras", sentences=2)

# Get full page object
page = wk.page("IIT Madras")

print(page.url)
```

---

## Data You Can Extract

From a page object:

* `page.url` → Wikipedia page link
* `page.content` → Full article text
* `page.summary` → Summary text
* `page.references` → List of reference links
* `page.images` → List of image URLs

---

## Extracting Tables

Wikipedia tables can be extracted using:

```python
import pandas as pd

tables = pd.read_html(page.html())
```

First table is often not useful (e.g., table of contents).
Choose table index carefully.

---

## Key Takeaways

* Wikipedia library is easier than manual scraping.
* Allows quick access to structured content.
* Useful for:

  * Research tasks
  * Text analysis
  * Knowledge extraction
  * Dataset creation

---

## Important Note

Wikipedia pages are constantly edited, so table indices and content may change over time.
