# Git Fundamentals – Chapter 1: Introduction to Git

## Overview

Git is more than just a tool to store code – it’s the foundation of how modern tech teams collaborate, build, test, ship, and recover from mistakes. Whether you're in DevOps, development, or supporting infrastructure, Git is essential knowledge.

This module introduces Git from the ground up, covering its origins, the problems it solves, and why it's at the core of nearly every DevOps and software engineering workflow.

---

## 📌 Lesson 1: Git Intro

Git is a must-know tool for anyone in tech – not just developers.

This course focuses on explaining Git without jargon and with hands-on labs.

It covers both the theory and practice: how Git works internally and how to use it in real-world environments.

### Key Topics Across the Module:
- Git’s history and architecture
- Core Git commands (`git init`, `git add`, `git commit`)
- Branching, merging & resolving conflicts
- Advanced commands like `rebase`, `stash`, `cherry-pick`
- Git in team environments with CI/CD pipelines
- Hands-on labs and future bonus content for deeper dives

---

## Lesson 2: What is Version Control?

Version control is a system that tracks changes to code over time.

It allows teams to:
- Undo mistakes
- See who changed what
- Collaborate without interfering with each other

Git can track any code or config file, not just application code. Examples:
- Terraform modules
- Kubernetes YAML files
- CI/CD configuration files

> Think of Git like a time machine for code: you can go back, review changes, and revert if needed.

---

## Lesson 3: Centralised vs Distributed Version Control

### Centralised Version Control (e.g., SVN, CVS):
- One central server
- If it went down, no one could work or commit changes
- Developers had to lock files to avoid conflicts

### Git’s Distributed Model (Introduced in 2005):
- Every developer has a full copy of the repository and its history
- You can work offline, branch freely, and merge later
- Git makes collaboration fast, safe, and scalable

**Analogy:**
- **SVN**: Like Google Docs (one master file)
- **Git**: Like everyone having their own version of the doc, then merging changes when ready

&nbsp;

<img src="https://github.com/user-attachments/assets/b1c14a2e-0e93-4124-a08b-18100b5d03aa" width="400">

&nbsp;

---

## Lesson 4: Git Changed the Game

- Git was created by **Linus Torvalds** (creator of Linux) in **2005**
- Built to manage the fast-moving, complex development of the Linux kernel

### Key Innovations:
- Distributed version control
- No central bottleneck
- Fast and efficient branching & merging

### Today, Git is the default version control tool for:
- Open source
- Microservices
- Infrastructure-as-code
- Pipelines and deployments in DevOps

---

## Lesson 5: Git is Not a File Tracker

Git doesn't track files line-by-line like a document editor – it uses **snapshots**.

Each commit saves the entire state of the project at that moment.

Git stores data using a key-value store, with **SHA-1 hashes** identifying content.

- If the content changes, the hash changes.
- If the content is the same, Git reuses the same object – making it very efficient.

Git is **content-addressed**, not filename-based:
- The file name doesn’t matter – only the content does.

### Internally, Git uses:
- **Blobs** – file contents
- **Trees** – directories
- **Commits** – snapshots pointing to the tree structure

> This smart snapshot design is why Git is so fast, even with large projects or config files.

---

## Summary: Why Git Matters

By learning Git, you're not just learning a tool – you're learning a **core DevOps skill** that powers collaboration, automation, and infrastructure management at scale.

This chapter lays the foundation for understanding Git's core concepts, history, and advantages.

> The next chapters will go hands-on with essential commands and real workflows.
