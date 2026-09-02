# 003 — Gate the card hover state behind a fine-pointer media query

- **Status**: DONE (applied 2026-08-31, verified in Chrome 151)
- **Commit**: 855562c
- **Severity**: MEDIUM-HIGH
- **Category**: Accessibility
- **Estimated scope**: 2 files, six selector groups each

## Problem

There is not a single `@media (hover: hover)` query anywhere in `index.html` or
`work.html` (verified: `grep -c 'hover: *hover' index.html` returns `0`).

On a touch device, tapping a link fires `:hover` before the navigation commits. So
every tap on a project card triggers the full hover choreography — the hero photo
dissolves, the scrim clears, the card floods with its accent colour, the title
reverses from Ink to Paper, and the description and motif fade in — and then the
page navigates away. The visitor gets a jarring flash of a state they never asked
for, on every single tap. On a slow connection the flashed state can sit there for
a second or more before the case study loads.

AUDIT.md, "Accessibility": *"Touch devices trigger hover on tap, causing false
positives. Gate hover animations behind this media query."*

```css
@media (hover: hover) and (pointer: fine) {
  .element:hover { transform: scale(1.05); }
}
```

The six affected selector groups, identical in both files:

```css
/* index.html:250-251 / work.html:169-170 */
.project-card:hover .card-visuals,
.project-card:focus-visible .card-visuals{opacity:0}

/* index.html:293-294 / work.html:212-213 */
.project-card:hover .card-scrim,
.project-card:focus-visible .card-scrim{opacity:0}

/* index.html:324-325 / work.html:243-244 */
.project-card:hover .card-desc,
.project-card:focus-visible .card-desc{opacity:1}

/* index.html:367-368 / work.html:286-287 */
.project-card:hover .card-arrow,
.project-card:focus-visible .card-arrow{opacity:1;transform:translateX(0)}

/* index.html:371-374 / work.html:290-293 */
.project-card:hover .card-name,
.project-card:hover .card-cat,
.project-card:focus-visible .card-name,
.project-card:focus-visible .card-cat{color:var(--paper)}

/* index.html:388-389 / work.html:307-308 */
.project-card:hover .card-motif,
.project-card:focus-visible .card-motif{opacity:1;transform:scale(1)}
```

Each group pairs a `:hover` selector with a `:focus-visible` selector. Only the
`:hover` half may be gated — `:focus-visible` is how keyboard users reach this state
and it must keep working on every device.

## Target

Split each group: `:focus-visible` stays where it is (ungated), and the `:hover`
halves move into one shared `@media (hover: hover) and (pointer: fine)` block.

```css
/* target — the :focus-visible halves stay exactly where each group is today */
.project-card:focus-visible .card-visuals{opacity:0}
.project-card:focus-visible .card-scrim{opacity:0}
.project-card:focus-visible .card-desc{opacity:1}
.project-card:focus-visible .card-arrow{opacity:1;transform:translateX(0)}
.project-card:focus-visible .card-name,
.project-card:focus-visible .card-cat{color:var(--paper)}
.project-card:focus-visible .card-motif{opacity:1;transform:scale(1)}

/* target — ONE new block, placed immediately after the
   `.project-card:focus-visible .card-motif{...}` rule.
   Only devices with a real pointer get the hover choreography. */
@media (hover: hover) and (pointer: fine){
  .project-card:hover .card-visuals{opacity:0}
  .project-card:hover .card-scrim{opacity:0}
  .project-card:hover .card-desc{opacity:1}
  .project-card:hover .card-arrow{opacity:1;transform:translateX(0)}
  .project-card:hover .card-name,
  .project-card:hover .card-cat{color:var(--paper)}
  .project-card:hover .card-motif{opacity:1;transform:scale(1)}
}
```

If plans 001 and 002 have already landed, their timing block also contains `:hover`
selectors. Those are timing-only declarations and are **harmless on touch** (they
change no visual state on their own), so they may stay ungated. Do not restructure
them; leave that block exactly as you find it.

The bloom spin block (`index.html:402-408` / `work.html:321-327`) also pairs
`:hover` with `:focus-visible` inside a `prefers-reduced-motion` query. Leave it
alone — plan 004 rewrites that block, and gating it here would collide.

## Repo conventions to follow

- Static multi-page site, no build step, CSS embedded per file. The same edit must
  land in **both** `index.html` and `work.html`, byte-identically.
- The codebase already uses feature queries of this shape for motion — see
  `@media(prefers-reduced-motion:no-preference)` at `index.html:539` and
  `@media(prefers-reduced-motion:reduce)` at `index.html:543`. Match that placement
  style: the query sits adjacent to the rules it modifies, not in a separate section.
- Note the existing file writes media queries without a space after `@media`
  (`@media(max-width:760px)`). For this query keep the spaces —
  `@media (hover: hover) and (pointer: fine)` — because it is copied verbatim from
  AUDIT.md and the spacing aids readability of a two-condition query. Consistency of
  values matters here; whitespace does not.

## Steps

Apply to **`index.html` first, then `work.html`**.

1. In each of the six groups listed under Problem, delete the `.project-card:hover …`
   selector line(s), leaving only the `.project-card:focus-visible …` selector(s) and
   the declaration block. For the `.card-name` / `.card-cat` group, that means
   deleting two `:hover` lines and keeping two `:focus-visible` lines.
2. Immediately after the (now `:focus-visible`-only)
   `.project-card:focus-visible .card-motif{opacity:1;transform:scale(1)}` rule,
   insert the `@media (hover: hover) and (pointer: fine){ … }` block from the Target
   section, verbatim.
3. Repeat both steps in `work.html`.

## Boundaries

- Do NOT gate, move, or delete any `:focus-visible` selector. Keyboard access to the
  hover state must survive on every device, including touch devices with a keyboard.
- Do NOT touch the bloom-spin block (`index.html:402-408` / `work.html:321-327`) —
  plan 004 owns it.
- Do NOT touch the timing block created by plans 001/002 if present.
- Do NOT gate `:active` press feedback (`index.html:643`) — press feedback is
  correct and wanted on touch.
- Do NOT change any duration, delay, easing, colour, or layout value. This plan
  moves selectors only; every declaration block is copied unchanged.
- Do NOT touch `Projects/*.html`, `aboutme.html`, or `swethafullportfolio.html`.
- Do NOT add dependencies or a build step.
- If a cited selector group does not match the excerpt above, STOP and report.

## Verification

- **Mechanical**: run
  `node .claude/skills/impeccable/scripts/detect.mjs --json --scope layout index.html work.html`
  if present — expect `[]`. Then confirm the count changed:
  `grep -c 'hover: hover' index.html work.html` — expect `1` for each file.
- **Confirm no hover rule escaped the gate** — every remaining bare
  `.project-card:hover` that sets a *visual* property should now be inside the media
  query. Check with:
  ```sh
  grep -n 'project-card:hover' index.html
  ```
  Expected results: the six selectors inside the new media block, plus (if plans
  001/002 landed) the timing-only selectors. Nothing else.
- **Feel check — desktop** (`http://localhost:8123/index.html`, mouse):
  - Hover a card: the full choreography still runs exactly as before this change.
  - Tab to a card with the keyboard: the same choreography runs on focus, and the
    Ultraviolet focus ring is visible.
- **Feel check — touch** (this is the point of the plan; DevTools emulation is not
  sufficient on its own, but is the minimum):
  - DevTools → Device Toolbar → any phone preset → reload. Tap a card. The card must
    navigate **without** the photo dissolving or the accent flooding first.
  - Better: open `http://<your-lan-ip>:8123/index.html` on a real phone and tap each
    of the three cards. No flash of the hover state before navigation.
  - Repeat on `work.html`.
- **Done when**: `@media (hover: hover) and (pointer: fine)` appears exactly once per
  file, every visual `:hover` rule for the cards lives inside it, all six
  `:focus-visible` rules remain ungated and working, and tapping a card on a real
  touch device shows no hover flash.
