# Crawling with CLI (https://www.youtube.com/watch?v=pLfH5TZBGXo)

### What I Learned

In this session, I learned how to crawl entire websites using command-line tools like `wget`.

Crawling allows downloading multiple linked pages recursively instead of scraping one page manually.

---

### Basic Example

```bash
wget --recursive --level=2 --no-parent https://study.iitm.ac.in/ds/
```

This downloads the website up to 2 levels deep.

---

### Important Concepts

* `--recursive` → Follow links
* `--level` → Control crawl depth
* `--no-parent` → Restrict to current directory
* `--convert-links` → Make links work offline

---

### robots.txt

* A file that tells crawlers what is allowed.
* Should be respected for ethical crawling.
* Overriding it can cause IP bans or legal issues.

---

### Tools Introduced

* wget
* wget2
* wpull
* HTTrack

---

### Key Takeaways

* Crawling downloads full site structure.
* Depth control is important.
* Always respect robots.txt.
* Useful for archiving and large-scale data collection.
