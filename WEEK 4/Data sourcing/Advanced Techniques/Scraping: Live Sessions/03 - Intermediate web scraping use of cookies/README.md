# Scraping Static vs Dynamic Websites (https://www.youtube.com/watch?v=DryMIxMf3VU)

### Static Website (Easy)

Example: Simple population table

* Use `urllib` + `BeautifulSoup`
* Inspect HTML
* Find pattern (table → rows → columns)
* Loop using `range()` and `len()`

---

# The Real Challenge: Login-Based Websites

Example: MovieLens

Problem:

* Website requires login
* Your homepage ≠ someone else's homepage
* Simple `urlopen()` won’t work

Why?

Because login-based sites use **cookies**.

---

# What Are Cookies?

When you log in:

* Browser sends login info to server
* Server sends back a **session cookie**
* Cookie proves you are authenticated

Each user gets:

```
ml4_session = unique_value
```

Different for every user.
Expires after logout or time limit.

---

# How to Find Cookies

1. Right-click → **Inspect**
2. Go to **Network**
3. Refresh page
4. Click first request
5. Scroll to **Request Headers**
6. Find `Cookie`

---

# Why `urllib` Failed

Even after copying cookies:

* `urllib` doesn’t handle cookies easily
* It requires cookie handlers

So we switch to:

# `requests` Library (Better for Cookies)

---

# Correct Method Using Requests

```python
import requests
import json

url = "FRONT_PAGE_API_URL"

cookies = {
    "ml4_session": "your_cookie_value_here"
}

x = requests.get(url, cookies=cookies)
```

Check status:

```python
x.status_code
```

`200` = Success
`401` = Unauthorized
`202` = Accepted

---

# Why Homepage URL Didn’t Work?

Modern websites:

* Don’t load full HTML
* Use **API calls**
* Fetch data dynamically via JSON

So we:

1. Open Network tab
2. Find correct API (e.g., `/api/user/me/frontpage`)
3. Use that API URL in Python

---

# Converting Response to JSON

```python
data = json.loads(x.text)
```

Now data becomes structured dictionary.

---

# Accessing Movie Titles

JSON structure:

```
data
 └── searchResult
      └── movie
           └── title
```

Extract:

```python
data = json.loads(x.text)

for i in range(5):
    print(data["data"][0]["searchResult"][i]["movie"]["title"])
```

Output:

* Shawshank Redemption
* Godfather
* Parasite
* Godfather Part II
* Usual Suspects

---

# Key Learnings

✔ Login-based scraping requires cookies
✔ Each user has unique session cookie
✔ Never share cookies (security risk)
✔ Modern websites use APIs instead of simple HTML
✔ Use `requests` for cookie-based authentication
✔ Convert response to JSON
✔ Navigate dictionary step-by-step

---

# Security Insight

If someone gets your session cookie:

* They can access your logged-in session
* No password needed
* That’s why cookies are sensitive

---

# Big Concept Learned

Scraping is not just:

```
find_all("table")
```

It involves:

* Inspecting APIs
* Understanding authentication
* Handling JSON
* Reading network traffic
* Debugging responses
