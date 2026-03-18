# HTML Slides using RevealJS (https://www.youtube.com/watch?v=a6ioNtv2H-E&list=PLoqZcxvpWzzf_C8QgHC9XbA-bn18qJ-QV)

## RevealJS – Interactive Presentations for Data Visualization

RevealJS is an **open-source HTML presentation framework** that allows you to create **interactive, responsive, and web-based presentations**. It enables developers and data analysts to present insights in a modern, dynamic format.

---

## What is RevealJS?

RevealJS is a framework that:

* Turns web pages into **interactive slide decks**
* Runs on any device with a browser (mobile, tablet, desktop)
* Supports **animations, transitions, and interactivity**

---

## Key Features

* Fully responsive presentations
* Markdown support for quick content creation
* Code highlighting for technical presentations
* Interactive elements (charts, iframes, demos)
* Animations and transitions
* Custom themes using CSS
* Works offline and online

---

## Installation

### Option 1: Using npm (Recommended)

```bash
npm install reveal.js
```

### Option 2: CDN (Quick Setup)

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js/dist/reveal.css">
<script src="https://cdn.jsdelivr.net/npm/reveal.js/dist/reveal.js"></script>
```

### Option 3: Create Project

```bash
npx create-reveal-app my-presentation
```

---

## Basic Structure

A simple RevealJS presentation:

```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="dist/reveal.css">
</head>
<body>
  <div class="reveal">
    <div class="slides">
      <section>Slide 1</section>
      <section>Slide 2</section>
    </div>
  </div>

  <script src="dist/reveal.js"></script>
  <script>
    Reveal.initialize();
  </script>
</body>
</html>
```

---

## Markdown Support

RevealJS allows writing slides using Markdown:

```html
<section data-markdown>
<textarea data-template>
## Slide Title
- Point 1
- Point 2
</textarea>
</section>
```

---

## Interactive Elements

* Charts using libraries like Chart.js
* Embedded content using iframes
* Live demos

Example:

```html
<iframe src="https://example.com"></iframe>
```

---

## Animations and Fragments

RevealJS supports step-by-step animations:

```html
<li class="fragment">First point</li>
<li class="fragment">Second point</li>
```

---

## Code Highlighting

```html
<pre><code class="language-python">
print("Hello World")
</code></pre>
```

---

## Custom Styling

You can customize using CSS:

```css
.reveal {
  font-family: Arial;
}
```

---

## Use Cases

* Data presentations
* Technical talks
* Project demos
* Educational content
* Interactive dashboards

---

## Best Practices

* Keep slides simple and minimal
* Use visuals instead of too much text
* Maintain consistent styling
* Optimize performance for large data
