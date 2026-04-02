# /add-lesson-plans

You are helping maintain the BioLearn9 self-paced biology training portal. Follow every step below in order. Do not skip steps.

---

## Step 0 — Sync with main

Ensure the working branch is `main` and pull the latest code:

```
git checkout main
git pull origin main
```

If there are uncommitted local changes, stop and tell the user to commit or stash them first.

---

## Step 0a — Confirm file location

Ask the user: **"Have you already moved your new lesson file(s) into the `grade-9/` folder locally? If they're somewhere else, please move them there before continuing."**

Wait for confirmation before proceeding.

---

## Step 1 — Detect new/updated files

Run `Glob` on `grade-9/*.html` and compare against the lesson plan files already linked in `index.html`.

Classify each unlinked or recently-modified file as one of:
- **New plan** — not yet in `index.html`
- **Update to existing plan** — already in `index.html` but the source file has changed

For raw upload files (files whose names don't follow the `bioN-slug.html` convention), note them separately — they'll need to be integrated.

Report what you found to the user and confirm before making any changes.

---

## Step 2 — Update existing lesson plans

For each file that maps to an **existing** plan:

1. Read the file and check it against the minimum BioLearn9 requirements:
   - Must link `../theme.css`
   - Must use `Syne` + `DM Sans` fonts from Google Fonts
   - Must have the standard header (BIOLEARN9 logo + nav links + `.catalog-badge` with correct BIO.X code)
   - Must have the standard footer
   - All nav links must use absolute GitHub Pages URLs
2. Fix only those violations. **Do not change the page's visual theme or color scheme** — if it has a dark theme or custom colors, preserve them.
3. **Dark theme protection:** `theme.css` defines light values for `--bg`, `--text`, `--muted`, `--card`, `--border`, and `--green`. If the page uses a dark theme, its `<style>` block must explicitly override all of these variables in `:root` to prevent theme.css from washing them out. Check that the `:root` block inside `<style>` includes dark values for every variable the page relies on. If any are missing, add them.
4. Save the corrected file.

---

## Step 3 — Integrate new lesson plans

For each **new** file (raw upload or properly named but not yet in `index.html`):

1. If the filename doesn't follow `bioN-slug.html`, determine the correct SOL number and topic slug and rename/copy it accordingly.
2. **Detect the theme:** Before making changes, determine whether the source file uses a dark theme (e.g. `background: #0d1b2a`, `--navy`, dark card backgrounds) or the standard light theme. Check the `body` background color or the `:root` CSS variables.
3. Ensure the file has:
   - `../theme.css` linked in `<head>` (in addition to any custom styles — do not replace custom styles)
   - The correct Google Fonts link: `Syne` + `DM Sans`
   - The standard header with the correct BIO.N badge
   - The standard footer: `Virginia SOL Biology · [Plan Title]`
   - All nav links using absolute GitHub Pages URLs
4. **If the file uses a dark theme:** ensure the `:root` block in `<style>` explicitly overrides every variable that `theme.css` sets to a light value — at minimum: the body background, `--text`, `--muted`, `--card`, `--border`, `--green`. Without these overrides, theme.css will replace dark values with light ones, making light-colored text unreadable on a light background.
5. Save to `grade-9/bioN-slug.html`.

---

## Step 4 — Update index.html

Open `index.html` and make the following changes:

### Plan card
Add a new `.plan-card` inside `<div class="plan-grid">`. Follow this template:

```html
<div class="plan-card">
  <div class="plan-head">
    <div class="plan-title">[Plan Title]</div>
    <div class="plan-grade">Grade 9</div>
  </div>
  <div class="plan-meta">[One-sentence description.]</div>
  <div class="plan-tags">
    <span class="tag blue">BIO.[N]</span>
    <span class="tag green">[X] lessons</span>
    <span class="tag orange">Labs + Quiz</span>
    <span class="tag purple">Self-Paced</span>
  </div>
  <div class="plan-actions">
    <a class="btn btn-primary" href="grade-9/bio[N]-[slug].html">Open Plan</a>
    <a class="btn btn-outline" href="#ov-bio[N]">Overview</a>
  </div>
</div>
```

### Overview card
Add a matching entry inside `<div class="overview-grid">`:

```html
<div id="ov-bio[N]" class="overview-card">
  <h3>[Plan Title] (BIO.[N])</h3>
  <p>[Two-sentence description of content and skills.]</p>
</div>
```

### Order all plan cards
After adding the new card, **reorder all `.plan-card` elements inside `.plan-grid` in ascending BIO.N order** (BIO.1 first, BIO.9 last). Do the same for `.overview-card` elements inside `.overview-grid`.

### Stat chip
Update the "plans live" count in `.quick-stats`:
```html
<div class="stat-chip"><strong>[N]</strong> plans live</div>
```

---

## Step 5 — Commit and push

Stage all changed files and commit:

```
git add -A
git commit -m "add/update lesson plan(s): [list of BIO.N codes changed]"
git push origin main
```

If the push is rejected (remote has new commits), run `git pull --rebase origin main` first, then push again.

Report the final git status to the user and confirm everything is live.
