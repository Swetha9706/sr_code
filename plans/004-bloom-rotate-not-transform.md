# 004 — Stop the bloom spin from clobbering its own scale-in

- **Status**: DONE (applied 2026-08-31, verified in Chrome 151)
- **Commit**: 855562c
- **Severity**: MEDIUM
- **Category**: Interruptibility (keyframes vs. transitions)
- **Estimated scope**: 2 files, one keyframe + one rule each

## Problem

All three card motifs are supposed to scale in on hover, from `scale(.92)` to
`scale(1)`. Two of them do. The FutureScope one does not — it pops in at full size —
because its rotation keyframe animates the **same `transform` property** the
scale-in transition needs, and a running CSS animation wins over a transition on the
same property.

```css
/* index.html:384-386 / work.html:303-305 — current */
.card-motif{
  /* … */
  opacity:0;
  transform:scale(.92);
  transition:opacity .3s cubic-bezier(0.22,1,0.36,1) .08s,
             transform .3s cubic-bezier(0.22,1,0.36,1) .08s;
}
```

```css
/* index.html:402-408 / work.html:321-327 — current */
@media(prefers-reduced-motion:no-preference){
  .project-card:hover .card-motif--bloom,
  .project-card:focus-visible .card-motif--bloom{
    animation:card-bloom-spin 2s linear infinite;
  }
}
@keyframes card-bloom-spin{to{transform:rotate(360deg)}}
```

**Confirmed in the browser, not inferred.** With the hover state applied, reading the
running animations on each motif:

```js
document.querySelector('.project-card--sip .card-motif').getAnimations()
// → ["CSSTransition/opacity", "CSSTransition/transform"]     ← scale-in runs
document.querySelector('.project-card--future .card-motif').getAnimations()
// → ["CSSTransition/opacity", "CSSAnimation/card-bloom-spin"] ← scale-in replaced

getComputedStyle(document.querySelector('.project-card--sip .card-motif')).transform
// → "matrix(0.92, 0, 0, 0.92, 0, 0)"   ← starts scaled down, transitions up
getComputedStyle(document.querySelector('.project-card--future .card-motif')).transform
// → "matrix(1, 0, 0, 1, 0, 0)"         ← already full size, no scale-in
```

There is a second, smaller defect in the same block: the animation has no
`animation-delay`, so the bloom starts rotating at 0ms while its own opacity is still
delayed. It spins invisibly for the first 60–80ms, then fades in mid-rotation.

AUDIT.md, "Interruptibility": keyframes and transitions competing for one property is
exactly the class of bug that makes motion inconsistent between sibling elements.

## Target

Animate the **independent `rotate` property** instead of `transform`. `rotate`,
`scale` and `translate` are separate CSS properties that compose with `transform`
rather than replacing it, so the scale-in transition and the rotation can both run.
Add an `animation-delay` matching the motif's entrance delay so the spin starts as
the motif becomes visible.

Browser support for the independent `rotate` property: Chrome 104+, Safari 14.1+,
Firefox 72+ — comfortably wider than the cross-document View Transitions this site
already relies on, so it introduces no new floor.

```css
/* target — replaces the keyframe */
@keyframes card-bloom-spin{to{rotate:360deg}}
```

```css
/* target — replaces the hover rule */
@media(prefers-reduced-motion:no-preference){
  .project-card:hover .card-motif--bloom,
  .project-card:focus-visible .card-motif--bloom{
    animation:card-bloom-spin 2s linear infinite;
    animation-delay:60ms;
  }
}
```

`animation-delay:60ms` assumes **plan 002 has landed** (it sets the motif's entrance
delay to 60ms). If plan 002 has **not** been applied, use `animation-delay:80ms` to
match the current 80ms delay at `index.html:385-386`. Everything else in this plan is
identical either way.

`.card-motif` must not also declare `rotate` — it does not today, and this plan must
not add one, or the animation and the base value would compete again.

## Repo conventions to follow

- Static multi-page site, no build step, CSS embedded per file. The same edit must
  land in **both** `index.html` and `work.html`, byte-identically.
- The bloom rotation exists because the FutureScope motif is the one animated node in
  the source Figma file (node `709:71`, a 2s rotation) — see the comment already above
  the rule: *"The bloom is the one animated node in the Figma: a 2s rotation. It only
  turns while the card is actually hovered."* Keep that comment and keep the 2s
  `linear` `infinite` timing; this plan changes **which property** is animated, not
  the motion itself.
- The existing `prefers-reduced-motion:no-preference` wrapper is correct and must
  stay — an infinite rotation is exactly the kind of motion reduced-motion users opt
  out of. Do not remove or weaken it.

## Steps

Apply to **`index.html` first, then `work.html`**.

1. Replace the keyframe
   `@keyframes card-bloom-spin{to{transform:rotate(360deg)}}`
   with
   `@keyframes card-bloom-spin{to{rotate:360deg}}`
   (`index.html:408`, `work.html:327`).
2. In the rule directly above it, add `animation-delay:60ms;` on its own line
   immediately after the `animation:card-bloom-spin 2s linear infinite;` declaration
   (`index.html:405`, `work.html:324`). Use `80ms` instead if plan 002 has not been
   applied — check whether `.project-card:hover .card-motif` declares
   `transition-delay:60ms` and match whatever value you find.
3. Repeat both steps in `work.html`.

## Boundaries

- Do NOT change `.card-motif`'s `transform:scale(.92)` or its transition — the whole
  point is that those now get to work.
- Do NOT add a `rotate` declaration to `.card-motif`'s base rule.
- Do NOT remove the `prefers-reduced-motion:no-preference` wrapper.
- Do NOT change the 2s duration, `linear` easing, or `infinite` count — that timing
  comes from the source design file.
- Do NOT apply rotation to the other two motifs (`--flower`, `--rainbow`). Only the
  bloom rotates.
- Do NOT touch `Projects/*.html`, and do NOT touch the page-transition block.
- Do NOT add dependencies or a build step.
- If the excerpts above do not match what you find, STOP and report.

## Verification

- **Mechanical**: run
  `node .claude/skills/impeccable/scripts/detect.mjs --json --scope layout index.html work.html`
  if present — expect `[]`.
- **Confirm the property conflict is gone** — on `index.html`, apply the hover state
  to the FutureScope card (DevTools → Styles → `:hov` → `:hover`) and run:
  ```js
  const m = document.querySelector('.project-card--future .card-motif');
  m.getAnimations().map(a => a.constructor.name + '/' + (a.animationName || a.transitionProperty));
  // BEFORE: ["CSSTransition/opacity", "CSSAnimation/card-bloom-spin"]
  // AFTER : ["CSSTransition/opacity", "CSSTransition/transform", "CSSAnimation/card-bloom-spin"]
  //          ^ the transform transition is back alongside the animation
  ```
  Then, immediately on hover (before the transition settles):
  ```js
  getComputedStyle(m).transform;  // expect a matrix near scale(0.92), NOT matrix(1,0,0,1,0,0)
  getComputedStyle(m).rotate;     // expect a non-zero angle once spinning
  ```
- **Feel check**: serve locally and open the work grid on both `index.html` and
  `work.html`:
  - Hover the **FutureScope** card and the **Sip & Scones** card in turn. Both motifs
    must now grow in the same way. Before this fix the bloom appeared at full size
    while the rainbow grew — watch specifically for that difference disappearing.
  - The bloom should begin rotating **as it becomes visible**, not already mid-spin.
  - In DevTools → Animations panel at 10% playback, hover FutureScope and confirm the
    motif is simultaneously scaling up *and* rotating for the first ~220ms.
  - DevTools → Rendering → "Emulate CSS prefers-reduced-motion: reduce", reload, and
    hover FutureScope: the motif should still fade in but must **not** rotate.
- **Done when**: `getAnimations()` on the bloom lists a `CSSTransition/transform`
  alongside the `CSSAnimation`, all three motifs scale in identically, the spin starts
  with the fade rather than before it, and reduced-motion still suppresses rotation.
