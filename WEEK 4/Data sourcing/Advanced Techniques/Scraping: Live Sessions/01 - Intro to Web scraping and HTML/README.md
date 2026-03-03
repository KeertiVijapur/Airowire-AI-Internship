# Intro to Web Scraping & HTML – Key Takeaways

## 1️ What is Web Scraping?

Web scraping = Automatically extracting data from websites instead of copying manually.

### Demonstrations:

* Extracted ~500 links from a Wikipedia page in seconds
* Scraped country data automatically into CSV
* Automated Amazon product extraction (multi-page)
* Used Selenium to open browser, navigate, extract, save data

Key Idea: Automation saves hours of manual effort.

---

## 2️ Why It’s Powerful

Practical Applications:

*  Price monitoring (Amazon, Flipkart, etc.)
*  Weather data collection
*  Research data gathering
*  News aggregation
*  Scheduled automation (via system commands)

---

## 3️ HTML Fundamentals (Very Important)

Web scraping requires understanding HTML structure.

### Basic HTML Structure

```html
<html>
  <head>
    <title>Page Title</title>
  </head>
  <body>
    Content here
  </body>
</html>
```

---

## 4️ Important HTML Tags Covered

### Headings

`<h1>` to `<h6>`
(h1 biggest, h6 smallest)

### Paragraph

`<p>`

### Line Break

`<br>`

### Horizontal Line

`<hr>`

### Link (Anchor Tag)

```html
<a href="https://example.com">Click Here</a>
```

### Image

```html
<img src="image.jpg" width="200">
```

### Table

```html
<table border="1">
  <tr>
    <th>Name</th>
    <th>Class</th>
  </tr>
  <tr>
    <td>Amit</td>
    <td>TDS</td>
  </tr>
</table>
```

### Lists

Unordered list:

```html
<ul>
  <li>Apple</li>
  <li>Mango</li>
</ul>
```

Ordered list:

```html
<ol>
  <li>Item 1</li>
  <li>Item 2</li>
</ol>
```

---

## 5️ Inspect Element (VERY IMPORTANT for Scraping)

Right click → Inspect

You can:

* View HTML structure
* Identify tags (`h1`, `p`, `img`, `table`)
* Locate image sources (`src`)
* Locate links (`href`)
* Modify page temporarily

This is how scrapers understand what to extract.

---

## 6️ Network Tab (Advanced Insight)

In DevTools → Network tab:

You can:

* Monitor API calls
* See background requests
* Inspect data responses (JSON)
* Understand how data loads dynamically

This is critical for advanced scraping.

---

## 7️ Tools Mentioned

* Notepad (basic)
* VS Code (recommended)
* Selenium
* CSV export
* Inspect tool
* Network monitoring

---

## 8️ Key Concept Difference

| HTML                 | Python                    |
| -------------------- | ------------------------- |
| Structure of webpage | Logic & computation       |
| Markup language      | Programming language      |
| Displays content     | Processes & extracts data |
