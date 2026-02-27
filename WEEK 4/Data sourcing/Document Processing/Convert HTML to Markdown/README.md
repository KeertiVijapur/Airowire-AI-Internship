# Converting HTML to Markdown (https://www.youtube.com/watch?v=HPSK7q13-40)

## Objective

Convert HTML content into:

* Clean Markdown
* Plain text
* LLM-ready structured documents

Used for:

* NLP preprocessing
* RAG pipelines
* SEO analysis
* Knowledge base building
* Website archiving
* Data mining
* Offline content storage

---

# Why Convert HTML?

HTML contains:

* Navigation menus
* Ads
* Scripts
* Boilerplate
* Styling tags

For AI pipelines, we need:

* Clean structure
* Headings preserved
* Content without clutter
* Markdown for chunking

---

# Tools Covered

| Tool             | Type                     | Best For                     |
| ---------------- | ------------------------ | ---------------------------- |
| defuddle-cli     | HTML → Markdown          | Clean structure preservation |
| pandoc           | Universal converter      | Precise academic conversion  |
| lynx             | HTML → Text              | Fast extraction              |
| w3m              | HTML → Text/Markdown     | Better layout than lynx      |
| Crawl4AI         | Crawl + Clean extraction | AI data collection           |
| markdown-crawler | Crawl + Convert          | Bulk website archiving       |

---

# 1️ defuddle-cli

Specialized HTML → Markdown tool.

Good at:

* Preserving structure
* Keeping links
* Producing readable markdown

### Batch Conversion

```bash
find . -name "*.html" -exec npx --package defuddle-cli -y defuddle parse {} --md -o {}.md \;
```

### What it does:

* Finds all HTML files
* Converts each to markdown
* Saves as `.md`

Best for:

* Content migration
* Publishing pipelines

---

# 2️ Pandoc (Swiss Army Knife)

Most powerful document converter.

Supports:

* HTML
* PDF
* DOCX
* LaTeX
* EPUB
* Markdown
* and more

### Batch Conversion

```bash
find . -name "*.html" -exec pandoc -f html -t markdown_strict -o {}.md {} \;
```

### Why Pandoc?

* High formatting accuracy
* Preserves tables
* Preserves citations
* Ideal for academic work

Best for:

* Documentation systems
* Research papers
* Precise structure retention

---

# 3️ Lynx (Fast Text Extraction)

Terminal text browser.

Converts HTML → plain text.

### Batch Conversion

```bash
find . -type f -name "*.html" -exec sh -c '
for f; do
  lynx -dump -nolist "$f" > "${f%.html}.txt"
done
' sh {} +
```

Best for:

* Speed
* Large batch jobs
* Quick scraping

Weakness:

* Loses advanced formatting

---

# 4️ w3m (Better than Lynx for Layout)

More thorough rendering.

```bash
find . -type f -name "*.html" -exec sh -c '
for f; do
  w3m -dump -T text/html -cols 80 -no-graph "$f" > "${f%.html}.md"
done
' sh {} +
```

Better for:

* Tables
* Slightly complex layouts
* Basic JS sites

---

# Tool Comparison

| Tool         | Speed     | Quality   | Best Use              |
| ------------ | --------- | --------- | --------------------- |
| defuddle-cli | Slow      | High      | Publishing            |
| pandoc       | Slow      | Very High | Academic precision    |
| lynx         | Fast      | Low       | Bulk quick extraction |
| w3m          | Very Slow | Medium    | Table-heavy pages     |

---

# Optimizing Batch Processing

## Parallel Processing

```bash
find . -name "*.html" | parallel "pandoc -f html -t markdown_strict -o {.}.md {}"
```

## Filter Large Files Only

```bash
find . -name "*.html" -type f -size -1M -exec pandoc -f html -t markdown -o {}.md {} \;
```

## Error Handling

```bash
find . -name "*.html" -exec sh -c '
for f; do
  pandoc -f html -t markdown "$f" -o "${f%.html}.md"
done
' sh {} +
```

---

# Choosing the Right Tool

If you need:

*  Speed → lynx
*  Precision → pandoc
*  Clean readable markdown → defuddle-cli
*  Better tables → w3m

---

# Combined Crawling + Conversion

Sometimes you need to:

1. Crawl website
2. Extract main content
3. Convert to markdown
4. Store structured output

---

# Crawl4AI

Optimized for AI-ready extraction.

Installation:

```bash
uv venv
source .venv/bin/activate
uv pip install crawl4ai
crawl4ai-setup
```

Best for:

* AI dataset creation
* Boilerplate removal
* Structured article extraction

---

# markdown-crawler

All-in-one crawling + markdown conversion.

```bash
uv venv
source .venv/bin/activate
uv pip install markdown-crawler

markdown-crawler -t 5 -d 3 -b ./markdown https://example.com
```

Options:

* `-t 5` → 5 threads
* `-d 3` → crawl depth 3
* `-b` → output directory

Best for:

* Bulk site archiving
* RAG knowledge base building
