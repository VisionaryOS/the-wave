# The Wave - Agent Instructions

## Assessment Context
**Module:** HEP504 Web Development (Abertay University)  
**Assessment:** Portfolio Part 1 - Tech News Web Page  
**Weighting:** 25% of module grade  
**Due:** Monday Week 4, 12:00 noon

## Hard Constraints
- **HTML + CSS ONLY** - No JavaScript, no frameworks, no build tools
- **Single page** - `index.html` + `css/` folder
- **Decision logging** - After EVERY change, append to `decisions.md`

## Assessment Requirements Checklist

### Task 1: Webpage Structure (HTML)
- [ ] Tech news theme with at least **3 news articles**
- [ ] Semantic HTML5 tags: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`
- [ ] Proper heading hierarchy (one `<h1>`, no skipped levels)
- [ ] **Source references** for any quoted/sourced news content
- [ ] **HTML comments** documenting code sections and decisions

### Task 2: Style and Colour (CSS)
- [ ] Engaging colours demonstrating CSS colour properties
- [ ] Font styling (different fonts, weights, sizes)
- [ ] Style effects (gradients, shadows, transitions, transforms)
- [ ] Well-organised, commented CSS

### Task 3: CSS Image Gallery
- [ ] Image gallery similar to [W3Schools CSS Image Gallery](https://www.w3schools.com/css/css_image_gallery.asp)
- [ ] Hover effects on gallery images
- [ ] **Copyright-free images** (sourced from Unsplash, Pexels, or self-created)
- [ ] **Image credits/references** visible on page

### Task 5: Cross-Platform Testing
- [ ] Test appearance on desktop and mobile
- [ ] Document differences in report (screenshots)
- [ ] Note: Site doesn't need to look perfect on mobile at this stage

## Quality Bar (Going Beyond Minimum)

### HTML5
- Semantic elements: header, nav, main, section, article, footer
- One `<h1>` per page, no skipped heading levels
- Every input has `<label>`, every button is `<button>`
- Skip link first, aria-labels on icons
- Comprehensive HTML comments explaining structure

### CSS
- Cascade layers: `@layer reset, base, components, utilities`
- OKLCH colors with `light-dark()` for theming potential
- Container queries > media queries for components
- Native nesting (max 3 levels), BEM naming
- Design tokens in `:root` custom properties
- Scroll-driven animations (progressive enhancement)

### Why Go Beyond?
> "Current web standards encourage minimalist websites; however, this assessment encourages you to create something unique, interesting, and colourful."

Our advanced architecture isn't complexity for complexity's sake - it's:
- **Maintainable**: Tokens mean one source of truth
- **Scalable**: BEM + layers prevent specificity wars
- **Modern**: Using 2024/2025 CSS features shows engagement with the field
- **Documented**: Every decision is logged and explainable

## Decision Log Format
After every file change, append to `decisions.md`:
```
[YYYY-MM-DD] [TYPE] Brief decision statement
- Goal: What you were trying to achieve
- Tried: What approaches you attempted
- Outcome: What worked and why
```
Types: `BUG` | `UX` | `CODE` | `STYLE`

## File Structure
```
the-wave/
├── index.html              # Single page with all content
├── css/
│   ├── main.css            # @import orchestrator
│   ├── base/
│   │   ├── tokens.css      # Design tokens
│   │   ├── reset.css       # Browser normalisation
│   │   └── typography.css  # Type scale, prose
│   ├── components/
│   │   ├── buttons.css
│   │   ├── cards.css
│   │   ├── gallery.css     # NEW: Image gallery styles
│   │   ├── inputs.css
│   │   ├── modal.css
│   │   └── tags.css
│   ├── layout/
│   │   ├── header.css
│   │   ├── sections.css
│   │   └── footer.css
│   ├── pages/
│   │   ├── hero.css
│   │   └── subscribe.css
│   └── utilities/
│       ├── accessibility.css
│       └── print.css
├── images/                  # NEW: Gallery images
│   └── gallery/
├── decisions.md             # Design decision log
└── AGENTS.md                # This file
```

## Report Sections (Reference)
The accompanying report should include:
1. **Title Page** - Name, student number, assessment title
2. **URL** - Link to site hosted on mayar server
3. **Introduction** - Brief overview of work undertaken
4. **Procedure/Methodology** - Detailed explanation with code snippets, screenshots
5. **Security & Legal** - Copyright considerations, image licensing
6. **Conclusion** - Critical evaluation against brief
7. **References** - Harvard style

## Image Sources (For Gallery)
Use copyright-free images from:
- [Unsplash](https://unsplash.com) - Free, no attribution required (but appreciated)
- [Pexels](https://pexels.com) - Free, no attribution required
- Self-created images/screenshots

Always credit sources on the webpage itself.
