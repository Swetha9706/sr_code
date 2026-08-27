# Prompt: Rewrite the testing content in Sip & Scones (sections 8, 9, 11)

Read `CLAUDE.md`, `DESIGN.md`, and `PRODUCT.md` first.

Edit `Projects/sip-scones.html` in place. This file is already on the correct design system and already has the right section structure — this is a content correction and enrichment pass on sections 8 ("Testing"), 9 ("Screens"), and 11 ("If I Built This Again"), using real detail from the source PDF report that isn't in the file yet.

## Fix first: the current text conflates two separate testing rounds

Section 8's intro paragraph currently reads: "Two interface concepts were tested using paper prototypes and a Wizard of Oz method, manually simulating interactions while two participants used the system." This merges two distinct rounds from the source material into one:

- **Round one** — an early paper-prototype round comparing two layout concepts, tested with **several peers** via Wizard of Oz (manually simulating the interface rather than a working build).
- **Round two** — a later round with **two participants** completing a full order-and-pay task on the finished LiveCode prototype.

Keep these separate throughout sections 8 and 9. Don't reuse "two participants" to describe round one.

## Section 8 ("Testing") — replace the intro paragraph and add a new paper-prototype passage before the existing task-script callout

Replace the current intro paragraph with:

> Testing happened in two rounds, on two different builds.
>
> Before any code, the orders page was tested on paper. The prototype mirrored the three-tiered stand, with three buttons for Tier 1, Tier 2, and Tier 3. Each button opened a dialog of dishes for that tier. Diners could pick up to three dishes per layer, and tap again to remove one. Holding a selection showed allergy and ingredient information. Tapping outside closed the dialog. A drinks button sat top-right, continue bottom-right.
>
> We tested two layout concepts against each other with several peers, using Wizard of Oz: manually simulating the interface's responses rather than building it. One version kept all three tiers visible throughout ordering. The other zoomed in on the tier being customised, fading the rest out.
>
> Once the LiveCode prototype was built, we ran a second round. Two participants, each given a persona, had one task: place and pay for an order using the digital ordering system.

Keep the existing task-script `.callout` block as-is, but add a small label clarifying it belongs to round two — e.g. change `Task script · given to participants` to `Task script · round two, LiveCode prototype`.

The existing comparison table (Option 01 · Chosen / Option 02) stays as-is structurally, but confirm its framing now reads correctly as round-one output (peer testing on paper prototypes), not something conducted with the same two participants as round two.

## Section 8 — replace the findings grid ("What testing revealed")

Replace the current 4-item `.find-grid` content with a two-part structure: a short paragraph covering round one's outcome, then the findings from round two.

**Round one outcome (new, add as a `.body` paragraph before the findings grid, under a "What testing revealed" method-label if one doesn't already introduce this):**

> The paper-prototype round settled the layout question. Full-tier view won clearly. Peers found it easier to assess their choices in one glance, without jumping between tiers. Populating the tray as they ordered worked like a progress bar, a form of visual storytelling shown to improve user experience (Li et al., 2020).

**Round two findings — replace the 4 existing `.find` cards with these, keeping the same card structure (`find-k` / `find-title` / `find-text`):**

1. **Key finding — Strong concept, minimal friction**: Both participants completed the task with only minor issues.
2. **Gap identified — Menu switching felt rigid**: Participants wanted to move between the food tiers and the drinks menu to build better pairings, instead of a fixed one-way sequence.
3. **Accessibility note — Onboarding needed clearer cues**: Especially for diners whose first language isn't English.
4. **Loyalty screen — Validated the Help feature**: One participant couldn't make sense of the loyalty screen at first, then used the Help button to resolve it. The Help feature had been built speculatively, anticipating diners might need a server on standby for exactly this kind of moment — testing confirmed the anticipation was right.

## Section 9 ("Screens") — add the paper prototype before the LiveCode gallery

Insert a short passage before the existing screenshot gallery, introducing it as the "after" to the paper prototype's "before":

> The paper prototype came first. Three tier buttons sat beside an empty stand graphic. Dialogs stood in for what would later become radio-button menus. A mouse-hold gesture did the job a real tap would later do for allergy info. It was meant to be disposable, cheap enough to throw away a layout that didn't work.
>
> The four LiveCode screens below are what that paper version became, once the tier-selection concept was validated.

If a paper-prototype image/asset exists (referenced as Figure 4/5 in the source PDF), ask me for the file before assuming there's nothing to show — don't leave this as text-only if a real image is available. If no image exists, text-only is fine.

## Section 11 ("If I Built This Again") — tighten stack item 01

Replace the current item 01 ("Memory & navigation" — "Use stored variables to support back buttons and order revisions...") with:

> **Menu switching**
> Let diners move freely between the food tiers and the drinks menu instead of following one fixed sequence. This was the clearest, most specific request from testing.
> *Back-button navigation is found especially user-friendly in ordering & shopping interfaces — Obendorf et al., 2007*

Keep the existing citation. Items 02–06 are unchanged.

## Constraints

- Don't invent details beyond what's in the source PDF — if something about the paper-prototype phase isn't specified (exact peer count, exact date), leave it general rather than inventing a number.
- Keep the Li et al. (2020) and Obendorf et al. (2007) citations exactly as worded above; don't duplicate the Li citation if it's already used elsewhere in the file.
- No new colors, fonts, or component types needed — this pass reuses the existing `.callout`, `.find`, `.stack-row`, and `.body` patterns already in the file.
- Confirm you're editing `Projects/sip-scones.html`.
