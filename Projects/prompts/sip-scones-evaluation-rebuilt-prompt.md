# Prompt: Rewrite Evaluation ("What did the tooling teach me?") and update "If I Built It Again" items

Read `CLAUDE.md`, `DESIGN.md`, and `PRODUCT.md` first.

Edit `Projects/sip-scones.html` in place. This is a content pass on section 10 (Evaluation) and section 11 (If I Built This Again) — no new components, no re-skin, both sections already use existing patterns (`.two-col`, `.stack-row`).

## Before writing any code: ask me these two questions

1. **Section 10 — merge or replace?** The current section 10 already covers two of the same points as the new copy below (the memory-system cut, and "designed before confirming feasibility"), just in fewer words. Should the new copy **fully replace** the current `.two-col` content, or should I **merge** them, keeping anything from the current version that isn't already covered? My default is full replacement, since the new copy is more specific and covers the same ground — confirm before proceeding.
2. **Section 11, items 01/03/05 — keep separate or consolidate?** All three now reference the same underlying technical gap (an array-based memory system for storing selections), described from three angles: navigation (01), a checkout summary (03), and account recall (05). Keep them as three distinct items, or fold 03 into 05 as a single "memory system" item? My default is to keep them separate, since they're user-facing features, not the same feature — confirm before proceeding.

## Section 10 ("What did the tooling teach me?") — replace the `.two-col` content

Replace both columns' paragraphs with:

**Column 1:**
> LiveCode let visuals act as functional objects directly. Instead of hand-coding every part of a component, we could import a custom graphic and use the Property Inspector to get it working in a few lines of code. That made the harder parts of functional programming less intimidating, and more usable for a design-led project. We could also move objects around a card and see the final layout update live, without writing anything — a real advantage for designers working visually.
>
> The tiered tea stand benefited most. It was the thematic backbone of the whole concept, and it doubled as a visual progress indicator as diners built their order. Using imagery to show progress through a task is a known method for improving user experience through storytelling (Li et al., 2020).

**Column 2:**
> LiveCode was also a hard environment to learn. Core functions, including the Project Browser (the tool for understanding a project's logic and configuration), were buried in menus and hard to find. The syntax is simplified, but it still assumes foundational knowledge of how LiveCode models objects, and few tutorials exist outside the official documentation. Undo was limited to a single action, which made mistakes costly. This version of LiveCode asked for more functional-programming experience than we had as beginners. More time spent learning the environment itself, before building in it, would have helped.
>
> We'd prototyped and tested with users early on. Even so, several planned features got cut or simplified in the final build, to keep the task flow from becoming cluttered. In hindsight, we approached prototyping backwards. We designed functionality before confirming we could actually build it in LiveCode. That cost us a system to store and recall variables, which turned out to be beyond our skill level at the time. We simulated what we couldn't fully build instead.

If I answered "merge" to question 1 above, weave in whichever specific details from the current column text aren't already covered (e.g. the "designer-led build" framing, the "tiered-tray metaphor was the right decision" closing line) rather than dropping them silently.

## Section 11 ("If I Built It Again") — update items 01, 02, 03, 05; leave 04 and 06 unchanged

**Item 01 — retitle to "Menu switching & backtracking":**
> Let diners move between the food tiers and drinks menu, and back to change an earlier choice, instead of following one fixed sequence. Right now, revisiting a tier resets it: the `on openCard` function disables every option again, so changing your mind means starting the whole order over. Back-button navigation works well in ordering and shopping interfaces (Obendorf et al., 2007).

Note this supersedes any earlier version of item 01 from a prior editing pass — use this version as final.

**Item 02 — "Smarter dialogs," replace body text:**
> Replace LiveCode's default dialog boxes with modal substacks that block other actions until closed (LiveCode, 2023a). Substacks can be styled beyond the default look, so dialogs would finally match the rest of the interface.

**Item 03 — "Visual checkout summary," replace body text:**
> Show the full tea tray and drink selections before payment, a moment to catch mistakes and see what's been built. This would use an array-based data structure (LiveCode, 2023b) to hold the full selection in memory.

(If I answered "consolidate" to question 2 above, fold this into item 05 instead of keeping it as a standalone item, and renumber 04/05/06 accordingly to 04/05.)

**Item 04 — unchanged.**

**Item 05 — "Real sign-up flow," replace body text:**
> Move beyond predefined personas toward real accounts and long-term reward tracking for returning diners. Loyalty data drives revisits and helps develop a business's value proposition (Piccoli, 2008). Recalling login details would need the same kind of array-based memory system as the checkout summary above.

(Adjust the cross-reference "as the checkout summary above" if items 03 and 05 get consolidated per question 2.)

**Item 06 — unchanged.**

## New: add an image slot to each stack item in section 11 — image only, no card treatment

The `.stack-row` component currently has no image slot — just a number, title, and body text. Add one, since I'll be providing an image for each of the (up to) six items after the content update lands.

**No cards anywhere in this addition.** Do not wrap the image in a bordered/tinted container, do not give it a `var(--card-base)` background fill, and do not add padding around it that would read as a card surface. DESIGN.md's No-New-Cards Rule applies here directly — this is exactly the kind of new element it warns against defaulting to. Use the **floating-image** treatment already established elsewhere in the file instead (see `.hero-img`, `.needs-media`): the image itself, rounded corners (14px per DESIGN.md's image radius token, not the 28px card radius), and — if a shadow is used at all — the same soft floating-image shadow (`0 12px 36px rgba(30,18,10,.14)`) that's reserved for lifting imagery, never the ambient "ready for interaction" shadow implied by a card.

- Extend `.stack-row` to a three-part layout: number, image, then title/text — or number + text on one side with the image alongside, whichever reads better against the existing `.stack-row` grid (`auto 1fr` currently; likely becomes `auto auto 1fr` or a nested flex/grid inside the text column). Keep the existing number treatment (italic Cormorant Garamond, Ultraviolet) as-is.
- Since I haven't provided the actual image files yet, use a clearly labeled placeholder rather than a broken `<img>` tag or an assumed filename — but the placeholder itself should follow the same no-card rule: a plain, muted-outline rectangle (hairline `var(--border)` outline only, `var(--paper)` or transparent fill, no card-base wash) with a centered `[IMAGE: item-01-menu-switching]`-style DM Mono label. Not a tinted, padded box — just a boundary marking where the image goes.
- Keep this responsive: images should stack above or below the text on mobile, following the same breakpoint logic already used for `.stack-row` at `max-width:720px`.
- Apply this image slot to all six items (or five, if items 03/05 get consolidated per question 2), not just the four that were touched by this content pass — I want visual consistency across the whole list, including items 04 and 06 which aren't otherwise changing.

## Constraints

- Keep all citations exactly as worded: Li et al. (2020), Obendorf et al. (2007), LiveCode (2023a), LiveCode (2023b), Piccoli (2008).
- Don't invent technical detail beyond what's specified above — if a citation's `LiveCode, 2023a` / `2023b` distinction matters for accuracy, keep 2023a for modal dialogs and 2023b for array-based data structures, as sourced.
- No new colors, fonts, or component types — reuse `.two-col`, `.stack-row`, `.cite` exactly as they already exist in the file.
- No new colors or fonts — the new image-slot treatment should reuse the existing floating-image radius (14px) and shadow vocabulary (see DESIGN.md Elevation section), not a card-style radius (28px), border, or tinted fill.
- Confirm you're editing `Projects/sip-scones.html`.
