# Report Writing Prompt

Use this prompt in a new conversation to write the report.

---

## Prompt

```
I need to write a 1000-word university report for my HEP504 Web Development assessment. 

**Read these files first to understand the codebase:**

1. Read /home/adam/projects/personal/the-wave/AGENTS.md (assessment requirements)
2. Read /home/adam/projects/personal/the-wave/report.md (report plan/structure)
3. Read /home/adam/projects/personal/the-wave/decisions.md (design decisions reference)
4. Read /home/adam/projects/personal/the-wave/index.html (full HTML)
5. Read /home/adam/projects/personal/the-wave/css/main.css (CSS architecture)
6. Read /home/adam/projects/personal/the-wave/css/base/tokens.css (design tokens)
7. Read /home/adam/projects/personal/the-wave/css/base/typography.css (fonts)
8. Read /home/adam/projects/personal/the-wave/css/components/cards.css (image gallery)
9. Read /home/adam/projects/personal/the-wave/css/components/modal.css (modals)
10. Read /home/adam/projects/personal/the-wave/css/components/tabs.css (tabs)
11. Read /home/adam/projects/personal/the-wave/css/layout/header.css (nav scroll)

**Then take screenshots using Chrome DevTools MCP:**

1. Open the local site: navigate to file:///home/adam/projects/personal/the-wave/index.html
2. Take desktop screenshot (1280px wide) - full page
3. Take mobile screenshot (390px wide iPhone) - use emulate to set viewport
4. Take screenshot of a card on hover (hover over a story card first)
5. Click a card to open modal, take screenshot
6. Click different tabs, take screenshot showing tab switching

**Then write the report following report.md structure:**

- Title page info (leave student number as placeholder)
- URL section (placeholder for mayar URL)
- Introduction (~100 words): theme, concept, what was built
- Procedure (~600 words): Tasks 1-5 with specific code references
- Security & Legal (~150 words): fair use, copyright
- Conclusion (~150 words): critical evaluation

**Writing style:**
- Simple, direct language (student voice, not AI)
- Specific examples from the actual code
- Reference line numbers when showing code
- Avoid: "comprehensive", "robust", "leverage", "utilizing", "facilitates"
- Use: "I chose", "this works by", "the reason for"

**Output format:**
- Markdown that can be converted to Word/PDF
- Code snippets with file:line references
- [SCREENSHOT: description] placeholders where images go
- Harvard references at the end

Do NOT use the Task tool. Read files directly, take screenshots directly.
```

---

## Screenshot Commands Reference

```
# List pages
mcp_chrome-devtools_list_pages

# Navigate to local file
mcp_chrome-devtools_navigate_page url="file:///home/adam/projects/personal/the-wave/index.html"

# Desktop viewport (1280x800)
mcp_chrome-devtools_emulate viewport={"width": 1280, "height": 800, "deviceScaleFactor": 1}

# Mobile viewport (iPhone 14)
mcp_chrome-devtools_emulate viewport={"width": 390, "height": 844, "deviceScaleFactor": 3, "isMobile": true, "hasTouch": true}

# Take screenshot
mcp_chrome-devtools_take_screenshot filePath="/home/adam/projects/personal/the-wave/screenshots/desktop-full.png" fullPage=true

# Take snapshot to find element UIDs
mcp_chrome-devtools_take_snapshot

# Hover over element
mcp_chrome-devtools_hover uid="[uid from snapshot]"

# Click element
mcp_chrome-devtools_click uid="[uid from snapshot]"
```

---

## Files to Delete After Report Done

- /home/adam/projects/personal/the-wave/decisions.md
- /home/adam/projects/personal/the-wave/report.md
- /home/adam/projects/personal/the-wave/REPORT_PROMPT.md
