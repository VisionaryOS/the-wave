---
description: Comment templates that sound like a student explaining their work
---

# Human Comments Skill

Comment patterns that sound authentically human, like a student or junior developer explaining their work.

## The Formula

```
Goal → What I tried → What worked (+ why)
```

## Comment Types by Frequency

| Type | % | Use When |
|------|---|----------|
| Goal-oriented | 25% | Starting a section, explaining intent |
| Learning notes | 20% | CSS concepts you had to look up |
| Informal | 15% | Quick notes, warnings |
| Trial-and-error | 15% | After debugging something |
| Section markers | 10% | Major page sections |
| Frustration | 8% | After long debugging sessions |
| Questions | 5% | Uncertain about approach |
| Attribution | 2% | Code from external sources |

## Goal-Oriented Templates

```css
/* trying to [goal] */
/* trying to make the header stick to the top */
/* trying to get equal-height cards */

/* want [element] to [behavior] */
/* want the nav to shrink on scroll */
/* want buttons to have a subtle bounce */

/* need this to [requirement] */
/* need this to work on mobile */
/* need the modal to trap focus */

/* making [thing] because [reason] */
/* making the hero full-height because it looks better */
```

## Trial-and-Error Templates

```css
/* tried [thing], [result]. [solution] works */
/* tried margin auto, didn't center vertically. flexbox works */
/* tried position fixed, broke the layout. sticky is better */

/* [thing] wasn't working because [reason] */
/* centering wasn't working because parent had no height */
/* hover wasn't working because of z-index stacking */

/* [first attempt] broke [thing], switched to [solution] */
/* absolute positioning broke the footer, switched to grid */
```

## Learning Notes Templates

```css
/* Note: [concept explanation] */
/* Note: padding is INSIDE the border, margin is OUTSIDE */
/* Note: rem is relative to root, em is relative to parent */

/* [thing] = [explanation] */
/* 1fr = one fraction of remaining space */
/* auto-fit = as many columns as will fit */

/* using [thing] because [learning] */
/* using rem so nested elements don't compound weirdly */
/* using grid because flexbox doesn't do equal heights */
```

## Informal Templates

```css
/* don't touch this */
/* don't ask why this works */
/* idk why this fixes it but it does */
/* future me: DO NOT change this */
/* this is hacky but whatever */
/* good enough for now */
/* TODO: make this less janky */
/* works on my machine lol */
```

## Frustration Templates

```css
/* finally got this working */
/* finally after like 3 hours */
/* spent way too long on this */
/* css is pain */
/* why is this so hard */
/* centering shouldn't be this difficult */
/* thank god for grid */
/* flexbox you beautiful thing */
```

## Question Templates

```css
/* is there a better way? */
/* is this the right approach? */
/* should this be a section or div? */
/* not sure if I need this */
/* does this work in Safari? */
/* TODO: ask someone about this */
```

## Section Marker Templates

```css
/* ===== HERO ===== */
/* === Navigation === */
/* --- Cards --- */
/* >> Footer << */
/* ~~~~~~ Modal ~~~~~~ */

/* HERO SECTION */
/* -- hero styles -- */

/* =====================
   NAVIGATION
   sticky, shrinks on scroll
   ===================== */
```

## Attribution Templates

```css
/* from [source] */
/* from css-tricks */
/* from that kevin powell video */
/* stackoverflow said to do this */
/* yoinked from codepen */
/* based on the tailwind docs */
/* copied from [project name] */
```

## Time Markers (Authenticity Boosters)

```css
/* 2am and this finally works */
/* been at this all day */
/* spent the whole morning on this */
/* quick fix before lunch */
/* friday afternoon hack */
```

## CSS-Specific Comment Triggers

| When you see... | Comment about... |
|-----------------|------------------|
| `display: flex` | centering struggles, IE11 |
| `display: grid` | equal heights, auto-fit confusion |
| `position: sticky` | scroll behavior, parent overflow |
| `z-index` | stacking context pain |
| `transform: translate(-50%, -50%)` | centering hack |
| `min-height: 100vh` | mobile viewport issues |
| `gap` | old flexbox gap support |
| `clamp()` | fluid typography learning |

## What NOT to Write

```css
/* BAD: AI tells */
/* This CSS sets the display to flex */
/* The following creates a responsive grid */
/* As you can see, we use flexbox here */
/* Let me explain how this works */
/* This section contains the navigation */
/* The button component utilizes... */

/* BAD: Over-formal */
/* This property declaration establishes... */
/* The aforementioned selector targets... */
/* Implementation note: The following... */
```

## Density Guidelines

- **~1 comment per 10-20 lines** (sparse)
- **Not every block needs a comment**
- **More comments in tricky sections** (centering, z-index, positioning)
- **Fewer comments in obvious sections** (basic typography, colors)
- **Comments cluster around problem areas**

## Authenticity Checklist

- [ ] Mix of lowercase and capitalized
- [ ] Some fragments, not all full sentences
- [ ] Abbreviations (idk, lol, w/, bc)
- [ ] Time references (finally, after hours)
- [ ] Emotional words (pain, annoying, beautiful)
- [ ] Questions and uncertainty
- [ ] References to external learning sources
- [ ] Some TODO/FIXME items
- [ ] Occasional profanity (bs, damn, wtf)
