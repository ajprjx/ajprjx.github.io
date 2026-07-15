# Personal Portfolio — Design Spec

**Date:** 2026-07-14
**Repo:** https://github.com/ajprjx/anjx.github.io

---

## Overview

A single-page personal portfolio hosted on GitHub Pages. One `index.html` + `style.css` in the repo root; no build step, no dependencies. Deploys automatically from the `main` branch.

---

## Color & Typography

| Token | Value |
|---|---|
| Background | `#0a0f1e` |
| Card background | `#141929` |
| Accent blue | `#3b82f6` |
| Text primary | `#f1f5f9` |
| Text muted | `#94a3b8` |
| Font | Inter, system-ui, sans-serif |

---

## Layout — Sections (top to bottom)

### 1. Nav (sticky)
- Left: site owner name as a text logo
- Right: anchor links — About · Projects · Contact
- Scrolls smoothly to each section
- Subtle bottom border on scroll

### 2. Hero (full-viewport-height, centered)
- Large display name (`h1`)
- One-line tagline below
- Two CTA buttons: "View Projects" (smooth-scroll to #projects) and "GitHub ↗" (opens profile in new tab)

### 3. About
- Two-column on desktop, stacked on mobile
- Left: 2–3 sentence bio paragraph
- Right: a small card showing 2–3 quick-stat items (e.g., years coding, languages, location) — decorative, easily customisable

### 4. Projects
- Section heading: "Projects"
- 3-column CSS Grid (collapses to 1 column on mobile)
- Each project card:
  - Thumbnail area (fixed-height div, dark blue background with project initials as large muted text — swap in a real screenshot by setting `background-image`)
  - Project name (`h3`)
  - One-line description
  - GitHub icon link (opens repo in new tab)
  - Entire card is clickable (links to GitHub)
- 6 placeholder projects included; user deletes/replaces

### 5. Contact
- Section heading: "Get in Touch"
- Short one-liner prompt
- Centered row of icon-circle buttons: GitHub, Email (mailto), LinkedIn
- Hover effect: soft blue glow ring (`box-shadow`)

### 6. Footer
- Copyright line + "Built with HTML & CSS"

---

## Interactions

- All navigation links: smooth scroll (`scroll-behavior: smooth`)
- Project cards: hover lifts card (`transform: translateY(-4px)`) and brightens border
- Contact icons: hover adds `box-shadow: 0 0 0 3px #3b82f6`

---

## Content Placeholders

All content is clearly marked for replacement:

- `YOUR NAME` — display name
- `YOUR TAGLINE` — hero subtitle
- `YOUR BIO` — about paragraph
- `PROJECT N NAME / DESC / GITHUB URL` — per project
- `YOUR EMAIL`, `YOUR GITHUB URL`, `YOUR LINKEDIN URL`

---

## Deployment

1. `index.html` + `style.css` at repo root
2. GitHub Pages: Settings → Pages → Source: Deploy from branch `main`, folder `/root`
3. Site publishes at `https://ajprjx.github.io/anjx.github.io/`

> **Note:** For a cleaner root URL (`https://ajprjx.github.io/`), the repo must be renamed to `ajprjx.github.io` in GitHub Settings. This is optional — the project-site URL works fine.

---

## Out of Scope

- JavaScript (none used)
- Build tools / bundlers
- Blog / CMS
- Contact form backend
