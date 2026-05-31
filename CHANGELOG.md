# Changelog

A running log of meaningful updates to the portfolio. Newest entries on top.

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
