# 📘 Advanced Git Usage

This section covers more advanced but essential Git features used in real-world DevOps and software development workflows. These concepts are critical for collaborating in teams, managing complex codebases, and contributing to projects safely and efficiently.

---

## 🔧 Lesson 16: Git Stash & Pop

Sometimes you need to switch branches quickly, but you're not ready to commit your current work. That’s where `git stash` comes in — it allows you to **temporarily save your uncommitted changes** and come back to them later.

### 🔹 Key Commands:

- `git stash`  
  Temporarily saves all uncommitted changes.

- `git stash list`  
  Shows a list of all saved stashes.

- `git stash apply`  
  Reapplies the latest stash (or a specific one) but keeps it in the list.

- `git stash pop`  
  Reapplies the stash and **removes it** from the list — great for cleaning up after reuse.

> ✅ Useful when switching branches mid-task without committing unfinished work.

---

## ⏪ Lesson 17: Reset, Revert & Cherry-Pick

These Git commands help you undo or manage commit history. Each serves a different purpose:

### 🔄 `git revert` – *Safe Undo*

- Creates a **new commit** that undoes a previous one.
- Keeps history intact — safe for **shared branches**.
- Ideal for fixing issues in production environments.

### ⚠️ `git reset` – *History Rewriter*

- Moves the branch pointer backwards.
- Types:
  - `--soft`: Keeps changes staged.
  - `--mixed`: Unstages changes (default).
  - `--hard`: **Deletes changes completely** — use with care!

> ⚠️ Avoid using reset on shared branches — it rewrites history and can break collaboration.

### 🍒 `git cherry-pick` – *Copy a Commit*

- Copies a **specific commit** from one branch to another.
- Useful for hotfixes without merging the entire branch.

&nbsp;

<img src="https://github.com/user-attachments/assets/2504cc0b-ce3b-4f3e-ac08-c8c7ac418974" width="400"/>

&nbsp;

---

## 🔁 Lesson 19: Forks & Pull Requests

Used in both open-source and enterprise GitHub workflows to safely propose and manage changes.

### ✂️ Fork:

- A personal copy of someone else’s repository.
- Used when you don’t have direct write access (e.g., external contributors).

### 📤 Pull Request (PR):

- A **proposal** to merge changes from your branch or fork.
- Enables code review, discussion, and collaboration before merging.
- Safe and clean — you don’t affect the original repo directly.

**Typical Flow:**

1. Fork the repo.
2. Clone your fork locally.
3. Create a branch and make changes.
4. Push to your fork.
5. Open a PR to the original project.

&nbsp;

<img src="https://github.com/user-attachments/assets/e06b6cfb-ccb7-480a-841c-dd044572ca3c" width="400"/>

&nbsp;

---

## 🤝 Lesson 20: Collaboration Best Practices

Git becomes truly powerful when used in teams. Here are some best practices:

- **Use branches to isolate work** to keep `main` stable.
- **Push your branch** to remote and open a PR for review.
- **Assign reviewers** and use GitHub's UI for comments
- **Fix merge conflicts** yourself. don’t leave it to others.
- Use GitHub tools like **Issues**, **Projects**, and **Discussions** for planning and collaboration.
- **Write clean, meaningful commit messages**  
  Avoid vague messages like “fixed stuff”.

> These practices improve visibility, maintain code quality, and keep teams aligned.

---

## 🔁 Lesson 21: Typical Git Workflow

The standard day-to-day workflow for most Git-based teams:

1. **Start fresh:** Pull the latest from `main` or clone the repo (start with the latest code, you don't want to work on something outdated)
2. **Create a new branch** for your work.
3. **Make changes locally.**
4. **Push your branch** to GitHub.
5. **Open a Pull/Merge Request** for code review.
6. **Review and merge.**
7. **Pull regularly** to stay up to date and avoid conflicts.

&nbsp;

<img src="https://github.com/user-attachments/assets/2b06f408-799e-4e72-814a-3b9757cee86b" width="400"/>

&nbsp;

> 📌 This workflow keeps development structured, clean, and collaborative.

---

## 🌲 Lesson 22: Trunk-Based Development

Trunk-based development is a software development approach where all developers work directly on the main branch (often called "trunk") or use very short-lived branches.

Short-lived branches are merged back into the main branch quickly, sometimes within a day or even a few hours.

### Key Practices

**Short Branches:**
Developers avoid long-running feature branches. Instead, they create small branches for quick changes and merge them back rapidly.

**Strong CI Pipelines:**
Every commit is automatically tested using continuous integration (CI) tools. This ensures that new code does not break the build.

**Code Quality Checks:**
Automated checks and reviews are in place so that only high-quality, working code is merged into the main branch.

### Benefits
**Faster Delivery:**
Enables teams to ship code more frequently and respond quickly to changes.

**High Code Quality:**
Automated testing and code checks help maintain a stable and reliable codebase.

**Adopted by Leading Tech Companies:**
Companies like Google and Meta (Facebook) use trunk-based development to move fast without sacrificing stability.

### Requirements

**Solid Test Coverage:**
Reliable automated tests are essential to catch issues early.

**Good Engineering Habits:**
Developers must follow best practices to ensure code quality and smooth collaboration.

&nbsp;


> Ideal for rapid delivery environments. Encourages discipline and fast feedback.

---

### ✅ Summary

This chapter builds on Git basics by introducing key workflows and commands used in real-life teams and production environments. Mastering these tools will improve your confidence in using Git collaboratively and effectively.

---
