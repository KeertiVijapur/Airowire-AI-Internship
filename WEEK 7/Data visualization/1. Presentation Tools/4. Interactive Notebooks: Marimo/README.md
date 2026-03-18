# Interactive Notebooks: Marimo (https://www.youtube.com/watch?v=9R2cQygaoxQ)

## Marimo – Reactive Python Notebooks

Marimo is a modern alternative to traditional notebooks like Jupyter. It introduces a **reactive execution model**, making notebooks more **reproducible, maintainable, and interactive**.

---

## What is Marimo?

Marimo is an **open-source Python notebook tool** that:

* Runs code reactively (like Excel spreadsheets)
* Automatically updates outputs when inputs change
* Eliminates issues like **hidden state in Jupyter notebooks**

---

## Why Marimo? (Problem with Traditional Notebooks)

### Issues in Jupyter Notebooks:

* Cells can be run in **any order**
* Leads to **hidden state problems**
* Outputs may not match the visible code
* Hard to debug and reproduce

Example:

* Variable defined in one cell but not visible
* Execution order confusion

👉 Result: Many notebooks are **not reproducible**

---

## Key Features of Marimo

### 1. Reactive Execution

* Automatically re-runs dependent cells
* Similar to **Excel recalculation**

👉 Change a variable → All dependent outputs update automatically

---

### 2. No Hidden State

* Execution is based only on visible code
* Ensures **reproducibility**

---

### 3. Directed Acyclic Graph (DAG) Model

* Cells are connected based on dependencies
* Ensures correct execution order

---

### 4. Interactive UI Elements

Example:

```python
import marimo as mo

slider = mo.ui.slider(1, 100)
mo.md(f"Value: {slider.value}")
```

* Creates interactive widgets
* Enables dynamic visualizations

---

### 5. Pure Python File Format

* Stored as `.py` instead of JSON
* Easier to:

  * Version control (Git)
  * Debug
  * Maintain

---

### 6. Run as Scripts

```bash
python notebook.py
```

* Notebooks can be executed like normal Python scripts

---

### 7. Share as Web Apps

```bash
marimo run notebook.py
```

* Convert notebooks into interactive web apps
* No need for users to know Python

---

## Common Operations

```bash
# Create notebook
uvx marimo new

# Run notebook
uvx marimo edit notebook.py

# Export notebook
uvx marimo export notebook.py
```

---

## Best Practices

### 1. Cell Design

* Keep cells small and focused
* Use clear variable names
* Avoid unnecessary complexity

### 2. Interactive Elements

* Use sliders and inputs for better UX
* Make data exploration dynamic

### 3. Version Control

* Use Git for tracking changes
* Keep notebooks clean and modular

---

## Key Learnings

* Learned how **reactive notebooks differ from Jupyter**
* Understood the concept of **hidden state issues**
* Explored **DAG-based execution**
* Learned how to build **interactive data apps**
* Understood benefits of **Python-based notebook format**

---

## Key Takeaways

* Marimo improves **reproducibility and debugging**

* Eliminates execution-order problems

* Combines:

  * Code
  * Visualization
  * Interactivity

* Useful for:

  * Data science
  * Research
  * Interactive dashboards
