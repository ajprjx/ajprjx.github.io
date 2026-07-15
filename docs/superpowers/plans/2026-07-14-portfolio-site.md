# Portfolio Site Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build and deploy a single-page dark-blue personal portfolio to GitHub Pages with hero, about, projects grid, and contact icon sections.

**Architecture:** Two files at repo root — `index.html` (full page structure) and `style.css` (all styles). No JavaScript, no build step. GitHub Pages serves directly from the `main` branch root.

**Tech Stack:** HTML5, CSS3 (custom properties, grid, flexbox), GitHub Pages

## Global Constraints

- No JavaScript
- No external dependencies (fonts loaded from system stack: Inter, system-ui, sans-serif)
- All placeholder text is ALL_CAPS_SNAKE_CASE so the user can find-and-replace easily
- Color palette: `--bg: #0a0f1e`, `--bg-card: #141929`, `--accent: #3b82f6`, `--text: #f1f5f9`, `--text-muted: #94a3b8`, `--border: #1e2d45`
- Repo: `/Users/alistairjoseph/Projects/anjx.github.io`

---

### Task 1: HTML scaffold, CSS foundation, Nav, Hero

**Files:**
- Create: `index.html`
- Create: `style.css`

**Interfaces:**
- Produces: working page at `index.html` with sticky nav and full-viewport hero

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

  <nav class="nav">
    <span class="nav-logo">YOUR_NAME</span>
    <ul class="nav-links">
      <li><a href="#about">About</a></li>
      <li><a href="#projects">Projects</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>

  <section class="hero">
    <div class="hero-content">
      <h1 class="hero-name">YOUR_NAME</h1>
      <p class="hero-tagline">YOUR_TAGLINE</p>
      <div class="hero-cta">
        <a href="#projects" class="btn btn-primary">View Projects</a>
        <a href="YOUR_GITHUB_URL" target="_blank" rel="noopener" class="btn btn-secondary">GitHub ↗</a>
      </div>
    </div>
  </section>

  <!-- About, Projects, Contact inserted in later tasks -->

  <footer>
    <p>© 2026 YOUR_NAME · Built with HTML &amp; CSS</p>
  </footer>

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
  --radius: 12px;
  --max-width: 1100px;
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  color: var(--text);
  font-family: Inter, system-ui, sans-serif;
  line-height: 1.6;
}

/* ── Nav ── */
.nav {
  position: sticky;
  top: 0;
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem 2rem;
  background: rgba(10, 15, 30, 0.9);
  border-bottom: 1px solid var(--border);
  backdrop-filter: blur(8px);
}

.nav-logo { font-weight: 700; font-size: 1.1rem; }

.nav-links {
  list-style: none;
  display: flex;
  gap: 2rem;
}

.nav-links a {
  color: var(--text-muted);
  text-decoration: none;
  font-size: 0.9rem;
  transition: color 0.2s;
}
.nav-links a:hover { color: var(--text); }

/* ── Hero ── */
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 2rem;
}

.hero-name {
  font-size: clamp(2.5rem, 8vw, 5rem);
  font-weight: 800;
  letter-spacing: -0.02em;
  margin-bottom: 1rem;
}

.hero-tagline {
  font-size: clamp(1rem, 3vw, 1.3rem);
  color: var(--text-muted);
  margin-bottom: 2.5rem;
}

.hero-cta { display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap; }

.btn {
  display: inline-block;
  padding: 0.75rem 1.75rem;
  border-radius: 8px;
  font-size: 0.95rem;
  font-weight: 600;
  text-decoration: none;
  transition: all 0.2s;
}
.btn-primary { background: var(--accent); color: #fff; }
.btn-primary:hover { background: #2563eb; }
.btn-secondary {
  background: var(--bg-card);
  color: var(--text);
  border: 1px solid var(--border);
}
.btn-secondary:hover { border-color: var(--accent); color: var(--accent); }

/* ── Shared ── */
.container { max-width: var(--max-width); margin: 0 auto; padding: 5rem 2rem; }

.section-title {
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 3rem;
}
.section-title::after {
  content: '';
  display: block;
  width: 40px;
  height: 3px;
  background: var(--accent);
  margin-top: 0.5rem;
}

footer {
  text-align: center;
  padding: 2rem;
  color: var(--text-muted);
  font-size: 0.85rem;
  border-top: 1px solid var(--border);
}
```

- [ ] **Step 3: Verify in browser**

```bash
open /Users/alistairjoseph/Projects/anjx.github.io/index.html
```

Expected: dark page loads, sticky nav at top with name + 3 links, full-viewport hero with name/tagline and two buttons.

- [ ] **Step 4: Commit**

```bash
cd /Users/alistairjoseph/Projects/anjx.github.io
git add index.html style.css
git commit -m "feat: add nav and hero sections"
```

---

### Task 2: About section

**Files:**
- Modify: `index.html` (add About section before footer)
- Modify: `style.css` (add About styles)

**Interfaces:**
- Consumes: `.container`, `.section-title` from Task 1
- Produces: `#about` section with two-column bio + stats layout

- [ ] **Step 1: Add About HTML to `index.html`**

Insert this block between `</section>` (hero close) and `<footer>`:

```html
  <section class="about" id="about">
    <div class="container">
      <h2 class="section-title">About</h2>
      <div class="about-grid">
        <p class="about-bio">YOUR_BIO — a short paragraph about who you are, what you build, and what you care about. Two or three sentences works well here.</p>
        <div class="about-stats">
          <div class="stat">
            <span class="stat-value">N+</span>
            <span class="stat-label">Years coding</span>
          </div>
          <div class="stat">
            <span class="stat-value">X</span>
            <span class="stat-label">Projects shipped</span>
          </div>
          <div class="stat">
            <span class="stat-value">YOUR_CITY</span>
            <span class="stat-label">Location</span>
          </div>
        </div>
      </div>
    </div>
  </section>
```

- [ ] **Step 2: Add About CSS to `style.css`** (append after the `footer` block)

```css
/* ── About ── */
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  align-items: start;
}

.about-bio { color: var(--text-muted); font-size: 1.05rem; line-height: 1.8; }

.about-stats { display: flex; flex-direction: column; gap: 1.5rem; }

.stat { display: flex; flex-direction: column; }
.stat-value { font-size: 2rem; font-weight: 700; color: var(--accent); line-height: 1; }
.stat-label { font-size: 0.85rem; color: var(--text-muted); margin-top: 0.25rem; }
```

- [ ] **Step 3: Verify**

```bash
open /Users/alistairjoseph/Projects/anjx.github.io/index.html
```

Expected: scrolling below hero shows About section with bio text on the left and three stat values on the right.

- [ ] **Step 4: Commit**

```bash
cd /Users/alistairjoseph/Projects/anjx.github.io
git add index.html style.css
git commit -m "feat: add about section"
```

---

### Task 3: Projects section

**Files:**
- Modify: `index.html` (add Projects section)
- Modify: `style.css` (add Projects styles)

**Interfaces:**
- Consumes: `.container`, `.section-title` from Task 1
- Produces: `#projects` 3-column card grid; each card is a full `<a>` link to a GitHub repo

- [ ] **Step 1: Add Projects HTML to `index.html`**

Insert after the closing `</section>` of the About block:

```html
  <section class="projects" id="projects">
    <div class="container">
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

        <a class="project-card" href="YOUR_GITHUB_URL/PROJECT_5_REPO" target="_blank" rel="noopener">
          <div class="project-thumb"><span>P5</span></div>
          <div class="project-body">
            <h3>PROJECT_5_NAME</h3>
            <p>PROJECT_5_DESCRIPTION</p>
          </div>
        </a>

        <a class="project-card" href="YOUR_GITHUB_URL/PROJECT_6_REPO" target="_blank" rel="noopener">
          <div class="project-thumb"><span>P6</span></div>
          <div class="project-body">
            <h3>PROJECT_6_NAME</h3>
            <p>PROJECT_6_DESCRIPTION</p>
          </div>
        </a>

      </div>
    </div>
  </section>
```

- [ ] **Step 2: Add Projects CSS to `style.css`**

```css
/* ── Projects ── */
.projects { background: var(--bg-card); }

.projects-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
}

.project-card {
  background: var(--bg);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  overflow: hidden;
  text-decoration: none;
  color: var(--text);
  display: block;
  transition: transform 0.2s, border-color 0.2s;
}
.project-card:hover { transform: translateY(-4px); border-color: var(--accent); }

.project-thumb {
  height: 140px;
  background: var(--bg-card);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 3.5rem;
  font-weight: 800;
  color: #1e2d45;
  letter-spacing: -0.02em;
  /* Replace placeholder with a screenshot:
     background-image: url('img/thumb-project-1.png');
     background-size: cover;
     background-position: center; */
}

.project-body { padding: 1.25rem; }
.project-body h3 { font-size: 1rem; font-weight: 600; margin-bottom: 0.4rem; }
.project-body p { font-size: 0.875rem; color: var(--text-muted); line-height: 1.5; }
```

- [ ] **Step 3: Verify**

```bash
open /Users/alistairjoseph/Projects/anjx.github.io/index.html
```

Expected: Projects section shows 6 cards in a 3-column grid on a slightly different background. Cards lift on hover.

- [ ] **Step 4: Commit**

```bash
cd /Users/alistairjoseph/Projects/anjx.github.io
git add index.html style.css
git commit -m "feat: add projects grid section"
```

---

### Task 4: Contact section, footer, responsive breakpoints

**Files:**
- Modify: `index.html` (add Contact section)
- Modify: `style.css` (add Contact styles + media queries)

**Interfaces:**
- Consumes: `.container`, `.section-title` from Task 1
- Produces: `#contact` with three icon-circle buttons (GitHub, Email, LinkedIn); mobile layout collapses grids to single column

- [ ] **Step 1: Add Contact HTML to `index.html`**

Insert after the closing `</section>` of the Projects block, before `<footer>`:

```html
  <section class="contact" id="contact">
    <div class="container">
      <h2 class="section-title">Get in Touch</h2>
      <p class="contact-prompt">YOUR_CONTACT_PROMPT — e.g. "Open to opportunities and interesting projects."</p>
      <div class="contact-icons">

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
  </section>
```

- [ ] **Step 2: Add Contact CSS + responsive breakpoints to `style.css`**

```css
/* ── Contact ── */
.contact-prompt {
  color: var(--text-muted);
  margin-bottom: 2.5rem;
  font-size: 1.05rem;
}

.contact-icons { display: flex; gap: 1.25rem; }

.icon-btn {
  width: 52px;
  height: 52px;
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
.icon-btn svg { width: 22px; height: 22px; }

/* ── Responsive ── */
@media (max-width: 768px) {
  .about-grid { grid-template-columns: 1fr; gap: 2rem; }
  .projects-grid { grid-template-columns: 1fr; }
  .nav-links { gap: 1rem; }
}

@media (max-width: 480px) {
  .nav { padding: 1rem; }
  .nav-links { display: none; }
  .container { padding: 3rem 1.25rem; }
}
```

- [ ] **Step 3: Full visual verification**

```bash
open /Users/alistairjoseph/Projects/anjx.github.io/index.html
```

Check:
- Scroll all 4 sections: hero → about → projects → contact
- Hover a project card (lifts + blue border)
- Hover a contact icon (blue glow ring)
- Nav links scroll smoothly to each section
- Resize window narrow — grids collapse to single column

- [ ] **Step 4: Commit**

```bash
cd /Users/alistairjoseph/Projects/anjx.github.io
git add index.html style.css
git commit -m "feat: add contact section and responsive breakpoints"
```

---

### Task 5: Deploy to GitHub Pages

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

If the page already exists (returns 409), it's already enabled — skip.

- [ ] **Step 3: Verify Pages is live**

```bash
gh api repos/ajprjx/anjx.github.io/pages --jq '.html_url,.status'
```

Expected: URL printed (e.g. `https://ajprjx.github.io/anjx.github.io/`) and status `built` or `building`. If `building`, wait ~60 seconds and re-run.

- [ ] **Step 4: Open live site**

```bash
open "$(gh api repos/ajprjx/anjx.github.io/pages --jq '.html_url')"
```

Expected: the deployed portfolio loads in the browser at the GitHub Pages URL.
