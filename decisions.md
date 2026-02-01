# Design & Architecture Decisions

> A living document of the reasoning behind every significant choice in this codebase.

---

## Table of Contents

1. [Architecture](#architecture)
2. [CSS Organization](#css-organization)
3. [Design Tokens](#design-tokens)
4. [Component Reuse](#component-reuse)
5. [Navigation](#navigation)
6. [Hero Section](#hero-section)
7. [Modals](#modals)
8. [Typography](#typography)
9. [Visual Design](#visual-design)
10. [Accessibility](#accessibility)
11. [Performance](#performance)

---

## Architecture

### Modular CSS with @import

**Decision:** Split monolithic 1500-line CSS into 16 focused modules using CSS `@import`.

**Why:**
- Pure HTML5/CSS3 constraint means no build tools (Sass, PostCSS)
- `@import` is valid CSS3 and works in all browsers
- Each file has a single responsibility (SOLID principle)
- Developers can find and edit specific styles quickly
- Reduces merge conflicts in team environments

**Structure:**
```
css/
├── main.css              # Import orchestrator
├── base/                 # Foundation
│   ├── tokens.css        # Design tokens (single source of truth)
│   ├── reset.css         # Normalize browser defaults
│   └── typography.css    # Text styles, prose
├── components/           # Reusable UI pieces
│   ├── buttons.css
│   ├── tags.css
│   ├── inputs.css
│   ├── cards.css
│   └── modal.css
├── layout/               # Page structure
│   ├── header.css
│   ├── sections.css
│   └── footer.css
├── pages/                # Page-specific styles
│   ├── hero.css
│   └── subscribe.css
└── utilities/            # Helpers
    ├── accessibility.css
    └── print.css
```

**Trade-off:** Multiple HTTP requests vs. maintainability. For a small project, maintainability wins. For production at scale, a build step would concatenate these.

---

## CSS Organization

### Import Order Matters

**Decision:** Strict import order in `main.css`:
1. Base (tokens → reset → typography)
2. Components
3. Layout
4. Pages
5. Utilities

**Why:**
- CSS cascade means later rules override earlier ones
- Tokens must load first (everything depends on them)
- Reset must come before any styled components
- Utilities load last so they can override when needed

### BEM Naming Convention

**Decision:** Use Block__Element--Modifier pattern consistently.

**Examples:**
```css
.story-card              /* Block */
.story-card__content     /* Element */
.story-card--hero        /* Modifier */
```

**Why:**
- Self-documenting class names
- Flat specificity (no nesting wars)
- Clear relationship between HTML and CSS
- Widely understood convention

---

## Design Tokens

### Why Tokens?

**Decision:** All design values live in CSS custom properties in `tokens.css`.

**Why:**
- **Single source of truth:** Change `--color-cyan` once, updates everywhere
- **Consistency:** Impossible to accidentally use `#0095ff` vs `#0094ff`
- **Maintainability:** Non-designers can safely adjust values
- **Documentation:** Token file IS the design spec

### Token Categories

| Category | Purpose | Example |
|----------|---------|---------|
| `--color-*` | Brand and UI colors | `--color-cyan`, `--color-text` |
| `--text-*` | Font size scale | `--text-lg`, `--text-2xl` |
| `--weight-*` | Font weights | `--weight-bold`, `--weight-black` |
| `--space-*` | Spacing scale | `--space-4`, `--space-8` |
| `--radius-*` | Border radii | `--radius-lg`, `--radius-full` |
| `--icon-*` | Icon sizes | `--icon-md`, `--icon-lg` |
| `--z-*` | Z-index layers | `--z-sticky`, `--z-modal` |
| `--duration-*` | Animation timing | `--duration-fast` |

### Spacing Scale

**Decision:** Use a constrained spacing scale (4px base).

```css
--space-1: 0.25rem;   /* 4px */
--space-2: 0.5rem;    /* 8px */
--space-3: 0.75rem;   /* 12px */
--space-4: 1rem;      /* 16px */
--space-6: 1.5rem;    /* 24px */
--space-8: 2rem;      /* 32px */
...
```

**Why:**
- Consistent visual rhythm
- Prevents "pixel pushing" debates
- Aligns to 4px grid (industry standard)
- Skip values (no `--space-7`) force intentional jumps

---

## Component Reuse

### DRY: Don't Repeat Yourself

**Decision:** Extract repeated patterns into reusable components.

**Example: Tags**

Before (duplicated):
```css
.modal__tag { ... }        /* 15 lines */
.story-card__tag { ... }   /* 10 lines */
.tag { ... }               /* 15 lines */
```

After (consolidated):
```css
.tag { ... }               /* Base component */
.tag--purple { ... }       /* Variant */
.tag--glass { ... }        /* Variant for dark backgrounds */
```

**HTML uses composition:**
```html
<span class="tag">Policy</span>
<span class="tag tag--purple">Healthcare</span>
<span class="tag tag--glass">Open Source</span>
```

**Why:**
- One place to update tag styles
- Smaller CSS bundle
- Consistent appearance guaranteed
- Easier to add new variants

### Components vs. Context-Specific Styles

**Decision:** Components handle appearance; context handles layout.

```css
/* Component: appearance */
.tag { 
    padding: ...; 
    font-size: ...; 
    background: ...; 
}

/* Context: layout */
.story-card__content .tag { 
    margin-bottom: var(--space-3); 
}
```

**Why:** Tags shouldn't know they're inside a story card. Story cards decide how to space their children.

---

## Navigation

### Floating Pill Navigation

**Decision:** Nav starts transparent/wide in hero, animates to compact white pill on scroll.

**Why:**
- Hero needs visual breathing room (no competing elements)
- Scrolled state provides clear "I'm navigating" affordance
- Pill shape is modern, friendly, approachable
- White background ensures readability over any content

### Scroll-Driven Animation

**Decision:** Use CSS `animation-timeline: scroll()` for nav transformation.

```css
.nav {
    animation: nav-pill linear both;
    animation-timeline: scroll();
    animation-range: 0 300px;
}
```

**Why:**
- Zero JavaScript required
- Buttery smooth (compositor thread)
- Progressive enhancement (fallback for unsupported browsers)
- Native performance optimization

### Constrained Width in Hero

**Decision:** Nav max-width is `40rem` even at top of page (not full viewport).

**Why:**
- Full-width nav felt too spread out
- Content felt disconnected from logo
- Constrained width creates intimate, focused feel
- Subtle but significant UX improvement

---

## Hero Section

### Viewport-Filling Hero

**Decision:** Hero is `min-height: 100svh` (full viewport).

**Why:**
- Creates dramatic first impression
- Establishes visual hierarchy (this is THE headline)
- `svh` unit accounts for mobile browser chrome
- Story cards peek from bottom, inviting scroll

### Gradient Background

**Decision:** Blue-to-cyan-to-white vertical gradient.

```css
background: linear-gradient(
    180deg,
    rgb(71, 114, 255) 0%,    /* Deep blue */
    rgb(0, 172, 255) 45%,    /* Bright cyan */
    rgb(255, 255, 255) 100%  /* White */
);
```

**Why:**
- Blue conveys trust, intelligence, technology
- Gradient adds depth without imagery
- White fade creates seamless transition to content
- No image dependencies (fast loading)

### Decorative Dots

**Decision:** Floating animated dots instead of complex illustrations.

**Why:**
- Pure CSS (no image assets)
- Subtle, non-distracting
- Adds life without competing with content
- Easy to remove or adjust

---

## Modals

### CSS-Only Modal with :target

**Decision:** Modals open/close using URL hash and `:target` pseudo-class.

```css
.modal { opacity: 0; visibility: hidden; }
.modal:target { opacity: 1; visibility: visible; }
```

**Why:**
- Zero JavaScript
- Browser back button closes modal (expected UX)
- Bookmarkable/shareable article URLs
- Accessible (works with keyboard navigation)

### Prevent Scroll Chaining

**Decision:** Add `overscroll-behavior: contain` to modal container.

```css
.modal__container {
    overflow-y: auto;
    overscroll-behavior: contain;
}
```

**Why:**
- Without this, scrolling past modal bottom scrolls the page behind
- Creates jarring, confusing experience
- `contain` traps scroll within the modal
- Small line of CSS, massive UX improvement

### Close Returns to Stories

**Decision:** Modal close links to `#stories` not `#!` or `#top`.

```html
<a href="#stories" class="modal__close">×</a>
```

**Why:**
- User was viewing stories, return them there
- `#!` would scroll to top (disorienting)
- Maintains user's mental context
- Feels like "closing" rather than "navigating away"

### Backdrop Blur

**Decision:** Modal backdrop uses `backdrop-filter: blur(8px)`.

**Why:**
- Indicates content behind is "paused"
- Reduces visual noise
- Creates depth hierarchy
- Modern, polished feel

---

## Typography

### Font Stack

**Decision:** Three-font system:
- **Nunito** (UI) - Friendly, rounded sans-serif for headlines and interface
- **Source Serif 4** (Reading) - Comfortable serif for article body text
- **JetBrains Mono** (Code) - Monospace for dates and technical content

**Why:**
- Serif for long-form reading reduces eye strain
- Sans-serif headlines create clear hierarchy
- Personality fonts make brand distinctive
- All fonts from Google Fonts (free, fast CDN)

### Type Scale

**Decision:** Use a constrained modular scale.

```
xs:   0.75rem   (12px)
sm:   0.875rem  (14px)
base: 1rem      (16px)
lg:   1.125rem  (18px)
xl:   1.25rem   (20px)
2xl:  1.5rem    (24px)
3xl:  1.75rem   (28px)
4xl:  2.5rem    (40px)
5xl:  3.125rem  (50px)
6xl:  4.375rem  (70px)
```

**Why:**
- Predictable, harmonious relationships
- Prevents arbitrary font sizes creeping in
- Fluid `clamp()` for responsive headlines uses these as bounds

### Black Weight for Headlines

**Decision:** Use `font-weight: 900` (black) for major headlines.

**Why:**
- Creates strong visual anchor
- Matches modern design trends (Apple, Stripe, Linear)
- Nunito's black weight is particularly well-designed
- Clear hierarchy without needing larger sizes

---

## Visual Design

### Bright & Airy Theme

**Decision:** White backgrounds, generous whitespace, vibrant accent colors.

**Why:**
- AI news can feel intimidating; bright design feels approachable
- White space lets content breathe
- Vibrant colors (cyan, purple, orange, green) create energy
- Trust and optimism over dark "tech dystopia" vibes

### Color-Coded Topics

**Decision:** Each topic has a signature color:
- Breakthroughs: Cyan
- Policy: Purple
- Healthcare: Orange
- Open Source: Green

**Why:**
- Instant visual categorization
- Memorable brand associations
- Makes scanning content faster
- Adds visual interest to grid layouts

### Rounded Corners Everywhere

**Decision:** Generous border-radius on cards, buttons, inputs (`--radius-lg` to `--radius-full`).

**Why:**
- Friendly, approachable feel
- Modern design language
- Consistency across all components
- Matches the "wave" brand (fluid, organic)

---

## Accessibility

### Skip Link

**Decision:** First focusable element is "Skip to content" link.

```html
<a href="#main" class="skip-link">Skip to content</a>
```

**Why:**
- Screen reader and keyboard users can bypass navigation
- Required for WCAG compliance
- Hidden visually until focused
- Costs nothing, helps many

### Semantic HTML

**Decision:** Use appropriate HTML5 elements throughout.

```html
<header>, <nav>, <main>, <section>, <article>, <footer>
<time datetime="...">
<h1> → <h2> → <h3> (proper hierarchy)
```

**Why:**
- Screen readers announce structure
- SEO benefits from semantic markup
- Future-proof (browsers may add features)
- Self-documenting code

### Focus Visible

**Decision:** Custom focus styles only on keyboard navigation.

```css
:focus-visible { outline: 2px solid var(--color-cyan); }
:focus:not(:focus-visible) { outline: none; }
```

**Why:**
- Mouse users don't see focus rings (cleaner)
- Keyboard users get clear focus indicators (accessible)
- Browser handles the detection

### ARIA Labels

**Decision:** All interactive elements have accessible names.

```html
<a href="#stories" class="modal__close" aria-label="Close">×</a>
<div class="hero__decoration" aria-hidden="true">
```

**Why:**
- `×` is visual, not descriptive
- Decorative elements hidden from screen readers
- Clear purpose for every interactive element

---

## Performance

### No JavaScript

**Decision:** Entire site works without JavaScript.

**Why:**
- Fastest possible load time
- Works with JS disabled
- No framework overhead
- Proves CSS is more capable than people think

### Preconnect Fonts

**Decision:** Preconnect hints for Google Fonts.

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
```

**Why:**
- Browser establishes connection early
- Reduces font loading delay
- No downside (tiny HTML addition)

### No Images in Core Layout

**Decision:** Hero, cards, and decorations use CSS only.

**Why:**
- Gradients and shapes render instantly
- No network requests for visual elements
- Responsive without `srcset` complexity
- Placeholder icons are Unicode/emoji (zero bytes)

### CSS Animation on Compositor

**Decision:** Animations use `transform` and `opacity` only.

**Why:**
- These properties animate on GPU compositor thread
- No layout thrashing
- 60fps even on low-end devices
- Scroll-driven animations are especially smooth

---

## Decisions NOT Made

### What We Avoided

| Avoided | Why |
|---------|-----|
| Dark mode | Scope constraint; bright theme is intentional |
| CSS preprocessor | Pure CSS3 constraint |
| CSS-in-JS | Not applicable (no JS) |
| Utility-first CSS | BEM is clearer for this scale |
| CSS Grid everywhere | Flexbox sufficient; Grid where needed |
| Custom fonts (self-hosted) | Google Fonts CDN is faster globally |
| Image optimization | No images in current scope |

---

## Future Considerations

If this project grows:

1. **Build step** - Concatenate CSS imports for fewer requests
2. **Dark mode** - Add `prefers-color-scheme` media query
3. **More articles** - Consider pagination or infinite scroll
4. **Real images** - Add `srcset` and lazy loading
5. **Form submission** - Add backend or serverless function
6. **Analytics** - Consider privacy-respecting options

---

---

## Session Log

### [2026-02-01] [CODE] Updated AGENTS.md with assessment requirements
- **Goal:** Align project documentation with HEP504 Portfolio Part 1 brief
- **Tried:** Mapped assessment tasks against existing implementation
- **Outcome:** Added assessment context, requirements checklist, and identified gaps:
  - Missing: CSS Image Gallery (Task 3)
  - Missing: Source references for news articles
  - Missing: Image credits/attribution
  - Kept advanced CSS quality bar - brief encourages "unique, interesting, colourful"

### [2026-02-01] [STYLE] Fixed story card text legibility
- **Goal:** Make article headlines and tags readable over background images
- **Tried:** 
  - Original gradient overlay was too weak (transparent to 0.8 black)
  - Text had no shadow and was competing with busy images
- **Outcome:** 
  - Strengthened overlay gradient (0.1 → 0.2 → 0.6 → 0.95) for much better contrast
  - Added `text-shadow` to headlines for pop against any background
  - Improved `.tag--glass` with stronger background, border, and shadow
  - Increased bottom padding on card content for breathing room
  - Reduced title font size slightly (`text-2xl` → `text-xl`) for better fit

### [2026-02-01] [STYLE] Removed colored tints from story card backgrounds
- **Goal:** Fix weird color outline/tint appearing behind card images
- **Tried:** Identified colored gradient overlays (rgba 0.3 opacity) layered on background images
- **Outcome:** 
  - Removed colored gradient overlays from all three card backgrounds
  - Now just clean images with the dark gradient overlay for text legibility
  - Explicitly set `.story-card__title` color to `#fff` for guaranteed white text
  - Changed fallback colors to neutral dark (#1a1a2e) instead of theme colors

### [2026-02-01] [UX] Scroll-to-top button hidden in hero, shows on scroll
- **Goal:** Button should not appear when user is at top of page in hero viewport
- **Tried:** 
  - Considered JavaScript scroll listeners (rejected - no JS constraint)
  - Considered sticky positioning tricks (too hacky, doesn't achieve goal)
  - Used CSS scroll-driven animations with `animation-timeline: scroll()`
- **Outcome:**
  - Button starts at `opacity: 0` with `pointer-events: none`
  - `animation-range: 10vh 20vh` triggers fade-in after scrolling 10% of viewport
  - Progressive enhancement: older browsers see button always (acceptable fallback)
  - Zero JavaScript, buttery smooth performance on GPU compositor thread
  - Added detailed CSS comment explaining the approach for assessment documentation

### [2026-02-01] [UX] Replaced featured article with "Note from the founder"
- **Goal:** Create more personal, trust-building section below hero
- **Tried:** 
  - "Read the full story" button felt disconnected from the site's purpose
  - Featured article competed with hero story cards
- **Outcome:**
  - New `.founder-note` component with personal quote styling
  - Uses semantic `<blockquote>` for the founder's words
  - Cyan left border on quote for visual interest
  - Uppercase label "A NOTE FROM THE FOUNDER" establishes context
  - Attribution with name and role builds credibility
  - No external link - keeps users on site, focused on newsletter value prop

### [2026-02-01] [UX] Expanded story card gallery to 6 cards
- **Goal:** More content, better scroll/drag experience
- **Tried:** Cards were getting cut off on hover due to overflow:hidden
- **Outcome:**
  - Added 3 new cards: Robotics, Research, Climate
  - Thickened border to 5px white at 60% opacity
  - Changed hero overflow to `overflow-x: clip; overflow-y: visible`
  - Removed justify-content:center for natural scroll
  - Added new background image CSS classes for new cards

### [2026-02-01] [CODE] Restructured modals as TLDR summaries with source links
- **Goal:** Assessment requires source references; avoid plagiarism risk
- **Tried:** Long-form articles felt like we were copying content
- **Outcome:**
  - Each modal now 2 short paragraphs - our own editorial summary
  - Prominent "Read full article" button links to real source
  - Updated to real publication dates
  - Removed subheadings for cleaner, faster reading
  - Real sources: EU Parliament, MIT News, DeepSeek GitHub, Boston Dynamics blog, Anthropic research, DeepMind blog

### [2026-02-01] [UX] Replaced email subscription with Yes/No vote buttons
- **Goal:** Change CTA from email signup to interest validation
- **Tried:** Email form felt presumptuous for a concept/prototype stage
- **Outcome:**
  - Title changed to "Would you want this to exist?"
  - Description asks if a newsletter like this would be useful
  - Two buttons: "Yes" (cyan, primary) and "No" (ghost style)
  - Proper ARIA labelling with `role="group"` and descriptive aria-labels
  - `.btn--vote` styles with hover states and smooth transitions
  - Keeps `.subscribe` class/section structure for minimal CSS changes

### [2026-02-01] [UX] Collapsible footer image credits
- **Goal:** Reduce footer clutter while keeping required image attribution visible
- **Tried:** Credits list took up too much space in footer
- **Outcome:**
  - Used native HTML `<details>` and `<summary>` elements
  - CSS-only toggle - no JavaScript required
  - Shows "Image credits +" when collapsed, "Image credits -" when expanded
  - Semantic and accessible - works with keyboard and screen readers
  - Hidden by default, one click reveals all Unsplash attribution links
  - Satisfies assessment requirement for visible image credits without visual clutter

### [2026-02-01] [STYLE] Logo bar visibility and styling
- **Goal:** Fix "Curated from" source logos being invisible (white on white)
- **Tried:** Logo bar was white text sitting on the white fade of hero gradient
- **Outcome:**
  - Changed color from `--color-white` to `--color-hero-top` (blue) for both text and logos
  - Increased logo font-size from `--text-base` to `--text-xl` for better visibility
  - Removed opacity values that were dimming the text
  - Added `font-family: var(--font-primary)` to "Curated from" text for consistency
  - Inverted hover effect (now fades to 0.7 opacity on hover instead of 1)
  - Updated mobile breakpoint to use `--text-base` instead of `--text-sm`

### [2026-02-01] [STYLE] Logo bar typography refinement
- **Goal:** Make logo bar look more polished, matching hero title styling
- **Tried:** Initial blue styling looked plain and cramped
- **Outcome:**
  - Applied `--weight-extrabold` with positive letter-spacing (0.05em) for readability
  - Font-size `--text-xl` (1.25rem) balanced with spacing
  - Spread out logos with `--space-10` (2.5rem) horizontal gap

### [2026-02-01] [UX] Hero vertical rhythm optimization
- **Goal:** Fit all hero content above the fold with proper visual grouping
- **Tried:** Uniform gap caused poor visual hierarchy
- **Outcome:**
  - Removed hero flex gap (set to 0) for manual control
  - Increased nav-to-content spacing: `padding-top: calc(nav-height + --space-12)`
  - Kept eyebrow/title/subtitle tightly grouped (small internal margins)
  - Added `margin-bottom: --space-8` to hero__content for space before cards
  - Pushed logo-bar down with `margin-top: --space-12` to separate from cards
  - Creates clear visual groups: [nav] -- [text block] -- [cards] -- [logo bar]

### [2026-02-01] [CODE] Restructured content to 4 topic sections with 12 articles
- **Goal:** Organise articles by theme relevant to Human Factors & Web Development course
- **Tried:** Previous structure had 6 articles with mixed topics
- **Outcome:**
  - Created 4 colorful topic boxes: Human-AI Interaction (cyan), Design & UX (purple), Accessibility (orange), Ethics & Bias (green)
  - Each topic contains 3 article cards (12 total)
  - Topic boxes use full-width colorful backgrounds with white text
  - Cards inside flex to fill available width
  - Mobile responsive: cards stack on narrow screens
  - Topics directly relevant to student's degree focus

### [2026-02-01] [CODE] Created 12 new article modals with real source links
- **Goal:** Assessment requires source references; provide TLDR summaries linking to real journalism
- **Tried:** Needed modals matching the 12 story cards in topic sections
- **Outcome:**
  - Each modal has 2-paragraph editorial summary (our own writing, not copied)
  - "Read full article at [Source]" button links to real articles
  - Sources: MIT Technology Review, Wired, Nature, The Verge, NYT, Fast Company
  - Modal close returns user to #topics (not #top) for better UX
  - Tags match topic categories: Human-AI, Design, Accessibility, Ethics
  - Proper dates for each article

### [2026-02-01] [CODE] Updated footer image credits for 12 gallery images
- **Goal:** Assessment requires visible image attribution for all copyright-free images
- **Tried:** Previous credits list was for old article set
- **Outcome:**
  - Listed all 12 Unsplash images with photographer credits and links
  - Organised by topic section for easy reference
  - Kept collapsible `<details>` element to reduce footer clutter
  - Summary text now reads "Image credits (Unsplash)" for clarity

### [2026-02-01] [STYLE] Logo bar visibility fix
- **Goal:** Fix "Curated from" source logos being invisible (white on white gradient)
- **Tried:** Logo bar had white text on the white-fading portion of hero gradient
- **Outcome:**
  - Changed color to `--color-hero-top` (blue) to contrast with white background
  - Added proper letter-spacing (0.05em) for readability
  - Removed opacity that was dimming text

### [2026-02-01] [STYLE] Publication wordmark typography
- **Goal:** Make source publication names look like authentic brand wordmarks
- **Tried:** Considered downloading actual logos - copyright concerns for academic submission
- **Outcome:**
  - Used CSS-only styled text wordmarks (common "featured in" pattern)
  - Each publication has unique BEM modifier class (e.g., `logo-bar__logo--wired`)
  - Brand-appropriate typography applied:
    - MIT Tech Review: Black weight, tight tracking (technical)
    - Wired: Black weight, uppercase, wide letter-spacing (bold tech)
    - Nature: Serif font, italic (academic journal)
    - The Verge: Extrabold, tight tracking (modern digital)
    - NYT: Serif font, wider letter-spacing (classic newspaper)
    - Fast Company: Black weight, tight tracking (business)
  - Maintains visual harmony through consistent color and base sizing
  - Responsive sizing on mobile (`--text-sm`)
  - No copyright/trademark concerns with text-based approach

### [2026-02-01] [STYLE] Enhanced story card hover animation and source badge redesign
- **Goal:** Create smoother, more unique card hover effect; make source badges sleeker
- **Tried:** 
  - Original hover was basic scale(1.02) with fast duration - felt generic
  - Source badges (`.tag--glass`) were large rounded pills that competed with content
- **Outcome:**
  - **Hover animation improvements:**
    - Custom cubic-bezier easing `(0.34, 1.56, 0.64, 1)` for bounce-out effect
    - 3D lift: `translateY(-12px) scale(1.02) rotateX(2deg)` creates depth
    - Layered box-shadows for realistic elevation (20px + 8px blur)
    - Background image zooms slower (0.6s) with brightness boost on hover
    - Content container lifts 4px to follow card movement
    - Button reacts to card hover state for unified experience
  - **Source badge redesign:**
    - Reduced from pill to small rectangular label (`border-radius: sm`)
    - Smaller padding and 0.65rem font size
    - Uppercase with 0.04em letter-spacing for refined look
    - Subtler glass effect: 12% white bg instead of 25%
    - Thinner border (15% opacity vs 30%)
    - Badge lifts slightly on card hover
  - All transitions use compositor-friendly properties (transform, opacity, filter)
  - Progressive enhancement - works without scroll-driven animations

### [2026-02-01] [UX] Fixed modal close causing page scroll
- **Goal:** Closing a modal should return user to their previous scroll position
- **Tried:** Modal close/backdrop links pointed to `#topics`, causing browser to scroll there
- **Outcome:**
  - Changed all modal close and backdrop links from `href="#topics"` to `href="#!"`
  - `#!` is a "null" anchor - doesn't match any element ID
  - Browser clears the URL hash without scrolling to any element
  - User stays exactly where they were when they opened the modal
  - Common CSS-only modal pattern for zero-scroll close behaviour

### [2026-02-01] [UX] CSS-only topic tabs with color coordination
- **Goal:** Add tabbed navigation to "Explore by Topic" section without JavaScript
- **Tried:** Radio button hack with `:checked` selector - standard CSS-only tab pattern
- **Outcome:**
  - Hidden radio inputs control which panel is visible
  - Labels styled as tab buttons with card-like hover animations
  - Color-coded active states matching topic colors:
    - Human-AI = Cyan (`--color-cyan`)
    - Design & UX = Purple (`--color-purple`)
    - Accessibility = Orange (`--color-orange`)
    - Ethics & Bias = Green (`--color-green`)
  - Active tabs lift with `translateY(-4px)` and colored shadow (matching card animations)
  - Smooth fade-in animation on panel switch
  - Cards sized at 280px flex-basis with 320px max for balanced layout
  - Proper ARIA roles (`tablist`, `tab`, `tabpanel`) for accessibility
  - No JavaScript - pure CSS using sibling selectors

### [2026-02-01] [UX] Progressive disclosure "Read story" island
- **Goal:** Replace static button with iOS Dynamic Island-style reveal on hover
- **Tried:** 
  - Initial attempt with button sliding up from below card (clipped by overflow)
  - Negative positioning (clipped by overflow:hidden)
  - Box-shadow extension to bridge gap between island and border
- **Outcome:**
  - New `.story-card__island` component replaces `.story-card__btn`
  - Island is hidden by default (`height: 0`, `opacity: 0`)
  - On card hover: grows upward from bottom edge (`height: 36px`)
  - Content area lifts up (`translateY(-32px)`) to reveal island beneath
  - Flat bottom corners connect visually to card's white border
  - Rounded top corners only (`border-radius: md md 0 0`)
  - Box-shadow extends downward to close any subpixel gap with border
  - Removed image zoom on hover for cleaner interaction
  - Spring easing (`cubic-bezier(0.34, 1.56, 0.64, 1)`) for satisfying animation
  - HTML restructured: island moved outside `.story-card__content` for proper positioning

### [2026-02-01] [STYLE] Increased badge-to-title spacing in hero
- **Goal:** Add more vertical separation between the "Live" eyebrow pill and the hero title
- **Tried:** Badge was sitting too close to the title text below it
- **Outcome:**
  - Added `margin-bottom: var(--space-4)` (16px) to `.badge` component
  - Creates clear visual breathing room between the status indicator and headline
  - Improves hero section hierarchy and readability

### [2026-02-01] [UX] Secret founder reveal with playful collapsible
- **Goal:** Transform founder intro into a fun "easter egg" style interaction
- **Tried:** Previous founder section was always visible - felt disconnected from the playful brand
- **Outcome:**
  - Used native `<details>` and `<summary>` for CSS-only collapsible (no JS)
  - Trigger styled as large pill button with "psst... click me" teaser text
  - Section title-like typography (`--weight-black`, `clamp()` sizing)
  - Hover state: subtle scale up only (no background color change)
  - On open: trigger hides completely, founder content fades in with `translateY` animation
  - Vote CTA moved inside the reveal - flows naturally after founder intro
  - Added `.subscribe--inline` modifier for embedded CTA styling
  - Creates cohesive "secret" experience: click → meet founder → decide to subscribe

### [2026-02-01] [STYLE] Reusable light rays component (underwater sun effect)
- **Goal:** Create animated "god rays" / volumetric lighting effect to reinforce "the wave" underwater brand theme
- **Tried:** 
  - Bubbles rising animation - felt too busy and distracting
  - Static gradient overlays - lacked the dynamic underwater feel
- **Outcome:**
  - Created modular `css/components/light-rays.css` component
  - Uses CSS custom properties (`--angle`, `--duration`, `--delay`) for each ray
  - Technique combines: linear gradients with transparency, keyframe animations, transform (rotate, scale), filter (blur)
  - Rays positioned at edges to avoid clashing with centered white text
  - Animation pulses opacity (0.1 → 0.85) and width (scaleX 0.5 → 1.5)
  - Reused across: hero section, subscribe card, all 4 topic boxes
  - DRY principle: same HTML structure (`<div class="light-rays">`) works everywhere
  - Progressive enhancement: works without affecting content if animations disabled
- **References:**
  - MDN Web Docs - CSS Gradients: https://developer.mozilla.org/en-US/docs/Web/CSS/gradient
  - MDN Web Docs - CSS Animations: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animations
  - CSS-Tricks - A Complete Guide to CSS Gradients: https://css-tricks.com/a-complete-guide-to-css-gradients/
  - W3Schools - CSS Animations: https://www.w3schools.com/css/css3_animations.asp

### [2026-02-01] [STYLE] Hero section elevation - award-winning design pass
- **Goal:** Elevate hero from "startup template" to distinctive, memorable experience
- **Tried:** Analyzed current state against award-winning site patterns
- **Outcome:**
  - **Staggered card heights:** Middle card 420px, sides 380px, middle elevated -20px. Creates visual tension and draws eye to center.
  - **Grain texture overlay:** SVG noise pattern at 3% opacity adds tactile depth to flat gradient.
  - **Toned-down logo bar:** Added 60% opacity and 90% scale to reduce competition with hero content.
  - **On-brand headline:** Changed "This is the wave." → "Catch the wave." - action-oriented, ties to brand metaphor.
  - **Decorative wave shape:** Added subtle SVG wave at hero bottom (15% opacity white) reinforcing brand identity.
  - All changes are pure CSS, no JavaScript, maintaining assessment constraints.

### [2026-02-01] [CODE] Removed mini-cards and verified all modal links
- **Goal:** Fix ugly mini-card design in "Show more" section and ensure all external links work
- **Tried:** 
  - Mini-cards were duplicates of existing content with poor styling
  - Many modal links were 404s (Wired, NYT, Fast Company articles)
- **Outcome:**
  - Removed entire "Show more" section from Interaction panel (mini-cards weren't adding value)
  - Removed unused CSS for `.topic-box__more`, `.story-card--small` from tabs.css
  - Verified and replaced all modal links with working URLs:
    - Article 2: OpenAI ChatGPT blog ✓
    - Article 3: Anthropic Claude 3.5 Sonnet ✓
    - Article 4: Figma AI ✓
    - Article 5: Adobe Firefly ✓
    - Article 6: Vercel Generative UI ✓
    - Article 7, 8, 9: Be My Eyes / OpenAI Be My Eyes ✓
    - Article 10: EEOC AI Hiring Initiative ✓
    - Article 11: Nature Model Collapse study ✓
    - Article 12: TIME Kenyan AI Workers investigation ✓
  - Updated modal dates to match actual publication dates
  - Updated modal content to align with new sources
  - All links verified working as of February 2026

---

## [2026-02-01] UX: CTA Section Copy Update

- **Goal:** Make newsletter CTA feel more personal and conversational
- **Tried:** Original text "Three curated AI stories delivered every Sunday." felt formulaic
- **Outcome:** Changed to "tech stories I know you'll find interesting" - more casual, personal voice that matches the site's editorial tone

---

*Last updated: February 2026*
