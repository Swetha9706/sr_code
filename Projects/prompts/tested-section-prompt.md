# Prompt: Replace the "How was it tested?" section

Copy everything below into your coding agent.

---

Replace the **entire** "How was it tested?" section on my site with the following. Keep my existing site's `<section>` wrapper conventions (id, scroll anchor, etc.) but replace all inner markup. Do not rewrite any of the copy — use it verbatim.

## Design tokens

```
Ink (text)        #141018
Body text (muted) #575165
Plum accent       #5642EA
Deep plum         #630F49
Nectar (highlight)#FFCAA6
Paper background  #FCFBFA
Hairline          #ddd6ec
```

Fonts (Google Fonts):
- `Cormorant Garamond` 600, 400i, 600i — headings and the verdict line
- `Lora` 400, 500 — all body copy
- `DM Mono` 400, 500, 500i — eyebrows, table labels, captions

```html
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,600;1,400;1,600&family=DM+Mono:ital,wght@0,400;0,500;1,500&family=Lora:wght@400;500&display=swap" rel="stylesheet">
```

## Layout, top to bottom

Section container: `max-width: 1180px`, centred, `padding: 4rem 3rem`, background Paper.

**1. Eyebrow** — a 1.6rem × 1px Plum rule, then `How was it tested?` in DM Mono, 0.7rem, uppercase, `letter-spacing: .16em`, Plum.

**2. Headline** — Cormorant Garamond 600, `clamp(1.9rem, 3.6vw, 2.8rem)`, `line-height: 1.1`, `max-width: 24ch`:

> Layout mattered *more than expected*

("more than expected" is italic and Plum.)

**3. Lede** — Lora, 1.125rem, `line-height: 1.65`, Ink, `max-width: 60ch`:

> Testing happened on paper, before a line of code was written.

**4. Two-column prose row** — `grid-template-columns: 1fr 1fr; gap: 3.5rem; margin-top: 3rem`. Each column has a top hairline (`1px solid #ddd6ec`) with `padding-top: 1.15rem`, a DM Mono uppercase Plum eyebrow, then Lora 0.98rem / 1.7 body in muted text, `max-width: 44ch`.

Column A eyebrow: `Paper · Wizard of Oz`

> The orders page mirrors the three-tiered stand used to serve English afternoon tea. Three buttons sit on the left: Tier 1, Tier 2, Tier 3. Click one and a dialog opens with the dishes available for that tier. Diners pick up to three dishes per layer, and click a dish again to remove it. Holding a dish opens a second dialog with its allergy and ingredient information. Clicking anywhere outside closes it. A recommended-drinks button sits top right. Continue, bottom right, moves on to drink choices and confirming the order.

Column B eyebrow: `Two concepts, compared`

> We tested two versions of the main ordering screen with several peers. The first keeps all three tiers on screen for the whole ordering process. The second zooms in on the tier being customised and fades the others out. Neither was built. We used Wizard of Oz testing, where a person manually stands in for the interface's responses.

**5. Prototype figures** — `margin-top: 3.25rem`, grid `1.35fr .65fr`, `gap: 2.5rem`, `align-items: flex-start`. Collapses to a single column under ~900px.

Both images: `display: block`, `width: 100%`, `height: auto`, `border-radius: 14px`, `border: 1px solid #ddd6ec`, `loading="lazy"`.

Captions: DM Mono, 0.7rem, `letter-spacing: .06em`, muted, `line-height: 1.6`, sitting 1rem below the image.

- Left figure — `PaperPrototype-2.png`. Caption: `Option 1: the full-tier layout, with all three tiers and their dishes laid out on the stand at once.`
  Alt: *Hand-drawn paper prototype of the full-tier concept: a three-tiered stand labelled Tier 1, Tier 2, and Tier 3, with paper strips of sandwiches, pastries, and sweets to place on each tier, a Recommended drink note, and a Continue button.*
- Right figure — `PaperPrototype-1.png`. Caption: `Option 2: a selection screen, with tea and drink options in left-and-right carousels.`
  Alt: *Hand-drawn paper prototype of a selection screen: rows of teacups and drinks in left-and-right carousels, a home icon top-left, and a Continue button top-right.*

**6. Comparison matrix eyebrow** — `margin-top: 4rem`, same rule-plus-DM-Mono treatment as the section eyebrow: `Layout comparison`.

**7. Comparison matrix** — `margin-top: 1.5rem`. Horizontally scrollable wrapper (`overflow-x: auto`) around a `min-width: 640px` relatively-positioned track. No card, no box — hairlines only.

Every row is a grid: `grid-template-columns: 200px 1fr 1fr; gap: 0 1.5rem`.

*Column highlight:* an absolutely-positioned Nectar (`#FFCAA6`) panel at `opacity: .34`, `border-radius: 14px`, `pointer-events: none`, spanning the full height of the track behind the **second** column (the winning one). Position it at `left: calc(200px + .75rem)` with `width: calc((100% - 200px - 3rem) / 2 + 1.5rem)`. The whole column tints — do not use a badge or pill. The Full-Tier View cells get `padding: 0 1.5rem` so text sits inside the wash.

*Header row:* `align-items: end`, `padding: 1.5rem 0 1.1rem`, `border-bottom: 1px solid #141018` (heavier than the body rules).
- Col 1: `Criterion` — DM Mono, 0.7rem, uppercase, muted.
- Col 2 (highlighted): kicker `Cohesive experience` in DM Mono uppercase Deep Plum `#630F49`, then `Full-Tier View` in Cormorant Garamond 600, 1.5rem, Ink.
- Col 3: kicker `Condensed context` in DM Mono uppercase muted, then `Single-Tier Focus` in Cormorant Garamond 600, 1.5rem, muted.

*Body rows:* `align-items: baseline`, `padding: 1.6rem 0`, `border-bottom: 1px solid #ddd6ec`. Criterion in DM Mono 0.7rem uppercase muted; Full-Tier cell in Lora 1rem Ink; Single-Tier cell in Lora 1rem muted.

| Criterion | Full-Tier View | Single-Tier Focus |
|---|---|---|
| Overall feel | Felt close to assembling a physical tea stand | Cleaner per-screen, but lost context |
| Sense of control | Diners could see the whole order at once | Diners felt less in control of the total meal |
| Visual metaphor | Reinforced the afternoon tea ritual | Reduced clutter, but broke the metaphor |
| Task completion | Both users completed with minor issues | Both users completed with minor issues |

**8. Verdict block** — `margin-top: 3.5rem`, top hairline, `padding-top: 2.5rem`, grid `1.15fr 1fr`, `gap: 3.5rem`, `align-items: start`.

Left (Cormorant Garamond 600 **italic**, `clamp(1.6rem, 3vw, 2.2rem)`, `line-height: 1.3`, `letter-spacing: -.015em`, Ink):

> The full-tier view felt more intuitive *and satisfying*

("and satisfying" is set upright — `font-style: normal` — and Plum, so it reads as a lift out of the italic.)

Right (Lora 1.05rem / 1.7, muted, `max-width: 52ch`):

> Peers preferred keeping all three tiers in view. It let them read their picks in one linear pass, instead of jumping tier to tier to check whether the choices paired well. Populating the tiers as they ordered also read as progress through the order, a form of visual storytelling shown to improve user experience (Li et al., 2020).

## Responsive

Under ~900px: the two prose columns, the figure grid, and the verdict block all collapse to one column. Keep the matrix horizontally scrollable rather than stacking it, and keep the Nectar highlight aligned to the second column at all widths.

## Rules

- Verbatim copy. Do not reword, retitle, or add headings.
- No cards, shadows, or gradients. Hairlines and the single Nectar wash carry all the structure.
- `text-wrap: pretty` on the headline and the verdict line.
- Anchor styles: define `a` (Plum) and `a:hover` (Ink) even if the section has no links.
