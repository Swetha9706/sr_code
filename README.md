# Swetha Ramachandran — Portfolio

Source code for Swetha Ramachandran's design portfolio website.

🔗 **Live site:** [siddharthsubramaniam1996.github.io/sr_code](https://siddharthsubramaniam1996.github.io/sr_code/)

## About

A personal portfolio showcasing UX/product design work, including case studies for Krētha, FutureScope, and Sip & Scones. Built with plain HTML and CSS — no framework, no build step.

## Project structure

```
sr_code/
├── index.html              ← Home page
├── aboutme.html            ← About Me
├── work.html               ← Project grid
├── swethafullportfolio.html
├── Projects/
│   ├── kretha.html         ← Krētha case study
│   ├── futurescope_Remix.html  ← FutureScope case study
│   ├── sip-scones.html     ← Sip & Scones case study
│   └── (project images)
└── (root-level images)
```

## Running locally

No setup needed — just open `index.html` in any browser.

```bash
git clone https://github.com/siddharthsubramaniam1996/sr_code.git
cd sr_code
open index.html
```

## Deployment

The site is deployed two ways:
1. **GitHub Pages** (auto-deploys from `main`)
2. **cPanel hosting** (manual upload to `public_html/`)

---

## Personal workflow notes

> The section below is a working guide for updating the site — not relevant to visitors.

### How to update

Open Claude Code and describe the change you want, e.g.:
- *"Change the email address in aboutme.html"*
- *"Add a new project card to work.html"*
- *"Update the bio text"*

Then say *"push the updates to GitHub"* — Claude will commit and push.

### cPanel upload

After pushing to GitHub, log in to cPanel → **File Manager → public_html**, and re-upload whichever file changed. The folder structure must match the layout above.

If you add a new image, upload it to the same folder as the HTML file that uses it.
