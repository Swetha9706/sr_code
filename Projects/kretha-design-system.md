# Krētha Design System
**Design System · v1.0 · October 2024 · Product Development**

A clean, product-focused design language built for clarity and confidence across every surface.

---

## Color Palette

| Name | Hex | Usage |
|------|-----|-------|
| Navy | `#0d1a33` | Primary brand, text, backgrounds |
| Blue | `#3B6BF0` | Actions, links, interactive elements |
| Blue Light | `#6B91F7` | Hover states, accents |
| Blue Pale | `#EEF2FE` | Backgrounds, tags, highlights |
| Muted | `#838383` | Secondary text, placeholders, captions |
| Border | `#e8e8e8` | Dividers, input borders, card borders |
| Success | `#1D9E75` | Positive states, published, saved |
| Warning | `#BA7517` | Pending, review required |
| Danger | `#E24B4A` | Errors, destructive actions |

---

## Typography

### Fonts

| Role | Family | Weight |
|------|--------|--------|
| Display | Paytone One | 400 (Regular) |
| Body | DM Sans | 300, 400, 500, 600 |
| Mono | DM Mono | 400, 500 |

### Scale

| Level | Font | Size | Weight | Usage |
|-------|------|------|--------|-------|
| Display / H1 | Paytone One | 32–42px | 400 | Hero headings, page titles |
| Heading / H2 | DM Sans | 22px | 600 | Section headings |
| Heading / H3 | DM Sans | 16px | 600 | Card titles, subsections |
| Body | DM Sans | 14px | 400 | Paragraphs, descriptions |
| Caption | DM Sans | 12px | 400 | Metadata, hints, timestamps |
| Mono / Code | DM Mono | 12px | 400 | Code tokens, hex values, labels |

---

## Spacing Scale

Based on an 8-point grid system.

| Token | Value | Usage |
|-------|-------|-------|
| xs | 4px | Icon gaps, tight inline spacing |
| sm | 8px | Component internal padding |
| md | 12px | Input padding, small gaps |
| base | 16px | Default padding, list spacing |
| lg | 24px | Section gaps, card padding |
| xl | 32px | Large component spacing |
| 2xl | 48px | Section separation |
| 3xl | 64px | Page-level layout gaps |

---

## Border Radius

| Name | Value | Usage |
|------|-------|-------|
| Sharp | 4px | Compact elements, changelog header |
| Default | 8px | Buttons, inputs, badges |
| Card | 12px | Cards, panels, dropdowns |
| Large | 16px | Hero sections, modals |
| Pill | 100px | Tags, badges, avatars |

---

## Buttons

### Variants

| Variant | Background | Text | Border | Usage |
|---------|------------|------|--------|-------|
| Primary | `#0d1a33` | White | — | Main actions |
| Blue | `#3B6BF0` | White | — | Secondary CTA |
| Outline | Transparent | `#0d1a33` | `#e8e8e8` | Tertiary actions |
| Ghost | Transparent | `#838383` | — | Minimal actions |
| Danger | `#E24B4A` | White | — | Destructive actions |

### Sizes

| Size | Font | Padding | Border Radius |
|------|------|---------|---------------|
| Small | 12px | 5px 12px | 6px |
| Default | 14px | 8px 18px | 8px |
| Large | 15px | 11px 24px | 10px |

---

## Form Inputs

### States

| State | Border | Notes |
|-------|--------|-------|
| Default | `#e8e8e8` | Resting state |
| Focus | `#3B6BF0` | Active / selected |
| Error | `#E24B4A` | Validation failure |
| Disabled | `#e8e8e8` | Reduced opacity, not interactive |

### Specs

- **Font:** DM Sans, 14px, weight 400
- **Padding:** 8px 12px
- **Border radius:** 8px
- **Hint text:** 11px, `#838383`
- **Error text:** 11px, `#E24B4A`

---

## Badges & Tags

| Variant | Background | Text Color | Usage |
|---------|------------|------------|-------|
| Default | `#f0f0f0` | `#0d1a33` | Neutral labels |
| Primary | `#EEF2FE` | `#3B6BF0` | Active, informational |
| Success | `#E1F5EE` | `#0F6E56` | Published, completed |
| Warning | `#FAEEDA` | `#854F0B` | Pending, review |
| Danger | `#FCEBEB` | `#A32D2D` | Error, failed |
| Navy | `#0d1a33` | White | Version numbers, key labels |

**Specs:** 11px · DM Sans · weight 500 · border-radius 20px · padding 3px 10px

---

## Alerts

| Type | Background | Border | Icon |
|------|------------|--------|------|
| Info | `#EEF2FE` | `#b5c9f9` | `ti-info-circle` |
| Success | `#E1F5EE` | `#9FE1CB` | `ti-circle-check` |
| Warning | `#FAEEDA` | `#FAC775` | `ti-alert-triangle` |
| Danger | `#FCEBEB` | `#F7C1C1` | `ti-alert-circle` |

**Structure:** Icon + Title (600 weight) + Message (80% opacity, 12px)

---

## Cards

### Stat Card

```
┌─────────────────────────┐
│ Card Title              │
│ Subtitle / period       │
│                         │
│  4,218                  │
│  ↑ 12% vs last month    │
└─────────────────────────┘
```

- **Border:** 0.5px solid `#e8e8e8`
- **Border radius:** 12px
- **Padding:** 1.25rem
- **Stat font:** Paytone One, 28px
- **Trend up:** `#1D9E75` · Trend down: `#E24B4A`

---

## Changelog Component

Faithfully reproduced from the Figma file.

```
┌──────────────────────────────────────┐
│  Changelog                           │
├──────────────────────────────────────┤
│  ●                                   │
│  │  October 15, 2024                 │
│  │  [avatar] iMedhas · Oct 15, 2024  │
│  │  — Testing Versions               │
│  ●                                   │
│     November 2, 2024                 │
│     [avatar] kretha-team             │
│     — Component library v1.0 shipped │
├──────────────────────────────────────┤
│  Made with Design version            │
└──────────────────────────────────────┘
```

### Specs

| Element | Style |
|---------|-------|
| Header title | DM Sans, 18px, weight 600, `#0d1a33` |
| Date | DM Sans, 13px, weight 600, `#0d1a33` |
| Meta / author | DM Sans, 11px, weight 400, `#838383` |
| Description | DM Sans, 12px, weight 400, `#555555` |
| Timeline dot | 9px circle, border 2px, color matches status |
| Timeline line | 1px, `#e8e8e8` |
| Footer | DM Sans, 10px, `#838383` |
| Card border | 1px solid `#e8e8e8`, border-radius 8px |
| Box shadow | `0px 12px 24px rgba(0,0,0,0.1)` |

---

## Shadows

| Name | Value | Usage |
|------|-------|-------|
| Subtle | `0 1px 3px rgba(0,0,0,0.06), 0 4px 12px rgba(0,0,0,0.06)` | Cards, panels |
| Medium | `0 4px 16px rgba(0,0,0,0.10)` | Dropdowns, popovers |
| Elevated | `0px 12px 24px rgba(0,0,0,0.10)` | Modals, changelog card |

---

## Icons

Krētha uses **Tabler Icons** (outline style). Common icons:

| Icon | Class | Usage |
|------|-------|-------|
| Add | `ti-plus` | Create actions |
| Upload | `ti-upload` | File upload |
| Download | `ti-download` | Export |
| Settings | `ti-settings` | Configuration |
| User | `ti-user` | Profile, account |
| Search | `ti-search` | Search inputs |
| Info | `ti-info-circle` | Info alerts |
| Check | `ti-circle-check` | Success states |
| Warning | `ti-alert-triangle` | Warning alerts |
| Error | `ti-alert-circle` | Error alerts |
| Trash | `ti-trash` | Delete actions |
| Edit | `ti-edit` | Edit actions |

---

## Usage Guidelines

### Do
- Use **Navy** (`#0d1a33`) for primary text and high-emphasis UI
- Use **Blue** (`#3B6BF0`) for interactive elements and calls-to-action
- Use **Paytone One** only for display/hero text — keep body copy in DM Sans
- Maintain 8px minimum spacing between interactive elements
- Use semantic colors (success/warning/danger) consistently across alerts, badges, and states
- Apply 0.5px borders for card separators and subtle divisions

### Don't
- Mix Paytone One with other display fonts
- Use Danger red for non-error contexts
- Apply box shadows to flat/ghost elements
- Use muted gray (`#838383`) for primary interactive text
- Override border-radius inconsistently within a component type

---

*Krētha Design System · v1.0 · Made with Design version*
