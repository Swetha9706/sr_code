# Swetha Ramachandran — Portfolio

This is the source code for your portfolio website.

---

## How to update your portfolio

Whenever you want to change something — a project, your bio, a colour, anything — follow these steps:

### Step 1 — Make your changes
Open Claude Code and describe what you want to change. For example:
- *"Change the email address in the contact section of aboutme.html"*
- *"Add a new project card to work.html"*
- *"Update the bio text in aboutme.html"*

Claude will make the changes directly to the files.

### Step 2 — Push to GitHub
Once Claude has made the changes, tell it:

> *"Push the updates to GitHub"*

Claude will commit and push everything for you.

### Step 3 — Upload to cPanel
Log in to your cPanel hosting, go to **File Manager → public_html**, and re-upload whichever file was changed. It will overwrite the old version and your live site will update immediately.

---

## File map — what lives where

| File | What it is |
|---|---|
| `index.html` | Home page |
| `aboutme.html` | About Me page |
| `work.html` | My Work page (project grid) |
| `Projects/kretha.html` | Krētha case study |
| `Projects/futurescope_Remix.html` | FutureScope case study |
| `Projects/sip-scones.html` | Sip & Scones case study |
| `10 1.jpg`, `Online world-connect 1.png`, etc. | Images used on the site |

---

## cPanel upload reminder

When uploading to cPanel, the folder structure must match exactly:

```
public_html/
├── index.html
├── aboutme.html
├── work.html
├── 10 1.jpg
├── Online world-connect 1.png
├── Pic.png
├── Vector.png
└── Projects/
    ├── kretha.html
    ├── futurescope_Remix.html
    └── sip-scones.html
```

If you add a new image, upload it to the same folder as the HTML file that uses it.
