# Report Plan

**Word count:** 1000 words ±10% (900-1100), excluding references

---

## 1. Title Page
- Name: Shamaila Hussain
- Student Number: [NUMBER]
- Assessment: Portfolio Part 1 - Tech News Web Page

---

## 2. URL
```
http://mayar.abertay.ac.uk/~[username]/
```

---

## 3. Introduction (~100 words)

**What to cover:**
- "the wave" - an AI news aggregator concept
- Theme: making AI news approachable (bright, not dystopian)
- 18 articles across 6 colour-coded topics
- Built with pure HTML5/CSS3, no JavaScript
- Exceeds brief requirements (3+ articles, image gallery, styling)

---

## 4. Procedure/Methodology (~600 words)

### Task 1: HTML Structure

**Tags used:**
- Semantic: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`
- Content: `<h1>`-`<h4>` (proper hierarchy), `<p>`, `<time datetime="">`
- Interactive: `<a>`, `<input type="radio">`, `<label>`, `<details>`, `<summary>`
- Media: `<img>` with `alt` attributes

**Key decisions:**
- Single `<h1>` for the main headline
- `<article>` for each news story (semantically correct)
- `<time datetime="">` for machine-readable dates
- Comments document each section (see code)

**Code snippet:** Show the semantic structure of a modal

### Task 2: CSS Styling

**Colours:**
- Topic colour-coding (cyan=Security, purple=Relationships, etc.)
- Vibrant palette on white background for approachable feel
- CSS custom properties for consistency (`--color-cyan`, etc.)

**Fonts:**
- Nunito (sans-serif) for UI - friendly, modern
- Source Serif 4 for article text - easier reading
- Google Fonts CDN

**Effects:**
- Gradients: hero section blue-to-white
- Shadows: layered shadows on cards for depth
- Transitions: hover lift effects on cards and tabs
- Transforms: `translateY` for smooth animations

**Code snippet:** Show the hover effect on story cards

### Task 3: CSS Image Gallery

**Implementation:**
- Story cards function as the gallery
- Images with CSS `background-image`
- Hover effects: 14px lift, scale, shadow glow
- Overlay gradient for text readability
- "Read" pill reveals on hover

**How it meets W3Schools requirements:**
- Responsive flex layout ✓
- Hover effects ✓
- Descriptions (titles over images) ✓
- Click interaction (opens modal) ✓

**Image sources:**
- Editorial images from original articles (fair use for educational commentary)
- Credits in footer, grouped by publication

**Code snippet:** Show the card hover CSS

### Task 4: Mayar Upload

- Uploaded via SFTP to mayar server
- Tested URL works
- [Include screenshot of live site]

### Task 5: Cross-Platform Testing

**Desktop (Chrome):**
- [Screenshot]
- Full layout renders correctly
- Hover effects work
- Scroll animations smooth

**Mobile (iPhone/Android):**
- [Screenshot]
- Layout adapts (cards stack)
- Touch targets adequate (44px minimum)
- Some features different:
  - Hover effects don't apply (no hover on touch)
  - Scroll animations still work
  - Modals slide up from bottom (mobile pattern)

**Differences noted:**
- Cards don't lift on mobile (expected - no hover)
- FAB centres on mobile vs right-aligned on desktop
- Tab pills wrap to multiple rows

---

## 5. Security & Legal (~150 words)

**Copyright considerations:**

- **Article images:** Used under fair use doctrine for educational commentary
  - Images are from the original news articles being discussed
  - Not used commercially
  - Credited in footer with links to sources
  - Transformative use (curated news aggregation context)

- **Fonts:** Google Fonts - open source, free for commercial/personal use

- **Code:** Original work, no copied code

**References to cite:**
- UK Copyright, Designs and Patents Act 1988
- Fair dealing for criticism/review (Section 30)
- W3Schools for CSS techniques

---

## 6. Conclusion (~150 words)

**How brief was met:**

| Task | Requirement | Achievement |
|------|-------------|-------------|
| 1 | HTML structure, 3+ articles | 18 articles, semantic HTML5, comments |
| 2 | CSS colours, fonts, effects | Design tokens, 3 fonts, gradients, shadows, transitions |
| 3 | Image gallery with hover | Card gallery exceeds W3Schools example |
| 4 | Mayar upload | Working URL provided |
| 5 | Cross-platform test | Desktop/mobile screenshots, differences documented |

**Critical evaluation:**
- Exceeded minimum requirements significantly
- CSS-only interactions (modals, tabs) demonstrate advanced techniques
- Could improve: responsive typography, reduced file size
- Learning: importance of design tokens, BEM naming

---

## 7. References (Harvard)

```
Mozilla Developer Network (2024) CSS @layer. Available at: https://developer.mozilla.org/en-US/docs/Web/CSS/@layer (Accessed: [date])

W3Schools (2024) CSS Image Gallery. Available at: https://www.w3schools.com/css/css_image_gallery.asp (Accessed: [date])

UK Government (1988) Copyright, Designs and Patents Act 1988. Available at: https://www.legislation.gov.uk/ukpga/1988/48/contents (Accessed: [date])

Google Fonts (2024) Nunito. Available at: https://fonts.google.com/specimen/Nunito (Accessed: [date])
```

---

## Screenshots Needed

1. Desktop full page
2. Mobile full page
3. Card hover effect
4. Modal open
5. Tabs switching
6. Code snippet: semantic HTML structure
7. Code snippet: card hover CSS
8. Code snippet: colour tokens

---

## Notes

- Keep language simple, direct
- Avoid AI-smell phrases ("comprehensive", "robust", "leverage")
- Show understanding through specific examples, not generic claims
- Reference W3Schools since they mention it in the brief
