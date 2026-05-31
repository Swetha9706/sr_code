# Portfolio Links to Update

Here are all the locations where you need to replace placeholder links with your actual contact information:

## 1. LinkedIn Profile

**Current placeholder:** `https://www.linkedin.com/in/your-profile`

**Files to update:**
- [index.html:629](../index.html#L629) — Footer contact
- [Projects/futurescope_Remix.html](../Projects/futurescope_Remix.html) — Footer links (updated)

**What to change:**
```html
<!-- BEFORE -->
<a href="https://www.linkedin.com/in/your-profile" target="_blank" rel="noopener noreferrer">LinkedIn</a>

<!-- AFTER (replace your-username with your actual LinkedIn) -->
<a href="https://www.linkedin.com/in/swetha-ramachandran" target="_blank" rel="noopener noreferrer">LinkedIn</a>
```

---

## 2. Email Address

**Current email used:** `swetha.ramachandran17@gmail.com`

This email is already set throughout the portfolio (cases studies CTAs, footer contact). 
**If you want to change it**, search and replace in these files:

- [index.html](../index.html) — Lines 628-630
- [Projects/kretha.html](../Projects/kretha.html) — CTA section
- [Projects/futurescope_Remix.html](../Projects/futurescope_Remix.html) — Footer + CTA
- [Projects/sip-scones.html](../Projects/sip-scones.html) — CTA section

**Current usage:**
```html
<!-- Email links (mailto: automatically opens email client) -->
<a href="mailto:swetha.ramachandran17@gmail.com">Email me</a>
<a href="mailto:swetha.ramachandran17@gmail.com">Get in Touch</a>
```

---

## 3. Social Media / Other Profiles

**Dribbble, GitHub, Twitter, etc.:**

Currently, placeholder social links are not shown (they were removed in cleanup). If you want to add them back:

### Option A: Add to Footer (index.html)
After the LinkedIn link, add:
```html
<a href="https://dribbble.com/your-username" target="_blank" rel="noopener">Dribbble</a>
<a href="https://twitter.com/your-handle" target="_blank" rel="noopener">Twitter</a>
<a href="https://github.com/your-username" target="_blank" rel="noopener">GitHub</a>
```

### Option B: Add to Case Study Footers
In each case study (Kretha, FutureScope, Sip-Scones), the footer has links. You can add social there too.

---

## 4. Phone Number (Optional)

**Currently removed** from the footer (as per your request). If you want to add it back:

```html
<p><a href="tel:+919876543210">+91 98765 43210</a></p>
```

Location: [index.html:630](../index.html#L630) (after email)

---

## Quick Checklist

- [ ] Update LinkedIn URL to your actual profile
- [ ] Confirm `swetha.ramachandran17@gmail.com` is correct (or search/replace it)
- [ ] Add social media links if desired (Dribbble, Twitter, etc.)
- [ ] Test all mailto: and tel: links on desktop and mobile
- [ ] Verify external links open in new tabs (target="_blank" is set)

---

## Files Modified in Phase 1

✅ **Completed:**
1. Removed "Other Works" nav link from index.html
2. Added real footer contact with mailto: email links
3. Added breadcrumb navigation to all case studies (Kretha, FutureScope, Sip-Scones)
4. Added CTA sections to end of each case study

**Ready for Phase 2:** Content enhancements (problem statements, about page personality, testimonials)
