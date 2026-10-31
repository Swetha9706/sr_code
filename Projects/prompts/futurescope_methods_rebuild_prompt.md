# Prompt: Rebuild Research Methods Section — FutureScope

Rebuild the Research Methods section of the FutureScope case study page. Replace whatever is currently in the `<!-- ══ RESEARCH METHODS ══ -->` section (from the section opening tag down to and including the closing `</section>`) with the structure described below. Keep the eyebrow label, section title, and process strip exactly as they are — only replace the method content below the process strip.

The new content is a single `<article>` containing five labelled sections. Each section (except the last) uses a two-column flex layout: a narrow left label column (160px, DM Mono 0.72rem uppercase, letter-spacing 0.18em, colour `#630F49`, line-height 1.6) and a wide right content column (flex 1, min-width min(100%, 300px), flex-direction column, gap 36px). Sections are separated by `border-bottom: 1px solid #141018` with `padding: 28px 0`. The article itself has no gap and sits `margin-top: 2.5rem`.

---

## Section 1 — Method header

A `<header>` with `display: flex`, `align-items: baseline`, `gap: 20px`, `padding-bottom: 28px`, `border-bottom: 1px solid #141018`.

- Left: DM Mono 0.72rem uppercase `#575165` — "Method 01"
- Right: Cormorant Garamond italic 500, `clamp(1.3rem, 2.2vw, 1.6rem)`, colour `#575165` — "Understand user behaviours, attitudes, and pain points around retirement planning."

---

## Section 2 — Survey execution

Left label: "Survey / execution"

Right column contains, in order:

### Large display number
Cormorant Garamond 500, `clamp(5rem, 11vw, 8.5rem)`, colour `#630F49`, line-height 0.8, letter-spacing -0.04em — "12". Beside it, same font italic, `clamp(1.6rem, 3vw, 2.2rem)` — "participants, via Reddit and Discord".

### Stat grid
`<dl>` with `display: grid`, `grid-template-columns: repeat(auto-fit, minmax(130px, 1fr))`, `gap: 20px 28px`. Five items, each a `<div>` with `padding-top: 12px` and `border-top: 1px solid #ddd6ec`. `<dt>` in Cormorant Garamond 500, 2.6rem, letter-spacing -0.02em. `<dd>` in DM Mono 0.68rem uppercase `#575165`.

| `<dt>` | `<dd>` |
|---|---|
| 11 | UK-based |
| 35% | Aged 25–30 |
| 63% | Aged 35–45 |
| 90% | Male |
| ½ *(italic)* | Nearly, in tech |

### Prose paragraphs
Max-width 680px, font-size 1.02rem, line-height 1.8. Two paragraphs:

1. "12 participants were recruited through Reddit and Discord. 11 were based in the UK. 35% were aged 25–30 and 63% were between 35 and 45. The sample was heavily male (90%), and nearly half worked in tech."
2. "This group had above-average financial literacy." + `<em>` in Cormorant Garamond 600, 1.25em, `#630F49`: "All of them still avoided retirement planning and felt anxious about it." + "That ruled out a simple knowledge gap."

### Retirement duration strip
Label: DM Mono 0.68rem uppercase `#575165` — "Expected retirement duration". Then two rows, each `display: flex`, `align-items: baseline`, `gap: 20px`, `padding: 10px 0`, `border-bottom: 1px solid #ddd6ec`.

| Left (DM Mono 0.75rem uppercase, fixed 120px) | Right (Cormorant Garamond 500, `clamp(2rem, 4vw, 2.8rem)`) |
|---|---|
| Under 30 | 10–15 *years* (years: 0.55em `#575165` non-italic) |
| Over 30 | 15–20 *years* — number in `#630F49` |

### Final paragraph
Same prose style. Ends with `<em>` in Cormorant Garamond 600, 1.25em, `#630F49` around: "travel, gardening, and pottery". Full text: "The only measurable age difference was expected retirement duration. In all other respects, confusion was consistent across ages. Around 50% said retirement did not factor into major purchasing decisions. When asked what a typical retirement day might look like, participants described [travel, gardening, and pottery] — but had no savings strategy aligned with any of it."

---

## Section 3 — Interview execution

Left label: "Interview / execution"

Right column contains, in order:

### Intro paragraph
"Four in-depth interviews with individuals aged 27–42. Both methods used a Buzzfeed-style quiz as a boundary object — drawn from Frith et al. (2005) and Bagnoli (2009) — with unlabelled imagery so participants could describe their future without being anchored by category labels."

### Display number pair
`display: flex`, `flex-wrap: wrap`, `align-items: baseline`, `gap: 12px 36px`.

- Left: Cormorant Garamond 500, `clamp(2.6rem, 6vw, 4.4rem)`, line-height 0.9, letter-spacing -0.03em — "£45,626". Below: DM Mono 0.68rem uppercase `#575165` — "per year".
- Middle: Cormorant Garamond italic 2rem `#575165` — "≈"
- Right: same as left but colour `#630F49` — "£950,000". Below: DM Mono 0.68rem uppercase `#575165` — "in retirement funds".

### Supporting paragraph
"At the end of each quiz, participants received a savings estimate from the HSBC Retirement Calculator. A luxury lifestyle result came to approximately £45,626 per year — around £950,000 in retirement funds." + `<em>` in Cormorant Garamond 600, 1.25em, `#630F49`: "Three of the four were surprised." + "One found it close to what they had been aiming for."

### Quote 1
`<blockquote>` with `display: flex`, `flex-direction: column`, `gap: 14px`. Quote text in Cormorant Garamond italic 500, `clamp(1.6rem, 3.5vw, 2.6rem)`, line-height 1.15, letter-spacing -0.02em. Opening `"` as `<span>` in `#630F49`. Attribution in DM Mono 0.68rem uppercase `#630F49`.

> "I'm nowhere near saving that amount, but this result makes me feel less anxious. It's about the sum I've been aiming for."
>
> — Interview participant — P2, male, 40

### Bridging paragraph
"A question posed after the Netflix preference slide —" + `<em>` in Cormorant Garamond 600, 1.2em, `#630F49`: '"Would you consider yourself an optimist or a realist?"' + "— surfaced something the direct retirement questions had not. One participant who had chosen a luxury lifestyle result responded:"

### Quote 2
Same blockquote structure as Quote 1.

> "I don't consider myself someone with a luxury lifestyle, but I think it's good to have ambitious goals."
>
> — Interview participant — P1, male, 42

---

## Section 4 — From finding to design decision

Left label: "From finding / to design / decision"

Right: `<ol>` with `list-style: none`, `display: flex`, `flex-direction: column`. Four `<li>` items, each `display: flex`, `flex-wrap: wrap`, `gap: 8px 28px`. Label column is 200px fixed. Text column is `flex: 1`, `min-width: 240px`, font-size 1rem, line-height 1.75.

### Item 1
`padding: 0 0 24px`, `border-bottom: 1px solid #ddd6ec`

- Label (Cormorant Garamond italic 500, 1.6rem, `#630F49`): "Personality question"
- Text: "The optimist/realist question directly informed the onboarding quiz. Framing the choice as optimist versus realist lets the service calibrate its tone to the user's actual outlook."

### Item 2
`padding: 24px 0`, `border-bottom: 1px solid #ddd6ec`

- Label: "Spectrum-based profiles"
- Text: "Removing labels from quiz options reduced bias and let participants respond by instinct. Several wanted to select more than one option — a signal that lifestyle expectations resist clean categories. This led to a spectrum-based profile system rather than fixed types."

### Item 3
`padding: 24px 0`, `border-bottom: 1px solid #ddd6ec`

- Label (Cormorant Garamond 500, 2.4rem, letter-spacing -0.02em, `#630F49`): "4 / 4"
- Text: "All four participants said they would use the service. The concept was not just analytically sound — users wanted it."

### Item 4
`padding-top: 24px`

A single paragraph, max-width 640px, Cormorant Garamond italic 1.25rem, line-height 1.5, `#575165`. Opens with `<span>` in DM Mono non-italic 0.68rem uppercase `#141018`: "McGonigal (2017)". Then: "— when asked to think about their distant future, people neurologically envision someone else, making choices for that self harder. This grounded the decision to design toward imagination rather than information."

---

## Section 5 — Core insight

Full-width, no two-column layout. `display: flex`, `flex-direction: column`, `gap: 28px`, `padding-top: 28px`.

- Label: DM Mono 0.72rem uppercase, letter-spacing 0.2em, `#630F49` — "The Core Insight"
- Main text: Cormorant Garamond 400, `clamp(1.6rem, 3vw, 2.6rem)`, line-height 1.15, letter-spacing -0.02em, max-width 820px — "Regardless of age, people are aimless about retirement planning not because they lack information, but because they lack" + `<em>` in font-weight 600 `#630F49` "imagination" + "about their future selves."
- Sub-line: Cormorant Garamond italic 500, `clamp(1.05rem, 1.6vw, 1.35rem)`, `#630F49` — "Most tools count. None help you imagine."

---

## Notes

- Fonts already loaded: Cormorant Garamond (Google Fonts), DM Mono (Google Fonts)
- Colours: `#630F49` plum accent — `#575165` muted — `#ddd6ec` border — `#141018` ink
- All styling via inline styles — no new CSS classes needed
- Do not touch anything outside the `<!-- ══ RESEARCH METHODS ══ -->` section
