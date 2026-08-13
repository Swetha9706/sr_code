# Prompt: Replace sections 01–02 content in Sip & Scones with the plainer-voice rewrite

Read `CLAUDE.md`, `DESIGN.md`, and `PRODUCT.md` first.

Edit `Projects/sip-scones-v2.html` in place — this file is already on the correct design system, so this is a content swap plus two small new components, not a re-skin.

## Before writing any code: ask me this question

Section 02 currently holds the "Design Principles" content (Unhurried interaction / Thematic coherence / Constrained delight, in a 3-item `.principles` grid). The new copy below replaces that section's content entirely with "The Concept" instead. **Do you want the three-principles content dropped, or folded into a later section** (e.g. worked into Key Features or Design Principles kept as a short aside elsewhere)? Don't delete it silently — confirm first.

## Replace section 01 ("Background") body copy with this text, verbatim

Keep the existing `sec-num` (01) and `sec-tag` ("Background"). Replace the two `<p class="body-t">` paragraphs and headline with:

**Headline** (style consistent with the existing `<em>` accent pattern — pick the emphasized word/phrase that fits, e.g. something like "What the *atmosphere* taught us about the design"):

**Body copy:**
> Designing for a digital afternoon tea experience meant thinking beyond functionality. It meant understanding what makes afternoon tea special in the first place.
>
> Early research showed afternoon tea isn't just a meal. It's a social experience, steeped in tradition and ambiance. A study by Lin and Chen (2022) found that 93% of afternoon tea patrons, mostly young women aged 24 to 29, choose a restaurant based on atmosphere first. That insight shaped our design direction. Space, mood, and pacing mattered as much as the food.

**New: 93% stat callout** — this doesn't exist as a component in this file yet (unlike Krētha/FutureScope, which already have one). Add a new lightweight stat-callout component here, matching the established visual language: a large Cormorant Garamond number, a short DM Mono caption underneath, source attribution in Muted. Place it directly after the paragraph above, inside section 01. Content: "93%" as the number; caption something like "of afternoon tea patrons choose a restaurant based on atmosphere first — Lin & Chen, 2022."

**New: design-challenge callout** — also new. This is not a quote (no attribution), so don't reuse `.pull-quote` for it — build a simple bordered or tinted callout box, italic Cormorant Garamond, no citation styling. Place it at the end of section 01:
> This led to a key design challenge.
>
> How do we introduce a digital ordering system without interrupting the ritual, aesthetic, or mood of the experience?

## Replace section 02 content entirely with "The Concept"

Change the `sec-tag` from "Design Principles" to "The Concept." Replace the current three-principle grid with:

**Headline** (same `<em>` pattern, your call on the exact phrase):

**Body copy:**
> We envisioned Sip & Scones as a fine-dining restaurant with a tech-enhanced twist. Instead of kiosks at the entrance or ordering through personal phones, we placed a tablet-based digital menu discreetly at each table. Diners keep control of the ordering process. The setting keeps its elegance and intimacy.
>
> The interface replicates the iconic three-tiered tea stand, allowing diners to:

**Bullet list** (use whatever list styling is already established elsewhere in the file for short feature lists):
- Customize each of the three afternoon tea tiers: Sandwiches, Scones, Sweets
- Choose drink pairings from a curated menu
- Review and complete their order at their own pace
- Track loyalty rewards through a visual system of stacked teacups

**Body copy, continued:**
> Replacing traditional waitstaff with digital menus and robotic delivery carts struck a balance between efficiency and experience. Diners could enjoy a quiet, uninterrupted afternoon and still benefit from shorter wait times and fewer order errors (Bankar & Suresh, 2015).

**Highlight the "biggest challenge" quote as a pull-quote** — reuse the existing `.pull-quote` component (the one currently holding "Technology should enhance the experience, not disrupt it." — Guiding design principle). Replace its content with:
> "Our biggest concern was losing the essence of afternoon tea. We wanted technology that enhanced the experience, not one that disrupted it. The design needed to feel intuitive, elegant, and invisible."

Since this is presented as a direct quote, keep the wording exactly as given — don't paraphrase or trim it. Drop the old "Guiding design principle" attribution line, since this quote isn't attributed to a named source in the original material — or replace it with something accurate if you want an attribution (e.g. "— Team reflection"), your call.

## Constraints

- Sections 03 onward (Screen Flow, Prototype Testing, etc.) are untouched by this prompt — don't renumber or edit them.
- Keep all citations (Lin & Chen 2022, Bankar & Suresh 2015) exactly as worded above.
- New components (stat callout, design-challenge callout) should be built from the CSS variables already defined in this file's `:root` — no new colors or fonts.
- This is still a draft file — confirm you're editing `Projects/sip-scones-v2.html`, not touching `Projects/sip-scones.html`.
