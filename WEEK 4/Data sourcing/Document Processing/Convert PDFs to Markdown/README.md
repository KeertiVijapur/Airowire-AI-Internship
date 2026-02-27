# Converting PDFs to Markdown (https://www.youtube.com/watch?v=v65Oyddfxeg)

## Objective

Learn how to convert PDFs and other documents into **Markdown format** for:

* LLM training & fine-tuning
* RAG pipelines
* Knowledge base creation
* Search indexing
* Dataset generation
* OCR workflows

Markdown is lightweight, human-readable, and ideal for LLM ingestion.

---

# Why Markdown?

Markdown:

* Is plain text
* Is platform independent
* Preserves semantic structure (headings, lists, tables)
* Is ideal for LLM chunking
* Converts easily to HTML / PDF / LaTeX

Example:

```
# Heading
**Bold Text**
- Bullet List
```

---

# Tools Covered

This lecture compares multiple tools:

| Tool                           | Best For                      |
| ------------------------------ | ----------------------------- |
| PyMuPDF4LLM                    | LLM-ready structured markdown |
| MarkItDown (Microsoft)         | Multi-format conversion       |
| Unstructured                   | Production pipelines          |
| GROBID                         | Academic reference extraction |
| Mistral OCR API                | Layout-aware OCR              |
| Azure AI Document Intelligence | Enterprise OCR                |

---

# 1️ PyMuPDF4LLM (LLM-Optimized)

Built on MuPDF engine.

Best for:

* Preserving structure
* LLM semantic extraction
* Clean markdown generation

### Command-Line Usage

```bash
PYTHONUTF8=1 uv run --with pymupdf4llm python -c '
import pymupdf4llm
h = open("output.md", "w")
h.write(pymupdf4llm.to_markdown("file.pdf"))
'
```

### What it does:

* Reads PDF
* Converts layout into structured markdown
* Removes noisy formatting
* Preserves semantic hierarchy

---

# 2️ MarkItDown (Microsoft Tool)

New Microsoft utility for multi-format → Markdown conversion.

Supports:

* PDF
* DOCX
* PPTX
* XLSX
* Images (OCR)
* Audio
* HTML
* JSON
* XML
* ZIP

---

## Installation

```bash
pip install markitdown
```

---

## Basic Python Usage

```python
from markitdown import MarkItDown

md = MarkItDown()
result = md.convert("file.pdf")

print(result.text_content)
```

---

## CLI Usage

```bash
markitdown file.pdf > output.md
```

Or with pipe:

```bash
cat file.pdf | markitdown > output.md
```

---

## With LLM (OCR Example)

You can integrate with OpenAI for OCR:

```python
from markitdown import MarkItDown
from openai import OpenAI

client = OpenAI(api_key="YOUR_KEY")

md = MarkItDown(llm=client, model="gpt-4o")

result = md.convert("image.png")
print(result.markdown)
```

Useful for:

* OCR on scanned images
* Clean markdown generation
* LLM-enhanced formatting

---

# 3️ Unstructured

Best for:

* Production pipelines
* Multi-format ingestion
* LLM preprocessing

Pros:

* 40+ file types
* Actively maintained
* Good integration support

Cons:

* Resource intensive

---

# 4️ GROBID

Best for:

* Academic papers
* Citation extraction
* Bibliographic metadata

Runs via Docker:

```bash
docker run -t --rm -p 8070:8070 lfoppiano/grobid:0.7.2
```

Process document:

```bash
curl -X POST -F "input=@paper.pdf" \
localhost:8070/api/processFulltextDocument > references.xml
```

---

# 5️ OCR-Based APIs

## Mistral OCR API

* Preserves layout
* Cloud-based
* Requires post-processing

## Azure AI Document Intelligence

* Enterprise-level OCR
* Strong SLA support
* May require fine-tuning

---

# Tool Comparison Summary

| Tool         | Strength                        | Weakness                | Best Use Case    |
| ------------ | ------------------------------- | ----------------------- | ---------------- |
| PyMuPDF4LLM  | Structure preservation          | Requires PyTorch        | LLM datasets     |
| MarkItDown   | Multi-format support            | Layout precision varies | Batch conversion |
| Unstructured | Wide format support             | Heavy resource usage    | Pipelines        |
| GROBID       | Academic extraction             | Narrow domain           | Research papers  |
| Docling      | Advanced document understanding | Installation complexity | Research apps    |
| MegaParse    | Robust conversion               | Requires OpenAI API     | Complex OCR docs |

---

# How to Choose

If your goal is:

* LLM-ready dataset → PyMuPDF4LLM
* Batch conversion → MarkItDown
* Academic citation parsing → GROBID
* Production ingestion pipeline → Unstructured
* Heavy OCR layout tasks → Mistral / Azure

---

# Best Practices for PDF Conversion

### 1️ Pre-process PDF

```bash
ocrmypdf --optimize 3 --skip-text input.pdf optimized.pdf
```

### 2️ For Scanned PDFs

```bash
ocrmypdf --force-ocr input.pdf ocr_ready.pdf
```

Then convert.

---

### 3️ Post-processing Example

Fix formatting:

```bash
sed -i 's/\([A-Z]\)\.\s/\1.\n/g' output.md
```
