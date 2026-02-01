---
description: CSS Grid/Flexbox, semantic HTML, accessibility, and modern CSS patterns
---

# Frontend Design Skill

Modern CSS architecture patterns for static HTML+CSS sites.

## CSS Cascade Layers

```css
/* main.css - define order FIRST */
@layer reset, base, components, utilities;

@import "base/reset.css" layer(reset);
@import "base/tokens.css" layer(base);
@import "components/card.css" layer(components);
@import "utilities/helpers.css" layer(utilities);
```

## Design Tokens

```css
:root {
  /* Colors - OKLCH for perceptual uniformity */
  --color-primary: oklch(55% 0.2 250);
  --color-surface: light-dark(#fff, #0a0a0a);
  --color-text: light-dark(#1a1a1a, #f5f5f5);
  
  /* Spacing - 4px base */
  --space-1: 0.25rem;  --space-2: 0.5rem;
  --space-4: 1rem;     --space-8: 2rem;
  --space-16: 4rem;    --space-32: 8rem;
  
  /* Typography */
  --text-sm: 0.875rem; --text-base: 1rem;
  --text-lg: 1.125rem; --text-xl: 1.25rem;
  --text-2xl: 1.5rem;  --text-4xl: 2.5rem;
  
  /* Radii */
  --radius-sm: 0.25rem; --radius-md: 0.5rem;
  --radius-lg: 1rem;    --radius-full: 9999px;
  
  /* Z-index scale */
  --z-base: 0; --z-dropdown: 10;
  --z-sticky: 20; --z-modal: 30;
  --z-toast: 40;
}

body { color-scheme: light dark; }
```

## Layout Patterns

### Holy Grail
```css
body {
  display: grid;
  grid-template-rows: auto 1fr auto;
  min-height: 100dvh;
}
```

### Responsive Grid (No Media Queries)
```css
.grid {
  display: grid;
  grid-template-columns: repeat(
    auto-fit, 
    minmax(min(300px, 100%), 1fr)
  );
  gap: var(--space-4);
}
```

### Container Queries
```css
.card-wrapper {
  container: card / inline-size;
}

@container card (width < 300px) {
  .card { flex-direction: column; }
}

@container card (width > 500px) {
  .card-title { font-size: var(--text-2xl); }
}
```

### Centering
```css
/* Single axis */
.center-x { display: flex; justify-content: center; }
.center-y { display: flex; align-items: center; }

/* Both axes */
.center { display: grid; place-items: center; }
```

## Modern Selectors

### :has() - Parent Selector
```css
/* Style parent when child has focus */
.form-group:has(:focus) {
  outline: 2px solid var(--color-primary);
}

/* Card with image gets different layout */
.card:has(img) {
  grid-template-rows: 200px auto;
}
```

### @scope - Encapsulation
```css
@scope (.card) to (.card-content) {
  /* Styles apply to .card but stop at .card-content */
  img { border-radius: var(--radius-md); }
  a { color: var(--color-primary); }
}
```

### Native Nesting
```css
.nav {
  display: flex;
  gap: var(--space-4);
  
  & a {
    color: var(--color-text);
    
    &:hover { color: var(--color-primary); }
    &[aria-current="page"] { font-weight: bold; }
  }
}
```

## Accessibility

### Reduced Motion
```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

### Focus Visible
```css
:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 2px;
}

:focus:not(:focus-visible) {
  outline: none;
}
```

### Skip Link
```css
.skip-link {
  position: absolute;
  top: -100%;
  left: 0;
  z-index: var(--z-toast);
  
  &:focus {
    top: 0;
    background: var(--color-primary);
    color: white;
    padding: var(--space-2) var(--space-4);
  }
}
```

### Screen Reader Only
```css
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}
```

## Typography

### Fluid Type
```css
h1 {
  font-size: clamp(
    var(--text-2xl),
    5vw + 1rem,
    var(--text-4xl)
  );
}
```

### Prose Container
```css
.prose {
  max-width: 65ch;
  
  & p { margin-block: 1em; }
  & h2 { margin-block: 1.5em 0.5em; }
  & ul, & ol { padding-inline-start: 1.5em; }
}
```

## File Structure

```
css/
├── main.css           # @layer definitions + imports
├── base/
│   ├── tokens.css     # Design tokens
│   ├── reset.css      # Josh Comeau's reset
│   └── typography.css # Font faces, prose
├── components/
│   ├── button.css
│   ├── card.css
│   └── modal.css
├── layout/
│   ├── header.css
│   └── footer.css
└── utilities/
    └── helpers.css    # .sr-only, .hidden
```
