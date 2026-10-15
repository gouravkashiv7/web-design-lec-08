# Git Commands: Quick Reference

The same file is in every lecture repo. Run these commands in the VS Code terminal (**Terminal → New Terminal**).

---

## Get this lecture's code

**No Git yet?** On the GitHub page, click the green **Code** button, then **Download ZIP**. Unzip it and open the folder in VS Code.

**With Git:**

```bash
git clone https://github.com/gouravkashiv7/web-design-lec-01.git
cd web-design-lec-01
```

Change `01` to the lecture number you need.

Already cloned it, and the trainer added something new?

```bash
git pull
```

---

## One-time setup (on a new computer)

```bash
git --version                                   # is Git installed?
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
```

Use the same email as your GitHub account.

---

## Put your own project on GitHub

**1. Start tracking your folder** (once per project):

```bash
cd yourname-project-1
git init
```

**2. Save a snapshot** (every time you finish a step):

```bash
git status                       # what changed?
git add .                        # stage every change
git commit -m "Add contact form"  # save it, with a short message
```

**3. Connect to GitHub** (once): create an **empty** repo on github.com (no README), then:

```bash
git remote add origin https://github.com/your-username/yourname-project-1.git
git push -u origin main
```

**4. Upload new commits** (every time after that):

```bash
git push
```

---

## Everyday commands

| Command | What it does |
|---|---|
| `git status` | Shows changed, new and staged files. Run it all the time. |
| `git add index.html` | Stages one file for the next commit |
| `git add .` | Stages every change in this folder |
| `git commit -m "message"` | Saves the staged changes as a snapshot |
| `git log --oneline` | Lists your commits, newest first |
| `git diff` | Shows exactly what changed since the last commit |
| `git push` | Uploads your commits to GitHub |
| `git pull` | Downloads new commits from GitHub |
| `git clone <url>` | Copies a repo from GitHub to your computer |
| `git restore index.html` | Throws away unsaved changes to one file (careful: can't be undone) |

---

## Good commit messages

Say **what** the commit does, starting with a verb:

| Good | Not helpful |
|---|---|
| `Add course table with caption` | `update` |
| `Fix broken logo path on about page` | `fixed stuff` |
| `Link styles.css from all four pages` | `asdf` |

Commit small and often: one finished step = one commit.

---

## Ignore files you don't want to upload

Create a file called `.gitignore` in your project folder:

```
.DS_Store
Thumbs.db
.vscode/
```

---

## When something goes wrong

| Message | What it means | Fix |
|---|---|---|
| `not a git repository` | You're in the wrong folder | `cd` into your project folder, or run `git init` |
| `nothing to commit` | You haven't changed anything since the last commit | Save your file in VS Code first |
| `Please tell me who you are` | Name and email aren't set | Run the one-time setup above |
| `rejected ... fetch first` | GitHub has commits you don't have | `git pull`, then `git push` again |
| `remote origin already exists` | You already connected this folder | `git remote -v` to see where it points |
| `Authentication failed` | GitHub no longer accepts your password here | Sign in through VS Code's prompt, or use a personal access token |

Stuck? Run `git status` first and read the whole message. It usually tells you the next command.
