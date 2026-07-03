# Git Cheatsheet

**Document Version:** 1.0
**Sprint:** 2 — Git & Version Control

---

# Purpose

This document provides a quick reference for commonly used Git commands, workflows, and best practices.

It is intended for day-to-day development, interview preparation, and rapid revision.

---

# Repository Initialization

| Command           | Purpose                         | Example                                      |
| ----------------- | ------------------------------- | -------------------------------------------- |
| `git init`        | Initialize a new Git repository | `git init`                                   |
| `git clone <url>` | Clone an existing repository    | `git clone https://github.com/user/repo.git` |

---

# Repository Status

| Command             | Purpose                  | Example             |
| ------------------- | ------------------------ | ------------------- |
| `git status`        | Show working tree status | `git status`        |
| `git log`           | Show commit history      | `git log`           |
| `git log --oneline` | Compact commit history   | `git log --oneline` |
| `git diff`          | Show unstaged changes    | `git diff`          |
| `git diff --staged` | Show staged changes      | `git diff --staged` |

---

# Staging & Committing

| Command                         | Purpose                | Example                                |
| ------------------------------- | ---------------------- | -------------------------------------- |
| `git add file.txt`              | Stage a specific file  | `git add README.md`                    |
| `git add .`                     | Stage all changes      | `git add .`                            |
| `git restore --staged file.txt` | Unstage a file         | `git restore --staged README.md`       |
| `git commit -m "message"`       | Create a commit        | `git commit -m "Add networking notes"` |
| `git commit --amend`            | Modify the last commit | `git commit --amend`                   |

---

# Branch Management

| Command                       | Purpose              | Example                       |
| ----------------------------- | -------------------- | ----------------------------- |
| `git branch`                  | List branches        | `git branch`                  |
| `git branch feature/login`    | Create a branch      | `git branch feature/login`    |
| `git switch feature/login`    | Switch branch        | `git switch feature/login`    |
| `git switch -c feature/login` | Create and switch    | `git switch -c feature/login` |
| `git branch -d feature/login` | Delete merged branch | `git branch -d feature/login` |

---

# Merging & Rebasing

| Command                   | Purpose          | Example                   |
| ------------------------- | ---------------- | ------------------------- |
| `git merge feature/login` | Merge a branch   | `git merge feature/login` |
| `git rebase main`         | Rebase onto main | `git rebase main`         |
| `git merge --abort`       | Cancel merge     | `git merge --abort`       |
| `git rebase --abort`      | Cancel rebase    | `git rebase --abort`      |

---

# Remote Repositories

| Command                       | Purpose                 | Example                            |
| ----------------------------- | ----------------------- | ---------------------------------- |
| `git remote -v`               | List remotes            | `git remote -v`                    |
| `git remote add origin <url>` | Add remote              | `git remote add origin <url>`      |
| `git fetch`                   | Download remote changes | `git fetch`                        |
| `git pull`                    | Fetch and merge         | `git pull origin main`             |
| `git push`                    | Push commits            | `git push origin main`             |
| `git push -u origin branch`   | Set upstream branch     | `git push -u origin feature/login` |

---

# Undo Operations

| Command                    | Purpose                          | Example                    |
| -------------------------- | -------------------------------- | -------------------------- |
| `git restore file.txt`     | Discard local file changes       | `git restore README.md`    |
| `git reset --soft HEAD~1`  | Undo commit, keep staged changes | `git reset --soft HEAD~1`  |
| `git reset --mixed HEAD~1` | Undo commit, unstage changes     | `git reset --mixed HEAD~1` |
| `git reset --hard HEAD~1`  | Undo commit and discard changes  | `git reset --hard HEAD~1`  |

> **⚠️ Warning:** `git reset --hard` permanently discards uncommitted work.

---

# Stashing

| Command           | Purpose                         | Example           |
| ----------------- | ------------------------------- | ----------------- |
| `git stash`       | Save uncommitted changes        | `git stash`       |
| `git stash list`  | List stashes                    | `git stash list`  |
| `git stash pop`   | Restore latest stash            | `git stash pop`   |
| `git stash apply` | Apply stash without removing it | `git stash apply` |

---

# Tags

| Command                | Purpose                | Example                |
| ---------------------- | ---------------------- | ---------------------- |
| `git tag`              | List tags              | `git tag`              |
| `git tag v1.0`         | Create lightweight tag | `git tag v1.0`         |
| `git push origin v1.0` | Push a tag             | `git push origin v1.0` |

---

# Common Workflows

## Daily Development Workflow

| Step                    | Command                              |
| ----------------------- | ------------------------------------ |
| Check repository status | `git status`                         |
| Pull latest changes     | `git pull`                           |
| Create feature branch   | `git switch -c feature-name`         |
| Stage changes           | `git add .`                          |
| Commit changes          | `git commit -m "Meaningful message"` |
| Push branch             | `git push -u origin feature-name`    |
| Create Pull Request     | Via Git hosting platform             |

---

## Synchronizing with Main

| Step                     | Command                               |
| ------------------------ | ------------------------------------- |
| Switch to main           | `git switch main`                     |
| Update main              | `git pull origin main`                |
| Return to feature branch | `git switch feature-name`             |
| Merge or rebase          | `git merge main` or `git rebase main` |

---

# Commit Message Guidelines

| Type          | Example                               |
| ------------- | ------------------------------------- |
| Feature       | `feat: add Docker networking notes`   |
| Fix           | `fix: correct Git workflow diagram`   |
| Documentation | `docs: update networking dictionary`  |
| Refactor      | `refactor: reorganize Linux concepts` |
| Test          | `test: add Git workflow examples`     |

---

# Best Practices

| Practice                         | Why It Matters                          |
| -------------------------------- | --------------------------------------- |
| Commit small, logical changes    | Easier review and rollback              |
| Write meaningful commit messages | Improves project history                |
| Pull before pushing              | Reduces merge conflicts                 |
| Use feature branches             | Keeps main branch stable                |
| Review changes before committing | Prevents accidental commits             |
| Never commit secrets             | Protects credentials and sensitive data |

---

# Related Documents

| Document           | Purpose                   |
| ------------------ | ------------------------- |
| README.md          | Sprint overview           |
| Dictionary.md      | Git terminology           |
| Analogies.md       | Mental models             |
| Interview.md       | Git interview preparation |
| Troubleshooting.md | Git debugging guide       |
