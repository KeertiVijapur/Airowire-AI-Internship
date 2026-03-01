# LLM Video Screen-Scraping (https://www.youtube.com/watch?v=2G1LqS6qO5s)

## Objective

Extract structured data from screen recordings using multimodal LLMs (Vision Models).

Instead of scraping:

* HTML
* APIs
* DOM elements

We scrape:

> What is visually visible on screen.

This bypasses:

* Authentication barriers
* Anti-scraping protections
* Obfuscated APIs
* Dynamic JS rendering
* CAPTCHA walls (when already logged in)

---

# Core Idea

1. Record your screen while scrolling through content
2. Upload video to a multimodal LLM (e.g., Gemini)
3. Ask it to extract structured data (JSON/CSV)

This is computer vision-based scraping.

---

# Why This Works

LLMs with vision capability:

* Process video as a sequence of frames
* Extract text from images
* Understand layout and semantics
* Output structured JSON

No DOM required.

---

# Quick Start Workflow

## Step 1 – Record Screen

Use any tool:

* QuickTime (Mac)
* Windows Game Bar
* Screen2Gif
* OBS Studio

Best settings:

* 1 frame per second
* Scroll slowly
* Keep videos short (30–60 seconds)
* Focus only on target content

---

## Step 2 – Upload to LLM

Upload video to:

* Google AI Studio (Gemini 1.5 Flash)

Then prompt:

```text
Turn this video into a JSON array where each item has:

{
  "date": "yyyy-mm-dd",
  "amount": float
}
```

You get structured output.

---

# Cost Analysis (Gemini 1.5 Flash)

* $0.075 per million tokens
* ~250 tokens per frame
* 1 frame per second

Example:

19 frames → ~$0.0004
1000 seconds → ~$0.018

Extremely cheap.

---

# Best Practices

## 1️ Recording Quality

* Frame only relevant content
* Maintain consistent scroll speed
* Pause briefly on important sections
* Use high contrast display

---

## 2️ Data Validation

* Always manually verify sample output
* Spot-check large datasets
* Run multiple passes if needed
* Log anomalies

---

## 3️ Error Handling

* Ask for structured JSON output
* Split long videos into segments
* Handle missing fields gracefully
* Include validation schema in prompt

---

# Use Cases

## Data Extraction

* Email aggregation
* Dashboard metrics
* Protected web content
* Legacy systems

---

## Data Journalism

* Public records
* Time-series extraction
* Government site scraping

---

## Business Intelligence

* Competitor pricing
* Market research
* Internal tool migration
* Report digitization

---

# Comparison to Traditional Scraping

| Method              | Requires DOM | Handles Auth       | Bypasses Anti-Scraping | Maintenance |
| ------------------- | ------------ | ------------------ | ---------------------- | ----------- |
| requests + BS4      | Yes          | No                 | No                     | High        |
| Playwright          | Yes          | Yes                | Sometimes              | Medium      |
| LLM Screen Scraping | No           | Yes (if logged in) | Yes                    | Low         |

This is the only method that works purely on visible pixels.

---

# When To Use It

Use LLM video scraping when:

* Website blocks automation
* APIs are hidden
* Heavy JS rendering
* Login-required content
* Anti-bot systems active
* Legacy internal dashboards

---

# Limitations

* Accuracy depends on video clarity
* Not ideal for huge datasets (better to use APIs)
* OCR errors possible
* May require post-processing cleanup

---

# Legal & Ethical Reminder

Even if technically possible:

* Respect Terms of Service
* Avoid paywall bypassing
* Don’t overload platforms
* Use responsibly
