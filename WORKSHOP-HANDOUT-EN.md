# Learn Git and GitHub — Workshop Handout (English)

**Version control from zero — Essential for Digital Humanities**

Use this handout during the live workshop. It summarizes the key concepts and commands you need.

---

## 1. Version control

- **What it is:** A way to save and track changes to your files over time. One project, one history of every change: who changed what, and when. You can go back to any earlier version.
- **Why it matters:** Without it, you can lose work, overwrite others’ changes, or forget what you changed. With it, you have a clear history and can collaborate safely.
- **For Digital Humanities:** Editions, corpora, datasets, and websites often involve teams, years of iteration, and the need to cite or reproduce a specific state. Many funders and publishers expect or recommend version control for transparency and reproducibility.

---

## 2. Git basics

### What is Git?

- Free, open-source tool for version control on your computer.
- Runs **locally**: full history lives in a hidden folder (a **repository**) inside your project.
- No internet needed to make commits—only when you share or back up (e.g. with GitHub).

### Essential commands

| Command | What it does |
|--------|----------------|
| `git init` | Turn the current folder into a Git repository |
| `git add <file>` or `git add .` | Stage files for the next commit |
| `git commit -m "Your message"` | Create a snapshot with a short message |
| `git status` | See modified, staged, and untracked files |
| `git log` | View commit history |
| `git log --oneline` | Compact one-line view of history |

### Workflow

1. Create or edit files.
2. `git add` the files you want to include.
3. `git commit -m "Clear, short message"`.
4. Use `git status` often to avoid committing the wrong files.

### .gitignore

- A file that lists **patterns** (one per line). Git ignores matching files: they won’t show as untracked and won’t be added with `git add .`.
- Use it for: secrets, API keys, build outputs, local config, caches, editor backups.
- Create with: `edit .gitignore` (in the tutorial) or any text editor. Commit `.gitignore` so the rules are shared.

### Fixing mistakes

| Command | What it does |
|--------|----------------|
| `git restore --staged <file>` | Unstage a file (remove from the next commit) |
| `git restore <file>` | Discard uncommitted changes in that file (use with care) |
| `git commit --amend -m "New message"` | Replace the last commit’s message (or add more staged changes into it) |
| `git reset --soft HEAD~1` | Undo last commit but keep changes staged |

---

## 3. Branching

- **Branch:** A separate line of development. You can try changes or work on features without affecting the main line.
- **Why:** Essential for trying ideas, working on features separately, and collaborating. In DH you might use a branch for a new edition variant or dataset update.

### Commands

| Command | What it does |
|--------|----------------|
| `git branch` | List branches (* = current) |
| `git checkout -b <name>` | Create and switch to a new branch |
| `git checkout <name>` | Switch to an existing branch |
| `git merge <branch>` | Merge that branch into the current branch |
| `git merge --squash <branch>` | Bring the other branch’s changes as one set of staged changes; you then commit once (no merge commit) |
| `git rebase <branch>` | Move your commits so they sit on top of the other branch (linear history) |
| `git branch -d <name>` | Delete a merged branch (keeps the list tidy) |

### Merge conflicts

- When two branches change the **same part** of the same file, Git cannot merge automatically.
- The file is marked with conflict markers: `<<<<<<<`, `=======`, `>>>>>>>`.
- **Resolve:** Open the file, choose the final content (keep one version, combine, or edit), remove the markers and the version you don’t want, then `git add` the file and `git commit`.

---

## 4. GitHub

- **What it is:** A website that hosts Git repositories in the cloud. Backup, visible history, and tools for collaboration: others can clone, suggest changes (pull requests), and you can manage issues and documentation.
- **Relation:** Git is local; GitHub is remote. Together they let you back up, share, and collaborate.

### Creating a repo on GitHub

- On GitHub: **New repository** → choose a name (e.g. `my-dh-project`) → you get a URL to connect your local repo.

### Remote and push/pull

| Command | What it does |
|--------|----------------|
| `git remote add origin <URL>` | Link your local repo to the remote (e.g. GitHub) |
| `git push -u origin main` | First push: send commits and set upstream |
| `git push` | Send your commits to the remote |
| `git pull` | Fetch and merge changes from the remote |
| `git clone <URL>` | Download a full copy of a repository (creates a new folder) |

**Tip:** Run `git pull` before `git push` to avoid rejections when others have pushed.

---

## 5. Collaboration and good practices

- Use **branches** for separate lines of work; use **pull requests** on GitHub to propose and review changes before merging.
- **Commit often** with clear, short messages.
- **Push regularly** so work is backed up.
- Add a **README** (e.g. `README.md`) to explain the project and how to use or contribute.
- Add a **license** so others know how they can reuse your data and code.
- **One branch per feature or fix**, then merge when ready.

---

## 6. Command cheatsheet (quick reference)

### Setup
```bash
git config user.name "Your Name"
git config user.email "your@email.com"
git init
```

### Basic workflow
```bash
git status
git add <file>    # or git add .
git commit -m "message"
git log
```

### Branches
```bash
git branch
git checkout -b <branch>
git checkout <branch>
git merge <branch>
git merge --squash <branch>
git rebase <branch>
git branch -d <branch>
```

### Remote (GitHub)
```bash
git remote add origin <URL>
git push -u origin main
git push
git pull
git clone <URL>
```

### Useful
```bash
git log --oneline
git remote -v
git restore --staged <file>
git restore <file>
git commit --amend -m "New message"
```

---

## 7. Key terms (glossary)

- **Repository (repo):** Folder managed by Git; contains project files and full commit history.
- **Commit:** A snapshot of the project at a point in time, with a message and unique ID.
- **Stage / staged:** Mark files as ready for the next commit with `git add`.
- **Remote / origin:** The version of the repo hosted elsewhere (e.g. GitHub); `origin` is the default name.
- **Push:** Send local commits to a remote. **Pull:** Fetch and merge from remote. **Clone:** Download a full copy of a repo.
- **Branch:** Separate line of development. **Merge:** Combine another branch into the current one.
- **Merge conflict:** Same part of same file changed in two branches; you resolve by editing the file and removing conflict markers.
- **Untracked:** File Git is not yet tracking. **.gitignore:** File listing patterns Git should ignore.

---

## 8. Next steps (on your own computer)

1. **Install Git:** https://git-scm.com/ (or your package manager).
2. **Create a GitHub account:** https://github.com
3. **Set up authentication** so you can push and pull:
   - **SSH keys** (recommended), or
   - **Personal access token** over HTTPS  
   See GitHub docs: “Connecting to GitHub with SSH” and “Managing your personal access tokens.”

Once Git is installed and authentication is set up, you can clone repos, push your work, and open pull requests from the command line or a GUI.

---

*Handout for the Learn Git and GitHub workshop. Tutorial: [https://humanities-data-lab.github.io/learn-git-and-github/](https://humanities-data-lab.github.io/learn-git-and-github/)*
