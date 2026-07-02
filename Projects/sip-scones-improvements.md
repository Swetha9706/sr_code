# Sip & Scones — Case Study Improvement Plan

## What's already working

- Strong dark hero with project metadata (Tools, Role, Brief, Outcome)
- Scroll progress bar and smooth reveal animations
- Visual flow journey pills showing the user's path
- Feature cards grid — readable and well-structured
- "What comes next" future scope section
- "Final Thoughts" gives a reflective close
- All referenced images exist and should render correctly
- Responsive layout handles mobile well

---

## Issues to fix (priority order)

---

### 1. Missing problem statement — *High priority*

**What's wrong:** The page opens with "User Needs" but never answers: *What problem were we solving? Why does it exist? Who has it?*

**What to add:** A dedicated **Problem** section before "User Needs", with:
- The context: why tablet ordering at a café?
- The pain point: what's broken about the current experience (paper menus, server dependency, ordering delay)?
- A crisp one-sentence problem statement, e.g.:  
  > *"How might we make afternoon tea ordering feel as elegant and unhurried as the ritual itself — without requiring staff to be present at every step?"*

**Where to insert:** Between the hero section and the current "User Needs" section.

---

### 2. No research methods section — *High priority*

**What's wrong:** The case study jumps from concept to testing with no explanation of *how* user needs were discovered. There's no mention of desk research, observations, or interviews before the prototype phase.

**What to add:** A **Research** section covering:
- What methods were used to understand afternoon tea context (secondary research? observations? competitor audit?)
- What questions you were trying to answer
- What the key early findings were that shaped the concept

Even one paragraph and two or three bullet-pointed insights would be enough. Without this, it reads like the concept came from nowhere.

---

### 3. "Both users" framing is underselling the work — *High priority*

**What's wrong:** "Both users completed their task with only minor issues" reveals this was tested with just 2 people, which can undermine credibility if not framed correctly.

**What to do:** Be direct and confident about it. Add a small metadata note to the testing section:

> *Small-scale guerrilla testing with 2 participants — sufficient for a formative prototype round focused on concept validation, not statistical significance.*

This is honest, shows you understand research methodology, and removes the risk that a reviewer misreads it as a limitation you're hiding.

---

### 4. Solo vs. team context is missing — *Medium priority*

**What's wrong:** The hero metadata says "Research, user flows, interface prototyping, usability testing, and LiveCode implementation" — a full-stack list — but doesn't say if this was a solo project or a team effort.

**What to add:** One of these in the hero meta row or a project context section:
- "Solo project" (if it was)
- "2-person team — I led research and UX; [name] handled LiveCode" (if it was collaborative)

Recruiters and hiring managers will want to know.

---

### 5. The pull quote is attributed to yourself — *Medium priority*

**What's wrong:** The quote *"Technology should enhance the experience, not disrupt it."* is cited as "Design principle, Sip & Scones" — meaning you wrote it. Pull quotes work best when they come from users or are framed as a hypothesis you tested.

**Options:**
- Replace with a real user quote from testing (even paraphrased: *"I just wanted to see the whole tray at once"*)
- Or reframe it as a hypothesis: *"We entered the project with one guiding principle: ..."* and drop the fake citation

---

### 6. User testing findings have no hierarchy — *Medium priority*

**What's wrong:** The six testing findings cards are presented as equal-weight insights, but they're not. "Full-tier view felt more intuitive" is the pivotal finding; "Minimal friction" is a supporting validation. They read as a flat list.

**What to do:** Restructure into two visual tiers:
- **Primary finding** (larger card or callout box): Full-tier view won — and why this mattered
- **Supporting findings** (smaller grid): The other five points

This makes the section skim-readable and shows design judgment about what was most important.

---

### 7. No Figma prototype link — *Medium priority*

**What's wrong:** For a UX case study, not linking to the interactive prototype is a missed opportunity. Hiring managers want to click through the experience, not just read about it.

**What to add:** A prototype link button in the hero metadata or in the "Key Features" section:

```html
<a href="[your-figma-link]" target="_blank" class="fl">View prototype →</a>
```

If the prototype is in LiveCode only and not shareable, note that explicitly: *"Live prototype built in LiveCode — not publicly hosted; screenshots and flow shown below."*

---

### 8. "What comes next" reads as a to-do list — *Low priority*

**What's wrong:** The six "What comes next" items are framed as future features. They'd be stronger framed as reflective designer insights: what would *you* do differently, and what did you learn that drove each decision?

**Suggested reframe:** Change the section label from "What comes next" to "If I built this again" and lead with a short paragraph:

> *Testing with real users surfaced gaps I wouldn't have caught alone. These are the changes I'd prioritise in a second iteration, and why.*

---

### 9. CTA buttons use inline JavaScript hover — *Low priority (code quality)*

**What's wrong:** The two buttons at the bottom of the page use `onmouseover` / `onmouseout` attributes to handle hover states. This is fragile and harder to maintain.

**What to do:** Move hover styles into the `<style>` block and add a class to each button:

```css
.cta-btn-primary { ... }
.cta-btn-primary:hover { transform: scale(1.05); box-shadow: 0 6px 20px rgba(0,0,0,.15); }
```

---

### 10. CSS variable `--orange` is teal — *Low priority (code quality)*

**What's wrong:** `:root` defines `--orange: #387470`, which is a teal-green. This causes no visual bug but is confusing when reading the code.

**What to do:** Rename the variable to `--teal` or `--accent` and do a find-replace across the file. This is a minor cleanup, but worth doing to keep the codebase readable.

---

## Summary table

| # | Issue | Priority | Effort |
|---|-------|----------|--------|
| 1 | Add problem statement section | High | ~30 min |
| 2 | Add research methods section | High | ~30 min |
| 3 | Reframe "both users" testing note | High | 5 min |
| 4 | Clarify solo vs. team | Medium | 5 min |
| 5 | Fix pull quote attribution | Medium | 5 min |
| 6 | Restructure testing findings hierarchy | Medium | ~20 min |
| 7 | Add Figma prototype link | Medium | 5 min |
| 8 | Reframe "What comes next" section | Low | 10 min |
| 9 | Replace inline JS hover with CSS | Low | 10 min |
| 10 | Rename `--orange` variable to `--teal` | Low | 5 min |

---

## Suggested revised section order

```
Hero (existing)
↓
Problem Statement  ← NEW
↓
Research Methods   ← NEW
↓
User Needs (existing — becomes "Key Insights" from research)
↓
The Concept (existing)
↓
User Flow (existing)
↓
Key Features (existing)
↓
Prototyping & Testing (existing — add participant context)
↓
User Testing Findings (existing — restructure hierarchy)
↓
Evaluation (existing)
↓
Final Thoughts (existing — add personal "what I learned" line)
↓
CTA (existing)
↓
Footer (existing)
```
