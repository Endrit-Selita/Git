# 🧪 Git Fundamentals – Chapter 6: Hands-On Git & GitHub

This chapter is all about applying what we've learned. It covers setting up Git, using GitHub, collaborating via branches, fixing mistakes, and automating with hooks. Every section below includes clear, real-world context so you know **exactly when, where, and why** to use each command.

---

## 🔐 Lesson 27 – Connecting to GitHub Remotes

After working on your code locally (in your terminal, on macOS/Linux/Windows), you’ll want to back it up online or collaborate with others. For this, you need to connect your local Git project to GitHub.

### ✅ Setup Instructions:
1. First, create a repository on GitHub (don’t tick “Initialise with README”).
2. Then in your terminal, inside your project folder:

```bash
git remote add origin git@github.com:yourusername/project.git
git push -u origin main
```

🧠 This links your local Git project to the remote on GitHub.  
💡 The `-u` flag sets `origin/main` as the default so you can just run `git push` later.

---

## 🧱 Lesson 28 – GitHub Sign-Up & Git Installation

### 🛠️ Step 1: Sign up for GitHub  
Go to [https://github.com](https://github.com) and create an account.

### 💻 Step 2: Install Git (Terminal):

| OS | Command |
|----|---------|
| macOS | `brew install git` |
| Ubuntu/Linux | `sudo apt install git` |
| Windows | `choco install git` (in Administrator PowerShell) |

After installation, run:

```bash
git --version
```

🧠 This confirms Git is installed and ready.

### 🛠️ Step 3: Configure your identity (required before commits):

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

💡 These values will appear in your commit history.

---

## 🔑 Lesson 29 – Creating SSH Keys for GitHub Access

When you push code, GitHub needs to verify it’s really you. SSH keys allow secure, password-free authentication.

### ✅ Generate SSH key (Terminal):

```bash
ssh-keygen -t ed25519 -C "you@example.com"
```

- Press enter to accept default location.
- A key pair is created in `~/.ssh/` (Linux/macOS) or `C:\Users\YourName\.ssh` (Windows).

### ✅ Add your SSH key to GitHub:
1. Run:
   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```
2. Copy the output, go to **GitHub → Settings → SSH and GPG Keys**, and paste it.

### ✅ Test connection:

```bash
ssh -T git@github.com
```

🧠 Now you're set up to securely push without typing your password.


---

## 📂 Lessons 30–32 – Creating & Pushing a Repository

Let’s say you’ve just started a new project.


### 💻 In your terminal:

```bash
mkdir my-project && cd my-project
git init
touch README.md
git add README.md
git commit -m "Initial commit"
```

🧠 This creates a local Git repo, adds a file, and saves your first snapshot.

### ✅ Now create a repo on GitHub → copy the SSH URL

Then run:

```bash
git remote add origin git@github.com:yourusername/my-project.git
git push -u origin main
```

🎯 Now your local work is linked to GitHub.


---

## 🌿 Lesson 33 – Branching & Merging (With Conflict Example)

Imagine you're building a new feature but don’t want to break the main code.


### ✅ Create a branch:

```bash
git checkout -b feature/login-page
```

💡 Now you're working on feature/login-page.



Make your changes, then:

```bash
git add .
git commit -m "Build login page"
```

Now you want to merge it into main.


### ✅ Merge into main:

```bash
git checkout main
git merge feature/login-page
```

🧠 If both branches edited the same line, Git will throw a conflict.



### ✅ Resolve Conflict:

1. Open the conflicting file — Git will mark the differences.

2. Manually edit and clean it up.

3. Then run:

```bash
git add <file>
git commit -m "Resolve merge conflict"
```

---

## 🔄 Lesson 34 – Real Git Workflow (Pull Request)

You're done coding and want your teammate to review your changes before merging.

1. Create a new branch:

`git checkout -b feature/about-page`

2. After making changes:


```bash
git checkout -b feature/about-page
git add .
git commit -m "Add about page"
git push -u origin feature/about-page
```

3. Go to GitHub and click “Compare & pull request”.


🧠 This starts a code review. Once approved, click “Merge”.


---

## ⏪ Lesson 35 – Undo in Git

| Situation | Command |
|-----------|---------|
| Discard local file changes | `git restore file.txt` |
| Unstage a file | `git restore --staged file.txt` |
| Undo last commit (keep changes) | `git reset --soft HEAD~1` |
| Undo last commit (unstage) | `git reset --mixed HEAD~1` |
| Undo and delete last commit | `git reset --hard HEAD~1` |
| Safe undo on shared branches | `git revert <commit>` |

⚠️ Never use `reset` on shared branches!


---

## 📥 Lesson 36 – Git Stash

You're midway through work on `feature/config-update`, but you're asked to hotfix something in `main`. You can't commit unfinished work — so you stash it.

✅ In terminal:

`git stash push -m "WIP: editing config"`

🧠 This hides your uncommitted changes. Now switch branches:

`git checkout main`

After fixing the issue, come back and recover your work:

```
git stash list
git stash pop
```

```bash
git stash push -m "WIP: editing config"
git checkout main
git stash list
git stash pop
```

💡 `git stash apply` restores without removing it from the list.


---

## 🧹 Lesson 37 – Git Rebase & Squash Commits

Let’s say your branch has 4 messy commits and you want to combine them before opening a pull request.

✅ Use rebase:

```bash
git rebase -i HEAD~4
```

Change the second, third, and fourth pick to squash.

Save and edit the final commit message.

🧠 This cleans up history. Use before pushing. Avoid rebasing branches others are using.


---

## 🍒 Lesson 38 – Cherry-Pick Commits

You fixed a bug in one branch and want to apply just that fix to another branch.

✅ In terminal:

1. Find the commit hash using:

`git log --oneline`

2. then:

```
git checkout release
git cherry-pick abc1234
```

```bash
git log --oneline
git checkout release
git cherry-pick <commit-hash>
```

💡 Applies that one commit into the current branch without merging everything.


---

## 🚫 Lesson 39 – Using .gitignore

Let’s say your app generates `node_modules/`, `env`, or `.log` files that you don’t want tracked.

✅ Create `.gitignore`:

```bash
node_modules/
.env
*.log
.DS_Store
```

Then:

```bash
git add .gitignore
git commit -m "Add gitignore"
```

🧠 Always create this at the start of a project.


---

## 🛠️ Lesson 40 – Amending Commits

Oops! Forgot to add a file or want to improve your last commit message?


```bash
git add forgotten-file.txt
git commit --amend
```

🧠 Rewrites the last commit. Great for small clean-ups before pushing.


---

## 🧪 Lesson 41 – Pre-Commit Hooks (Automation)

These stop broken or insecure code from being committed.

Install:

```bash
brew install pre-commit          # macOS  
sudo apt install pre-commit      # Linux  
choco install pre-commit         # Windows
```

Configure:

✅ In your Git repo:

`pre-commit install`


Create .pre-commit-config.yaml:

```yaml
# .pre-commit-config.yaml
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.4.0
    hooks:
      - id: end-of-file-fixer
      - id: trailing-whitespace
```

Run all hooks manually:

```bash
pre-commit run --all-files
```

Now every time you commit, it checks for trailing whitespace or missing newlines.


---

## ✅ Final Thoughts

- Linked local Git to GitHub via SSH
- Created branches and pull requests
- Resolved merge conflicts
- Cleaned up history with squash and rebase
- Used stash and cherry-pick to manage context switches
- Improved security and code quality with `.gitignore` and pre-commit hooks

🧠 Git is no longer just a set of commands — it's part of how I build, break, and fix things confidently in tech.
