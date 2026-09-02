# Animation plans — project card grid

Produced by `/improve-animations` against the hover and page-transition motion on the
project card grid. Audit commit: **855562c**.

All four plans touch the **same two files** — `index.html` and `work.html` — which
carry byte-identical card CSS because `work.html` was ported from `index.html`. Every
plan must be applied to both files or the two pages will drift.

## Plans

| # | Title | Severity | Category | Status |
| --- | --- | --- | --- | --- |
| [001](001-hover-exit-asymmetry.md) | Make the project-card hover exit snap instead of lingering | HIGH | Interruptibility | DONE |
| [002](002-compress-hover-envelope.md) | Compress the hover entrance envelope to under 300ms | HIGH | Easing & duration | DONE |
| [003](003-gate-hover-to-fine-pointers.md) | Gate the card hover state behind a fine-pointer media query | MEDIUM-HIGH | Accessibility | DONE |
| [004](004-bloom-rotate-not-transform.md) | Stop the bloom spin from clobbering its own scale-in | MEDIUM | Interruptibility | DONE |

## Recommended execution order

**001 → 002 → 003 → 004.** All four were applied in this order on 2026-08-31
(commit 855562c working tree) and verified in Chrome 151. Measured results:
exit 160ms with no delay on all six properties; entrance envelope 200/200/260/280/290ms
(longest chain 290ms, under the 300ms ceiling); six `:hover` rules gated with none
escaping; the bloom motif now reports `CSSTransition/transform` alongside its
`CSSAnimation`, with `transform: matrix(0.92,…)` at hover start and `rotate: 73.6deg`
once spinning.

## Dependencies

- **002 depends on 001.** Plan 001 restructures the hover transitions so the base rule
  owns the exit and a new `:hover` block owns the entrance. Plan 002 edits only that
  new block. Running 002 first has nothing to edit.
- **004 reads a value that 002 sets.** Plan 004 adds `animation-delay` to the bloom
  spin, matched to the motif's entrance delay — `60ms` after 002, `80ms` before it.
  The plan states both, so 004 can run at any point, but running it after 002 avoids
  a follow-up edit.
- **003 is independent** of the other three and can be applied at any point in the
  order. It is sequenced third only because it is a pure selector move and is easiest
  to review once the timing values have stopped changing.
- **001, 002 and 004 all touch rules near `index.html:384-408`.** Apply them one at a
  time and re-read the file between plans rather than batching the edits.

## Follow-up closed after execution

Plans 003 and 004 each scoped the bloom-spin rule out (003 deferred it to 004; 004
changed only the animated property), which left `.project-card:hover .card-motif--bloom`
as the one visual hover rule still ungated. Closed on 2026-08-31 by splitting it the
same way as the other six: `:focus-visible` stays under
`@media(prefers-reduced-motion:no-preference)`, and the `:hover` half moved to
`@media (prefers-reduced-motion: no-preference) and (hover: hover) and (pointer: fine)`.
Verified: seven gated hover rules, `ungatedVisualHover: []`.

## What these plans deliberately do not change

Recorded so a future audit does not re-report them:

- **Page-transition timing** (`--vt-shell:340ms`, `--vt-root:260ms`,
  `::view-transition-old(root){animation:none}`, `index.html:612-638`) — deliberate
  and documented in the source comments.
- **`[data-animate]` scroll reveals** (600ms, 80ms stagger, `index.html:539-543`) —
  a documented `DESIGN.md` decision; the 80ms stagger is already inside the 30–80ms
  guidance.
- **The house easing curve** `cubic-bezier(0.22,1,0.36,1)` — documented in
  `DESIGN.md`. AUDIT.md prefers a slightly stronger `cubic-bezier(0.23,1,0.32,1)`, but
  the repo's own curve is a settled decision and these plans keep it.

## Known findings with no plan yet

From the same audit, not selected for planning:

- **Token consolidation** — the house curve is hand-typed 10× in `index.html` while an
  identical value sits in `--vt-ease` (`index.html:616`), and the case studies define
  the same value as `--ease` (`Projects/kretha.html:33`). MEDIUM, mechanical.
- **Reduced motion does not cover the grid's movement** — `.card-motif`'s
  `scale(.92)→1` and `.card-arrow`'s `translateX(-6px)` still animate under
  `prefers-reduced-motion: reduce`. MEDIUM, small.
- **Hover crossfade double-exposes** — the photo and the description are both near 50%
  mid-transition; AUDIT.md suggests masking with `filter: blur(2px)`. LOW, needs a
  feel-check before committing to it.
- **`:active` scale vs. view-transition snapshot** — `.project-card:active{transform:scale(.985)}`
  (`index.html:643`) is applied at the instant the card is snapshotted as `case-shell`.
  Whether the 0.985 gets baked into the snapshot needs frame-by-frame confirmation.
  LOW, uncertain.
- **Out of scope of the grid**: `.hamburger span{transition:all .25s}`
  (`index.html:71`) — `transition: all` is always a finding.
