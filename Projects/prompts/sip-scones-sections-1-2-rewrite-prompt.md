# Prompt: Replace sections 01–02 content in Sip & Scones (plain paragraphs, no callouts) + embed prototype video

Read `CLAUDE.md`, `DESIGN.md`, and `PRODUCT.md` first.

Edit `Projects/sip-scones.html` in place — this file is already on the correct design system, so this is a content swap, not a re-skin.

## Before writing any code: ask me these questions

1. Section 02 currently holds the "Design Principles" content (Unhurried interaction / Thematic coherence / Constrained delight, in a `.principles` grid). The new copy below replaces that section's content entirely with "The Concept" instead. **Drop the three-principles content, or fold it into a later section?** Don't delete it silently — confirm first.
2. **The video file** — what's the filename and where does it live relative to `Projects/sip-scones.html` (e.g. alongside it in `/Projects/`)? What does it show — full prototype walkthrough, a single flow, the tiered-stand interaction specifically? That'll determine whether it belongs in section 02 (The Concept) near the interface description, or later in section 03/04 near the screen flow or prototype testing content. My default assumption is section 02, right after the feature list, but confirm placement.
3. What video format is it, and should it autoplay muted/loop (common for a portfolio demo clip) or be a click-to-play embed with controls?

## Replace section 01 ("Background") body copy with this text, verbatim — plain paragraphs, no callout boxes, no cards

Keep the existing `sec-num` (01) and `sec-tag` ("Background"). Replace the current headline and `<p class="body-t">` paragraphs with:

**Headline** (style consistent with the existing `<em>` accent pattern — pick the emphasized word/phrase that fits, e.g. something like "What the *atmosphere* taught us about the design"):

**Body copy — two plain paragraphs, nothing pulled into a separate box:**
> Designing for a digital afternoon tea experience meant thinking beyond functionality. It meant understanding what makes afternoon tea special in the first place.
>
> Early research showed afternoon tea isn't just a meal. It's a social experience, steeped in tradition and ambiance. A study by Lin and Chen (2022) found that 93% of afternoon tea patrons, mostly young women aged 24 to 29, choose a restaurant based on atmosphere first. That insight shaped our design direction. Space, mood, and pacing mattered as much as the food. This led to a key design challenge: how do we introduce a digital ordering system without interrupting the ritual, aesthetic, or mood of the experience?

That's the full section 01 body. The 93% stat and the design-challenge question both stay woven into the paragraph as continuous prose — do not pull either into a stat callout, a bordered box, a card, or any other separated component. No new components should be added to this section at all.

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

**Video embed** — insert here (or wherever confirmed in question 2 above), sized and framed consistently with how other media is presented elsewhere in this file (e.g. matching the rounded-corner/shadow treatment used on existing screenshots, if any). Use a native `<video>` element, not an external embed, unless the file is hosted elsewhere and you tell me otherwise.

**Body copy, continued:**
> Replacing traditional waitstaff with digital menus and robotic delivery carts struck a balance between efficiency and experience. Diners could enjoy a quiet, uninterrupted afternoon and still benefit from shorter wait times and fewer order errors (Bankar & Suresh, 2015).

**Pull-quote** — reuse the existing `.pull-quote` component (currently holding "Technology should enhance the experience, not disrupt it." — Guiding design principle). Replace its content with:
> "Our biggest concern was losing the essence of afternoon tea. We wanted technology that enhanced the experience, not one that disrupted it. The design needed to feel intuitive, elegant, and invisible."

Keep this quote's wording exactly as given. Drop the old "Guiding design principle" attribution, or replace it with something accurate (e.g. "— Team reflection") — your call.

## Constraints

- Sections 03 onward (Screen Flow, Prototype Testing, etc.) are untouched by this prompt — don't renumber or edit them, unless the video's confirmed placement (question 2) lands there instead.
- Keep all citations (Lin & Chen 2022, Bankar & Suresh 2015) exactly as worded above.
- No new visual components for section 01 — this section should read as plain prose only.
- Confirm you're editing `Projects/sip-scones.html` and that this is the intended target file before making changes.