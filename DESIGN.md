---
name: Swetha Ramachandran — Portfolio
description: A warm pastel-editorial design portfolio where a neutral paper shell frames loud, tactile work cards.
colors:
  paper: "#FCFBFA"
  card-base: "#EEEAF6"
  cotton-candy: "#F8D9FF"
  border: "#ddd6ec"
  ultraviolet: "#5642EA"
  highlighter: "#EBF985"
  nectar: "#FFCAA6"
  ice-blue: "#D4F5F9"
  lavender: "#CACAFF"
  plum: "#630F49"
  ink: "#141018"
  muted: "#575165"
typography:
  display:
    fontFamily: "'Self Modern Text', 'Cormorant Garamond', serif"
    fontSize: "clamp(2.6rem, 16vw, 104px)"
    fontWeight: 400
    lineHeight: 0.98
    letterSpacing: "-0.01em"
  headline:
    fontFamily: "'Cormorant Garamond', serif"
    fontSize: "clamp(2.8rem, 5vw, 5rem)"
    fontWeight: 600
    lineHeight: 0.93
    letterSpacing: "-0.025em"
  title:
    fontFamily: "'Cormorant Garamond', serif"
    fontSize: "1.25rem"
    fontWeight: 600
    lineHeight: 1.35
    letterSpacing: "-0.01em"
  body:
    fontFamily: "'Lora', serif"
    fontSize: "21px"
    fontWeight: 400
    lineHeight: 1.65
    letterSpacing: "normal"
  label:
    fontFamily: "'DM Mono', monospace"
    fontSize: "13px"
    fontWeight: 400
    lineHeight: 1.2
    letterSpacing: "0.18em"
  scale:
    label-2xs: "0.5625rem"
    label-xs: "0.62rem"
    label-sm: "0.7rem"
    label-12: "12px"
    label-base: "13px"
    label-lg: "14px"
    body-sm: "0.95rem"
    body: "1rem"
    body-lg: "18px"
    body-xl: "20px"
    body-2xl: "21px"
    title-sm: "1.3rem"
    title: "1.4rem"
    title-lg: "24px"
    heading-2xs: "1.15rem"
    heading-xs: "1.6rem"
    heading-sm: "1.8rem"
    heading: "1.9rem"
    heading-md: "2rem"
    heading-lg: "2.4rem"
    heading-xl: "2.6rem"
    heading-2xl: "2.8rem"
    heading-3xl: "3rem"
    heading-4xl: "3.2rem"
    heading-5xl: "3.5rem"
    display-sm: "34px"
    display: "5rem"
    display-lg: "6.2rem"
    display-xl: "104px"
rounded:
  tiny: "2px"
  sm: "8px"
  img: "14px"
  card: "28px"
  pill: "999px"
spacing:
  xs: "8px"
  sm: "16px"
  md: "28px"
  lg: "44px"
components:
  button-primary:
    backgroundColor: "{colors.ultraviolet}"
    textColor: "{colors.paper}"
    rounded: "{rounded.pill}"
    padding: "9px 18px"
  card-work:
    backgroundColor: "{colors.card-base}"
    textColor: "{colors.ink}"
    rounded: "{rounded.card}"
    padding: "2.2rem 2.2rem 1.8rem"
  footer:
    backgroundColor: "{colors.cotton-candy}"
    textColor: "{colors.ink}"
    padding: "44px"
---

# Design System: Swetha Ramachandran — Portfolio

## Overview

**Creative North Star: "The Soft Playground"**

This is a warm, pastel, personality-forward system built on paper and ink. The page shell is deliberately quiet — a soft off-white ground, restrained type, generous air — so that the work itself supplies every loud moment. Rounded pill shapes, scrolling marquee strips, hand-drawn squiggles, and tactile color-swap cards give the whole thing a friendly, made-by-a-human feel rather than corporate polish. It should read like an editorial magazine that decided to relax and play.

Color is the primary tool for depth and delight, not shadow. Surfaces sit flat on the paper; interest comes from tonal pastel layering, gently rotated floating images, and interaction that swaps a neutral card to a saturated accent. Ultraviolet is the one strong voice — it owns the chrome accents (eyebrows, marquees, CTAs, hover states) while the pastels stay reserved for the work cards. The result is calm at rest and warm on touch.

Explicitly rejected: dark mode, pure white (#ffffff) and pure black (#000000), neon, brutalism, dense data-heavy layouts, solid dark backgrounds anywhere, and heavy/bold type. Playfair Display is banned; Fraunces has crept into `aboutme.html` and is off-system.

**Key Characteristics:**
- A neutral paper shell that frames loud, colorful work.
- Warm and tactile: soft pill shapes, rounded 28px cards, friendly fills.
- Depth from color and layering, not shadows.
- One accent voice (Ultraviolet) against a pastel supporting cast.
- Hand-made touches — marquees, squiggles, "paper & ink" tone.

## Colors

A soft pastel palette on warm paper, where a single saturated accent does all the pointing and the pastels are held in reserve for the work.

### Primary
- **Ultraviolet** (#5642EA): The one strong voice. Nav CTA background, eyebrow rules, marquee strips, hover/focus states, active links, squiggle accents. Used sparingly against the neutral base.

### Secondary
Pastel card accents — each work card owns one, revealed on hover so color becomes an interaction reward:
- **Highlighter** (#EBF985): Krētha card hover fill.
- **Ice Blue** (#D4F5F9): FutureScope card hover fill.
- **Nectar** (#FFCAA6): Sip & Scones card hover fill.
- **Lavender** (#CACAFF): Available pastel accent for additional cards/tiles.

### Tertiary
- **Cotton Candy** (#F8D9FF): The footer surface and soft tinted panels — the one place a full pastel wash covers a whole region.
- **Plum** (#630F49): Dark accent for labels sitting on tinted/pastel cards where Ink would feel heavy.

### Neutral
- **Paper** (#FCFBFA): The page ground everywhere. Never pure white.
- **Card Base** (#EEEAF6): The resting fill of work cards before hover — a cool lavender-grey that reads as "waiting."
- **Ink** (#141018): Primary text and headlines. Never pure black.
- **Muted** (#575165): Secondary text, taglines, captions, copyright. Darkened from #6a6273 for WCAG AA/AAA contrast (7.3:1 on Paper).
- **Border** (#ddd6ec): Hairline dividers, underlines, and 1px separators.

### Named Rules
**The One Voice Rule.** Ultraviolet is the only saturated color allowed on the page shell (nav, eyebrows, marquees, CTAs, hover). Pastels belong to the work cards, never the chrome. Its rarity against the paper is what makes it read as intentional.

**The Color-Is-The-Hover Rule.** A work card's accent is hidden at rest (neutral Card Base) and only fills in on hover. Color is earned by interaction, not spent up front.

## Typography

**Display Font:** Self Modern (with Cormorant Garamond fallback) — the signature name ONLY.
**Editorial Serif:** Cormorant Garamond — section headings (italic 600), card names, nav brand, taglines.
**Body Font:** Lora — body copy and the hero tagline.
**Label/Mono Font:** DM Mono — nav links, eyebrows, tags, CTAs, marquees, card categories, copyright.

**Character:** An editorial serif voice — light-to-regular weight, oversized and confident but never heavy — paired with a precise monospace for all the small utilitarian type. The contrast between flowing italic serif headlines and clipped uppercase mono labels is the core typographic signature.

### Hierarchy
- **Display / Hero Name** (Self Modern, 400, clamp(2.6rem, 16vw, 104px), lh 0.98, -0.01em): The signature name in the hero only.
- **Headline** (Cormorant Garamond italic, 600, clamp(2.8rem, 5vw, 5rem), lh 0.93, -0.025em): Oversized section headings ("Selected work", "Get to know me").
- **Title** (Cormorant Garamond, 600, 1.25rem, -0.01em): Work card names; footer CTA scales this up to 34px.
- **Body** (Lora, 400, 18–21px, lh 1.65): Hero tagline and running prose; kept to ~560px measure.
- **Label** (DM Mono, 400–500, 12–14px, uppercase, letter-spacing 0.04em–0.18em): Eyebrows, nav links, tags, categories, marquees, copyright. Wider tracking (0.14–0.18em) for eyebrows and marquees; tighter (0.04em) for inline captions.

### Scale
The type ramp is intentionally broad and fluid — an editorial system, not a rigid 5-step scale. Serif headlines use `clamp()` across roughly 1.9rem → 6.2rem; DM Mono labels run fine, from ~9px (0.5625rem) micro-captions up to 14px. The enumerated steps in the frontmatter `typography.scale` are the discrete sizes the shipped system (this page and `index.html`) actually uses; stay on them rather than inventing new intermediate sizes.

### Named Rules
**The Signature-Name Rule.** Self Modern appears exactly once — the hero name. Everywhere else the serif voice is Cormorant Garamond.
**The Mono-For-Utility Rule.** Every small functional string (labels, tags, nav, timestamps, CTAs) is DM Mono uppercase with tracking; serifs are never used for utility text and mono is never used for headlines.
**The No-Fraunces Rule.** Do not load Playfair Display or Fraunces. The serif is Cormorant Garamond; the display face is Self Modern.

## Layout

Centered, generous, and single-column at heart. The hero is centered and oversized with short confident copy. Work is presented as a single centred column of full-width cards (max ~720px), flanked on wide viewports by thin 140px decorative side rails (`projects-with-deco` grid: `140px minmax(0,720px) 140px`) that drop away below the breakpoint. Section padding is generous (`4rem 3rem` desktop, `3.5rem 1.5rem` mobile); nothing is cramped. Marquee strips run full-bleed edge to edge. The footer is a two-part row (CTA left, meta right) that stacks to a column on mobile. Spacing rhythm steps roughly 8 / 16 / 28 / 44px.

## Elevation & Depth

Depth comes from **color and layering, not shadow**. Surfaces are flat on the paper at rest. The one place shadows appear is under the floating, gently-rotated card images (`0 12px 36px rgba(30,18,10,.14)`), which lift the collage imagery off the card face — a soft, warm, low shadow, never a hard drop. Cards themselves never lift; their depth signal is the color swap on hover, not a shadow or translate.

### Shadow Vocabulary (limited)
- **Floating image lift** (`box-shadow: 0 12px 36px rgba(30,18,10,.14)`): Only for the rotated collage images inside work cards.
- **Soft card rest** (`box-shadow: 0 8px 20px rgba(26,25,23,.08)`): Optional gentle ambient shadow for standalone tiles; keep barely-there.

### Named Rules
**The Flat-Paper Rule.** Surfaces are flat. If you reach for a shadow to create hierarchy, use color, tonal layering, or rotation instead. Shadows are reserved for lifting collage imagery, never for signalling interactivity.

## Shapes

Soft and rounded throughout — no sharp edges. The radius scale is deliberate: pills (999px) for all buttons, nav CTAs, and tags; large 28px corners on work cards; 14px on floating images; 8px on small surfaces. Floating images are set at slight rotations (±2–3°) for a hand-placed collage feel. Accents stay to simple primitives — arcs, circles, squiggle underlines, a small flower — never complex illustration. Hairline 1px borders in Border color handle dividers and underlines.

## Components

### Buttons
- **Shape:** Full pill (999px).
- **Primary (nav CTA):** Ultraviolet fill, Paper text, DM Mono 13px / 0.04em tracking, padding 9px 18px.
- **Hover:** Opacity drops to ~0.88; no lift, no color change. Unhurried.
- **Text CTA ("View work →", "Say hello →"):** DM Mono, Ultraviolet, no fill; the arrow gap widens on hover (`gap .55rem → .9rem`) as the micro-interaction.

### Cards / Containers
- **Corner Style:** 28px (work cards); 14px (floating images).
- **Background:** Card Base (#EEEAF6) at rest; swaps to the card's own pastel accent on hover (Highlighter / Ice Blue / Nectar).
- **Depth Strategy:** Flat surface; only the inner floating images carry a soft shadow. See Elevation.
- **Internal Padding:** 2.2rem sides, 1.8–2.2rem top/bottom; fixed height ~360px desktop / 300px mobile.
- **Behavior:** At rest the card shows rotated collage imagery; on hover the imagery fades out and a Cormorant Garamond description + arrow fade in over the accent fill. A gentle `background .45s cubic-bezier(0.22,1,0.36,1)` carries the color swap.

### Navigation
- **Style:** Sticky top bar on Paper; Cormorant Garamond brand mark left, DM Mono links + pill CTA right.
- **Links:** DM Mono, Muted, → Ultraviolet on hover (color .18s).
- **Mobile:** Links + CTA hidden behind a full-screen Paper overlay menu.

### Marquee (Signature Component)
- Full-bleed Ultraviolet strip, DM Mono uppercase text at 0.14–0.18em tracking in Paper/translucent white, scrolling infinitely (24–32s linear). Diamond/asterisk separators at reduced opacity. Used as a rhythmic divider and above the footer.

### Footer
- Cotton Candy surface. Cormorant Garamond "Say hello →" CTA at 34px (→ Ultraviolet on hover), DM Mono contact line + copyright in Muted. "Made with paper & ink" sign-off.

## Do's and Don'ts

### Do:
- **Do** keep the page shell neutral (Paper) and let the work cards supply all the saturated color.
- **Do** reserve Ultraviolet for chrome accents only, on ≤10% of any screen (The One Voice Rule).
- **Do** use full pills (999px) for buttons/tags and 28px corners for cards; nothing sharp.
- **Do** create depth with color, tonal layering, and slight rotation — not shadows (The Flat-Paper Rule).
- **Do** set utility text in DM Mono uppercase with tracking, and headlines in Cormorant Garamond italic.
- **Do** keep motion gentle and unhurried — `cubic-bezier(0.22,1,0.36,1)`, 0.2–0.65s, staggered reveals over scattered micro-interactions.

### Don't:
- **Don't** use pure white (#ffffff), pure black (#000000), or any solid dark background, in any section.
- **Don't** load Playfair Display or Fraunces; reconcile `aboutme.html` back to Cormorant Garamond (The No-Fraunces Rule).
- **Don't** put pastel accents on the nav, marquee, or footer chrome — pastels belong to work cards.
- **Don't** reach for shadows to signal interactivity; swap color instead.
- **Don't** set headlines heavy/bold — weight stays light-to-regular even when oversized.
