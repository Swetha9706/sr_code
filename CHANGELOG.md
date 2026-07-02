# Changelog

A running log of meaningful updates to the portfolio. Newest entries on top.

---

## 2026-07-02 — Dark mode, animated burst, hero responsive fixes + Sip & Scones v2

**Files:** `index.html`, `Projects/sip-scones.html`, `Projects/sip-scones-v2.html`

**Dark mode (`index.html`)**
- Added full `[data-theme="dark"]` CSS variable set covering background, borders, text, and pill colours.
- Added sun/moon theme toggle button to the nav (left side).
- Inline script at top of `<body>` reads `localStorage` and applies the theme before first paint, preventing flash. Falls back to `prefers-color-scheme` on first visit.

**Animated sunburst (`index.html`)**
- Replaced the static 8-ray starburst with a 24-ray `burst-sun` that simultaneously spins (7s) and folds flat and back open (3.6s scaleY cycle), from the Claude Design handoff.
- Anchored the burst to the top of the final N in RAMACHANDRAN using an `.n-anchor` inline-block span — burst tracks the letter at all font sizes via `bottom:100%`.
- Hero background image moved to a `::before` pseudo-element at `opacity:.45` so it fades independently of the hero content.

**Responsive fixes (`index.html`)**
- Shifted primary breakpoint from 1024px → 1100px; reduced hero gap from 5rem → 3rem to stop the right column being squeezed on mid-range viewports.
- Fixed burst media queries: the old `right`/`top` overrides were no longer effective after the n-anchor change; now correctly scopes `width`/`height` only, and hides the burst entirely at ≤860px.
- Added 600px breakpoint: shrinks photo, blob, flower; hides squig on large phones.

**Sip & Scones — code quality (`Projects/sip-scones.html`)**
- Renamed `--orange` CSS variable to `--teal` (value was `#387470`, a teal-green).
- Reframed "What comes next" section to "If I built this again" with a first-person reflective intro paragraph.
- Replaced inline `onmouseover`/`onmouseout` JS on CTA buttons with `.cta-btn-primary` / `.cta-btn-secondary` CSS classes.

**Sip & Scones v2 (`Projects/sip-scones-v2.html`)**
- New alternative layout inspired by editorial reference: numbered two-column section rows, comparison table (full-tier vs single-tier), CSS diamond flow diagram, dark full-bleed screens strip, minimal colour palette.

---

## 2026-06-03 — FutureScope Research Methods revamp + landing hero sizing

**Files:** `Projects/futurescope_Remix.html`, `index.html`

**FutureScope — Research Methods (`futurescope_Remix.html`)**
- Replaced the long accordion-driven Method 01 content with tightened narrative copy (objective → approach → quote → key findings) and a single consolidated insight.
- Replaced the competitor `<table>` with a 3-up card grid (HSBC / Mint / YNAB) using name + type chip + pink "Gap" label + one-liner.
- Added a process strip at the top of the section (Survey → Quiz boundary object → Interviews → Synthesis) so the section's shape reads at a glance.
- Method 01 now uses a 2-column narrative layout with a sticky vertical rail on the left (Objective / Approach / Quote / Key findings) and prose on the right.
- Promoted the participant pull-quote to a full-width Playfair italic statement between hairlines.
- Promoted the "core insight" callout to a full-width dark band attached to Method 01 — pink eyebrow, large serif statement, "imagination" emphasized in pink. Acts as the chapter break between Method 01 and Method 02.
- Added a centered synthesis line — *"Most tools count. None help you imagine."* — bridging Method 02 into the Research Question callout.
- Tightened method header so the numeral, "Method" eyebrow, and method name sit on a single horizontal row.
- Section reorder (earlier in the day): Solution moved to after Research Takeaways; Research Question callout reassigned to between Research Methods and Takeaways; alternating `s-white` / `s-alt` background classes adjusted to preserve the stripe pattern.

**Landing page (`index.html`)**
- Reduced hero name and role font sizes (~80% of prior); widened hero column gap from 2rem → 5rem so the headline sits closer to the visual.

**Rollback tag:** `pre-research-methods-revamp-2026-06-03` points at the commit before this work.

---

## 2026-06-01 — Landing page hero graphics motion & layout

**File:** `index.html`  
**Assets added:** `Background.svg`, `Flower.svg`, `Purple sun.svg`, `Swipe.svg`

- Replaced all four inline SVG decorations with external SVG files.
- Added CSS animations: Background blob fades/zooms in on load; Purple sun fades/zooms in; Flower spins slowly (12s loop); Swipe squiggle sways side to side (2.5s loop).
- Repositioned all decorative elements to match reference layout — flower upper-right, purple sun upper-left behind head, swipe lower-right.
- Added `prefers-reduced-motion` override to disable all animations for accessibility.

**Rollback tag:** `pre-hero-motion-2026-06-01` points at the commit before this work.

---

## 2026-05-31 — FutureScope case study restructure

**File:** `Projects/futurescope_Remix.html`

- **Project Brief** — replaced copy with a perception-problem framing: retirement planning treated as a behavior-change problem, not a rational-calculation one.
- **Initial Problem Discovery** — rewrote as "The scale of the problem":
  - 4-stat grid (67% / 52% / 47% / 43%) sourced from agediversity.org, OECD, and the UK Adult Financial Wellbeing Survey 2021.
  - "Why this problem matters" — 3-card layout mapping illustrations to contributing factors (early-planning absence, behavioral biases, advice avoidance).
  - "Six key barriers in the UK" — prose enumeration (psychological, cultural, awareness, digital exclusion, trust, socio-economic).
  - Removed the orphaned commented-out 6-card SVG barriers grid + duplicate `<img>` / `</section>` tags.
- **Research / Takeaways** — restructured from a 2-column grid into a single-column narrative:
  - Framing paragraph → Problem Statement quote → 3 insight paragraphs (imagination gap, anxiety, personalized support) → 3 numbered "central ideas" → Hypothesis callout.
  - Hypothesis moved here from the Project Brief (was duplicated, now lives only with the takeaways).

**Rollback tag:** `pre-futurescope-restructure-2026-05-31` points at the commit before this work.

---

## How to use this file

Every time you finish a meaningful set of changes, add a new dated section at the top with:
- The date in `YYYY-MM-DD` format
- A short title
- Bullets describing what changed and why (not how — the diff already shows that)
- A rollback tag if you created one

Keep entries short. If a change is too small to be worth a bullet, it's too small to log.
