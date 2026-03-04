# BBC Weather Location ID (API Interception) - (https://www.youtube.com/watch?v=IafLrvnamAw , https://www.youtube.com/watch?v=Uc4DgQJDRoI)

## What I Learned

In this session, I learned how to extract the **location ID** of a city from the BBC Weather website by inspecting the API calls made in the background.

Instead of scraping HTML directly, we:

1. Opened Developer Tools (Network tab)
2. Typed a city name in BBC’s search bar
3. Observed the API request being triggered
4. Found that the response contains a JSON object
5. Extracted the `id` field (location ID)

This ID is required to fetch weather data programmatically.

---

## Key Technical Points

* Used **browser DevTools → Network tab**
* Identified the API endpoint returning JSON
* Extracted fields like:

  * `id`
  * `name`
  * `country`
  * `latitude`, `longitude`

---

## Python Implementation

Libraries used:

```python
requests
json
urllib.parse (urlencode)
```

Flow:

* Construct API URL using `urlencode`
* Send GET request
* Parse JSON response
* Extract `id`
* Wrap everything inside a reusable function

---

## Example Output

| City        | Location ID |
| ----------- | ----------- |
| Los Angeles | 5368361     |
| New York    | 5128581     |
| Toronto     | 6167865     |

---

## Key Takeaways

* Many websites expose APIs behind UI search bars.
* Inspecting network calls is powerful.
* JSON-based APIs are cleaner than scraping raw HTML.
* URL construction using `urlencode` avoids messy string formatting.

---

# 📘 LECTURE 9 – Scraping BBC Weather Data

## What I Learned

After getting the location ID, this lecture focused on scraping **14-day weather forecast data** from BBC Weather.

Data extracted:

* Daily high temperatures
* Daily low temperatures
* Daily summaries

---

## Tools Used

```python
requests
BeautifulSoup
pandas
re (regex)
datetime
```

---

## Workflow

1. Use location ID to build weather URL
2. Fetch HTML using `requests.get()`
3. Parse HTML with `BeautifulSoup`
4. Extract:

   * High temps → class `day-temperature_high`
   * Low temps → class `day-temperature_low`
   * Summary → long string split using regex
5. Clean temperature values (remove ° symbol)
6. Create pandas DataFrame
7. Generate 14-day date range
8. Save data as CSV and Excel

---

## Important Observations

* HTML inspection is essential before scraping.
* Extracted lists contain unwanted data → cleaning required.
* Regex was used to split concatenated summaries.
* Data must be cleaned before converting to numeric type.

---

## Final Data Structure

| Date | High Temp | Low Temp | Summary |
| ---- | --------- | -------- | ------- |

---

## Key Learnings

* `requests` + `BeautifulSoup` are core scraping tools.
* Dynamic URL construction is better than hardcoding.
* Data cleaning is as important as extraction.
* Always check website legality before scraping.
