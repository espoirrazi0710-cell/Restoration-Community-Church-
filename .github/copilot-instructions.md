## Purpose
This file gives concise, project-specific guidance for AI coding agents working on this repository (a small static site). Follow these notes when proposing changes, edits, or refactors.

## Quick Architecture Summary
- Static site served from repository root; primary pages: [index.html](index.html) and [about.html](about.html).
- Styles sourced from SASS files in `assets/sass/` and compiled CSS is in `assets/css/` (see `assets/sass/main.scss`).
- JavaScript is plain ES5-style code with jQuery; key files: `assets/js/main.js`, `assets/js/util.js`, `assets/js/jquery.min.js`.
- Images go under `images/` and fonts under `webfonts/`. Repository includes a `CNAME` indicating GitHub Pages deployment.

## Primary workflows (how to test/preview changes)
- Compile SASS locally (if you edit styles):
  - `sass assets/sass:assets/css --no-source-map --style=expanded`
  - or watch during development: `sass --watch assets/sass:assets/css`
- Serve locally to preview HTML/CSS/JS: `python3 -m http.server 8000` then open `http://localhost:8000`.

## Conventions & Patterns (project-specific)
- Prefer editing SASS partials under `assets/sass/` (folders: `base/`, `components/`, `layout/`) rather than changing compiled files in `assets/css/`.
- Note: `index.html` currently contains a large amount of inline CSS. Before changing those rules, check whether equivalent styles exist in `assets/sass/` to avoid duplication.
- Keep the order of JS includes intact in HTML pages: `jquery.min.js` then vendor scripts (`breakpoints.min.js`, `browser.min.js`) then `main.js` and `util.js`.
- Don't rename or move root files (`index.html`, `CNAME`, `LICENSE.txt`) — the site relies on root-relative paths.

## Where to look for examples
- Header layout and navigation: [index.html](index.html) (large inline header styles and nav markup).
- SASS organization: `assets/sass/layout/_header.scss`, `assets/sass/components/_button.scss`, `assets/sass/base/_typography.scss` (use these partials for pattern examples).
- JS interactions for menu toggling: `assets/js/main.js`.

## When modifying code — safe edit checklist
1. If you change styles, modify SASS partials and recompile, not `assets/css/main.css` directly.
2. Run a local server and visually verify responsive behavior (mobile hamburger, dropdowns).
3. Preserve third-party assets and their load order (Google Fonts link, Font Awesome CSS, jQuery).
4. If you change file paths, update all references across HTML pages and `about/` subpages.

## Deployment notes
- This repo appears configured for GitHub Pages (root site, `CNAME`). Deploys expect the site at repository root — avoid generating build artifacts in different folders without coordination.

## Missing automated tooling
- There is no `package.json`, build scripts, or unit tests in the repo. Keep changes minimal and include explicit build instructions in PR descriptions when you add tooling.

## If uncertain
- Ask whether to: (a) update inline CSS in `index.html` or (b) port styles into `assets/sass/` and remove inline overrides.

---
If you want, I can expand this with suggested PR templates or add a tiny `Makefile`/`package.json` to standardize the SASS build and preview workflow.
