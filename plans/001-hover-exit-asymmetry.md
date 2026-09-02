# 001 — Make the project-card hover exit snap instead of lingering

- **Status**: DONE (applied 2026-08-31, verified in Chrome 151)
- **Commit**: 855562c
- **Severity**: HIGH
- **Category**: Interruptibility (asymmetric timing)
- **Estimated scope**: 2 files, ~6 declarations each

## Problem

Every hover transition on the project cards declares its `transition-delay` on the
**base** rule. A `transition-delay` on the base rule applies in **both** directions,
so the delays fire on mouse-*out* as well as mouse-in. Leaving a card, the arrow
waits 120ms doing nothing, then takes 300ms to fade — 420ms before the card is back
at rest. The card feels sticky to leave, and sweeping across the three-card grid
feels laggy because each exit drags.

AUDIT.md, "Interruptibility": *"Asymmetric timing: deliberate phases (press, hold,
destructive confirm) animate slower; the system's response snaps. Symmetric timing
on press-and-release is a finding."* Returning to rest is the system responding —
it should snap.

The same CSS exists in both files (`work.html` was ported verbatim from `index.html`).

```css
/* index.html:248 / work.html:167 — current */
.card-visuals{
  position:absolute;
  inset:0;
  pointer-events:none;
  transition:opacity .28s cubic-bezier(0.22,1,0.36,1);
}
```

```css
/* index.html:282 / work.html:201 — current */
.card-scrim{
  position:absolute;
  inset:0;
  pointer-events:none;
  transition:opacity .28s cubic-bezier(0.22,1,0.36,1);
}
```

```css
/* index.html:312 / work.html:231 — current (inside .card-desc) */
  transition:opacity .3s cubic-bezier(0.22,1,0.36,1) .06s;
```

```css
/* index.html:364 / work.html:283 — current (inside .card-arrow) */
  transition:opacity .3s ease .12s,transform .3s ease .12s;
```

```css
/* index.html:385-386 / work.html:304-305 — current (inside .card-motif) */
  transition:opacity .3s cubic-bezier(0.22,1,0.36,1) .08s,
             transform .3s cubic-bezier(0.22,1,0.36,1) .08s;
```

```css
/* index.html:342 and :354 / work.html:261 and :273 — current
   (inside .card-name and .card-cat respectively) */
  transition:color .28s cubic-bezier(0.22,1,0.36,1);
```

## Target

CSS resolves a transition from the **destination** state's computed style. So the
`:hover` / `:focus-visible` rule governs the *entrance*, and the base rule governs
the *exit*. Split them: base rules get a fast, delay-free exit; the hover rules
carry today's entrance durations and delays unchanged.

**This plan does not change how the hover looks going in.** It only makes coming
back out fast. Plan 002 retunes the entrance.

Exit value for every property: **160ms, no delay**, easing `cubic-bezier(0.22,1,0.36,1)`.
160ms is the fast end of AUDIT.md's "Button press feedback 100–160ms" band — the
right register for "the system responding".

```css
/* target — base rules (exit) */
.card-visuals{
  position:absolute;
  inset:0;
  pointer-events:none;
  transition:opacity 160ms cubic-bezier(0.22,1,0.36,1);
}

.card-scrim{
  /* …unchanged position/inset/pointer-events… */
  transition:opacity 160ms cubic-bezier(0.22,1,0.36,1);
}

/* inside .card-desc */
  transition:opacity 160ms cubic-bezier(0.22,1,0.36,1);

/* inside .card-arrow — note: bare `ease` is replaced by the house curve.
   AUDIT.md: bare `ease` on an entrance is a finding; entering elements use ease-out. */
  transition:opacity 160ms cubic-bezier(0.22,1,0.36,1),
             transform 160ms cubic-bezier(0.22,1,0.36,1);

/* inside .card-motif */
  transition:opacity 160ms cubic-bezier(0.22,1,0.36,1),
             transform 160ms cubic-bezier(0.22,1,0.36,1);

/* inside .card-name and .card-cat */
  transition:color 160ms cubic-bezier(0.22,1,0.36,1);
```

```css
/* target — NEW block, placed immediately after the existing
   `.project-card:hover .card-motif, .project-card:focus-visible .card-motif{...}`
   rule (index.html:388-389 / work.html:307-308).
   These carry the entrance timing that the base rules used to hold. */

/* Entering: each element keeps the duration and stagger it had before.
   The base rules above own the exit, which is uniformly 160ms with no delay. */
.project-card:hover .card-visuals,
.project-card:focus-visible .card-visuals,
.project-card:hover .card-scrim,
.project-card:focus-visible .card-scrim{
  transition-duration:280ms;
}
.project-card:hover .card-desc,
.project-card:focus-visible .card-desc{
  transition-duration:300ms;
  transition-delay:60ms;
}
.project-card:hover .card-motif,
.project-card:focus-visible .card-motif{
  transition-duration:300ms;
  transition-delay:80ms;
}
.project-card:hover .card-arrow,
.project-card:focus-visible .card-arrow{
  transition-duration:300ms;
  transition-delay:120ms;
}
.project-card:hover .card-name,
.project-card:hover .card-cat,
.project-card:focus-visible .card-name,
.project-card:focus-visible .card-cat{
  transition-duration:280ms;
}
```

## Repo conventions to follow

- This is a **static multi-page site with no build step**. CSS is embedded in a
  single `<style>` block per HTML file. There is no stylesheet to share — the same
  edit must be made in both `index.html` and `work.html`, byte-identically.
- The house easing curve is `cubic-bezier(0.22,1,0.36,1)`, documented in `DESIGN.md`
  ("Do keep motion gentle and unhurried — `cubic-bezier(0.22,1,0.36,1)`"). Write it
  literally. Do **not** introduce an `--ease` token in this plan; token consolidation
  is a separate, unselected finding.
- Exemplar of the pattern this plan introduces — the page-transition block already
  separates timing from the thing being animated using its own custom properties
  (`index.html:612-617`, `--vt-shell` / `--vt-title` / `--vt-root`). Follow the same
  instinct: timing lives with the state that owns it.
- Existing durations in this file are written in both `.28s` and `340ms` forms. Use
  **ms** for everything this plan adds, matching the newer page-transition block.

## Steps

Apply every step to **`index.html` first, then `work.html`**. The CSS is identical
in both; only the line numbers differ.

1. `.card-visuals` — replace `transition:opacity .28s cubic-bezier(0.22,1,0.36,1);`
   with `transition:opacity 160ms cubic-bezier(0.22,1,0.36,1);`
   (`index.html:248`, `work.html:167`).
2. `.card-scrim` — same replacement (`index.html:282`, `work.html:201`).
3. `.card-desc` — replace `transition:opacity .3s cubic-bezier(0.22,1,0.36,1) .06s;`
   with `transition:opacity 160ms cubic-bezier(0.22,1,0.36,1);` — note the delay is
   **removed** (`index.html:312`, `work.html:231`).
4. `.card-arrow` — replace `transition:opacity .3s ease .12s,transform .3s ease .12s;`
   with:
   ```css
   transition:opacity 160ms cubic-bezier(0.22,1,0.36,1),
              transform 160ms cubic-bezier(0.22,1,0.36,1);
   ```
   (`index.html:364`, `work.html:283`).
5. `.card-motif` — replace the two-line
   `transition:opacity .3s cubic-bezier(0.22,1,0.36,1) .08s, transform .3s … .08s;`
   with the same two properties at `160ms` and **no delay**
   (`index.html:385-386`, `work.html:304-305`).
6. `.card-name` and `.card-cat` — replace
   `transition:color .28s cubic-bezier(0.22,1,0.36,1);` with
   `transition:color 160ms cubic-bezier(0.22,1,0.36,1);`
   (`index.html:342` and `:354`; `work.html:261` and `:273`).
7. Insert the entire "target — NEW block" from the Target section immediately after
   the `.project-card:hover .card-motif, .project-card:focus-visible .card-motif`
   rule (`index.html:388-389`, `work.html:307-308`).

## Boundaries

- Do NOT touch `Projects/*.html`, `aboutme.html`, or `swethafullportfolio.html`.
- Do NOT touch the page-transition block (`@view-transition`, `--vt-*`,
  `::view-transition-*`) — that motion is deliberate and documented.
- Do NOT touch `[data-animate]` scroll-reveal timing (`index.html:539-543`) — the
  600ms reveal and 80ms stagger are a documented `DESIGN.md` decision.
- Do NOT change markup, colours, layout, or any non-motion property.
- Do NOT add an `--ease` token or otherwise consolidate curves — separate finding.
- Do NOT change the entrance durations/delays; this plan preserves them exactly
  (280/300ms and 60/80/120ms delays). Plan 002 retunes them.
- Do NOT add dependencies. There is no build step; do not introduce one.
- If the code at a cited line does not match the excerpt above, STOP and report.

## Verification

- **Mechanical**: no build or typecheck exists. Run
  `node .claude/skills/impeccable/scripts/detect.mjs --json --scope layout index.html work.html`
  if present — expect `[]`. Then confirm both files still parse: open each in a
  browser and check the console is free of CSS errors, and that
  `document.styleSheets[…].cssRules` enumerates without throwing.
- **Confirm the split actually took effect** — paste in DevTools console on
  `index.html`:
  ```js
  const c = document.querySelector('.project-card');
  const a = c.querySelector('.card-arrow');
  getComputedStyle(a).transitionDuration;  // expect "0.16s, 0.16s"  (resting/exit)
  getComputedStyle(a).transitionDelay;     // expect "0s, 0s"        (no exit delay)
  ```
  Then force the hover state (DevTools → Styles → `:hov` → check `:hover` on
  `.project-card`) and re-read: expect `0.3s, 0.3s` and `0.12s, 0.12s`.
- **Feel check**: serve locally (`python3 -m http.server 8123`), open
  `http://localhost:8123/index.html`, scroll to the work grid and:
  - Hover a card, then move the pointer off it. The photo should come back and the
    description/arrow/motif should clear **noticeably faster than they arrived**.
    Before this change they took the same 420ms both ways.
  - Sweep the pointer quickly left-to-right across all three cards. Each card should
    return to rest almost immediately behind the pointer — no trail of half-faded
    cards following you.
  - In DevTools → Animations panel, set playback speed to 10%, hover a card and then
    leave. Confirm on exit that **nothing waits** before it starts moving.
  - Repeat the whole check on `http://localhost:8123/work.html` — the grid there must
    behave identically.
- **Done when**: exit is 160ms with zero delay on all six properties, entrance is
  visually unchanged from before the edit, and `index.html` and `work.html` contain
  byte-identical card CSS (verify by diffing the two card blocks).
