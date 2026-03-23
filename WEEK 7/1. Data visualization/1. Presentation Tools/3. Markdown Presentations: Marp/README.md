# Markdown Presentations using Marp (https://www.youtube.com/watch?v=EzQ-p41wNEE)

## Marp – Markdown-Based Presentation Tool

Marp is a powerful tool that allows you to create **presentations using Markdown** directly from your text editor (like VS Code). It converts simple Markdown files into **beautiful, professional slides**.

---

## What is Marp?

Marp (Markdown Presentation Ecosystem) enables:

* Creating slides using **Markdown syntax**
* Fast and simple presentation creation
* Exporting presentations into multiple formats

---

## Key Features

* Write presentations using **Markdown**
* Built-in themes (Default, Gaia, Uncover)
* Syntax highlighting for code
* Math support (KaTeX / MathJax)
* Image handling and layouts
* Custom styling with CSS
* Export to HTML, PDF, PowerPoint

---

## Installation

### Using VS Code (Recommended)

1. Open Extensions in VS Code
2. Search for **Marp for VS Code**
3. Install the extension

---

## Basic Structure

A Marp presentation starts with front matter:

```markdown
---
marp: true
title: My Presentation
theme: default
paginate: true
---

# Slide 1
Content here

---

# Slide 2
More content
```

---

## Themes

Marp provides built-in themes:

* **default** → simple
* **gaia** → modern
* **uncover** → presentation-style

Example:

```markdown
---
theme: uncover
class: invert
---
```

---

## Code Blocks with Highlighting

````markdown
```python
print("Hello World")
````

````

- Automatically uses **syntax highlighting**
- Useful for technical presentations  

---

## Math Support  

Enable math rendering:

```markdown
---
math: katex
---
````

Examples:

* Inline: `$x^2 + y^2$`
* Block:

```markdown
$$
\frac{a}{b} = c
$$
```

---

## Images and Layouts

Basic image:

```markdown
![image](image.png)
```

### Side-by-side layout:

```markdown
![bg left](image.png)

- Point 1
- Point 2
```

---

## Styling with Directives

* Change background color
* Add headers/footers
* Customize slide appearance

Example:

```markdown
<!-- _backgroundColor: black -->
<!-- _color: red -->
```

---

## Columns (Advanced)

Using custom HTML + CSS:

```html
<div class="columns">
  <div>Column 1</div>
  <div>Column 2</div>
</div>
```

---

## Export Options

Marp supports multiple formats:

```bash
marp slides.md -o slides.html
marp slides.md -o slides.pdf
marp slides.md -o slides.pptx
```

Formats:

* HTML (best for interactivity)
* PDF (static)
* PowerPoint (slides as images)

---

## Key Learnings

* Learned how to create **presentations using Markdown**
* Understood **theme customization and styling**
* Explored **code, math, and image integration**
* Learned exporting presentations in multiple formats
* Understood limitations of different formats (HTML vs PDF vs PPT)

---

## Best Practices

* Keep slides **simple and minimal**
* Use **bullet points instead of paragraphs**
* Maintain consistent themes
* Use visuals for better understanding
