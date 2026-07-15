# Portfolio Site Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build and deploy a single-page dark-blue personal portfolio to GitHub Pages with a fixed left sidebar and a scrollable right panel containing Projects and Other Works sections.

**Architecture:** Two files at repo root — `index.html` (full page structure) and `style.css` (all styles). No JavaScript, no build step. GitHub Pages serves directly from the `main` branch root.

**Layout:**
- Left sidebar (~280px, sticky full-height): name, role/tagline, bio, contact icon links
- Right main panel (remaining width, scrollable): "Projects" grid then "Other Works" list

**Tech Stack:** HTML5, CSS3 (custom properties, grid, flexbox), GitHub Pages

## Global Constraints

- No JavaScript
- No external dependencies (fonts loaded from system stack: Inter, system-ui, sans-serif)
- All placeholder text is ALL_CAPS_SNAKE_CASE so the user can find-and-replace easily
- Color palette: `--bg: #0a0f1e`, `--bg-card: #141929`, `--accent: #3b82f6`, `--text: #f1f5f9`, `--text-muted: #94a3b8`, `--border: #1e2d45`
- Repo: `/Users/alistairjoseph/Projects/anjx.github.io`

---

### Task 1: Layout scaffold + left sidebar

**Files:**
- Create: `index.html`
- Create: `style.css`

**Interfaces:**
- Produces: two-column page shell with sticky sidebar showing name/bio/contact, and empty `<main>` ready for Task 2

- [ ] **Step 1: Create `index.html`**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>YOUR_NAME</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="layout">

    <aside class="sidebar">
      <div class="sidebar-inner">
        <h1 class="site-name">YOUR_NAME</h1>
        <p class="site-role">YOUR_ROLE</p>
        <p class="site-bio">YOUR_BIO — a short paragraph about who you are, what you build, and what drives you.</p>
        <div class="contact-links">

          <a href="YOUR_GITHUB_URL" target="_blank" rel="noopener" class="icon-btn" aria-label="GitHub">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor">
              <path d="M12 0C5.374 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23A11.509 11.509 0 0112 5.803c1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.566 21.797 24 17.3 24 12c0-6.627-5.373-12-12-12z"/>
            </svg>
          </a>

          <a href="mailto:YOUR_EMAIL" class="icon-btn" aria-label="Email">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <rect x="2" y="4" width="20" height="16" rx="2"/>
              <path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/>
            </svg>
          </a>

          <a href="YOUR_LINKEDIN_URL" target="_blank" rel="noopener" class="icon-btn" aria-label="LinkedIn">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor">
              <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 0 1-2.063-2.065 2.064 2.064 0 1 1 2.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
            </svg>
          </a>

        </div>
      </div>
    </aside>

    <main class="main">
      <!-- Projects and Other Works inserted in later tasks -->
    </main>

  </div>
</body>
</html>
```

- [ ] **Step 2: Create `style.css`**

```css
:root {
  --bg: #0a0f1e;
  --bg-card: #141929;
  --accent: #3b82f6;
  --text: #f1f5f9;
  --text-muted: #94a3b8;
  --border: #1e2d45;
  --sidebar-width: 280px;
  --radius: 12px;
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  color: var(--text);
  font-family: Inter, system-ui, sans-serif;
  line-height: 1.6;
  min-height: 100vh;
}

/* ── Two-column layout ── */
.layout {
  display: grid;
  grid-template-columns: var(--sidebar-width) 1fr;
  min-height: 100vh;
}

/* ── Sidebar ── */
.sidebar {
  position: sticky;
  top: 0;
  height: 100vh;
  overflow-y: auto;
  border-right: 1px solid var(--border);
  padding: 3rem 2rem;
  display: flex;
  flex-direction: column;
}

.sidebar-inner {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
  flex: 1;
}

.site-name {
  font-size: 1.5rem;
  font-weight: 800;
  letter-spacing: -0.02em;
  line-height: 1.2;
}

.site-role {
  font-size: 0.9rem;
  color: var(--accent);
  font-weight: 600;
}

.site-bio {
  font-size: 0.875rem;
  color: var(--text-muted);
  line-height: 1.7;
}

.contact-links {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
  margin-top: auto;
  padding-top: 1.5rem;
}

.icon-btn {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: var(--bg-card);
  border: 1px solid var(--border);
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--text-muted);
  text-decoration: none;
  transition: all 0.2s;
  flex-shrink: 0;
}
.icon-btn:hover {
  color: var(--accent);
  border-color: var(--accent);
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.25);
}
.icon-btn svg { width: 18px; height: 18px; }

/* ── Main panel ── */
.main {
  padding: 3rem;
  overflow-y: auto;
}

/* ── Section headings ── */
.section-title {
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--text-muted);
  text-transform: uppercase;
  letter-spacing: 0.08em;
  font-size: 0.8rem;
  margin-bottom: 1.5rem;
}

/* ── Responsive ── */
@media (max-width: 700px) {
  .layout { grid-template-columns: 1fr; }
  .sidebar { position: static; height: auto; border-right: none; border-bottom: 1px solid var(--border); }
  .contact-links { margin-top: 1rem; padding-top: 0; }
}
```

- [ ] **Step 3: Verify in browser**

```bash
open /Users/alistairjoseph/Projects/anjx.github.io/index.html
```

Expected: dark page, narrow sidebar on the left showing name/role/bio/icons, empty main area on the right.

- [ ] **Step 4: Commit**

```bash
cd /Users/alistairjoseph/Projects/anjx.github.io
git add index.html style.css
git commit -m "feat: add two-column layout and sidebar"
```

---

### Task 2: Projects section

**Files:**
- Modify: `index.html` (add Projects section inside `<main>`)
- Modify: `style.css` (add project grid + card styles)

**Interfaces:**
- Consumes: `.main`, `.section-title` from Task 1
- Produces: `#projects` section with a 2-column card grid; each card has a thumbnail, name, description, and links to GitHub

- [ ] **Step 1: Add Projects HTML inside `<main>` in `index.html`**

Replace `<!-- Projects and Other Works inserted in later tasks -->` with:

```html
      <section id="projects">
        <h2 class="section-title">Projects</h2>
        <div class="projects-grid">

          <a class="project-card" href="YOUR_GITHUB_URL/PROJECT_1_REPO" target="_blank" rel="noopener">
            <div class="project-thumb"><span>P1</span></div>
            <div class="project-body">
              <h3>PROJECT_1_NAME</h3>
              <p>PROJECT_1_DESCRIPTION</p>
            </div>
          </a>

          <a class="project-card" href="YOUR_GITHUB_URL/PROJECT_2_REPO" target="_blank" rel="noopener">
            <div class="project-thumb"><span>P2</span></div>
            <div class="project-body">
              <h3>PROJECT_2_NAME</h3>
              <p>PROJECT_2_DESCRIPTION</p>
            </div>
          </a>

          <a class="project-card" href="YOUR_GITHUB_URL/PROJECT_3_REPO" target="_blank" rel="noopener">
            <div class="project-thumb"><span>P3</span></div>
            <div class="project-body">
              <h3>PROJECT_3_NAME</h3>
              <p>PROJECT_3_DESCRIPTION</p>
            </div>
          </a>

          <a class="project-card" href="YOUR_GITHUB_URL/PROJECT_4_REPO" target="_blank" rel="noopener">
            <div class="project-thumb"><span>P4</span></div>
            <div class="project-body">
              <h3>PROJECT_4_NAME</h3>
              <p>PROJECT_4_DESCRIPTION</p>
            </div>
          </a>

        </div>
      </section>

      <!-- Other Works inserted in Task 3 -->
```

- [ ] **Step 2: Add Projects CSS to `style.css`** (append before the `@media` block)

```css
/* ── Projects ── */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.25rem;
  margin-bottom: 3.5rem;
}

.project-card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  overflow: hidden;
  text-decoration: none;
  color: var(--text);
  display: block;
  transition: transform 0.2s, border-color 0.2s;
}
.project-card:hover { transform: translateY(-3px); border-color: var(--accent); }

.project-thumb {
  height: 130px;
  background: var(--bg);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 3rem;
  font-weight: 800;
  color: #1e2d45;
  letter-spacing: -0.02em;
  /* Swap in a screenshot:
     background-image: url('img/thumb-project-1.png');
     background-size: cover; background-position: center; */
}

.project-body { padding: 1rem; }
.project-body h3 { font-size: 0.95rem; font-weight: 600; margin-bottom: 0.35rem; }
.project-body p { font-size: 0.8rem; color: var(--text-muted); line-height: 1.5; }
```

Also append to the `@media (max-width: 700px)` block:

```css
  .projects-grid { grid-template-columns: 1fr; }
```

- [ ] **Step 3: Verify**

```bash
open /Users/alistairjoseph/Projects/anjx.github.io/index.html
```

Expected: right panel shows "PROJECTS" label and a 2-column card grid with 4 placeholder cards. Cards lift on hover.

- [ ] **Step 4: Commit**

```bash
cd /Users/alistairjoseph/Projects/anjx.github.io
git add index.html style.css
git commit -m "feat: add projects grid"
```

---

### Task 3: Other Works section + final responsive polish

**Files:**
- Modify: `index.html` (add Other Works section)
- Modify: `style.css` (add other-works styles + responsive finalisation)

**Interfaces:**
- Consumes: `.main`, `.section-title`, `.projects-grid` margin-bottom from Tasks 1–2
- Produces: `#other-works` section as a compact item list below Projects; page fully responsive at ≤700px

- [ ] **Step 1: Add Other Works HTML to `index.html`**

Replace `<!-- Other Works inserted in Task 3 -->` with:

```html
      <section id="other-works">
        <h2 class="section-title">Other Works</h2>
        <ul class="works-list">

          <li class="work-item">
            <a href="YOUR_GITHUB_URL/OTHER_1_REPO" target="_blank" rel="noopener">
              <span class="work-name">OTHER_1_NAME</span>
              <span class="work-desc">OTHER_1_DESCRIPTION</span>
            </a>
          </li>

          <li class="work-item">
            <a href="YOUR_GITHUB_URL/OTHER_2_REPO" target="_blank" rel="noopener">
              <span class="work-name">OTHER_2_NAME</span>
              <span class="work-desc">OTHER_2_DESCRIPTION</span>
            </a>
          </li>

          <li class="work-item">
            <a href="YOUR_GITHUB_URL/OTHER_3_REPO" target="_blank" rel="noopener">
              <span class="work-name">OTHER_3_NAME</span>
              <span class="work-desc">OTHER_3_DESCRIPTION</span>
            </a>
          </li>

          <li class="work-item">
            <a href="YOUR_GITHUB_URL/OTHER_4_REPO" target="_blank" rel="noopener">
              <span class="work-name">OTHER_4_NAME</span>
              <span class="work-desc">OTHER_4_DESCRIPTION</span>
            </a>
          </li>

          <li class="work-item">
            <a href="YOUR_GITHUB_URL/OTHER_5_REPO" target="_blank" rel="noopener">
              <span class="work-name">OTHER_5_NAME</span>
              <span class="work-desc">OTHER_5_DESCRIPTION</span>
            </a>
          </li>

        </ul>
      </section>
```

- [ ] **Step 2: Add Other Works CSS to `style.css`** (append before the `@media` block)

```css
/* ── Other Works ── */
.works-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 0;
  border: 1px solid var(--border);
  border-radius: var(--radius);
  overflow: hidden;
}

.work-item a {
  display: flex;
  align-items: baseline;
  gap: 1rem;
  padding: 0.85rem 1.1rem;
  text-decoration: none;
  color: var(--text);
  border-bottom: 1px solid var(--border);
  transition: background 0.15s;
}
.work-item:last-child a { border-bottom: none; }
.work-item a:hover { background: var(--bg-card); }

.work-name {
  font-size: 0.9rem;
  font-weight: 600;
  white-space: nowrap;
  flex-shrink: 0;
}
.work-desc {
  font-size: 0.8rem;
  color: var(--text-muted);
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```

- [ ] **Step 3: Full visual check**

```bash
open /Users/alistairjoseph/Projects/anjx.github.io/index.html
```

Check:
- Sidebar is sticky, shows name/role/bio/icons
- Right panel: "PROJECTS" label + 2-column cards, then "OTHER WORKS" label + list rows
- Hover a project card — lifts, blue border
- Hover a works row — subtle background highlight
- Hover a contact icon — blue glow ring
- Narrow the window below 700px — sidebar stacks above main content, project grid goes 1-column

- [ ] **Step 4: Commit**

```bash
cd /Users/alistairjoseph/Projects/anjx.github.io
git add index.html style.css
git commit -m "feat: add other works section and responsive layout"
```

---

### Task 4: Deploy to GitHub Pages

**Files:** None (configuration only)

**Interfaces:**
- Consumes: `main` branch with `index.html` at root
- Produces: live site at `https://ajprjx.github.io/anjx.github.io/`

- [ ] **Step 1: Push to remote**

```bash
cd /Users/alistairjoseph/Projects/anjx.github.io
git push origin main
```

- [ ] **Step 2: Enable GitHub Pages via GitHub CLI**

```bash
gh api repos/ajprjx/anjx.github.io/pages \
  --method POST \
  -f build_type=legacy \
  -f source[branch]=main \
  -f source[path]=/
```

If the call returns a 409 (already exists), skip — Pages is already enabled.

- [ ] **Step 3: Verify Pages status**

```bash
gh api repos/ajprjx/anjx.github.io/pages --jq '.html_url,.status'
```

Expected: a URL and status `built` or `building`. If `building`, wait ~60 s and re-run.

- [ ] **Step 4: Open live site**

```bash
open "$(gh api repos/ajprjx/anjx.github.io/pages --jq '.html_url')"
```

Expected: the deployed portfolio loads at the GitHub Pages URL.
