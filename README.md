# BioLearn9

Self-paced biology training portal for 9th grade students, hosted on GitHub Pages.

## Live Site

**https://sabisudh-droid.github.io/training/**

## Structure

```
training/
├── index.html                              ← Catalog home page
├── about.html                              ← Instructor bio
├── contact.html                            ← Contact form
├── theme.css                               ← Shared design system (all pages link this)
├── .nojekyll                               ← Disables Jekyll (plain HTML site)
├── CLAUDE.md                               ← Authoring guide for Claude
├── .claude/
│   └── skills/
│       └── add-lesson-plans/
│           └── SKILL.md                   ← /add-lesson-plans skill
└── grade-9/
    ├── bio1-experimental-design.html       ← BIO.1 Experimental Design & Lab Skills
    ├── bio2-biomolecules-enzymes.html      ← BIO.2 Biomolecules & Enzymes
    ├── bio3-cell-structure.html            ← BIO.3 Cell Structure & Function
    ├── bio4-genetics-heredity.html         ← BIO.4 Genetics & Heredity
    ├── bio5-photosynthesis.html            ← BIO.5 Photosynthesis & Cellular Respiration
    ├── bio6-dna-rna-protein-synthesis.html ← BIO.6 DNA, RNA & Protein Synthesis
    ├── bio7-evolution-natural-selection.html ← BIO.7 Evolution & Natural Selection
    ├── bio8-ecology-systems.html           ← BIO.8 Ecology & Systems
    └── bio9-human-body-systems.html        ← BIO.9 Human Body Systems
```

## Lesson Plans (9 live)

| Code | Title | Status |
|------|-------|--------|
| BIO.1 | Experimental Design & Lab Skills | ✅ Live |
| BIO.2 | Biomolecules & Enzymes | ✅ Live |
| BIO.3 | Cell Structure & Function | ✅ Live |
| BIO.4 | Genetics & Heredity | ✅ Live |
| BIO.5 | Photosynthesis & Cellular Respiration | ✅ Live |
| BIO.6 | DNA, RNA & Protein Synthesis | ✅ Live |
| BIO.7 | Evolution & Natural Selection | ✅ Live |
| BIO.8 | Ecology & Systems | ✅ Live |
| BIO.9 | Human Body Systems | ✅ Live |

## Adding a New Lesson Plan

### Option 1 — Use the Claude skill (recommended)

With Claude Code open in this repo, run:

```
/add-lesson-plans
```

The skill will scan `grade-9/` for new files, integrate them into the design system, update `index.html`, and commit + push automatically.

### Option 2 — Manual

See **CLAUDE.md** for the full step-by-step guide. Short version:

1. Copy `grade-9/bio5-photosynthesis.html` as the starting template and rename it `bio[N]-[slug].html`.
2. Update the content (title, SOL standard, videos, slides, vocab, lab, quiz, assignment).
3. Add a plan card to the `plan-grid` in `index.html` (in BIO.N ascending order).
4. Add a matching entry to the `overview-grid` in `index.html`.
5. Update the "plans live" stat chip count.

## Design System

- **Theme:** Light theme — `#F0F4F8` background, `#1D9E75` green primary, white cards.
- **Shared styles:** All pages link `theme.css` — never embed dark-mode `:root` overrides.
- **Typography:** `Syne` for headings, `DM Sans` for body — loaded via Google Fonts.
- **Navigation:** All nav links use absolute GitHub Pages URLs.
- **Template:** `grade-9/bio5-photosynthesis.html` is the canonical reference implementation.

## Local Preview

Open `index.html` directly in a browser. Video iframes require GitHub Pages to load due to browser security restrictions on `file://` URLs.

## Deployment

Pushes to `main` deploy automatically via GitHub Pages. No build step — plain HTML/CSS/JS.
Pages source must be set to **`/ (root)`** (not `/docs`) in repo Settings → Pages.
