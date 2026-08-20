# Changelog

A running log of meaningful updates to the portfolio. Newest entries on top.

---

## 2026-08-20 — Sip & Scones §01–§02 rewrite: "The Concept", User Needs video split, mp4 video

**File:** `Projects/sip-scones.html` · **New asset:** `Projects/Sip-Scones Assets/lauren-hemmert-jensen-dupe.mp4`

**Sections 01–02 (completing `prompts/sip-scones-sections-1-2-rewrite-prompt.md` against the live file)**
- The prompt originally targeted the since-deleted `sip-scones-v2.html` draft and had only partly landed in the Session-10 merge (only the 93% stat-callout). Applied the missing pieces to the **live** file.
- **§02 → "The Concept"**: replaced the three Design Principles (`.coda`) with the verbatim concept copy, a new `.feature-list` (tiers / drink pairings / own-pace review / stacked-teacup loyalty) and the Bankar & Suresh (2015) closing paragraph; removed the now-dead `.coda` CSS.
- **Band → "biggest concern" pull-quote**: repurposed the guiding-principle `.band` to the verbatim quote, attributed "Team reflection."

**Section 01 — "User Needs" two-column layout**
- Rebuilt Background into a two-column split: portrait **video left**, copy right, matching a supplied reference screenshot.
- Applied the prompt's verbatim §01 copy: headline "What the *atmosphere* taught us about the design" + the Lin & Chen (2022) research paragraphs.
- Removed the nectar 93% `.stat-callout` box (and its CSS); re-integrated the design challenge as an **editorial closer** — hairline top rule + DM Mono "The design challenge" eyebrow + the question in Cormorant italic with "the ritual, aesthetic, or mood" emphasized in Ultraviolet.

**Video**
- Transcoded `lauren-hemmert-jensen-dupe.mov` → **`.mp4`** with macOS `avconvert` (H.264, 1080×1920 portrait, 7.4s, 9.3 MB). `.mov` (QuickTime) doesn't decode in Chrome; mp4 does.
- Rewired `<video>` to `<source>` mp4-primary + `.mov` fallback. Verified in Chrome (localhost): mp4 autoplays, loops, muted, `readyState` 4.

**Housekeeping:** snapped two impeccable-hook-flagged font sizes back onto the DESIGN.md ramp.

_Note: all of the above remains **uncommitted** in the working tree. The latest commit is still `430a2c9` "docs: log Session 10 push + close session 11" (2026-08-18); `main` is level with `origin/main`. Not pushed / not deployed — pending review. The new `.mp4` also needs a cPanel upload to `public_html/Projects/Sip-Scones Assets/` when published._

---

## 2026-08-06 — Design system captured; About page promoted & reworked; Krētha case study restructured (draft)

**Files:** `PRODUCT.md`, `DESIGN.md`, `.impeccable/`, `aboutme.html`, `Projects/kretha-restructured.html`, `Swetha-Ramachandran-Resume.pdf`

**Design system captured (impeccable plugin)**
- Added `PRODUCT.md` (product truth: recruiter-first audience, positioning, real bio, brand commitments).
- Added `DESIGN.md` documenting the Warm Editorial-Minimalist pastel system — "The Soft Playground" north star, Cormorant Garamond / Lora / DM Mono / Self Modern, Paper #FCFBFA + Ultraviolet #5642EA + pastel palette, named rules, and an enumerated `typography.scale`.
- Added `.impeccable/design.json` sidecar (tonal ramps, shadows, motion, component snippets).

**About page (`aboutme.html`)**
- Promoted the on-brand v2 draft into the live file (real bio: iMedhas/Krētha, Goldsmiths, Rage, Remidio, Stirred, Srishti); retired the old Hanken Grotesk/Fraunces design; removed `aboutme-v2.html`.
- Merged the duplicate Contact section and Footer into one Cotton Candy footer (contact CTA + button row, then sign-off + copyright, with a subtle "SR" watermark).
- Converted the auto-scrolling skills marquee into a static wrapping disciplines strip (all labels visible); kept the footer marquee but added pause-on-hover/focus.
- Removed the Dribbble button and the email · instagram · read.cv line.
- Wired the "Resume ↓" button to the new `Swetha-Ramachandran-Resume.pdf` (download) and LinkedIn to `linkedin.com/in/swetharux`.
- Split the single Experience section into **Work Experience** and **Education**.

**Krētha case study (`Projects/kretha-restructured.html` — new draft)**
- Standalone restructure of the case study onto the portfolio design system (replaced the original Playfair/DM Sans/dark/orange with Cormorant/Lora/DM Mono, Paper+Ultraviolet+pastel).
- Skimmable, question-headed format with quick-facts bar, named research methods, a research→decision mapping table, hypothesis band, three solution flows, and reflection.
- Real content only; missing assets/figures flagged inline with `[NEEDS REAL NUMBER]` / `[NEEDS REAL SCREENSHOT]`. Live `Projects/kretha.html` left untouched.

**Tooling**
- Added a shared detector ignore for the documented Elevation shadow `rgba(30,18,10,.14)` in `.impeccable/config.json`; refreshed the `.impeccable/design.json` sidecar.

_Note: all of the above remains uncommitted in the working tree (not pushed / not deployed) pending review._

---

## 2026-08-02 — Full homepage redesign: nav, hero, projects, footer, off-the-clock section

**File:** `index.html`

**Design direction locked in:** Warm Editorial-Minimalist, pastel palette — Paper #FCFBFA, Ultraviolet #5642EA, Cotton Candy #F8D9FF, Ink #141018, Muted #6a6273. Added full spec to `CLAUDE.md`. No pure white or black anywhere.

**Nav**
- Rebuilt top nav: solid Paper background, 26px 44px padding, 1px border.
- Brand wordmark in Cormorant Garamond 24px weight-500; links in DM Mono 13px muted (work, about, journal); ultraviolet pill CTA reading "Chat with me".

**Hero**
- Replaced two-column photo layout with a centered, single-column editorial hero.
- Eyebrow in DM Mono 13px uppercase ultraviolet; name in Self Modern Text 104px weight-400 (switched CDN from Self Modern to Self Modern Text for an upright, non-calligraphic cut); ultraviolet wavy SVG squiggle; tagline in Lora 21px 1.65 line-height muted.

**Projects**
- Project cards (Krētha, FutureScope, Sip & Scones) placed in a single centred column.
- Flanked by two decorative cotton-candy tiles: hand-drawn SVG rainbow (three concentric arcs: #ddd6ec, Nectar, Ultraviolet) top-left; four-petal Nectar flower with Ultraviolet centre bottom-right. Tiles hidden on mobile.

**Off the clock**
- Added a personal section between projects and the footer: 280px portrait placeholder + story block (eyebrow, Cormorant heading, Lora body), centred at max-width 860px.

**Footer**
- Two-part footer: full-width Ultraviolet marquee strip ("THINK WE VIBE? ✦ LET'S MAKE SOMETHING WARM") above a Cotton Candy footer.
- Footer: "Say hello →" in Cormorant Garamond 34px left-aligned; email · instagram · read.cv contact line; "© 2026 — made with paper & ink" bottom-right.

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
