# BioLearn9 — Claude Instructions

Self-paced biology training portal for 9th grade students, hosted on GitHub Pages at:
**https://sabisudh-droid.github.io/training/**

---

## Project Structure

```
training_v2/
├── index.html          ← Catalog home page (lists all lesson plans)
├── about.html          ← Instructor bio page
├── contact.html        ← Contact form (mailto: integration)
├── theme.css           ← Shared design system — ALL pages link this
├── CLAUDE.md           ← This file
├── artifacts/
│   └── 1516655843740.jpeg   ← Instructor profile photo
└── grade-9/
    ├── bio3-cell-structure.html
    ├── bio4-genetics-heredity.html
    ├── bio5-photosynthesis.html    ← Reference template for new plans
    └── bio8-ecology-systems.html
```

---

## Design System

All pages share a **photosynthesis-inspired light theme** defined in `theme.css`.

### Key CSS Variables (from `theme.css`)

| Variable | Value | Use |
|---|---|---|
| `--green` | `#1D9E75` | Primary accent, buttons, highlights |
| `--gd` | `#085041` | Dark green — headings, logo, sidebar bg |
| `--gm` | `#9FE1CB` | Mid green — gradients, badges |
| `--gl` | `#E1F5EE` | Light green — tag backgrounds, hover states |
| `--bg` | `#F0F4F8` | Page background |
| `--surface` | `#F8FAFC` | Secondary surface (header bg, input bg) |
| `--card` | `#ffffff` | Card background |
| `--border` | `#E2E8F0` | Borders and dividers |
| `--text` | `#1A202C` | Primary body text |
| `--muted` | `#64748B` | Secondary/subdued text |
| `--shadow` | `0 2px 8px rgba(0,0,0,.07)` | Card shadow |
| `--shadow-md` | `0 4px 16px rgba(0,0,0,.1)` | Hover/elevated shadow |
| `--blue` | `#378ADD` | Secondary accent |
| `--amber` | `#BA7517` | Tertiary accent |
| `--purple` | `#534AB7` | Quaternary accent |
| `--coral` | `#D85A30` | Extra accent |

### Typography

- **Headings:** `Syne` (weight 400/600/700/800)
- **Body:** `DM Sans` (weight 300/400/500)
- Both loaded via Google Fonts — include this in every page's `<head>`:

```html
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
```

### Standard Header (every page must use this)

```html
<header>
  <div class="top-bar">
    <a class="logo" href="https://sabisudh-droid.github.io/training/">BIOLEARN<span>9</span></a>
    <div class="nav-links">
      <a class="nav-link" href="https://sabisudh-droid.github.io/training/">Catalog</a>
      <a class="nav-link" href="https://sabisudh-droid.github.io/training/about.html">About</a>
      <a class="nav-link" href="https://sabisudh-droid.github.io/training/contact.html">Contact</a>
      <a class="catalog-badge" href="https://sabisudh-droid.github.io/training/#catalog">BIO.X</a>
    </div>
  </div>
</header>
```

- Replace `BIO.X` with the plan's SOL code (e.g. `BIO.6`).
- All nav links use **absolute GitHub Pages URLs** on every page — both root-level and `grade-9/` pages. This ensures navigation works correctly regardless of where the file is opened.

### Standard Footer (every page)

```html
<footer>
  Virginia SOL Biology · [Page Title]
</footer>
```

---

## How to Add a New Lesson Plan

Follow these steps **in order**.

### Step 1 — Create the lesson plan HTML file

1. Copy `grade-9/bio5-photosynthesis.html` as the starting template (it is the cleanest reference implementation).
2. Rename it using kebab-case: `grade-9/bio[N]-[topic-slug].html`
   Example: `grade-9/bio6-evolution.html`
3. In the new file's `<head>`:
   - Update `<title>` to match the new plan name.
   - Keep both `<link>` tags (Google Fonts + `../theme.css`).
4. Update the **header** badge text from `BIO.5` to the new SOL code.
5. Update the **hero section**: title, subtitle, Virginia SOL standard tags.
6. Replace all lesson content (videos, slides, vocab, lab, quiz, assignment) with the new plan's material.
7. Keep all interactive JavaScript (tab switching, progress bar, quiz logic, lab simulation) — only update the data inside it.

### Step 2 — Add the plan card to `index.html`

Open `index.html` and find the `<div class="plan-grid">` section. Add a new `.plan-card` **before** the "coming-soon" cards:

```html
<div class="plan-card">
  <div class="plan-head">
    <div class="plan-title">[Plan Title]</div>
    <div class="plan-grade">Grade 9</div>
  </div>
  <div class="plan-meta">[One-sentence description of what students learn.]</div>
  <div class="plan-tags">
    <span class="tag blue">BIO.[N]</span>
    <span class="tag green">[X] lessons</span>
    <span class="tag orange">Labs + Quiz</span>
    <span class="tag purple">Self-Paced</span>
  </div>
  <div class="plan-actions">
    <a class="btn btn-primary" href="grade-9/bio[N]-[topic-slug].html">Open Plan</a>
    <a class="btn btn-outline" href="#ov-bio[N]">Overview</a>
  </div>
</div>
```

If the plan is not yet ready, wrap it in `<div class="plan-card coming-soon">` and replace the `<a>` button with `<span class="btn btn-primary">Coming Soon</span>`.

### Step 3 — Add the plan overview card to `index.html`

Find the `<div class="overview-grid">` section and add:

```html
<div id="ov-bio[N]" class="overview-card">
  <h3>[Plan Title] (BIO.[N])</h3>
  <p>[Two-sentence description of content and skills covered.]</p>
</div>
```

The `id` must match the `href="#ov-bio[N]"` anchor on the plan card.

### Step 4 — Update the stat chip in `index.html` (optional)

In the `.quick-stats` row at the top of the hero, update the "plans live" count:

```html
<div class="stat-chip"><strong>[N]</strong> plans live</div>
```

---

## Tag Color Conventions (index.html plan cards)

| Tag class | Meaning |
|---|---|
| `tag blue` | SOL standard code (BIO.1, BIO.3 …) |
| `tag green` | Lesson count or module type |
| `tag orange` | Included activities (Labs, Quiz, Case Studies …) |
| `tag purple` | Delivery format (Self-Paced, Blended …) |

---

## Linking Paths

| File location | Link to `theme.css` | Nav links (About, Contact, Catalog) |
|---|---|---|
| Root (`index.html`, `about.html`, `contact.html`) | `href="theme.css"` | Absolute GitHub Pages URLs |
| `grade-9/` pages | `href="../theme.css"` | Absolute GitHub Pages URLs |

Always use absolute GitHub Pages URLs for nav links so navigation works correctly on GitHub Pages and from local file opens alike.

---

## What NOT to change

- Do not remove the `theme.css` link from any page — it is the single source of truth for the design system.
- Do not reintroduce dark-mode CSS variables (`--bg: #0a0e1a`, `#111827`, etc.) — all pages use the light theme.
- Do not rename CSS variables defined in `theme.css` without updating all pages that use them.
- Do not change the `BIOLEARN9` logo text or its link target without updating every page.
- The photosynthesis page (`bio5-photosynthesis.html`) had dark theme override blocks removed in March 2026 — do not re-add them.

---

## Live Deployment

The site deploys automatically via GitHub Pages on push to the default branch. No build step required — all files are plain HTML/CSS/JS.

Local preview: open `index.html` directly in a browser. Video iframes require GitHub Pages to load due to browser security restrictions on `file://` URLs.
