# AGENTS.md

## Site Goal

This repository is being transformed from Jiadong Mao's personal website into the **Jiadong Mao Lab** website. The site should present a lab identity while preserving Jiadong's existing scholarly material and the blog series **Birth of a Naturalist**.

The reference structure is Heejung Shim's lab website, with all comparable pages except Journal Clubs.

## Technical Context

- This is a Quarto website.
- Source pages are `.qmd` files in the repository root and under `blog/`.
- The generated site is written to `docs/`, as configured in `_quarto.yml`.
- GitHub Pages likely serves from `docs/`.
- Do not edit generated `docs/` files by hand unless preserving legacy generated pages that no longer have source files.
- Render with Quarto after source changes. In this environment, Quarto may be available at:
  `/Applications/RStudio.app/Contents/Resources/app/quarto/bin/quarto`

## Current Source Page Map

- `_quarto.yml`: site title, navigation, theme, output directory.
- `index.qmd`: lab homepage.
- `research.qmd`: lab research themes and funded projects.
- `people.qmd`: PI, current members, alumni, joining note.
- `software.qmd`: lab software and related publications.
- `publications.qmd`: publications grouped by year.
- `courses.qmd`: teaching, workshops, short courses, guest lectures.
- `contact.qmd`: contact details and prospective member guidance.
- `blog/index.qmd`: blog listing for **Birth of a Naturalist**.
- `invited.qmd`: existing talks and workshops archive; keep as a secondary page even if not in main navigation.
- `funded-projects.qmd`: existing funded-project page; content has also been folded into `research.qmd`.

## Navigation Plan

The main navigation should remain:

1. Home
2. Research
3. People
4. Software
5. Publications
6. Courses
7. Birth of a Naturalist
8. Contact

Do not add Journal Clubs unless explicitly requested.

## Content Preservation Rules

- Preserve **Birth of a Naturalist** and existing blog post URLs where possible.
- Do not delete old generated blog pages casually. Some old posts may exist only in `docs/blog/posts/...` without corresponding source `.qmd` files.
- Keep `invited.qmd` as an archive of talks/workshops unless the user explicitly asks to remove it.
- Keep `funded-projects.qmd` unless the user explicitly asks to remove or redirect it.
- `media/mao-lab-logo_blue-8.png` is the lab logo. It is currently used as the favicon and homepage logo.
- `media/newUpperBody.jpg` is used for the PI photo on the People page.
- `media/smallHeadShot.jpeg` was deleted before the lab-site reorganization; do not restore it unless the user asks.

## Placeholder Policy

Placeholders are acceptable where lab-specific details are not yet available, but they should be explicit and easy to replace. Current placeholder areas include:

- News items on the homepage.
- Current students, researchers, visitors, and alumni on People.
- Software/package links for Phi-Space, Phi-Space ST, NeighbourNet, phylobar, CellDiffusion, StableMate, DIVAS, and analysis repositories.
- Formal course history.
- University profile, Google Scholar, ORCID, office address, lab GitHub, scholarship links, and postdoc fellowship guidance.

Prefer writing placeholders as short content prompts, not vague filler text.

## Tone and Style

- The site should feel like an academic lab website: clear, restrained, research-focused, and easy to scan.
- Keep the voice warm and interdisciplinary.
- Emphasize statistics, machine learning, biomedical discovery, single-cell and spatial omics, multi-omics integration, and longitudinal clinical/biomedical data.
- Preserve the personal intellectual voice in the blog, but keep the lab pages more institutional and outward-facing.

## Design Notes

- Use Quarto's existing `cosmo` theme unless asked to redesign.
- Keep custom CSS in `styles.css`.
- Avoid heavy decorative design. Use typography, spacing, and simple bordered sections.
- The current logo has substantial internal padding, so it works better as a homepage/logo asset than as a tiny navbar image.
- If a tighter logo file is added later, it can be used in `_quarto.yml` as `navbar.logo`.

## Rendering and Validation

After source edits, render the site:

```sh
/Applications/RStudio.app/Contents/Resources/app/quarto/bin/quarto render
```

If Quarto reports `unable to open database file`, rerun with writable cache paths or outside the sandbox:

```sh
env XDG_CACHE_HOME=/private/tmp/quarto-cache DENO_DIR=/private/tmp/quarto-deno /Applications/RStudio.app/Contents/Resources/app/quarto/bin/quarto render
```

Useful checks:

```sh
git diff --check -- '*.qmd' '*.yml' '*.css'
test -f docs/research.html
test -f docs/people.html
test -f docs/software.html
test -f docs/courses.html
test -f docs/contact.html
test -f docs/blog/index.html
```

`git diff --check` on generated `docs/*.html` may report Quarto-generated trailing whitespace. Do not manually churn generated HTML just to satisfy whitespace checks.

## Generated Output Notes

Quarto may remove generated pages that have no source `.qmd`, such as old `docs/about.html`, `docs/random.html`, or stale top-level figure caches. That is usually acceptable.

Exception: preserve old generated blog posts under `docs/blog/posts/` if they represent existing public blog URLs. If restoring old generated blog pages, also preserve any shared CSS/JS assets they reference, especially:

- `docs/site_libs/bootstrap/bootstrap.min.css`
- `docs/site_libs/quarto-html/quarto-syntax-highlighting.css`

## Future Content Tasks

Good next improvements:

- Replace homepage News placeholder with dated items.
- Add real lab members and alumni.
- Add software links and lab GitHub organization links.
- Add formal course history.
- Add University profile, Google Scholar, ORCID, and office address.
- Consider redirecting or recreating source `.qmd` files for any old blog posts that only exist as generated HTML.
