# Scraping IMDb Top 250 using JavaScript (https://www.youtube.com/watch?v=YVIKZqZIcCo)

## What I Learned

In this session, I learned how to scrape data directly from a website using **JavaScript inside the browser console**, without using Python or external libraries.

Target: **IMDb Top 250 Movies**

Extracted:

* Movie title
* Year
* Duration
* Rating
* Number of votes
* Movie link

---

## Tools Used

* Chrome DevTools (F12 → Console)
* JavaScript (`querySelector`, `querySelectorAll`)
* `.map()` and arrow functions
* `copy()` to export data

---

## Basic Workflow

1. Open IMDb Top 250 page
2. Open DevTools → Console
3. Inspect HTML structure
4. Select all movie elements using:

```javascript
const items = document.querySelectorAll('.ipc-metadata-list-summary-item');
```

5. Extract required fields using `.map()`:

```javascript
const data = Array.from(items).map(item => ({
  title: item.querySelector('.ipc-title__text')?.textContent,
  link: item.querySelector('a')?.href
}));
```

6. Use:

```javascript
copy(data);
```

7. Paste into JSON → CSV converter / Excel

---

## Key Concepts Used

* `querySelector()` → Select single element
* `querySelectorAll()` → Select multiple elements
* `.map()` → Transform NodeList into structured data
* Optional chaining `?.` → Avoid errors if element missing
* DOM inspection via Elements tab

---

## Key Takeaways

* Websites can be scraped directly from browser using JavaScript.
* Understanding HTML structure is critical.
* No backend or Python needed for simple scraping.
* Data extraction depends on page class names (can break if website updates).

---

## Important Note

IMDb’s HTML structure may change, so selectors must be updated accordingly.
