# History, Branching & Merging  


This module covers some of Git’s most powerful features, essential for any developer or DevOps engineer working with Infrastructure as Code, CI/CD pipelines, or collaborative software projects. Below are my summarised notes from each lesson.

---

## 🧠 Lesson 10: Viewing Git History

One of Git's superpowers is tracking your projects history.

Understanding Git history is crucial for debugging and collaboration. Whether you’re identifying why a pipeline failed or who last edited a configuration file, Git's history tools help trace everything.

### 🔧 Key Commands:
- `git log`  
  Shows the full commit history. Useful for reviewing recent changes.

- `git log --oneline --graph`  
  Visualises your commit history and branch structure in a clean and concise way.

- `git show <commit>`  
  Displays details of a specific commit — author, message, and code changes.

- `git diff`  
  Compares **unstaged** changes to the last commit.

- `git diff --staged`  
  Compares **staged** changes to the last commit — great before committing.

- `git blame <file>`  
  Shows who last modified each line of a file. Handy for understanding why a change was made.

- `git reflog`  
  Tracks every HEAD movement — even deleted branches or bad rebases can sometimes be recovered with this.

> ⚠️ These tools are not just for software developers. They're just as useful for tracking changes in Terraform, Helm, CI pipelines, and other DevOps configurations.

---

## 🔄 Lesson 11: Git vs GitHub – What's the Difference?

Many beginners confuse Git with GitHub — but they are not the same.

| Git                             | GitHub (or GitLab, Bitbucket, etc.)               |
|----------------------------------|---------------------------------------------------|
| A version control tool           | A cloud-based platform                            |
| Runs locally on your machine     | Hosted online for team collaboration              |
| Open source, CLI based           | Offers GUIs, pull requests, CI/CD features        |
| Works offline                    | Requires internet for full functionality          |

- **Think of Git** as your personal notebook — it stores your work privately.
- **Think of GitHub** as a shared whiteboard — it allows your team to collaborate publicly or within an organisation.

> Git is the foundation; platforms like GitHub build collaboration and automation features on top of it.

---

## 🌱 Lesson 12: Branching 101

Branching is one of Git’s core strengths, allowing you to work on features or bug fixes without affecting the main codebase.

### 🔧 Key Commands:
- `git branch`  
  Lists all branches. Does **not** switch branches.

- `git switch -c <branch>`  
  Creates and switches to a new branch. A modern, beginner-friendly command.

- `git switch <branch>`  
  Switches to an existing branch.

- `git checkout -b <branch>`  
  Older way to create and switch branches. Still works, just more verbose.

- `git branch -d <branch>`  
  Deletes a branch (if merged).

> 💡 `git switch` is recommended for beginners as it's more readable and explicit.

---

## 🔀 Lesson 13: Merging

Merging combines work from one branch into another — commonly into `main`, `dev`, or `master`.

### 🔧 Key Command:
- `git merge <branch>`  
  Merges another branch into your current one.

### 🧩 Types of Merges:
- **Fast-forward**:  
  If no other changes were made, Git simply moves the branch pointer forward.

- **Recursive (true) merge**:  
  If both branches have diverged, Git creates a **merge commit** to join histories.

### ⚠️ Merge Conflicts:
If the same file was changed on both sides, Git may not know how to combine them. You’ll need to manually resolve the conflict.

> Merging is how collaboration happens in Git. It’s central to all team workflows.

---

## Lesson 14: Visualising Branches & Logs

To understand what’s going on under the hood, Git provides ways to visualise history, merges, and branching.

### 🔧 Recommended Commands:
- `git log --oneline`  
  A compact view of commit history.

- `git log --oneline --graph`  
  Adds a visual branch/tree structure.

- `git log --oneline --graph --all`  
  The **"GOAT"** of log views — shows all branches, merges, and commits clearly.

> Great for debugging issues, understanding project flow, and reviewing pull requests.

---

## 🔁 Lesson 15: Rebase vs Merge

This is an advanced topic but valuable when cleaning up your Git history.

| Merge                              | Rebase                                       |
|------------------------------------|----------------------------------------------|
| Preserves full history             | Rewrites commit history                      |
| Adds a merge commit                | Creates a linear timeline                    |
| Preferred for shared workflows     | Best for tidying up before pull requests     |
| Safe for collaboration             | Risky if used on shared branches             |

### 🚨 Rule of Thumb:
> ✅ Use **Merge** when working with teams  
> ✅ Use **Rebase** to clean your personal branch history before pushing  
> ❌ Do **not** rebase shared branches — it rewrites history and can cause conflicts

---

## Final Thoughts

Understanding how to navigate Git’s history, create and manage branches, and collaborate through merging or rebasing is key to becoming confident in version control. These tools are used every day in DevOps to manage codebases, infrastructure definitions, and CI/CD automation.

---

🛠 *Repository maintained as part of my DevOps learning journey. Notes based on real course transcripts and personal practice.*
