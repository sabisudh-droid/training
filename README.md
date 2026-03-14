# BioLearn9

Self-paced biology training plans for 9th grade students, hosted on GitHub Pages.

## Live Site

**https://sabisudh-droid.github.io/training/**

## Structure

```
training_v2/
├── index.html                        ← Catalog home page
├── about.html                        ← Instructor bio
├── contact.html                      ← Contact form
├── theme.css                         ← Shared design system (all pages link this)
├── CLAUDE.md                         ← Authoring guide for adding new plans
└── grade-9/
    ├── bio3-cell-structure.html      ← BIO.3 Cell Structure & Function
    ├── bio4-genetics-heredity.html   ← BIO.4 Genetics & Heredity
    ├── bio5-photosynthesis.html      ← BIO.5 Photosynthesis & Cellular Respiration
    └── bio8-ecology-systems.html     ← BIO.8 Ecology & Systems
```

## How to Add a New Plan

See **CLAUDE.md** for the full step-by-step guide. Short version:

1. Copy `grade-9/bio5-photosynthesis.html` as the starting template and rename it.
2. Update the content (title, SOL standard, videos, slides, vocab, lab, quiz, assignment).
3. Add a plan card to the `plan-grid` in `index.html`.
4. Add a matching entry to the `overview-grid` in `index.html`.

## Style

- **Theme:** Photosynthesis-inspired light theme — `#F0F4F8` background, `#1D9E75` green primary, white cards.
- **Shared styles:** All pages link `theme.css` (root pages) or `../theme.css` (grade-9 pages).
- **Typography:** `Syne` for headings, `DM Sans` for body — loaded via Google Fonts.
- **Navigation:** All nav links use absolute GitHub Pages URLs.
- **Logo:** `BIOLEARN9` always links to `https://sabisudh-droid.github.io/training/`.

## Local Preview

Open `index.html` directly in a browser. Use the **Open Plan** buttons to navigate to modules.

> Some embedded video iframes may not load on `file://` URLs. Use GitHub Pages for full functionality.
