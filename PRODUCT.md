# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Users

Primary: **in-house recruiters and hiring managers** evaluating Swetha for a full-time product/UX design role. They arrive skimming fast and need quick proof of craft, range, and process depth before committing to a case study.

Secondary: **prospective freelance / agency clients** assessing whether to hire her for project work. The site should serve them too, but recruiter fit comes first. Design decisions resolve toward the recruiter when the two audiences conflict.

## Product Purpose

A personal design portfolio for Swetha Ramachandran (UX researcher, UI designer, and graphic designer). It exists to convert a cold visitor into a warm contact — but only after the work has done the persuading. Success is a message/email that arrives *because* the case studies earned trust, not a contact form clicked in a vacuum. The work carries the argument; the "Say hello" CTA closes it.

## Positioning

Design "that thinks, then looks good" — research-rooted UX paired with a graphic-design sensibility, refined through visible craft. The differentiator is the combination: rigorous user research *and* editorial/brand/type fluency in one designer, presented through a warm, human voice rather than corporate polish. Range across digital product, brand identity, and editorial/print is the proof of that combination.

## Operating Context

- Multi-page static site. Core pages: `index.html` (home), `aboutme.html` (about), `work.html` (project grid), `swethafullportfolio.html` (full portfolio view). Case studies live in `/Projects/`.
- Visitor journey: land on home hero → scan selected work → open a case study → reach the "off the clock" personal section → contact. The About page carries the fuller narrative and credentials.
- `-v2.html` variants exist in the root (`index-v2.html`, `aboutme-v2.html`, `Projects/sip-scones-v2.html`) as in-progress redesign drafts alongside the shipped pages.

## Capabilities and Constraints

- Static HTML/CSS only — no framework, no build step, no JavaScript framework. CSS is embedded per-page in `<style>` tags. This is a deliberate, durable constraint; new work stays within it.
- Deploys two ways: GitHub Pages (auto from `main`) and cPanel (manual re-upload of changed files to `public_html`). Push only to `main`.
- Fonts are the committed families: Self Modern (hero name only), Cormorant Garamond (headings/brand), Lora (body), DM Mono (utility/labels). Playfair Display is explicitly banned.

## Brand Commitments

- Name: **Swetha Ramachandran**. Signature name is set in Self Modern (display), fallback Cormorant Garamond.
- Voice: conversational, warm, human — "Chat with me," "Think we vibe?," "Hi, I'm ___." Approachable over corporate. Copy leans into the messy, human side of design.
- Visual world: warm editorial-minimalist pastel system, documented in CLAUDE.md ("Portfolio — Design Direction 3a"). Light palette only — never pure white (#ffffff) or pure black (#000000), never solid dark backgrounds. Accent color is Ultraviolet (#5642EA); work cards each carry their own pastel accent while the page shell stays neutral.
- Tone signature: "made with paper & ink" footer; small hand-drawn accents (squiggle, flower) used sparingly.

## Evidence on Hand

Real, built case studies (treat as genuine work; paths are actual pages):
- **Krētha** — `Projects/kretha.html`. B2B SaaS platform redesign for a procurement marketplace; research-driven UX and refined interface system.
- **FutureScope** — `Projects/futurescope_Remix.html`. Brand identity for a futurist consulting firm; visual-language system.
- **Sip & Scones** — `Projects/sip-scones.html`. Mobile UX for a cozy café ordering app; micro-interactions and browse-to-checkout flow.

Real contact: **swetha.ramachandran17@gmail.com**; plus Instagram and read.cv links (verify handles before relying on them).

Real bio/experience (in the live `aboutme.html`, promoted from the v2 draft on 2026-08-05): based in Pune; UI/UX Designer at **iMedhas Consultancy Services** (Hyderabad) leading Krētha; **MSc User Experience Engineering, Goldsmiths, University of London**; earlier roles at **Rage Communications** (Chennai), **Remidio Innovative Solutions** (Bangalore), and **Stirred Creative Advertising** (Bangalore, clients incl. Digit Insurance, CGH Earth, Harman); **B.Des Visual Communication & Strategic Branding, Srishti Institute** (Bangalore). The iMedhas → Krētha link matches the real case study, so treat this experience as genuine — but confirm dates/titles with Swetha before citing externally.

**Retired placeholder (do NOT reuse):** the old `aboutme.html` design listed fabricated employers (Nucleus Design Co., Lightwave Agency) and round-number stats (5+ years, 40+ projects, 20 clients, 3 awards). That design was replaced; those specifics are template filler and must never be recorded, cited, or expanded as truth. Where a page needs credentials or numbers, request confirmed values rather than inventing them.

## Product Principles

1. **The work persuades; contact closes.** Order the experience so a visitor is convinced by case studies before the CTA asks for anything.
2. **Recruiter-first, skimmable.** Reward a fast skim with immediate proof of craft and range; let depth reward the visitor who stays.
3. **Range is the argument.** Show UX research, product UI, brand identity, and editorial/graphic work together — the breadth is the differentiator, not a distraction.
4. **Warm, human voice — never corporate.** Every headline and label sounds like a person, not a case-study template.
5. **No fabricated credentials.** Never invent or inflate employers, metrics, clients, or awards. Unconfirmed claims stay out until Swetha verifies them.

## Accessibility & Inclusion

No formal standard established. The committed palette carries a real risk of low contrast (pastel accents, muted secondary text `#6a6273` on paper `#FCFBFA`); future work should check text/background contrast against WCAG AA and not let the light-on-light aesthetic drop legibility.
