# Prompt: Restructure Krētha Case Study

Read `CLAUDE.md`, `DESIGN.md`, and `PRODUCT.md` in this repo before doing anything — they define the design system, tech constraints, and product principles this case study has to follow.

Restructure `Projects/kretha.html` as a **new standalone draft** — save it as `Projects/kretha-restructured.html` (do not overwrite `Projects/kretha.html` or touch anything else in the live codebase). I want to review the draft, then merge the parts I like into the real file myself.

Use this structural template, adapted from a UX case study format I liked (Julia Fernandez's "Help Assist Her"), but apply it through the existing Krētha design system — don't introduce new fonts, colors, or component patterns:

## Format to follow

1. **Hero** — existing hero image, title, one-line value proposition (what Krētha does, for whom). Headline in Cormorant Garamond italic per DESIGN.md hierarchy — not the Self Modern display face, which is reserved for the signature name only.
2. **Quick-facts bar** — scannable meta row using DM Mono uppercase labels: Role / Platform / Stakeholders / Timeline (real values only — e.g. my actual role at iMedhas, B2B/web platform, whoever I worked with, real project timeline). No invented specifics.
3. **Brief + Overview** — 2-3 sentences in Lora body copy: why this project exists, my role on it, who else is involved.
4. **Problem discovery** — a question-style header ("What problem am I solving?") followed by a bolded, standalone problem statement in Cormorant Garamond, not buried in a paragraph.
5. **Research/validation section**, broken into named methods (e.g. "RESEARCH METHOD 01: STAKEHOLDER INTERVIEWS"), each with:
   - A question-style header
   - Big standalone stat callouts styled per the Title/Headline scale in DESIGN.md — but **only using numbers I actually have**. Per PRODUCT.md's "No fabricated credentials" principle, do not invent metrics (no made-up "%," "clicks reduced," or interview counts). If I don't have a hard number for something, phrase it qualitatively and flag it with `[NEEDS REAL NUMBER]` so I can fill it in.
6. **Research → Decision mapping** — the piece the original case study was missing: a short table or connected list showing which research finding led to which specific design decision. Don't leave this implicit.
7. **Hypothesis / "So what" statement** — one sentence, bolded, standalone.
8. **The Solution** — walk through 3-5 key features, each formatted as: short headline (Cormorant Garamond) → 1-2 sentence body (Lora) → screenshot, using the existing floating-image treatment (14px radius, slight rotation, soft shadow per DESIGN.md Elevation section — no drop shadows used to signal interactivity elsewhere).
9. **Reflection** — "Things I learned," including one honest "if I had more time" note. Don't force a fake happy ending if the project is still in progress — say so.
10. Keep all question-style section headers throughout — they're the backbone that makes the whole thing skimmable in under a minute.

## Design system constraints (non-negotiable)

- Static HTML/CSS only, styles embedded in `<style>` tags — no JS framework, no build step, per CLAUDE.md.
- Fonts: Self Modern (signature name only, do not reuse here), Cormorant Garamond (headings/titles), Lora (body), DM Mono (labels/eyebrows/tags). No Playfair Display, no Fraunces.
- Colors from the documented palette only: Paper `#FCFBFA` background, Ink `#141018` text, Muted `#6a6273` secondary text, Ultraviolet `#5642EA` as the single chrome accent, Card Base `#EEEAF6` at rest with the card's assigned pastel (Highlighter `#EBF985` for Krētha) on hover. Never pure white/black, never a solid dark background.
- Shapes: 28px card corners, 14px image corners, full pill (999px) buttons/tags. No sharp edges.
- Depth from color/layering, not shadows — shadows only for the floating collage images (Elevation section, DESIGN.md).
- Motion: gentle, `cubic-bezier(0.22,1,0.36,1)`, staggered reveals over scattered micro-interactions.
- Check text/background contrast for the stat callouts and labels against WCAG AA — PRODUCT.md flags pastel-on-paper and muted-on-paper as a known contrast risk.

## Content rules

- Every research finding must connect to a stated design decision — no orphaned stats.
- Keep persona/user-type sections tight — 2-3 max, each clearly differentiated (no repeated needs across personas), and relevant to a B2B procurement audience, not a consumer app.
- Voice stays warm and conversational per PRODUCT.md brand commitments — not corporate case-study template language — while still reading as credible to a recruiter skimming fast.
- Never invent employers, metrics, clients, dates, or outcomes. Where real data isn't available, mark it clearly rather than filling the gap.
- Pull actual content from `Projects/kretha.html` and any linked research/design assets already in the repo; ask me for anything not already documented rather than guessing.

## Deliverable

A new file, `Projects/kretha-restructured.html`, containing the full restructured case study on the existing design system — ready for me to review section by section before merging anything into `Projects/kretha.html`.
