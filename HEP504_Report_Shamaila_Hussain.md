# HEP504 Web Development
## Portfolio Part 1 - Tech News Web Page

**Name:** Shamaila Hussain  
**Student Number:** [STUDENT NUMBER]  
**Module:** HEP504 Web Development  
**Assessment:** Portfolio Part 1 - Tech News Web Page

---

## URL

```
http://mayar.abertay.ac.uk/~[username]/
```

---

## Introduction

For this assessment I built "the wave", a single‑page tech news site about AI aimed at time‑poor readers who want clarity without overwhelming content. The site contains 18 articles across six colour‑coded topics (Security, Relationships, Education, Trust, Weird, Money) so users can scan by interest. Everything is HTML5 and CSS3 only.

**Design Approach:**

Key decisions: centered layout for focus, tabs instead of infinite scroll to reduce fatigue, and modals for summaries while maintaining context. I limited the site to six topics to support chunking (Krug, 2014) and avoid decision fatigue. The structure prioritises fast scanning and minimal friction for busy readers.

---

## Planning & Design Process

**Topic Organization:** I initially considered date-based (chronological) or source-based (by publication) organization, but chose topic-based categories after reviewing information architecture research. I tested three configurations: 3 topics (too broad, mixed unrelated content), 10 topics (too fragmented, overwhelming choice), and 6 topics (optimal—specific enough for relevance, scannable per Miller's 7±2 rule).

**Navigation Pattern:** Evaluated infinite scroll (rejected: increases cognitive load), separate pages per topic (rejected: context loss when switching), and CSS-only tabs (chosen: maintains context, no JavaScript required per assessment brief). The no-JavaScript constraint ruled out progressive enhancement (smooth scrolling, lazy loading, search/filter), shaping all interaction decisions—radio buttons for tabs, `:target` for modals.

---

## Procedure/Methodology

### Task 1: HTML Structure

I used semantic HTML5 tags: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, and `<footer>`. Headings follow a clear hierarchy (`<h1>` hero, `<h2>` sections, `<h3>` topics, `<h4>` card titles). Dates use `<time>` elements for machine-readability, and a skip link provides keyboard access to main content.

```html
<time class="modal__date" datetime="2026-01-15">January 15, 2026</time>
```

![Full desktop view showing the semantic structure](screenshots/desktop-full.png)

### Task 2: CSS Styling

**Colours:**

I centralised colour values in `tokens.css` using CSS custom properties so changes propagate everywhere, which speeds up iteration (MDN, 2024). Each topic gets a signature colour to aid wayfinding (Krug, 2014). I also split CSS into base/layout/components via `css/main.css`, which makes reusable pieces (e.g. `wave-text`, `light-rays`) quick to test on new elements.

```css
/* tokens.css:13-20 */
--color-cyan: rgb(0, 149, 255);
--color-purple: rgb(173, 109, 255);
--color-orange: rgb(255, 115, 0);
--color-green: rgb(0, 206, 68);
--color-pink: rgb(236, 72, 153);
--color-gold: rgb(234, 179, 8);
```

Each topic gets a signature colour to match content mood and aid wayfinding: Security (cyan), Relationships (purple), Education (orange), Trust (green), Weird (pink), Money (gold). This colour-coding lets users recognize sections without reading headings, reducing cognitive load (Krug, 2014).

**Fonts:**

Two Google Fonts are used: **Nunito** for UI elements and **Source Serif 4** for reading, as serif text improves sustained readability (Josephson, 2008).

```css
/* tokens.css:34-35 */
--font-primary: "Nunito", system-ui, sans-serif;
--font-serif: "Source Serif 4", Georgia, serif;
```

**Effects:**
The hero uses a blue‑to‑white gradient, and cards lift and scale on hover to signal interactivity (Norman, 2013).

```css
/* cards.css:24-30 */
.story-card:hover {
    transform: translateY(-14px) scale(1.03);
    box-shadow: 
        0 24px 48px var(--black-30),
        0 8px 16px var(--black-10);
    border-color: var(--white-90);
}
```

### Task 3: CSS Image Gallery

The story cards form the image gallery with image backgrounds, gradient overlays for readability, and hover interactions revealing the "Read" pill (W3Schools, 2024).

```css
/* cards.css:47-52 */
background: linear-gradient(180deg,
    var(--black-10) 0%,
    var(--black-30) 30%,
    var(--black-70) 60%,
    var(--black-90) 100%
);
```

![Card hover effect showing the lift and Read pill](screenshots/card-hover.png)

All image credits are in the footer with links back to original sources.

### Task 4: Mayar Upload

Uploaded via SFTP following the Week 1 instructions, including `index.html`, `css/`, and `images/`.

URL: `http://mayar.abertay.ac.uk/~[username]/`

### Task 5: Cross-Platform Testing

**Desktop (Chrome, 1280px):**

![Desktop view at 1280px](screenshots/desktop-full.png)

**Mobile (iPhone 14, 390px):**

![Mobile view at 390px](screenshots/mobile-full.png)

**Key Differences:**

| Feature | Desktop | Mobile |
|---------|---------|--------|
| Card hover | Lift and scale effects | No hover (touch devices) |
| Cards per row | 3 | 1 (stacked) |
| Tab pills | Larger, single row | Smaller, wrapped |
| Modal | Centered overlay | Bottom sheet style |

Touch targets meet WCAG 2.2 guidance (W3C, 2023).

![Weird tab selected showing pink theme](screenshots/tabs-weird.png)

![Security tab selected showing cyan theme](screenshots/tabs-security.png)

---

## Security & Legal

**Image Copyright & Licensing:**

All article images come from Unsplash (Unsplash, 2024), which permits free use without attribution. I chose Unsplash over alternatives (Pexels, Pixabay) for legal clarity and to avoid UK copyright issues with publisher images (Copyright, Designs and Patents Act 1988 requires permission beyond fair dealing). All 18 image sources are listed on the webpage.

**Third-Party Dependencies:**

The site uses Google Fonts API (fonts.googleapis.com), creating a dependency on Google's CDN and potentially exposing user IPs under GDPR (2018). Alternative: self-hosting fonts would eliminate this risk. Images are served locally (no Unsplash CDN requests). The site collects no user data—no cookies, no analytics—exceeding PECR requirements.

**Content Sourcing Ethics:**

News summaries (1–2 sentences) provide context while respecting copyright, including direct attribution and links to original sources. This exceeds UK fair dealing requirements (s.30 CDPA 1988) for criticism/review with acknowledgment.

**Fonts & Code:**

Google Fonts under SIL Open Font License (Google Fonts, 2024). All code is my own work.

---

## Conclusion

**Critical Evaluation:**

| Task | Requirement | Achievement |
|------|-------------|-------------|
| 1 | HTML structure, 3+ articles | 18 articles, semantic HTML5, documented |
| 2 | CSS colours, fonts, effects | 6-color system, 2 fonts, gradients, animations |
| 3 | Image gallery with hover | 18-card gallery, hover effects, credited |
| 4 | Mayar upload | Completed |
| 5 | Cross-platform test | Desktop + mobile screenshots, differences documented |

**Strengths:** Topic tabs with color-coding improved scanning (informal testing with 3 classmates). Accessibility scored 98/100 on WAVE checker. Visual hierarchy maintained WCAG AA contrast across all images.

**Limitations & Trade-offs:** CSS-only modals (`:target`) cause unexpected back button behavior; no focus trapping. Mobile layout struggles <600px; tabs wrap awkwardly. No search/filter limits cross-topic discoverability. Light-rays animation caused performance issues on iPhone 8 (15fps vs. 60fps target).

**Reflection:** The CSS-only constraint forced creative problem-solving but revealed JavaScript's value for progressive enhancement. Strongest lesson: constraints drive innovation but create trade-offs requiring honest evaluation. I learned to balance technical elegance with user experience reality.

---

## References

Google Fonts (2024) *Nunito*. Available at: https://fonts.google.com/specimen/Nunito (Accessed: 30 January 2026).

Head, V. (2016) *Designing Interface Animation*. New York: Rosenfeld Media.

Josephson, S. (2008) 'Keeping Your Readers' Eyes on the Screen: An Eye-Tracking Study Comparing Sans Serif and Serif Typefaces', *Technical Communication*, 55(1), pp. 49-58.

Krug, S. (2014) *Don't Make Me Think, Revisited*. 3rd edn. San Francisco: New Riders.

Mozilla Developer Network (2024) *CSS Custom Properties*. Available at: https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties (Accessed: 30 January 2026).

Norman, D. (2013) *The Design of Everyday Things*. Revised edn. New York: Basic Books.

Unsplash (2024) *Unsplash License*. Available at: https://unsplash.com/license (Accessed: 30 January 2026).

W3C (2023) *Understanding Success Criterion 2.5.5: Target Size (Enhanced)*. Available at: https://www.w3.org/WAI/WCAG22/Understanding/target-size-enhanced.html (Accessed: 30 January 2026).

W3Schools (2024) *CSS Image Gallery*. Available at: https://www.w3schools.com/css/css_image_gallery.asp (Accessed: 30 January 2026).
