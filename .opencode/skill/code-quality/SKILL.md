---
description: HTML/CSS naming conventions, semantic structure, and anti-patterns to avoid
---

# Code Quality Skill

Naming conventions, semantic HTML, and patterns to avoid.

## HTML Semantic Structure

### Document Outline
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Page Title</title>
</head>
<body>
  <a href="#main" class="skip-link">Skip to content</a>
  
  <header>
    <nav aria-label="Primary">
      <!-- main navigation -->
    </nav>
  </header>
  
  <main id="main">
    <h1>Page Title</h1>
    <!-- content -->
  </main>
  
  <footer>
    <nav aria-label="Footer">
      <!-- footer links -->
    </nav>
  </footer>
</body>
</html>
```

### Heading Hierarchy
```html
<!-- GOOD: Logical hierarchy -->
<h1>Page Title</h1>
  <h2>Section</h2>
    <h3>Subsection</h3>
  <h2>Another Section</h2>

<!-- BAD: Skipped levels -->
<h1>Page Title</h1>
  <h4>Subsection</h4>  <!-- Skipped h2, h3 -->
```

### Article vs Section
```html
<!-- Article: Self-contained, syndicatable -->
<article>
  <h2>Blog Post Title</h2>
  <time datetime="2024-01-15">Jan 15, 2024</time>
  <p>Content that makes sense on its own...</p>
</article>

<!-- Section: Thematic grouping WITH heading -->
<section>
  <h2>Features</h2>
  <!-- Must have a heading to be semantic -->
</section>

<!-- Div: Styling only, no semantic meaning -->
<div class="card-grid">
  <!-- Just a wrapper for CSS -->
</div>
```

### Interactive Elements
```html
<!-- GOOD: Native elements -->
<button type="button">Click me</button>
<a href="/page">Go to page</a>
<dialog id="modal">...</dialog>
<details>
  <summary>Show more</summary>
  <p>Hidden content</p>
</details>

<!-- BAD: Div abuse -->
<div onclick="...">Click me</div>  <!-- Use button -->
<div role="button">Click me</div>  <!-- Use button -->
<a href="#" onclick="...">Action</a>  <!-- Use button -->
```

### Forms
```html
<!-- GOOD: Proper labels -->
<label for="email">Email</label>
<input type="email" id="email" name="email" required>

<!-- GOOD: Grouped inputs -->
<fieldset>
  <legend>Shipping Method</legend>
  <label><input type="radio" name="ship"> Standard</label>
  <label><input type="radio" name="ship"> Express</label>
</fieldset>

<!-- BAD: Placeholder as label -->
<input placeholder="Email">  <!-- No label! -->
```

## CSS Naming Conventions

### Simple Dash-Case (Preferred)
```css
/* Block */
.card { }
.nav { }
.hero { }

/* Children (dash-separated) */
.card-title { }
.card-body { }
.card-footer { }

/* Variants (data attributes) */
.card[data-variant="featured"] { }
.btn[data-size="lg"] { }
```

### BEM (When Needed)
```css
/* Block */
.story-card { }

/* Element */
.story-card__title { }
.story-card__meta { }

/* Modifier */
.story-card--featured { }
.story-card--compact { }
```

### Anti-Pattern Names to Avoid
```css
/* BAD: Too generic */
.container { }  /* Container of what? */
.wrapper { }    /* Wrapper of what? */
.content { }    /* All content? */
.item { }       /* Item in what context? */

/* GOOD: Domain-specific */
.hero { }
.card-grid { }
.nav-drawer { }
.article-meta { }
```

## CSS Anti-Patterns

### Explicit Defaults (Don't Do)
```css
/* BAD: Browser already does this */
div { display: block; }
span { display: inline; }
img { max-width: auto; }

/* GOOD: Only declare what you're changing */
.card { display: flex; }
```

### Magic Numbers
```css
/* BAD: Arbitrary values */
.modal { z-index: 9999; }
.header { height: 73px; }
.gap { margin-top: 17px; }

/* GOOD: Token-based */
.modal { z-index: var(--z-modal); }
.header { height: auto; padding: var(--space-4); }
.gap { margin-top: var(--space-4); }
```

### Deep Nesting
```css
/* BAD: Too specific, hard to override */
.page .content .card .card-body .card-title span { }

/* GOOD: Flat, composable */
.card-title { }
```

### !important Abuse
```css
/* BAD: Specificity war */
.btn { color: blue !important; }
.btn-red { color: red !important; }

/* GOOD: Use cascade layers */
@layer components {
  .btn { color: blue; }
}
@layer utilities {
  .text-red { color: red; }  /* Wins via layer order */
}
```

## Accessibility Checklist

### Required
- [ ] `<html lang="en">`
- [ ] Skip link first in DOM
- [ ] One `<main>` element
- [ ] One `<h1>` per page
- [ ] No skipped heading levels
- [ ] All inputs have labels
- [ ] All images have alt text
- [ ] Focus styles visible
- [ ] 44x44px touch targets
- [ ] 4.5:1 text contrast

### Interactive
- [ ] Buttons for actions
- [ ] Links for navigation
- [ ] ARIA labels on icon-only buttons
- [ ] `aria-current="page"` on nav links

### Motion
- [ ] `prefers-reduced-motion` respected
- [ ] No auto-playing animations
- [ ] Pause controls for animations
