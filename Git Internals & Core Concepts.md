# Chapter 2: Git Internals & Core Concepts

This chapter dives into the inner workings of Git. As someone new to DevOps and Git, these lessons helped me understand what’s really going on under the surface. Below are my structured notes on core concepts, Git terminology, and the flow of how Git handles your files.

---

## Lesson 6 – Git Terminology

Understanding Git means getting familiar with some key terms. Here's a breakdown of the essential ones:

| Term               | Explanation                                                                                                                                 |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| **Repository (Repo)**     | A project tracked by Git. If a folder contains a `.git` directory, it's considered a Git repo.                                         |
| **Commit**                | A snapshot of your files at a point in time, along with metadata (author, timestamp, message, parent commit).                         |
| **Branch**                | A pointer to a commit. Common branches include `main`, `master`, or `dev`, as well as feature branches like `feature/login`.          |
| **Remote**                | A version of your repo hosted elsewhere (e.g., GitHub, GitLab). Typically referred to as `origin`.                                     |
| **Staging Area (Index)**  | A buffer zone for files before committing. You stage changes here with `git add`.                                                      |
| **Blob**                  | Binary Large Object. Stores the actual content of files—not the file names.                                                            |
| **Tree**                  | Represents directory structure, mapping file paths to blobs and other trees.                                                           |
| **Refs (References)**     | Includes branches, tags, and special pointers like `HEAD`.                                                                             |
| **Tag**                   | A reference to a specific commit—often used for marking release points (e.g., `v1.0`, `v2.0`).                                         |
| **HEAD**                  | A reference to your current location—i.e., the branch or commit you're working on.                                                     |
| **Index (on disk)**       | The actual file where staged data is saved before a commit is created.                                                                 |
| **Object Store**          | `.git/objects/` stores all objects (blobs, trees, commits, tags), each identified by a SHA-1 hash. Git’s internal database of history. |

---

## 📁 Lesson 7 – The `.git` Directory

Every Git repo contains a hidden `.git` folder—this is the heart of your Git project. Without it, Git can’t function.

Here’s what lives inside:

| Path             | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| `.git/refs`      | Stores references like branches and tags.                                  |
| `.git/objects`   | Known as the Object Store – commits, blobs, and trees saved by SHA hashes. |
| `.git/config`    | Repository-specific settings like username, email, and remote URLs.        |
| `.git/HEAD`      | Points to the branch or commit you're currently on.                        |
| `.git/index`     | Represents the staging area – where Git prepares the next snapshot.        |

&nbsp;

> ⚠️ If the `.git` folder is deleted, your project becomes just regular files—no Git history, no branches, no configuration.  
> **No `.git`, no Git.**

---

## 🛠️ Lesson 8 – Common Git Commands

These are some of the most frequently used Git commands, essential for day-to-day Git operations:

| Command                     | Description                                                                 |
|-----------------------------|-----------------------------------------------------------------------------|
| `git init`                  | Starts a new Git repository.                                               |
| `git add <file>`            | Stages changes for the next commit.                                        |
| `git commit -m "..."`       | Commits staged changes as a snapshot.                                      |
| `git status`                | Shows what’s staged, what’s changed, and what’s not being tracked.         |
| `git log`                   | Displays commit history.                                                   |
| `git diff`                  | Shows the difference between file versions. Great for reviewing changes.   |
| `git config`                | Used to set user identity and repo-specific settings.                      |
| `git help`                  | Displays help for Git commands.                                            |
| `git clone <url>`           | Copies a remote repository to your local machine.                          |
| `git rm <file>`             | Removes a file from Git tracking.                                          |
| `git mv <old> <new>`        | Renames a file while preserving history.                                   |
| `git restore`               | Undoes changes in a clean and controlled way without rolling back commits. |

> **Tip:** You don’t need to memorise everything! Use `git help <command>` when in doubt.

---

## Lesson 9 – The Three Areas of Git

Git operates using three main areas:

1. **Working Directory**  
   Where you actively make changes to files. At this stage, Git isn't tracking them yet.

2. **Staging Area (Index)**  
   A prep zone where files are staged using `git add`. These are the files Git will include in the next commit.

3. **Repository (.git)**  
   The actual database of commits. Once you commit, files move from the staging area to the repository.

### Git Workflow Summary:

[Working Directory] → (git add) → [Staging Area] → (git commit) → [Repository]

&nbsp;

<img src="https://github.com/user-attachments/assets/ef582ab9-7898-4e08-8581-489c1ceb5759" width="400">

&nbsp;


> 💡 Simply saving a file does **not** mean Git is tracking it.  
> You need to `add` it, then `commit` it.

---

## Key Takeaways

- The `.git` directory is the **engine room** of your Git project.
- Git tracks changes using a **3-step workflow**:  
  Working Directory → Staging Area → Repository.
- Core commands like `git add`, `git commit`, and `git status` form the backbone of version control.
- Understanding the terminology early on helps prevent confusion later when things get more complex.
