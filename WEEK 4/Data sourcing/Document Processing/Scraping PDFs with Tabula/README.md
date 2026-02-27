# Scraping PDFs using Tabula (Python) - (https://www.youtube.com/watch?v=yDoKlKyxClQ)

## What I Learned

In this session, I learned how to:

1. Download multiple PDF files from a given URL
2. Extract tabular data from those PDFs
3. Convert extracted tables into structured formats like CSV

This is useful when data is published in PDF format instead of CSV or Excel.

---

## Libraries Used

```python
BeautifulSoup
requests
os
tabula
pandas
```

---

## Part 1 – Downloading Multiple PDFs from a URL

### Workflow

1. Pass the target URL (hosting multiple PDFs)
2. Parse the webpage using `BeautifulSoup`
3. Identify all links ending with `.pdf`
4. Loop through them
5. Download and save locally

Example logic:

```python
import requests
from bs4 import BeautifulSoup

response = requests.get(url)
soup = BeautifulSoup(response.text, "html.parser")

for link in soup.find_all("a"):
    href = link.get("href")
    if href and href.endswith(".pdf"):
        # download file
```

PDF filenames are extracted using string split (`split("/")[-1]`).

---

## Part 2 – Extracting Tables from PDF using Tabula

Some PDFs contain structured tables (e.g., league standings, financial reports).

Tabula helps extract these tables.

Basic usage:

```python
import tabula

tables = tabula.read_pdf("file.pdf", pages=18)
```

This returns table data as a pandas DataFrame.

---

## Controlling Extraction Area

Sometimes Tabula extracts extra text.

To fix this, we can specify the exact table area:

```python
tabula.convert_into(
    "file.pdf",
    "output.csv",
    output_format="csv",
    pages=18,
    area=[top, left, bottom, right]
)
```

This restricts extraction to a specific region on the page.

---

## Key Observations

* PDFs often contain noise (extra text below tables).
* Manual cleaning may still be required.
* Coordinates improve accuracy.
* Extracted tables can be converted to CSV for analysis.

---

## Use Case Example

Downloaded multiple Premier League season PDFs and extracted:

* Final standings
* Club statistics
* Season data

Converted extracted tables into structured DataFrames for further analysis.

---

## Key Takeaways

* Data sourcing is not always CSV or API-based.
* PDFs require document processing tools.
* BeautifulSoup → identifies PDF links.
* Tabula → extracts tabular data.
* Cleaning is still required after extraction.
* Or prepare internship diary entry for this lecture too
