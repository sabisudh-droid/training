# training

Self-paced biology training plans hosted on GitHub Pages.

## Structure

- `index.html`: Catalog home page that lists all available plans.
- `grade-9/`: Grade 9 plan modules (one HTML per plan).
  - `bio3-cell-structure.html`: BIO.3 Cell Structure & Function module.
  - `photosynthesis_respiration_lesson_final.html`: BIO.5 Photosynthesis & Cellular Respiration module.

## Live Site

- Home page: https://sabisudh-droid.github.io/training/

## How to Add a New Plan

1. Duplicate an existing module in `grade-9/` and rename it (kebab-case preferred).
2. Update the plan content (title, lesson data, videos, assignments, quiz).
3. Add a plan card to `index.html`:
   - Title, grade, short summary
   - Tags (BIO.* alignment, lesson count, labs/quiz, self-paced)
   - Link the **Open Plan** button to the new HTML path (e.g. `grade-9/your-plan.html`)
4. Add a matching entry in the **Plan Overviews** section and update the `Overview` anchor on the card.

## Style Consistency Rules

- Typography: `Syne` for headings, `DM Sans` for body.
- Theme: Dark background, high-contrast text, and neon-accent borders.
- Navigation: `BIOLEARN9` logo always links to the catalog home page.
- Catalog badge: `PLAN CATALOG` links to `#catalog` on the home page.
- Contrast: light text on dark surfaces, dark text on light surfaces.

## Local Preview

Open `index.html` in a browser. Then use the **Open Plan** buttons to navigate to modules in `grade-9/`.

Note: Some embedded video iframes may not load on `file://` URLs. Use GitHub Pages for full functionality.
