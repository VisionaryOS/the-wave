# Extracted Comments Archive

Good comments from the codebase, preserved for potential strategic reinsertion.

---

## CSS Architecture

### main.css
```css
/* Layer order (lowest to highest specificity):
   1. base      - tokens, typography, animations
   2. layout    - page structure (header, hero, sections, footer)
   3. components - reusable UI pieces
   4. utilities - helper classes, effects (highest specificity) */
```

### header.css
```css
/* Design decision: once the user scrolls past the hero into the topics
   section, we hide the "Start reading" CTA button. At that point they're
   already reading, so the button becomes redundant and just adds clutter.
   Showing only the centered logo keeps things clean and focused on the
   content. It's a small touch but makes the browsing feel more intentional. */
```

```css
/* Two scroll-driven animations:
   1. Pill formation (0-300px) - transparent to white pill
   2. Center shrink (60vh-80vh) - shrinks to logo-only width before topics */
```

```css
/* Clip text when animating width to 0 */
```

### cards.css
```css
/* Allow island to extend below into border area */
```

```css
/* Clip to rounded corners since card has overflow:visible */
```

```css
/* Content lifts up on hover to reveal pill */
```

```css
/* pill slides up on hover - translateY smoother than animating height */
```

### tabs.css
```css
/* tabs - radio button hack, :checked shows the right panel */
```

```css
/* All panels stack in same cell */
grid-area: 1 / 1;
```

```css
/* Scroll offset for anchor links */
scroll-margin-top: 6rem;
```

### hero.css
```css
/* Subtle grain texture overlay for depth */
```

### logo-bar.css
```css
/* Brand-accurate typography variants */
```

### modal.css (if exists)
```css
/* Prevent scroll chaining - traps scroll within modal */
overscroll-behavior: contain;
```

---

## HTML Structure Comments

### index.html
```html
<!-- SEO -->
<!-- Open Graph / Social -->
<!-- Theme -->
<!-- Fonts -->
<!-- Styles -->
```

These meta section labels are useful for navigation.

---

## Useful Pattern Explanations

### Scroll-driven animations
```css
animation: anim-name linear both;
animation-timeline: scroll();
animation-range: 0 300px;
```

### CSS-only tabs
```css
/* Hidden radio inputs control which panel is visible via :checked */
#tab-name:checked ~ .tabs__panels .tabs__panel--name { ... }
```

### CSS-only modal
```css
/* :target pseudo-class shows modal when URL hash matches */
.modal:target { opacity: 1; visibility: visible; }
```

---

*Archive created during audit - February 2026*
