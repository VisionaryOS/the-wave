# Design Decisions

> Reasoning behind significant architecture and design choices.

---

## Architecture

### Modular CSS with @import
Split CSS into 16 focused modules using native `@import` statements.

- Pure HTML5/CSS3 constraint (no Sass, PostCSS, build tools)
- Single responsibility per file makes code easier to navigate
- Trade-off: Multiple HTTP requests vs maintainability — at this scale, maintainability wins

### Cascade Layers
```css
@layer base, layout, components, utilities;
```
Controls specificity without `!important`. Utilities always win when needed, no specificity wars.

### BEM Naming
`.block__element--modifier` pattern throughout. Self-documenting class names with flat specificity.

---

## Design Tokens

All design values live in CSS custom properties (`tokens.css`).

**Why tokens:**
- Single source of truth — change `--color-cyan` once, updates everywhere
- Prevents inconsistency (`#0095ff` vs `#0094ff` accidents)
- The token file IS the design specification

**Intentional gaps in scales:**
- Spacing skips values (no `--space-7`) to force deliberate choices
- Alpha scale uses 20% increments (10/30/50/70/90) not every 5%

---

## Visual Design Philosophy

### Bright & Airy
White backgrounds, generous whitespace, vibrant accent colours.

AI news often feels intimidating or dystopian. A bright, optimistic design makes the content feel approachable. White space lets content breathe rather than overwhelming the reader.

### Topic Colour Coding
Each topic has a signature colour for instant categorisation:
- Security → Cyan
- Relationships → Purple  
- Education → Orange
- Trust → Green
- Weird → Pink
- Money → Gold

This creates visual variety while maintaining consistency within categories.

### Rounded Corners
Generous `border-radius` on all components reinforces the "wave" brand (fluid, organic) and creates a friendly, modern feel.

---

## Typography

### Three-Font System
- **Nunito** (UI): Friendly rounded sans-serif — approachable without being childish
- **Source Serif 4** (Reading): Comfortable serif for article text — easier on eyes for longer content
- **JetBrains Mono** (Dates): Monospace for timestamps — technical precision

### Heavy Headlines
`font-weight: 900` for major headlines creates strong visual anchors and clear hierarchy without needing larger sizes.

---

## Key UX Patterns

### CSS-Only Interactions
All interactive patterns work without JavaScript:

| Pattern | Technique | Benefit |
|---------|-----------|---------|
| Modals | `:target` pseudo-class | Bookmarkable URLs, back button closes |
| Tabs | Radio `:checked` + siblings | State persists, no JS needed |
| Scroll effects | `animation-timeline: scroll()` | 60fps GPU-composited |
| Collapsibles | `<details>`/`<summary>` | Native browser behaviour |

### Progressive Enhancement
`@supports` queries provide fallbacks for browsers without scroll-driven animations. The site works everywhere, enhanced where supported.

### Mobile Patterns
- Modals become bottom sheets (thumb-friendly, matches native apps)
- FAB centres on mobile (neutral thumb position)
- 44px minimum touch targets (Apple HIG guideline)

---

## Accessibility

- **Skip link:** First focusable element for keyboard users
- **Semantic HTML:** Proper landmarks (`<header>`, `<nav>`, `<main>`, `<article>`, `<footer>`)
- **Heading hierarchy:** Single `<h1>`, no skipped levels
- **Focus visible:** `outline` on `:focus-visible` only (keyboard users see it, mouse users don't)
- **ARIA labels:** All interactive elements have accessible names
- **`aria-hidden`:** Decorative elements hidden from screen readers

---

## Performance

- **No JavaScript:** Entire site functions without JS
- **Preconnect:** Early connection to Google Fonts CDN
- **Compositor animations:** Only `transform` and `opacity` animate (GPU-accelerated, 60fps)
- **No image dependencies for layout:** Gradients and CSS effects load instantly

---

## Task 3: Image Gallery

The story cards satisfy all W3Schools CSS Image Gallery requirements:
- Images in responsive flex layout
- Hover effects (scale, shadow, lift, border glow)
- Descriptions (article titles over images)
- Click interaction (opens modal)
- Image credits in footer

The cards are a more sophisticated implementation than the basic tutorial example.

---

*HEP504 Web Development · Abertay University · February 2026*
