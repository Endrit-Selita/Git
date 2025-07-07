## 🧠 Chapter 5: Git Best Practices

This chapter covers real-world advice to help keep your Git history clean, avoid common mistakes, and work professionally in team environments. These habits are essential whether you're a solo developer or part of a larger DevOps team.

---

### Lesson 23: Commit Hygiene & Best Practices

Write clear, structured commit messages and keep your Git history clean. Your messages should be telling a story.

#### Good Commit Messages
- Use clear, descriptive messages:
  - ✅ `Fix navbar logo alignment`
  - ✅ `Add user middleware`
  - ❌ `final update`, `stuff`, `fix again`
- Your commit message should explain **what** was changed and **why**.

#### Squash Before Merge
- Avoid merging PRs with messy, multiple work in progress commits like:
  - `fix typo`
  - `broken test again`

- Squash them into a single, meaningful commit before merging to `main`.

#### One Logical Change per Commit
- Keep changes focused:
  - ✅ One commit for bug fix
  - ✅ One commit for documentation update
- Easier to track, rollback, and debug issues later.

#### Avoid Noisy History
- Don’t fill your commit log with messages like `merge main into main`, `final_final_really_final`.
- Take a moment to write meaningful messages – it makes collaboration easier long-term.

---

### ⚙️ Lesson 24: Pre-Commit Hooks & Automation

Catch mistakes early and keep code clean using automation.

#### What Are Pre-Commit Hooks?
- Tools that run checks **before** a commit is made.
- Helps catch:
  - Syntax errors
  - Bad formatting
  - Secrets and sensitive data

#### Common Tools
| Tool        | Use Case            |
|-------------|---------------------|
| `pre-commit` | General pre-commit automation |
| `Husky`      | Node/JavaScript projects      |
| `tflint`, `tfsec` | Terraform security and formatting  |

#### Benefits
- Prevents broken or insecure code from being committed
- Saves time in code review and debugging
- Promotes consistent standards across the team

#### Run in CI/CD Pipelines Too
- These tools also run in CI (e.g., GitHub Actions)
- Ensures code is scanned and safe before deploying

---

### Lesson 25: Common Mistakes in the Real World

Even experienced developers make mistakes. Avoid these common errors:

#### ❌ Forgetting to Pull Before Push

Always `git pull` first to avoid conflicts.

- Why? Someone rlse pushed before you and you alway pull to make sure you are in syn before pushing.
  
Do `git pull --rebase` before you start work to keep things clean.

#### ❌ Force Pushing to Shared Branches

- Avoid: `git push --force`
  
Use with extreme caution — you can wipe out teammates' work.

#### ❌ Committing Secrets (API Keys, Tokens, etc.)
Use `.gitignore`, `git-secrets`, or `trufflehog` to prevent this.

Leaked secrets can be scraped by bots within minutes.

#### ❌ Merging Without Code Review
- Even in small teams, review what you merge.
- Pull Requests are a chance to double-check quality and intent.

#### ❌ Not Using `.gitignore` Properly
Prevent committing:

`node_modules`

`.env files`

`.DS_Store (MacOS)`

- Keeps your repo clean and secure

  <img src="https://github.com/user-attachments/assets/64a23d44-d29b-42c5-bf81-f28829039036" width="400">



---

### 🧱 Lesson 26: Git at Scale

In large organisations, Git is used differently. Here’s how big teams manage it:

#### 🔹 Monorepos

- Everything in one big repo (used by Google, Meta, Uber)

- Simplifies dependencies but requires smarter tooling

#### 🔹 Build Tools for Scale

| Tool                   | Purpose                                |
|------------------------|----------------------------------------|
| `turbo`, `nx`, `bazel` | Builds only affected parts of the repo |
| `sparse-checkout`      | Clones only specific folders           |
| `git-lfs`              | Manages large media files              |


#### 🔹 Cleaning and Refactoring

- Use git-filter-repo or BFG to:

- Remove old secrets

- Delete folders from commit history

#### 🔹 Submodules vs Subtrees

- Submodules: Fragile, but useful for microservices

- Subtrees: More stable and Git-native

#### 🔹 Security and Automation at Scale

- Use bots and hooks to enforce standards

- Security tools scan for issues automatically

- Even infrastructure (e.g., Kubernetes configs) is now managed via Git (`ArgoCD`, `Flux`)

---

### 🔐 Lesson 27: Git Security & Secrets Hygiene

One of the most dangerous mistakes is committing secrets.

#### 🛡️ Prevention Tools

Tool	Purpose

| Tool          | Purpose                          |
| ------------- | -------------------------------- |
| `.gitignore`  | Prevent tracking sensitive files |
| `git-secrets` | Detects secrets in commits       |
| `trufflehog`  | Scans for sensitive data leaks   |


#### ❗ If You Leak a Secret

- Revoke it immediately (e.g., AWS key)

- Generate a new one

- Clean Git history using:

`git filter-repo` or `BFG Repo Cleaner`

#### 🔎 Monitor Your Logs

- Regularly check git log

- Some bots can alert you to suspicious activity

- Git is powerful, but with that comes responsibility. Build safe habits early and you’ll avoid critical issues later.
