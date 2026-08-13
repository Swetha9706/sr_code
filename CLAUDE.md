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
  - **Mandatory after every push**: verify the Pages build succeeded and the live site returns 200, following step 4 of `session_close.md` (Pages builds can fail silently and leave the site at a 404; retrigger the build via the API until it reports `built`).
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

## Frontend Aesthetics

Avoid generic, "AI slop" design. Make creative, distinctive frontends that surprise and delight. Specifically:

**Typography**: Choose fonts that are beautiful, unique, and interesting. Avoid generic families (Arial, Inter, Roboto, system fonts); opt for distinctive choices that elevate the aesthetic.

**Color & Theme**: Commit to a cohesive aesthetic. Use CSS variables for consistency. Dominant colors with sharp accents outperform timid, evenly-distributed palettes. Draw from IDE themes and cultural aesthetics for inspiration.

**Motion**: Use animations for effects and micro-interactions. Prioritize CSS-only solutions. Focus on high-impact moments: one well-orchestrated page load with staggered reveals (`animation-delay`) creates more delight than scattered micro-interactions.

**Backgrounds**: Create atmosphere and depth rather than defaulting to solid colors. Layer CSS gradients, use geometric patterns, or add contextual effects that match the overall aesthetic. Keep backgrounds light — avoid solid dark backgrounds entirely, even as a variation. Depth and atmosphere should come from subtle gradients, texture, or layered light tones, not from darkness.

**Avoid**:
- Solid dark backgrounds, in any section or component
- Overused font families (Inter, Roboto, Arial, Space Grotesk, system fonts)
- Clichéd color schemes (particularly purple gradients on white backgrounds)
- Predictable layouts and component patterns
- Cookie-cutter design that lacks context-specific character

Interpret creatively and make unexpected choices that feel genuinely designed for this specific portfolio context. Vary fonts, textures, and aesthetics within a light overall palette — think outside the box.

## Portfolio — Design Direction (3a: Warm Editorial-Minimalist, pastel)

When building or extending this portfolio, follow this direction. It is warm, restrained, calm, and human — avoid dark-mode, neon, brutalism, dense data-heavy layouts, and stock corporate imagery. **Never use pure white (#ffffff) or pure black (#000000).**

### Layout & structure
- Generous whitespace throughout; nothing cramped.
- Centered, oversized hero with short, confident headline copy ("Hi, I'm ___").
- Asymmetric bento/collage grid for work: mix photography, video stills, and UI screenshots at varied sizes (e.g. one large 2×2 image, a wide accent card, two small icon tiles, a wide motion card) — never uniform equal cards.
- Each work card carries its own accent color/mood; the page shell stays neutral so the work provides the visual "loud" moments.
- Soft rounded corners (~20px) on all cards and buttons; no sharp edges.
- A warm "off the clock" personal section near the footer (casual portrait + a few human lines of story).
- Thin accent-colored marquee strip, then a soft footer with a "Say hello →" CTA.
- Small hand-drawn accents used sparingly for personality: a squiggle underline beneath the hero, a little rainbow, a flower. Keep SVGs to simple primitives (arcs, circles).

### Typography
- **Display — Self Modern**: hero signature name ONLY (fallback: Cormorant Garamond).
- **Editorial serif — Cormorant Garamond**: section headings, nav brand, tagline, card names.
- **Body — Lora**: body text and hero tagline.
- **Utility/data — DM Mono**: nav links, eyebrows, tags, CTAs, card labels.
- Do **NOT** load or reference Playfair Display.
- Headlines oversized and confident, but weight stays light-to-regular — never heavy/bold.

### Color palette (pastel)

| Role | Token | Hex |
|---|---|---|
| Page background | Paper | `#FCFBFA` |
| Surfaces / footer | Cotton Candy | `#F8D9FF` |
| Borders / dividers | — | `#ddd6ec` |
| Primary accent (nav CTA, squiggle, eyebrows, marquee, hover) | Ultraviolet | `#5642EA` |
| Card accent | Highlighter | `#EBF985` |
| Card accent | Nectar | `#FFCAA6` |
| Card accent | Ice Blue | `#D4F5F9` |
| Card accent | Lavender | `#CACAFF` |
| Dark accent / labels on tinted cards | Plum | `#630F49` |
| Primary text | Ink | `#141018` |
| Secondary text | Muted | `#575165` |

Accents are used sparingly against the neutral base — page chrome (nav, shell, footer) stays quiet; only the work cards introduce color to show range.

### Motion & tone
- Smooth scroll-triggered fades and gentle reveals; no snappy or glitchy transitions. Micro-interactions feel unhurried — motion supports calmness.
- Copy is conversational and warm ("Chat with me", "Think we vibe?", "Hi, I'm ___") — approachable over corporate polish.