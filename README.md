# Learn Git and GitHub

An interactive, bilingual (English / Français) module-based tutorial for **Git and GitHub**, assuming **zero prior knowledge** of version control. It follows the same module system as the parent project [Learn HTML, CSS & Accessible Web Design](../).

**Live site:** [https://humanities-data-lab.github.io/learn-git-and-github/](https://humanities-data-lab.github.io/learn-git-and-github/)

## Who it’s for

- Anyone new to version control, Git, or GitHub  
- **Digital Humanities** students and researchers: the course explains why version control matters for DH (reproducibility, collaboration, transparency, citing specific versions of corpora or editions)

## What’s inside

- **Version Control** – What it is and why it matters for Digital Humanities  
- **Git Basics** – Repositories, `git init`, `git add`, `git commit`, `git status`  
- **GitHub** – What GitHub is, creating a repo, `git push`, `git clone`, `git pull`  
- **Collaboration** – Good practices for DH projects (branches, pull requests, README, licensing)

Content is in **English** and **French** (via `translations.json`). Progress is stored in the URL hash so you can bookmark or share your place.

## How to run

From the **repository root** (so that `../styles.css` resolves):

```bash
# From learn-html-css-accessibility/
python3 -m http.server 8000
```

Then open: **http://localhost:8000/learn-git-github/index.html**

(Translations are loaded from `translations.json`; `fetch` requires a real HTTP server, not `file://`.)

## Structure

- **index.html** – Single-page React app: welcome screen, progress by section, lessons, glossary, certificate  
- **translations.json** – All UI and lesson strings for `en` and `fr`  
- **styles.css** – Overrides for the “command block” (read-only terminal-style commands); base layout and components come from **../styles.css** in the parent project  

The model matches the HTML/CSS course: categories, lessons keyed by id, `getTranslatedLesson()`, glossary tooltips, and a completion certificate.

## Certificate

Completing all lessons unlocks a shareable certificate (name and progress in the URL). No data is stored on any server.
