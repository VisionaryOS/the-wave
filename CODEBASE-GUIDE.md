# THE WAVE - Complete Codebase Guide

**Last Updated:** Feb 2, 2026
**Project:** HEP504 Web Development (Abertay University)
**Assessment:** Portfolio Part 1 - Tech News Web Page (25% of module grade)
**Due:** Monday Week 4, 12:00 noon

---

## QUICK CONTEXT

You've built **"the wave"** - a clean, modern tech news aggregator website that curates AI/tech stories into digestible daily feeds. It's a **static HTML + CSS site** (no JavaScript, no frameworks) that displays 18 tech news articles organized by topic.

**Theme:** AI and technology news focusing on ethics, security, culture, and economics
**Author/Founder:** Shamaila Hussain
**Status:** ~95% complete - website fully functional, report mostly done, pending manual verification tasks

---

## DIRECTORY STRUCTURE

```
the-wave/
├── index.html                          # Single-page site (778 lines)
├── css/
│   ├── main.css                        # Master file with @imports
│   ├── base/
│   │   ├── tokens.css                  # Color vars, spacing, fonts (design tokens)
│   │   ├── animations.css              # Keyframes and transitions
│   │   └── typography.css              # Font rules and text styles
│   ├── components/
│   │   ├── buttons.css                 # .btn classes (primary, vote, FAB)
│   │   ├── badge.css                   # .badge (status indicator)
│   │   ├── tags.css                    # .tag (source labels like "WIRED", "BBC")
│   │   ├── cards.css                   # .story-card (image gallery items)
│   │   ├── modal.css                   # Article detail panels
│   │   ├── tabs.css                    # CSS-only tabs for "Past Waves"
│   │   ├── logo-bar.css                # Source attribution logos
│   │   ├── light-rays.css              # Decorative ray animations
│   │   ├── topic-box.css               # Topic section styling
│   │   ├── founder-note.css            # Founder story section
│   │   └── interactions.css            # Interactive elements (votes, etc)
│   └── layout/
│       ├── header.css                  # Sticky nav bar
│       ├── hero.css                    # Featured stories section
│       ├── topics.css                  # Topics wrapper
│       └── footer.css                  # Footer, credits, FAB button
├── images/
│   ├── articles/                       # 18 article images (01-dark-bedroom.jpg through 18-chip.jpg)
│   └── founder.jpg                     # Shamaila's photo
├── screenshots/                        # 5 mobile/desktop test screenshots
├── TASKS.md                            # TODO checklist for submission
├── AGENTS.md                           # Assessment requirements
├── HEP504_Report_Shamaila_Hussain.md   # Report document
└── HEP504_Report_Shamaila_Hussain.pdf  # Report PDF (generated)
```

---

## PROJECT ARCHITECTURE

### Design Philosophy: BEM + CSS Layers + No Build Tools

```
CSS Architecture (in order of specificity):
├── @layer base
│   ├── Design tokens (colors, spacing, fonts)
│   ├── Animations (keyframes, transitions)
│   └── Typography (font rules)
├── @layer layout
│   ├── Page structure (header, hero, topics, footer)
│   └── Viewport-level positioning
├── @layer components
│   ├── Reusable UI blocks (buttons, cards, modals, tabs)
│   └── Internal element styling
└── @layer utilities (if needed)
```

**Naming Convention:** BEM (Block\_\_Element--Modifier)
- `.story-card` = block
- `.story-card__title` = element
- `.story-card--hero` = modifier
- This keeps specificity flat and prevents cascade hell

---

## PAGE STRUCTURE (HTML WALK-THROUGH)

### 1. HEADER & NAVIGATION
```html
<header class="site-header">
  <nav class="nav">
    <a href="#top" class="nav__logo">
      <span class="wave-text">the wave</span> <!-- animated letter spans -->
    </a>
  </nav>
</header>
```
- **Sticky:** Header shrinks on scroll via CSS animation (not JS)
- **Skip link:** Accessibility feature linking to `#main-content`
- **Logo:** Animated "wave-text" - each letter in its own `<span>` for potential animations

---

### 2. HERO SECTION (Featured Stories)
```html
<section class="hero">
  <div class="light-rays"> <!-- 6 animated ray backgrounds -->
  <div class="hero__content">
    <p class="badge"> <!-- "Live" indicator -->
    <h1 class="hero__title">Catch the wave.
    <p class="hero__subtitle">Three tech stories a day...
  <div class="hero__cards">
    <!-- 3 story cards linking to articles #15, #1, #18 -->
  <div class="hero__footer">
    <div class="logo-bar"> <!-- Logos of source publications -->
```
- **Featured:** 3 prominent story cards with background images
- **Light rays:** Decorative animated background elements
- **Logo bar:** Shows which publications are being curated (BBC, NYT, Verge, Ars, 404, WIRED)

---

### 3. TOPICS SECTION (CSS-Only Tabs)
```html
<section class="section section--topics">
  <fieldset class="tabs">
    <!-- 6 radio inputs controlling which panel shows -->
    <input type="radio" name="topic-tab" id="tab-weird" checked>
    <input type="radio" name="topic-tab" id="tab-money">
    <!-- etc for: relationships, security, education, trust -->

    <div class="tabs__nav">
      <!-- 6 labels styled as tab buttons -->
    <div class="tabs__panels">
      <!-- 6 hidden panels, one shown per radio selection -->
```

**Topics & Articles Per Topic:**
1. **WEIRD** (pink) - Strange AI stories
   - Article #16: AI-Generated Anti-ICE Videos
   - Article #17: Is China Winning the AI Race?
   - Article #18: Moltbot Taking Over Silicon Valley

2. **MONEY** (gold) - Financial/investment stories
   - Article #19: OpenAI $100B Funding
   - Article #20: Nvidia vs Amazon/Google Chips
   - Article #21: Data Centers & Gas Boom

3. **RELATIONSHIPS** (purple) - AI as social partners
   - Article #4: Social Network for AI Agents
   - Article #5: Replaced Friends With AI Gaming
   - Article #6: Burned Out With AI Coding Agents

4. **SECURITY** (cyan) - Safety & privacy issues
   - Article #1: ChatGPT Suicide Lullaby
   - Article #2: AI Chat App Data Breach
   - Article #3: Cyber Chief Leaked Secrets

5. **EDUCATION** (orange) - Learning & academic impact
   - Article #13: AI Tool Going Viral
   - Article #14: UK Gen Z Using AI for Loneliness
   - Article #15: AI Toy Exposed Kids' Chats

6. **TRUST** (green) - AI-generated content/misinformation
   - Article #10: cURL Ditches Bug Bounties (AI Slop)
   - Article #11: YouTube AI Slop Channels Disappearing
   - Article #12: AI Slop Flooding Research

**How It Works (CSS-Only):**
- Clicking a tab label toggles its radio button (`:checked`)
- CSS selector `.tabs__input:checked ~ .tabs__panels .tabs__panel` reveals the matching panel
- No JavaScript needed!

---

### 4. ARTICLE MODALS (Full Story Details)
```html
<article id="article-1" class="modal">
  <a href="#!" class="modal__backdrop"></a>
  <div class="modal__container">
    <header class="modal__header">
      <h2>ChatGPT Wrote a Suicide Lullaby...</h2>
      <span class="tag">Security</span>
      <time datetime="2026-01-15">January 15, 2026</time>
    <div class="modal__content">
      <p class="modal__lead">Article preview text...</p>
    <a href="https://..." class="btn btn--primary">Read full article</a>
    <a href="#!" class="modal__close">&times;</a>
```

**Modal Interaction (CSS `:target`):**
- Clicking a story card links to `#article-1` (etc.)
- CSS shows the modal when matched: `.modal:target { display: block; }`
- Clicking backdrop or X button links to `#!` (kills the target), hiding modal
- No JavaScript whatsoever!

**18 Articles Total:**
- Articles 1-15: Main content articles
- Articles 16-21: Topic panel articles (some are duplicated in hero/cards)
- Each has: title, source publication, publication date, summary, link to original

---

### 5. FOOTER
```html
<footer class="footer">
  <!-- Hidden founder story (revealed by clicking "psst...") -->
  <details class="secret-reveal">
    <article class="founder-note">
      <h2>"I just wanted clarity..."</h2>
      <img src="images/founder.jpg" alt="Shamaila Hussain">
      <span class="founder-note__name">Shamaila Hussain</span>
      <span class="founder-note__role">Founder, Mother, Student</span>
      <!-- Vote buttons: "I'd subscribe" / "Not for me" (CSS-only) -->

  <!-- Simple footer -->
  <div class="footer__simple">
    <a href="#top" class="footer__logo">the wave</a>
    <p class="footer__copy">made with ❤️ by Shamaila Hussain</p>

    <!-- Image credits (expandable details) -->
    <details class="footer__credits">
      <summary>Image credits</summary>
      <div class="footer__credits-groups">
        <!-- All 18 Unsplash photo links -->
```

**Features:**
- **Founder story:** Reveals on click via `<details>` element (not JS)
- **Vote buttons:** Radio inputs styled as buttons - click toggles state, shows "Thanks" message
- **Image credits:** Expandable section with links to all 18 Unsplash photos
- **FAB button:** Floating action button (sticky) at bottom-right, scrolls to top

---

## CSS LAYER BREAKDOWN

### `css/base/tokens.css` - Design System
Colors, spacing units, font families, breakpoints defined as CSS variables:
```css
--color-primary: #4772FF (blue - brand color)
--color-primary-dark: #2C5AFF
--color-secondary: various topic colors (pink, gold, purple, cyan, orange, green)
--color-text: #1a1a1a
--space-*: 4px, 8px, 12px, 16px... (8px grid)
--font-ui: Nunito (sans-serif, for interface)
--font-reading: Source Serif 4 (serif, for article text)
```

### `css/base/animations.css` - Motion Design
```css
@keyframes slide-in-top /* hero content entrance */
@keyframes float /* light rays gentle bobbing */
@keyframes pulse-dot /* badge status indicator */
@keyframes shrink-header /* header on scroll */
```

### `css/base/typography.css` - Text Styling
```css
body, h1, h2, h3, p /* base font rules */
.hero__title /* Large display text, animated letters */
.story-card__title /* Card headlines */
.modal__lead /* Article previews */
```

### Layout Files - Page Structure

**`layout/header.css`:**
- `.site-header` - sticky, shrinks on scroll
- `.nav` - flexbox layout
- `.wave-text` - animated letter spans

**`layout/hero.css`:**
- `.hero` - full viewport height featured section
- `.hero__content` - centered text block
- `.hero__cards` - 3-column grid of featured stories
- `.hero__footer` - logo bar at bottom

**`layout/topics.css`:**
- `.section.section--topics` - wrapper for tabs section

**`layout/footer.css`:**
- `.footer` - main footer container
- `.footer__simple` - basic footer info
- `.fab` - floating action button

### Component Files - UI Elements

**`components/cards.css`:**
- `.story-card` - Article preview card with hover effects
- `.story-card--hero` - Large featured variant
- Contains: background image, title, source tag, read time, "Read" CTA button
- Hover: Image scales, shadows enhance, overlay effects

**`components/modal.css`:**
- `.modal` - Hidden by default, shown via `:target`
- `.modal__backdrop` - Clickable area to close
- `.modal__container` - Card styling
- `.modal__header`, `.modal__content`, `.modal__close`

**`components/tabs.css`:**
- `.tabs` - Fieldset containing radio inputs
- `.tabs__nav` - Tab button bar
- `.tabs__panel` - Each topic panel
- `.tabs__panel--weird`, `.tabs__panel--money` etc (color variants)
- CSS media queries for responsive adjustments

**`components/buttons.css`:**
- `.btn` - Base button styling
- `.btn--primary` - Blue CTA buttons
- `.btn--vote` - Subscribe/Not interested toggles
- `.btn--vote.btn--yes` (green), `.btn--vote.btn--no` (red)
- All use `:active`, `:hover` states (CSS-only)

**`components/tags.css`:**
- `.tag` - Source publication labels
- `.tag--glass` - Frosted glass effect variant
- Colors: BBC (red), NYT (navy), Verge (blue), Ars (orange), 404 (purple), WIRED (teal)

**`components/badge.css`:**
- `.badge` - "Live" indicator on hero
- `.badge__dot` - Animated red pulsing dot

**`components/logo-bar.css`:**
- `.logo-bar` - Publication sources display
- `.logo-bar__item` - Individual logo styling
- Each publication has a `.logo-bar__item--[abbrev]` class

**`components/light-rays.css`:**
- `.light-rays` - Container with 6 ray `<span>`s
- Each ray rotates and bobs via animations

**`components/topic-box.css`:**
- `.topic-box` - Topic panel header styling
- `.topic-box--pink`, `.topic-box--gold` etc (6 color variants)
- Contains: title, description, light rays, 3-card grid

**`components/founder-note.css`:**
- `.founder-note` - Expanded founder story
- `.founder-note__avatar` - Circular image
- `.founder-note__content` - Text and photo layout

**`components/interactions.css`:**
- `.secret-reveal` - Hidden founder story container
- `.secret-reveal__trigger` - "psst..." button
- `.vote` - Radio button voting group
- `.vote__thanks` - Hidden message revealed on click

---

## KEY TECHNIQUES (HTML + CSS ONLY)

### 1. CSS-Only Tabs
```css
/* Radio input controls visibility */
.tabs__input { display: none; }
.tabs__input:checked ~ .tabs__panels .tabs__panel { display: none; }
.tabs__input:nth-child(1):checked ~ .tabs__panels #panel-weird { display: block; }
.tabs__input:nth-child(2):checked ~ .tabs__panels #panel-money { display: block; }
/* etc for all 6 topics */
```

### 2. CSS-Only Modals
```css
/* Article detail appears via :target selector */
.modal { display: none; position: fixed; }
.modal:target { display: flex; }
```

### 3. Header Shrink on Scroll
```css
/* CSS animation triggered via class change (but NO JS!) */
@keyframes shrink-header {
  from { height: 80px; }
  to { height: 50px; }
}
/* In real site: Would need observer, but design supports no-JS approach */
```

### 4. BEM Naming Prevents Conflicts
```css
.hero__cards { grid layout }
.hero__cards > .story-card { flex items }
.story-card__title { h2 inside card }
.story-card__bg { background image holder }
.story-card--hero { bigger variant }
```

### 5. Design Tokens Ensure Consistency
```css
/* All colors referenced from base/tokens.css */
--color-primary: used for buttons, links, hero
--color-secondary-weird: pink theme
--color-secondary-money: gold theme
/* Change one token, entire theme updates */
```

---

## IMAGE ORGANIZATION

**Location:** `images/articles/` (18 files)

| # | Filename | Current Unsplash ID | Status | Used In |
|---|----------|-------------------|--------|---------|
| 1 | 01-dark-bedroom.jpg | `_WwHrHHoaE4` | ✅ Verified | Article #1 (Hero), Security tab |
| 2 | 02-phone-dark.jpg | `9e9PD9blAto` | ✅ Verified | Article #2 (Security tab) |
| 3 | 03-government.jpg | `qoU5SsqIHJY` | ✅ Verified | Article #3 (Security tab) |
| 4 | 04-network.jpg | `JKUTrJ4vK00` | ⚠️ **UNVERIFIED** | Article #4 (Relationships tab) |
| 5 | 05-gaming.jpg | `m0l5J8Lqnzo` | ⚠️ **UNVERIFIED** | Article #5 (Relationships tab) |
| 6 | 06-coding-tired.jpg | `gUIJ0YszPig` | ⚠️ **UNVERIFIED** | Article #6 (Relationships tab) |
| 7 | 07-terminal.jpg | `4Mw7nkQDByk` | ⚠️ **UNVERIFIED** | Article #10 (Trust tab) |
| 8 | 08-screens.jpg | `hGV2TfOh0ns` | ⚠️ **UNVERIFIED** | Article #11 (Trust tab) |
| 9 | 09-papers.jpg | `lwGfBjfKW2U` | ✅ Verified | Article #12 (Trust tab) |
| 10 | 10-code-editor.jpg | `OqtafYT5kTw` | ⚠️ **UNVERIFIED** | Article #13 (Education tab) |
| 11 | 11-lonely-phone.jpg | `iZVRrfL_oDQ` | ✅ Verified | Article #14 (Education tab) |
| 12 | 12-dinosaur-toy.jpg | `alNlyjzup80` | ✅ Verified | Article #15 (Hero), Education tab |
| 13 | 13-protest.jpg | `OfgYGYBNcB4` | ✅ Verified | Article #16 (Weird tab) |
| 14 | 14-china.jpg | `uKyzXEc2k_s` | ✅ Verified | Article #17 (Weird tab) |
| 15 | 15-lobster.jpg | `BmW-9U2VnqU` | ✅ Verified | Article #18 (Hero), Weird tab |
| 16 | 16-money.jpg | `oW6LlU_VZkc` | ✅ Verified | Article #19 (Money tab) |
| 17 | 17-datacenter.jpg | `M5tzZtFCOfs` | ✅ Verified | Article #20 (Money tab) |
| 18 | 18-chip.jpg | `FO7JIlwjOtU` | ✅ Verified | Article #21 (Money tab) |

**⚠️ CRITICAL:** 6 images need verification before submission!

---

## REMAINING TASKS (FROM TASKS.MD)

### ✅ COMPLETED
- HTML structure with 18+ articles (actually 21 unique articles, some repeated)
- CSS styling (colors, fonts, gradients, shadows, transitions)
- Image gallery with hover effects
- Cross-platform testing screenshots
- Image credits in footer
- Source references for all articles
- Report document written
- ~1075 words in report (within 900-1100 limit)

### ⚠️ TODO - MANUAL TASKS

#### 1. **Verify 6 Unsplash URLs (HIGH PRIORITY)**
Use TinEye.com to reverse search each image file and verify the photo IDs are correct:
- `04-network.jpg` - currently: `JKUTrJ4vK00`
- `05-gaming.jpg` - currently: `m0l5J8Lqnzo`
- `06-coding-tired.jpg` - currently: `gUIJ0YszPig`
- `07-terminal.jpg` - currently: `4Mw7nkQDByk`
- `08-screens.jpg` - currently: `hGV2TfOh0ns`
- `10-code-editor.jpg` - currently: `OqtafYT5kTw`

**How:**
1. Go to https://tineye.com/
2. Upload each image from `images/articles/`
3. Find the unsplash.com result
4. Extract photo ID (last part of URL)
5. Update the link in footer (lines 462-468 in `index.html`)

#### 2. **Add Student Number**
Edit `HEP504_Report_Shamaila_Hussain.md` line 5:
Replace `[STUDENT NUMBER]` with your actual number

#### 3. **Upload to Mayar Server**
- Connect via SFTP to `mayar.abertay.ac.uk`
- Upload: `index.html`, `css/` folder, `images/` folder
- Test at `http://mayar.abertay.ac.uk/~[username]/`
- Verify all images load and CSS works

#### 4. **Update Report with Mayar URL**
Replace `[username]` in report with your actual Mayar username

#### 5. **Convert Report to PDF**
- Use VS Code "Markdown PDF" extension, OR
- Use Pandoc: `pandoc HEP504_Report_Shamaila_Hussain.md -o HEP504_Report_Shamaila_Hussain.pdf`
- Or paste into Google Docs and export

#### 6. **Create Submission Files**
**File naming (CRITICAL):**
- Report PDF: `Report_ShamailaHussain_[STUDENTNUMBER]_Practical1.pdf`
- Code ZIP: `ShamailaHussain_[STUDENTNUMBER]_Practical1.zip`

**ZIP contents:**
```
ShamailaHussain_XXXXXXX_Practical1.zip
├── index.html
├── css/
│   ├── main.css
│   ├── base/
│   ├── components/
│   └── layout/
├── images/
│   ├── articles/
│   └── founder.jpg
└── screenshots/
```

#### 7. **Submit on Canvas**
Upload TWO separate files:
1. The report PDF
2. The ZIP file

Check: "This assignment submission is my own, original work"

---

## QUICK REFERENCE: KEY FILES

| File | Purpose | Key Classes/IDs |
|------|---------|-----------------|
| `index.html` | Single-page HTML | `.site-header`, `.hero`, `.tabs`, `.modal`, `.footer` |
| `css/main.css` | Master stylesheet | @layer imports, no actual rules |
| `css/base/tokens.css` | Design tokens | `--color-*`, `--space-*`, `--font-*` |
| `css/base/animations.css` | Animations | `@keyframes float`, `shrink-header`, `pulse-dot` |
| `css/components/cards.css` | Story cards | `.story-card`, `.story-card--hero`, `.story-card__* ` |
| `css/components/tabs.css` | Topic selector | `.tabs__input:checked`, `.tabs__panel` |
| `css/components/modal.css` | Article details | `.modal:target`, `.modal__container` |

---

## DESIGN DECISIONS & PRINCIPLES

### 1. **NO JAVASCRIPT** (Assessment Requirement)
- All interactivity via CSS `:checked`, `:target`, `<details>` elements
- Modals work via anchor link `:target` selector
- Tabs work via radio button `:checked` state
- Hidden content via `<details>` element (native HTML)

### 2. **Semantic HTML5**
- Proper heading hierarchy (one `<h1>` per page)
- Article elements for content sections
- `<header>`, `<nav>`, `<main>`, `<footer>` landmarks
- `<time>` elements for dates
- `<details>` and `<summary>` for expandable content

### 3. **BEM Naming Convention**
- Avoids CSS cascade complexity
- Classes are reusable and predictable
- Specificity stays flat (no deep nesting)

### 4. **CSS Layers for Organization**
- Base (tokens, animations, typography)
- Layout (page structure)
- Components (UI blocks)
- No specificity wars, clear ordering

### 5. **Mobile-Responsive Design**
- Breakpoints defined in tokens
- Cards and grids adjust column counts
- Typography scales via relative units
- Modals adapt to small screens

### 6. **Accessibility Features**
- Skip link to main content
- ARIA labels on interactive elements
- Semantic form structure (fieldsets, legends)
- Color contrast compliant
- Keyboard navigation supported

---

## WEBSITE FLOW (User Journey)

```
1. User visits page
   → Sees sticky header with "the wave" logo
   → Full-screen hero section with 3 featured stories
   → Logo bar showing source publications

2. Scroll down to "Past Waves"
   → 6 topic tabs: Weird, Money, Relationships, Security, Education, Trust
   → Click a tab → shows 3 articles for that topic
   → Each topic has its own color scheme

3. Click on any story card
   → CSS :target shows modal overlay
   → Modal shows: title, source, date, summary, link to full article
   → Click X or backdrop to close

4. Continue scrolling
   → Footer with "psst..." button (hidden founder story)
   → Image credits expandable section
   → Copyright info

5. Bottom right
   → Floating action button (FAB) appears after scrolling
   → Click to scroll back to top

6. Throughout
   → Hover effects on cards (scale, shadow)
   → Smooth transitions and animations
   → Consistent color palette across all topics
```

---

## TECHNICAL DEBT / NOTES FOR FUTURE

1. **Header shrink animation:** Currently designed for CSS-only, but truly works with JS. Could add JS observer if needed for future version.

2. **Unverified Unsplash IDs:** 6 images need verification before submission (marked in table above).

3. **Report:** Needs student number and Mayar URL added before final submission.

4. **Server upload:** Mayar server upload not yet done (Task 4).

5. **PDF conversion:** Report still in markdown format, needs conversion to PDF.

---

## HOW TO TEST LOCALLY

1. **Open in browser:**
   ```bash
   open index.html
   # or
   python -m http.server 8000
   # then visit http://localhost:8000
   ```

2. **Test responsive:**
   - Resize browser window (test mobile, tablet, desktop)
   - Check that tabs and modals work
   - Verify all images load

3. **Test interactivity (all CSS-only!):**
   - Click topic tabs → panels switch
   - Click story cards → modals appear
   - Click X or backdrop → modals close
   - Click "psst..." → founder story appears
   - Click vote buttons → shows "Thanks"
   - Click image credits → expands/collapses

4. **Check console:**
   - Should have zero JavaScript errors
   - No console warnings

---

## COMMON ISSUES & SOLUTIONS

**Problem:** Images not loading
- **Solution:** Check `images/articles/` folder exists, all 18 files present
- Verify image filenames match exactly in HTML

**Problem:** Tabs not switching
- **Solution:** Ensure radio buttons have correct `id` and `aria-controls`
- Check CSS selector in `.tabs__input:checked ~ ...`

**Problem:** Modals not appearing
- **Solution:** Check article `id` matches card `href="#article-N"`
- Verify `.modal:target` rule in modal.css

**Problem:** Unsplash links broken
- **Solution:** Verify photo IDs in footer credits links
- Some IDs need TinEye verification (marked in table above)

---

## FINAL CHECKLIST BEFORE SUBMISSION

- [ ] All 18 Unsplash URLs verified and working
- [ ] Student number added to report
- [ ] Mayar URL tested and working
- [ ] Report converted to PDF
- [ ] Report filename: `Report_ShamailaHussain_[STUDENTNUMBER]_Practical1.pdf`
- [ ] ZIP filename: `ShamailaHussain_[STUDENTNUMBER]_Practical1.zip`
- [ ] ZIP contains: `index.html`, `css/`, `images/`, `screenshots/`
- [ ] Report NOT inside ZIP
- [ ] Both files uploaded to Canvas
- [ ] Assignment declaration checked
- [ ] All images load on live server
- [ ] CSS loads correctly on live server
- [ ] Tabs work on live server
- [ ] Modals work on live server
- [ ] All links point to correct articles

---

## ASSESSMENT RUBRIC (Your Grading)

**Task 1 (HTML Structure):** 18 articles, semantic HTML5, proper headings, source references
- ✅ Complete

**Task 2 (CSS Styling):** Colors, fonts, gradients, shadows, transitions
- ✅ Complete

**Task 3 (Image Gallery):** Hover effects, copyright-free images, credits visible
- ✅ Complete (pending image verification)

**Task 4 (Mayar Upload):** Server hosting, working URL in report
- ⏳ Pending server upload

**Task 5 (Testing):** Desktop + mobile screenshots, documented in report
- ✅ Screenshots taken (in `/screenshots/` folder)

**Report Sections:** Title, URL, intro, methodology, security/legal, conclusion, references
- ✅ All sections present in markdown

---

## QUICK GIT STATUS

Latest commits show:
- Added critical analysis and planning narrative to report
- Created image credits and submission checklist
- Refactored images and simplified markup
- Added strategic code comments
- Trimmed alpha tokens, consolidated close opacities

Current branch: `main`
Untracked files: `HEP504_Report_Shamaila_Hussain.pdf` (just generated)

---

**Good luck with final submission! You've built something really clean and well-structured.** 🌊
