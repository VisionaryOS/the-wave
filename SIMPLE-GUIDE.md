# THE WAVE - SIMPLE EXPLANATION FOR HUMANS

**This is the dumbed-down version with NO JARGON.**

---

## WHAT DID YOU BUILD? (The Elevator Pitch)

You built a **website that shows tech news articles**.

Think of it like this:
- **Old way:** You go to BBC.com, then NYT.com, then WIRED.com to read news = annoying, takes forever
- **Your way:** All the best tech news is already picked out for you, organized by topic, in ONE place

It's called "the wave" because you can "catch" the important news without drowning in all the garbage news.

---

## THE THREE THINGS THAT MAKE A WEBSITE

### 1. **HTML** = The Skeleton (Structure)
Think of HTML like the bones of a body.

```
Your body:
- Head (with brain)
- Neck
- Torso
- Arms
- Legs

A website:
- Header (the top menu bar)
- Hero section (the big featured section)
- Topics section (the tabs)
- Footer (the bottom part)
```

**HTML just says:** "Here's where stuff goes. This is a header. This is a picture. This is a button."

It DOESN'T say how it looks. It just says what it IS.

**File:** `index.html` - This is 778 lines of "here's what this website contains"

### 2. **CSS** = The Skin/Clothes (Appearance)
Think of CSS like the clothes you wear and makeup you apply.

HTML says: "I have a face"
CSS says: "Make the face blue, put the nose in the center, make the eyes big and sparkly"

```
HTML says: <button>Click me</button>
CSS says: Make it blue, round the corners, make text bigger,
          change color when I hover over it
```

**Why it matters:** Without CSS, a website looks like a boring document with just black text and links.
WITH CSS, it looks cool with colors, animations, and design.

**Files:** Everything in the `css/` folder

### 3. **JavaScript** = The Brain (Interactivity)
Think of JavaScript like the instructions that make things HAPPEN.

```
HTML: <button>Click me</button>
CSS: Make it blue
JavaScript: When someone clicks it, do this thing...
```

**Important:** YOUR website DOESN'T HAVE JavaScript. This is intentional. More on that below.

---

## WHAT IS EACH PART OF YOUR WEBSITE?

### THE HEADER (Top Bar)
```
┌─────────────────────────────────┐
│  the wave          [stay scrolled to]
└─────────────────────────────────┘
```

**What it is:** A sticky bar at the top with your site's name.

**"Sticky" means:** Even when you scroll down, it stays at the top. It's like a menu bar in an app.

**Why:** So users can always go back to the top or navigate around.

---

### THE HERO SECTION (The Big Welcome Part)
```
┌────────────────────────────────────────┐
│                                        │
│      Catch the wave.                   │
│  Three tech stories a day.             │
│                                        │
│  [Image] [Image] [Image]              │
│  (3 big featured article cards)        │
│                                        │
│  Curated from: BBC NYT WIRED etc      │
│                                        │
└────────────────────────────────────────┘
```

**What it is:** The first thing you see. It's like a magazine cover.

**Why:** Grabs attention. Shows the 3 best stories of the day + shows which publications you're curating from.

---

### THE TABS SECTION ("Past Waves")
```
┌──────────────────────────────────────┐
│  [Weird] [Money] [Relationships]     │
│  [Security] [Education] [Trust]      │
│                                      │
│  When you click "Money":             │
│  ┌──────────────────────────────────┐
│  │ 3 articles about AI & money      │
│  │ [Article] [Article] [Article]    │
│  └──────────────────────────────────┘
└──────────────────────────────────────┘
```

**What it is:** Like Spotify playlists, but for news topics.

**Why:** Helps people find news they care about. Money person? Click Money. Security paranoid? Click Security.

**The magic trick:** Clicking a tab SWITCHES what you see, using ONLY CSS + HTML. No JavaScript.

---

### THE ARTICLE DETAIL (Modal)
When you click on a story card:

```
┌────────────────────────────────────────┐
│  [X]                                   │
│  ChatGPT Wrote a Suicide Lullaby      │
│  Security | January 15, 2026           │
│                                        │
│  A wrongful death lawsuit has been... │
│                                        │
│  [Read full article at Ars Technica]   │
└────────────────────────────────────────┘
```

**What it is:** A pop-up card with the full story summary.

**"Modal" means:** A window that appears on top of everything else. Like a pop-up.

**Why:** You can read a preview without leaving the page.

---

### THE FOOTER (Bottom)
```
┌──────────────────────────────────────┐
│  the wave                            │
│  made with ❤️ by Shamaila            │
│  [psst... click me] (hidden story)    │
│  Image credits                        │
└──────────────────────────────────────┘
```

**What it is:** The boring legal stuff at the bottom, PLUS...

**The cool part:** Click "psst... click me" to see Shamaila's founder story.

**Why she built it:** She was busy (new baby, school, business) but still wanted to read tech news. So her partner started picking the best articles for her. Now she shares those picks here.

---

## HOW MANY ARTICLES? (The Article Breakdown)

You have **18 unique news articles** organized into **6 topics**:

### WEIRD (Pink) - Strange AI stories
- Article 1: AI Video Generator Making Videos
- Article 2: Is China Winning AI?
- Article 3: Moltbot Controlling Silicon Valley

### MONEY (Gold) - Money & business
- Article 4: OpenAI Raising $100 BILLION
- Article 5: Amazon/Google Beating Nvidia at Chips
- Article 6: Data Centers Causing Gas Shortage

### RELATIONSHIPS (Purple) - AI as friends?
- Article 7: Social Network FOR AI AGENTS (not humans, literally agents talking to each other)
- Article 8: Guy Replaced Real Friends With AI Gaming Buddy
- Article 9: Someone Burned Out Using AI Coding Tools

### SECURITY (Cyan/Light Blue) - Dangerous AI stuff
- Article 10: ChatGPT Turned Kid's Bedtime Story into Suicide Lullaby (lawsuit filed)
- Article 11: AI Chat App Leaked 50 MILLION Private Conversations
- Article 12: US Cyber Security Chief Accidentally Uploaded Secret Docs to ChatGPT

### EDUCATION (Orange) - Learning & AI
- Article 13: This AI Tool Is Going Viral (5 ways people use it)
- Article 14: British Gen Z Using AI to Feel Less Lonely
- Article 15: AI Toy Exposed 50,000 Kids' Chats to Public

### TRUST (Green) - Fake AI Content
- Article 16: cURL Project Killed Their Bug Bounty (too much AI spam)
- Article 17: YouTube Banning AI Spam Channels
- Article 18: AI Spam Flooding Scientific Research Papers

**Why 6 topics?** Different people care about different things. Some care about money, some about security, some about ethics. This lets people find what matters to them.

---

## THE CSS FOLDER (Making It Look Good)

### What's CSS?
CSS = **"How to make it pretty"**

HTML says: "This is a button"
CSS says: "Make it blue, round it, make it bigger, add a shadow under it, when I hover make it darker"

### The Files

**`css/main.css`** = The LIST of all other CSS files
- Like a table of contents
- Imports all the other CSS files in the right order

**`css/base/tokens.css`** = The Design Dictionary
**What's "tokens"?** A token is a variable (a container that holds a value)

```
Example:
Token: --color-primary = #4772FF (that blue color)

Then everywhere you want that blue, you just say:
color: var(--color-primary)

If you want to change the blue later, you change it in ONE place.
All places automatically get the new color.
```

**Why this matters:** You don't have to search through 1000 lines of CSS to change the color. You change it once at the top.

---

**`css/base/animations.css`** = The Movement Rules

**What's an animation?** Something that MOVES or CHANGES OVER TIME.

```
Example: "Fade in" animation
Start: transparent (invisible)
Middle: getting more visible
End: fully visible

This takes 0.5 seconds

So the logo slowly appears instead of POOF appearing instantly.
```

**Why?** Makes the site feel smooth and polished instead of robotic.

---

**`css/base/typography.css`** = The Text Rules

**"Typography" = how text looks**

- What font? (Nunito for buttons, Source Serif for articles)
- How big? (Headers = 48px, body text = 16px)
- How bold? (Regular, bold, extra bold)
- Line spacing? (Make it readable)

**Why different fonts?**
- **Nunito** = Modern, clean, good for buttons/menus
- **Source Serif** = Elegant, easy to read for long articles

You ever notice some websites are hard to read? That's bad typography. Yours is good.

---

**`css/layout/` files** = Page Structure

Think of these like: "Where should things go on the page?"

- **header.css** = "The top bar lives here and is sticky"
- **hero.css** = "The big featured section is full-width, images are in a 3-column grid"
- **topics.css** = "The topics section wrapper styling"
- **footer.css** = "Bottom stuff goes to the bottom, spread out like this"

**Layout = the skeleton structure**
**Components = the clothes on the skeleton**

---

**`css/components/` files** = The UI Parts

Think of these like LEGO blocks. Each file styles one type of block:

- **buttons.css** = Blue buttons, green buttons, red buttons - all button variations
- **cards.css** = The story cards with images, titles, read time. When you hover, it scales up slightly.
- **modal.css** = The pop-up article boxes
- **tabs.css** = The topic selector tabs
- **tags.css** = The little "WIRED" / "BBC" labels
- **light-rays.css** = The decorative glowing rays in the background
- **founder-note.css** = The "psst" hidden story section
- **interactions.css** = Things that respond to clicks/hovers

---

## THE JARGON EXPLAINED

### BEM Naming
**What it is:** A naming system for CSS classes so you don't mess things up.

**Problem it solves:** Without rules, CSS class names get messy:
```
.button
.button2
.button-big
.big-button
.largeButton
.lg-btn
(chaos - nobody knows which one to use)
```

**BEM solution:** Follow a pattern:
- **Block** = The main thing (`.story-card`)
- **Element** = Part of the block (`.story-card__title`)
- **Modifier** = A variation (`.story-card--hero`)

```
So:
.story-card = the card itself
.story-card__title = the title inside the card
.story-card__image = the image inside the card
.story-card--hero = a BIGGER version of the card
```

**Why?** Prevents accidents and makes names predictable.

---

### CSS Layers
**What it is:** Organizing CSS by importance level.

```
Level 1 (Base): Basic stuff - colors, animations, fonts
Level 2 (Layout): Page structure - where things go
Level 3 (Components): Individual UI blocks
Level 4 (Utilities): Overrides for special cases
```

**Why?** When two rules conflict, the higher level wins. No fighting.

---

### Modal
**What it is:** A pop-up window.

**Where you see them:**
- "Are you sure?" pop-ups
- Sign-up forms that overlay the page
- Your article detail cards

**Why?** Let people see more info without leaving the page.

---

### Semantic HTML
**What it is:** Using the RIGHT HTML tag for the RIGHT job.

```
WRONG:
<div>My Article Title</div>

RIGHT:
<article>
  <h2>My Article Title</h2>
  <time>January 15, 2026</time>
  <p>Article content...</p>
</article>
```

**Why?**
- Screen readers (for blind people) understand it better
- Search engines understand it better
- Future you (when you forget what you built) understands it better

---

### :checked and :target
**What these mean:** CSS selectors that find elements in specific states.

**:checked** = When a radio button or checkbox is SELECTED
```
<input type="radio" name="topic" id="tab-money">
<label>Money</label>

CSS:
#tab-money:checked ~ .panels { show the money panel }
```

**:target** = When a URL has #anchor and it matches an element's ID
```
URL: yoursite.com/#article-1
CSS:
#article-1:target { show this article modal }
```

**Why this is cool:** You can make things INTERACTIVE with ONLY HTML + CSS. No JavaScript needed!

---

### Hover Effect
**What it is:** Something that changes when you move your mouse over it.

```
Normal state: Card is 1x size
Hover state: Card grows to 1.1x size, shadow gets darker

User sees: Smooth growth animation, makes it feel alive
```

**Why?** Tells the user "this is clickable!" and makes the site feel responsive.

---

### Gradient
**What it is:** A color that smoothly CHANGES from one color to another.

```
Example:
Top of button = Blue (#4772FF)
Bottom of button = Dark Blue (#2C5AFF)

Smooth transition between them

Looks more 3D and modern than flat color
```

---

### Responsive Design
**What it is:** A website that looks good on phones, tablets, and desktops.

**How it works:**
- On desktop: 3 article cards per row
- On tablet: 2 article cards per row
- On phone: 1 article card per row

**Why?** Phone screens are tiny. If you show 3 cards, they'd be unreadable.

---

### Unsplash
**What it is:** A website with FREE photos you can use.

**Why important for your assignment:**
- The photos are copyright-free
- You can use them legally
- You just have to credit the photographer

**Your problem:** 6 photo IDs might be wrong. Need to verify using TinEye.

**Why TinEye?** It's reverse image search. Upload your photo, it finds where it came from online.

---

## THE SECRET TRICK: NO JAVASCRIPT!

### What's JavaScript?
**JavaScript = the instructions that make things HAPPEN**

```
User clicks button
→ JavaScript runs
→ Something changes on the page
```

Example: Click "show password" checkbox, password text appears.

### Your website has ZERO JavaScript
Instead, you use:
1. **HTML radio buttons** for tabs
2. **HTML anchor links** for modals (the #article-1 in the URL)
3. **HTML <details> element** for the hidden founder story

### How tabs work (NO JavaScript):
```
User clicks "Money" tab
→ Radio button becomes :checked
→ CSS rule sees #tab-money:checked
→ That CSS rule shows the money panel
→ Money articles appear

Everything happens with CSS! It's magic.
```

### Why do this?
1. **Assignment requirement** - No JavaScript allowed
2. **Performance** - Loads faster, no code to download
3. **Reliability** - No bugs, no crashes
4. **Accessibility** - Works with old browsers, screen readers

---

## THE IMAGES (18 Photos)

You have 18 photos from Unsplash showing different tech/AI topics:

| What's in photo | Used for which article |
|-----------------|----------------------|
| Dark bedroom | ChatGPT suicide lullaby |
| Phone with glow | AI chat app leak |
| Secret documents | US cyber chief leak |
| Network cables | Social network for AI agents |
| Gaming setup | Replaced friends with AI |
| Tired person coding | Burned out with AI |
| Terminal screen | cURL spam bounties |
| Multiple screens | YouTube AI spam |
| Science papers | AI spam in research |
| Code editor | AI tool going viral |
| Phone silhouette | Gen Z using AI |
| Robot toys | AI toy exposed kids |
| Protest scene | AI-generated videos |
| Shanghai city | China AI race |
| Lobster | Moltbot weird story |
| Money | OpenAI funding |
| Data center | Gas shortage |
| Computer chip | Nvidia losing to Amazon/Google |

**Problem:** 6 of these photo IDs are UNVERIFIED. Might be wrong.

**Solution:** Use TinEye.com to check each one before submitting.

---

## THE REPORT (What You Wrote)

Your report explains:
1. **What you built** - The website
2. **How you built it** - HTML + CSS technique
3. **Why you chose certain things** - Design decisions
4. **Safety/legal stuff** - Images are copyright-free, fonts are licensed
5. **How it works** - CSS-only interactivity
6. **Screenshots** - Proof it works on desktop + mobile

**Why a report?** Your professor wants to know you UNDERSTAND what you built, not just copied code.

---

## BEFORE YOU SUBMIT (The Checklist)

### ✅ Already Done
- Website is built
- 18 articles are there
- CSS makes it look good
- Report is written
- Screenshots are taken

### ⚠️ Still Need to Do

#### 1. Verify the 6 Unconfirmed Photos
**What to do:** Use TinEye.com
1. Go to TinEye.com
2. Click "Upload Image"
3. Pick each of these 6 photos from your computer:
   - 04-network.jpg
   - 05-gaming.jpg
   - 06-coding-tired.jpg
   - 07-terminal.jpg
   - 08-screens.jpg
   - 10-code-editor.jpg
4. Look at the results
5. Find the Unsplash result
6. Copy the photo ID (last part of URL)
7. Update the link in your footer

**Why?** If a photo ID is wrong, the link is broken. Professor will notice.

---

#### 2. Add Your Student Number
**Where:** In the report file
**What to change:** Replace `[STUDENT NUMBER]` with your actual number

**Why?** Professor needs to know who submitted it

---

#### 3. Upload to Mayar Server
**What's Mayar?** Abertay's server where you host websites

**How to do it:**
1. Connect via SFTP (file transfer)
2. Upload 3 things:
   - `index.html`
   - `css/` folder
   - `images/` folder
3. Test the URL
4. Make sure everything loads

**Why?** Assignment requires it to be hosted somewhere public

---

#### 4. Update Report with Your Mayar URL
**Where:** The report document
**What to add:** Your actual Mayar URL

**Why?** Professor will visit it to check your work

---

#### 5. Convert Report to PDF
**What to do:** Take your markdown file and turn it into a PDF

**Easiest ways:**
- Google Docs: Copy/paste the text, download as PDF
- VS Code extension: "Markdown PDF"
- Command line: `pandoc file.md -o file.pdf`

**Why?** Canvas probably requires PDF format

---

#### 6. Name Everything Correctly
**Report file name:**
```
Report_ShamailaHussain_[STUDENTNUMBER]_Practical1.pdf

Example:
Report_ShamailaHussain_1234567_Practical1.pdf
```

**Code ZIP file name:**
```
ShamailaHussain_[STUDENTNUMBER]_Practical1.zip

Example:
ShamailaHussain_1234567_Practical1.zip
```

**Why the specific names?** Professor's computer automatically sorts by this format.

---

#### 7. Put the Right Stuff in the ZIP
**ZIP should contain:**
```
ShamailaHussain_1234567_Practical1.zip
├── index.html (main file)
├── css/ (folder with all CSS files)
├── images/ (folder with all images)
└── screenshots/ (folder with test screenshots)
```

**What NOT to put in ZIP:**
- The report PDF (separate file!)
- git stuff
- node_modules (you don't have this)
- Random notes

**Why?** Keeps it organized and professional

---

#### 8. Submit TWO Files on Canvas
**File 1:** The report PDF (alone)
**File 2:** The ZIP file (alone)

**NOT:** Don't put the report inside the ZIP

**Why?** Canvas needs to access the report separately to check it

---

## WHAT WILL THE PROFESSOR LOOK FOR?

### Task 1: HTML Structure
- ✅ Do you have 18+ articles? YES
- ✅ Semantic HTML tags used? YES
- ✅ Proper heading structure? YES
- ✅ Article source references visible? YES
- ✅ HTML commented? YES

### Task 2: CSS Styling
- ✅ Colors used well? YES (6 different color themes)
- ✅ Different fonts? YES (Nunito + Source Serif)
- ✅ Gradients, shadows, transitions? YES
- ✅ CSS is organized? YES (BEM + layers)
- ✅ CSS is commented? YES

### Task 3: Image Gallery
- ✅ Hover effects on images? YES (cards scale up, shadows change)
- ✅ Copyright-free images? YES (Unsplash)
- ✅ Credits visible? YES (footer details)

### Task 4: Mayar Server
- ⏳ Hosted on Mayar? Not yet
- ⏳ Working URL in report? Not yet

### Task 5: Testing
- ✅ Tested on desktop? YES (screenshots)
- ✅ Tested on mobile? YES (screenshots)
- ✅ Documented differences? YES (in report)

---

## COMMON MISTAKES TO AVOID

❌ **Mistake:** Wrong Unsplash IDs
✅ **How to avoid:** Verify all 6 unconfirmed ones with TinEye before submitting

❌ **Mistake:** Forgot to add student number
✅ **How to avoid:** Update the report BEFORE converting to PDF

❌ **Mistake:** Report inside the ZIP file
✅ **How to avoid:** Submit 2 separate files on Canvas

❌ **Mistake:** Wrong filenames
✅ **How to avoid:** Copy the exact format from this guide

❌ **Mistake:** Images don't load on Mayar server
✅ **How to avoid:** Test everything works BEFORE submitting

---

## THE SIMPLE SUMMARY

### What You Built:
A news site that shows 18 AI/tech articles organized by 6 topics, with zero JavaScript.

### How It Works:
- **HTML** = the structure (article card, modal, tabs)
- **CSS** = the styling (colors, animations, layout)
- **No JavaScript** = tabs work with radio buttons, modals work with anchor links

### What You Still Need to Do:
1. Verify 6 photos with TinEye
2. Add student number
3. Upload to Mayar server
4. Convert report to PDF
5. Name files correctly
6. Submit on Canvas

### Why You Built It This Way:
- Assignment says no JavaScript allowed
- BEM naming prevents CSS chaos
- CSS layers prevent conflicts
- Semantic HTML helps accessibility
- Design tokens make changes easy

### How to Pass:
- Verify all image links work
- Make sure Mayar upload works
- Submit correct filenames
- Make sure report is a PDF
- Keep report separate from code

---

**That's literally everything. You got this.** 🌊
