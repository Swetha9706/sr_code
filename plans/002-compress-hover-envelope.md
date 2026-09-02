# 002 — Compress the hover entrance envelope to under 300ms

- **Status**: DONE (applied 2026-08-31, verified in Chrome 151)
- **Commit**: 855562c
- **Severity**: HIGH
- **Category**: Easing & duration
- **Estimated scope**: 2 files, one CSS block each
- **Depends on**: **plan 001 must be applied first.** This plan edits the
  `:hover` / `:focus-visible` timing block that 001 creates. If that block is not
  present, STOP and run 001 first.

## Problem

The hover state is an orchestration of five staggered reveals, and the last one
finishes **420ms** after the pointer arrives:

| element | duration | delay | settles at |
| --- | --- | --- | --- |
| `.card-visuals` (photo fades out) | 280ms | 0 | 280ms |
| `.card-scrim` | 280ms | 0 | 280ms |
| `.card-desc` | 300ms | 60ms | 360ms |
| `.card-motif` | 300ms | 80ms | 380ms |
| `.card-arrow` | 300ms | 120ms | **420ms** |

AUDIT.md, "Easing & duration": *"UI animations stay under 300ms."* And on frequency:
a card hover is hit **tens of times per visit** as a visitor scans the grid, which
AUDIT.md places in the *"Remove or drastically reduce"* band. 420ms is 40% over the
hard ceiling for an interaction at that frequency.

The stagger itself is right and should be kept — AUDIT.md, "Cohesion & tokens", puts
useful stagger at **30–80ms** between items, and the current 60/80/120ms delays are a
slightly-too-wide version of exactly that idea. The fix is to compress, not to
flatten it into a single simultaneous fade.

After plan 001, the values live here (the block 001 inserts after
`.project-card:hover .card-motif, .project-card:focus-visible .card-motif`,
around `index.html:390` / `work.html:309`):

```css
/* current, post-001 */
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

## Target

New envelope: the last element settles at **290ms**, inside the 300ms ceiling. The
stagger tightens from 60/80/120ms to 40/60/90ms — still within AUDIT.md's 30–80ms
guidance, and the ordering (photo → description → motif → arrow) is preserved so the
reveal still reads as a sequence rather than a flash.

| element | duration | delay | settles at |
| --- | --- | --- | --- |
| `.card-visuals` | 200ms | 0 | 200ms |
| `.card-scrim` | 200ms | 0 | 200ms |
| `.card-name` / `.card-cat` colour | 200ms | 0 | 200ms |
| `.card-desc` | 220ms | 40ms | 260ms |
| `.card-motif` | 220ms | 60ms | 280ms |
| `.card-arrow` | 200ms | 90ms | **290ms** |

```css
/* target — replaces the block quoted above in full */
.project-card:hover .card-visuals,
.project-card:focus-visible .card-visuals,
.project-card:hover .card-scrim,
.project-card:focus-visible .card-scrim{
  transition-duration:200ms;
}
.project-card:hover .card-desc,
.project-card:focus-visible .card-desc{
  transition-duration:220ms;
  transition-delay:40ms;
}
.project-card:hover .card-motif,
.project-card:focus-visible .card-motif{
  transition-duration:220ms;
  transition-delay:60ms;
}
.project-card:hover .card-arrow,
.project-card:focus-visible .card-arrow{
  transition-duration:200ms;
  transition-delay:90ms;
}
.project-card:hover .card-name,
.project-card:hover .card-cat,
.project-card:focus-visible .card-name,
.project-card:focus-visible .card-cat{
  transition-duration:200ms;
}
```

## Repo conventions to follow

- Static multi-page site, no build step, CSS embedded per file. The same edit must
  land in **both** `index.html` and `work.html`, byte-identically.
- Durations in ms, matching the page-transition block (`index.html:612-617`).
- Do not touch the easing — the house curve `cubic-bezier(0.22,1,0.36,1)` is set on
  the base rules by plan 001 and is documented in `DESIGN.md`.
- Exemplar of a compressed, deliberately-ordered set of durations already in this
  repo: `--vt-shell:340ms` / `--vt-root:260ms` (`index.html:613-615`) — the shell
  leads, everything else trails it, and the whole thing is bounded.

## Steps

Apply to **`index.html` first, then `work.html`**.

1. Locate the timing block inserted by plan 001 — it begins with the selector list
   `.project-card:hover .card-visuals,` followed by
   `.project-card:focus-visible .card-visuals,` and contains only
   `transition-duration` / `transition-delay` declarations. It sits immediately after
   `.project-card:hover .card-motif, .project-card:focus-visible .card-motif{opacity:1;transform:scale(1)}`.
2. Replace that entire block with the "target" block above, verbatim.
3. Repeat in `work.html`.

## Boundaries

- Do NOT change the base (resting/exit) rules — plan 001 owns those, and the exit
  must stay at 160ms with no delay.
- Do NOT change the easing function anywhere.
- Do NOT reorder the reveal. The sequence photo → description → motif → arrow is
  intentional: the photo has to clear before the text over it is legible.
- Do NOT collapse the stagger to zero. Simultaneous reveal is a different design and
  is not what this plan asks for.
- Do NOT touch the page-transition block, `[data-animate]` scroll reveals, or
  anything in `Projects/*.html`.
- Do NOT add dependencies or a build step.
- If the block from step 1 is absent, plan 001 has not been applied — STOP and report.

## Verification

- **Mechanical**: run
  `node .claude/skills/impeccable/scripts/detect.mjs --json --scope layout index.html work.html`
  if present — expect `[]`.
- **Confirm the envelope** — in DevTools on `index.html`, force `:hover` on a
  `.project-card` (Styles → `:hov` → check `:hover`), then in the console:
  ```js
  const c = document.querySelector('.project-card:hover') || document.querySelector('.project-card');
  for (const sel of ['.card-visuals','.card-desc','.card-motif','.card-arrow']) {
    const el = c.querySelector(sel);
    const s = getComputedStyle(el);
    console.log(sel, s.transitionDuration, s.transitionDelay);
  }
  // expect .card-visuals 0.2s / 0s
  //        .card-desc    0.22s / 0.04s
  //        .card-motif   0.22s / 0.06s
  //        .card-arrow   0.2s,0.2s / 0.09s,0.09s
  ```
  Longest chain = 200ms + 90ms = **290ms**. If any total exceeds 300ms the plan is
  not done.
- **Feel check**: serve locally and open the work grid on both `index.html` and
  `work.html`:
  - Hover a card. The reveal should feel *prompt* — the description should be
    readable almost as soon as you land, not after a beat.
  - The stagger must still be perceptible. If the four elements now appear to arrive
    simultaneously, the delays were dropped rather than compressed — that is a
    regression, not a success.
  - In DevTools → Animations panel at 10% playback, hover once and confirm the
    order is still photo-out → description → motif → arrow.
  - Sweep quickly across all three cards. Combined with plan 001's fast exit, moving
    between neighbours should feel responsive rather than smeared.
- **Done when**: computed entrance timings match the table above, the longest chain
  is 290ms, the stagger order is unchanged, and both files carry identical values.
