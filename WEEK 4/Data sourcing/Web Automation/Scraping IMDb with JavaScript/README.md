# Scraping IMDb with JavaScript (Browser DevTools)

## What I Learned

In this session, I learned how to scrape data directly from a webpage using **JavaScript in the browser console**, without using Python.

Used Chrome DevTools to extract data from the **IMDb Top 250 movies page**.

---

## Tools Used

* Chrome DevTools (F12 / Inspect)
* `document.querySelectorAll()`
* JavaScript array methods (`map`)
* Clipboard copy function

---

## Basic Approach

1. Open IMDb Top 250 page
2. Open DevTools → Console
3. Inspect movie title elements
4. Use `querySelectorAll()` to select elements
5. Extract text using `.textContent`
6. Convert NodeList → Array
7. Copy results to clipboard

Example:

```javascript
const movies = Array.from(
  document.querySelectorAll(".cli-title")
).map(el => el.textContent.trim());

copy(movies);
```

---

## Key Concepts

* `querySelector()` → selects first matching element
* `querySelectorAll()` → returns NodeList
* Must convert NodeList to array using `Array.from()`
* `.textContent` is used to extract text
* `map()` helps transform elements efficiently

---

## Common Issues Faced

* Incorrect CSS selector
* Using wrong pseudo-class (`nth-child`)
* Forgetting `.textContent`
* Trying to directly use NodeList without converting

---

## Output

* Extracted movie titles
* Converted to JSON-like array
* Later exported to CSV / Excel

---

## Key Takeaways

* Browser console can be used as a lightweight scraper.
* JavaScript can directly interact with DOM elements.
* Useful for quick extraction without writing full scraping scripts.
* Understanding HTML structure is critical.
