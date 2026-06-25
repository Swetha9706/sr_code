# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

This is a static HTML/CSS website with no build steps or dependencies.

- **Local development**: Open any HTML file in a browser (e.g., `open index.html` on macOS, or double-click the file).
- **Live reload**: Not required; simply reload the browser after saving changes.
- **Testing**: No automated tests exist. Verify changes manually in the browser.
- **Linting/formatting**: No linter or formatter configured; maintain consistent HTML/CSS formatting manually.
- **Activity logging**: After making changes, append a brief description to `activity.log` (timestamped) to keep a record of work done.
- **Session logging**: Before ending a session (e.g., before running '/clear'), update `session_log.md` with the session end time and a brief summary, then follow the session close procedure outlined in `session_close.md`.
- **Deployment**:
  - GitHub Pages: Push to the `main` branch; the site deploys automatically to https://swetha9706.github.io/sr_code/
  - cPanel hosting: After pushing to GitHub, log in to cPanel → File Manager → `public_html`, and re-upload the changed file(s), preserving the folder structure.
  - **Important**: Always push changes to the `main` branch only; do not create or push to other branches unless explicitly instructed.
  - **Commit message**: Use clear, concise messages describing the change.

## Codebase Structure

The site is a simple multi-page static site built with plain HTML and CSS. No JavaScript framework or build tool is used.

**Core pages** (all in the repository root):
- `index.html` – Home page
- `aboutme.html` – About Me page
- `work.html` – Project grid overview
- `swethafullportfolio.html` – Full portfolio view

**Project case studies** (located in `/Projects/`):
- `kretha.html` – Krētha case study
- `futurescope_Remix.html` – FutureScope case study
- `sip-scones.html` – Sip & Scones case study
- Images for each case study are stored alongside their HTML files.

**Assets**:
- Root-level images (backgrounds, icons, etc.)
- SVG icons (e.g., `Swipe.svg`)
- Large raster assets (e.g., `Vector.png`)

**Styling**:
- CSS is embedded directly in each HTML file (in `<style>` tags) or linked via external stylesheets if present—inspect individual files to confirm.
- No external CSS framework is used; styling is custom.

**Typical workflow**:
1. Edit the relevant HTML file directly.
2. Preview changes locally by reloading the file in a browser.
3. Append a timestamped note to `activity.log` describing the change.
4. Commit and push changes to GitHub (main branch only).
5. If deploying via cPanel, re-upload the modified file to the corresponding path in `public_html/`.

At the end of each session, follow the session close procedure in `session_close.md` before clearing context (e.g., running '/clear').

There are no build scripts, package managers, or preprocessing steps. All edits are made directly to the source files.