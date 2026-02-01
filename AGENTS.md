# The Wave - Agent Instructions

## Hard Constraints
- **HTML + CSS ONLY** - No JavaScript, no frameworks, no build tools
- **Single page** - `index.html` + `css/` folder
- **Decision logging** - After EVERY change, append to `decisions.md`

## Quality Bar

### HTML5
- Semantic elements: header, nav, main, section, article, footer
- One `<h1>` per page, no skipped heading levels
- Every input has `<label>`, every button is `<button>`
- Skip link first, aria-labels on icons

### CSS
- Cascade layers: `@layer reset, base, components, utilities`
- OKLCH colors with `light-dark()` for theming
- Container queries > media queries for components
- Native nesting (max 3 levels), BEM naming
- Design tokens in `:root` custom properties

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
├── index.html
├── css/
│   ├── main.css          # @layer imports
│   ├── base/             # tokens, reset, typography
│   ├── components/       # buttons, cards, modal
│   ├── layout/           # header, sections, footer
│   └── utilities/        # accessibility, print
├── decisions.md
└── AGENTS.md
```
