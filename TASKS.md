# HEP504 Portfolio Part 1 - Remaining Tasks

## Status: ALMOST COMPLETE

---

## DONE (Website)

- [x] Task 1: HTML structure (18 articles, semantic HTML5, comments)
- [x] Task 2: CSS styling (colors, fonts, gradients, shadows, transitions)
- [x] Task 3: Image gallery (hover effects, copyright-free Unsplash images)
- [x] Task 5: Cross-platform testing (desktop + mobile screenshots in report)
- [x] Image credits visible in footer (18 images listed)
- [x] Source references for news articles (BBC, NYT, Verge, etc.)

## DONE (Report)

- [x] Title page (name, student number placeholder, assessment title)
- [x] URL section (placeholder ready)
- [x] Introduction
- [x] Procedure/Methodology (with code snippets)
- [x] Security & Legal section (copyright, fonts, licensing)
- [x] Conclusion (task-by-task evaluation)
- [x] References (Harvard style, 8 sources)
- [x] Screenshots (5 images in /screenshots folder)
- [x] Word count: ~1075 words (within 900-1100 limit)

---

## TODO (Manual Tasks - YOU Must Do)

### 1. Verify 6 Unsplash URLs (HIGH PRIORITY)

Use TinEye (https://tineye.com/) to reverse image search and find REAL Unsplash URLs for:

| Image File | Current URL (UNVERIFIED) | Action |
|------------|--------------------------|--------|
| `images/articles/04-network.jpg` | `JKUTrJ4vK00` | Verify or find correct |
| `images/articles/05-gaming.jpg` | `m0l5J8Lqnzo` | Verify or find correct |
| `images/articles/06-coding-tired.jpg` | `gUIJ0YszPig` | Verify or find correct |
| `images/articles/07-terminal.jpg` | `4Mw7nkQDByk` | Verify or find correct |
| `images/articles/08-screens.jpg` | `hGV2TfOh0ns` | Verify or find correct |
| `images/articles/10-code-editor.jpg` | `OqtafYT5kTw` | Verify or find correct |

**How to verify:**
1. Go to https://tineye.com/
2. Upload each image file
3. Look for unsplash.com results
4. Copy the photo ID (e.g., `abc123XYZ` from `unsplash.com/photos/abc123XYZ`)
5. Update `index.html` lines 462-468 with correct URLs

**Already verified (12 images):**
- 01-dark-bedroom = `_WwHrHHoaE4`
- 02-phone-dark = `9e9PD9blAto`
- 03-government = `qoU5SsqIHJY`
- 09-papers = `lwGfBjfKW2U`
- 11-lonely-phone = `iZVRrfL_oDQ`
- 12-dinosaur-toy = `alNlyjzup80`
- 13-protest = `OfgYGYBNcB4`
- 14-china = `uKyzXEc2k_s`
- 15-lobster = `BmW-9U2VnqU`
- 16-money = `oW6LlU_VZkc`
- 17-datacenter = `M5tzZtFCOfs`
- 18-chip = `FO7JIlwjOtU`

---

### 2. Add Student Number

Edit `HEP504_Report_Shamaila_Hussain.md` line 5:
```
**Student Number:** [STUDENT NUMBER]
```
Replace `[STUDENT NUMBER]` with your actual student number.

---

### 3. Upload to Mayar Server (Task 4)

Follow "Connecting to your webspace.pdf" from Week 1:

1. Connect via SFTP to mayar.abertay.ac.uk
2. Upload these folders/files:
   - `index.html`
   - `css/` (entire folder)
   - `images/` (entire folder)
3. Test at: `http://mayar.abertay.ac.uk/~[username]/`
4. Verify all images load and CSS works

---

### 4. Update Report with Mayar URL

Edit `HEP504_Report_Shamaila_Hussain.md` lines 13-15:
```
http://mayar.abertay.ac.uk/~[username]/
```
Replace with your actual Mayar URL.

Also update line 114 in the Task 4 section.

---

### 5. Convert Report to PDF

Export markdown to PDF. Options:
- VS Code: "Markdown PDF" extension
- Pandoc: `pandoc report.md -o report.pdf`
- Online: paste into Google Docs and export

---

### 6. Create Submission Files

**File naming (CRITICAL):**

1. **Report file:** 
   ```
   Report_ShamailaHussain_[STUDENTNUMBER]_Practical1.pdf
   ```

2. **Source code zip:**
   ```
   ShamailaHussain_[STUDENTNUMBER]_Practical1.zip
   ```

**Zip contents:**
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

**IMPORTANT:** Report must be submitted SEPARATELY, NOT inside the zip!

---

### 7. Submit on Canvas

Upload TWO files:
1. `Report_ShamailaHussain_[STUDENTNUMBER]_Practical1.pdf`
2. `ShamailaHussain_[STUDENTNUMBER]_Practical1.zip`

Check the box: "This assignment submission is my own, original work"

---

## Quick Checklist Before Submit

- [ ] All 18 Unsplash URLs verified and working
- [ ] Student number added to report
- [ ] Mayar URL added and tested
- [ ] Report converted to PDF
- [ ] Report filename correct
- [ ] Zip filename correct
- [ ] Report NOT inside zip
- [ ] Both files uploaded to Canvas
