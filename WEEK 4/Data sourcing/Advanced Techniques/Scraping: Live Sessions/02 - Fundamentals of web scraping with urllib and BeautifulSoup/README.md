# Web Scraping – Session 2 (https://www.youtube.com/watch?v=I3auyTYORTs)

## Tools Required

1. **Browser** (Chrome / Firefox / Edge)
2. **Google Colab** (to run Python online)

Colab lets you:

* Run Python in the cloud
* Avoid burdening your local CPU
* Share notebooks easily

---

# Step 1: Fetch HTML from a Website

Websites don’t send visual pages.
They send **HTML code**.
Your browser converts HTML → visual display.

To fetch HTML in Python:

```python
from urllib.request import urlopen

url = "https://en.wikipedia.org/wiki/2024_Chile_wildfires"
x = urlopen(url)

x.read()
```

`urlopen()` → Opens the webpage
`.read()` → Reads the HTML content

---

# Step 2: Clean HTML using BeautifulSoup

Raw HTML is messy.
BeautifulSoup formats and helps search inside it.

```python
from bs4 import BeautifulSoup

soup = BeautifulSoup(x.read(), "html.parser")
soup
```

Now the HTML is structured and readable.

---

# Step 3: Find Elements by Tag

### Get first title:

```python
soup.title
```

### Get first `<h1>`:

```python
soup.h1
```

### Get first `<a>` tag:

```python
soup.a
```

Important:

* `soup.tagname` → gives **first occurrence only**

---

# Step 4: Get All Tags

To get all elements:

```python
soup.find_all("a")
```

Example: Count images

```python
images = soup.find_all("img")
len(images)
```

---

# Step 5: Access Specific Element (Indexing)

Since `find_all()` returns a list:

```python
images[0]   # First image
images[4]   # Fifth image
```

Remember:
Python indexing starts from 0.

---

# 🏷 Step 6: Find Using Attributes (Class, Width, etc.)

Instead of searching all tags manually, use attributes.

### Example: Find table with specific class

```python
soup.find_all("table", {"class": "infobox vevent"})
```

Format:

```python
soup.find_all("tag", {"attribute": "value"})
```

You can use:

* class
* id
* width
* height
* src
* href
* colspan
* etc.

---

### Example: Find image with specific width

```python
soup.find_all("img", {"width": "220"})
```

---

# Step 7: Nested Tags (Hierarchy)

HTML is hierarchical.

Example structure:

```
table
 └── tr
      └── td
```

To go step by step:

```python
table = soup.find_all("table")[0]
rows = table.find_all("tr")
columns = rows[0].find_all("td")
columns[0]
```
