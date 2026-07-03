# Git Troubleshooting

**Document Version:** 1.0
**Sprint:** 2 — Git & Version Control

---

# Purpose

This document provides a structured approach to diagnosing, understanding, and resolving common Git issues encountered during day-to-day development.

The emphasis is on understanding the **root cause**, selecting the **correct resolution**, and adopting **preventive best practices**.

---

# Git Troubleshooting Workflow

| Step | Question                              | Recommended Command(s)                                     |
| ---- | ------------------------------------- | ---------------------------------------------------------- |
| 1    | What is the current repository state? | `git status`                                               |
| 2    | What changed?                         | `git diff`, `git diff --staged`                            |
| 3    | Where am I?                           | `git branch`, `git log --oneline --graph --decorate`       |
| 4    | Is the remote up to date?             | `git fetch`                                                |
| 5    | What exactly failed?                  | Read the Git error message completely before taking action |

---

# Repository State Issues

| Problem                    | Possible Cause                           | Resolution                                            |
| -------------------------- | ---------------------------------------- | ----------------------------------------------------- |
| Repository not initialized | Missing `.git` directory                 | Run `git init` or clone the repository again.         |
| Wrong repository           | Working in an incorrect directory        | Verify using `git remote -v` and `pwd`.               |
| Detached HEAD              | Checked out a commit instead of a branch | Create or switch back to a branch using `git switch`. |

---

# Staging & Commit Issues

| Problem                  | Possible Cause      | Resolution                                     |
| ------------------------ | ------------------- | ---------------------------------------------- |
| File not being committed | File not staged     | Run `git add <file>` before committing.        |
| Wrong file staged        | Incorrect `git add` | Use `git restore --staged <file>`.             |
| Wrong commit message     | Mistyped message    | Use `git commit --amend` (only if not pushed). |
| Nothing to commit        | No staged changes   | Verify using `git status`.                     |

---

# Branch Issues

| Problem                | Possible Cause         | Resolution                                          |
| ---------------------- | ---------------------- | --------------------------------------------------- |
| Cannot switch branches | Uncommitted changes    | Commit, stash, or discard changes before switching. |
| Branch not found       | Incorrect branch name  | Verify available branches using `git branch -a`.    |
| Deleted wrong branch   | Branch deleted locally | Recover from reflog if commits still exist.         |

---

# Merge Issues

| Problem        | Possible Cause                           | Resolution                                             |
| -------------- | ---------------------------------------- | ------------------------------------------------------ |
| Merge conflict | Same lines modified in multiple branches | Resolve conflicts manually, then commit the merge.     |
| Merge aborted  | Manual cancellation                      | Restart merge after resolving underlying issues.       |
| Unwanted merge | Incorrect merge target                   | Use `git merge --abort` if merge is still in progress. |

---

# Rebase Issues

| Problem                   | Possible Cause                 | Resolution                                           |
| ------------------------- | ------------------------------ | ---------------------------------------------------- |
| Rebase conflict           | Commit conflicts during replay | Resolve conflicts, then run `git rebase --continue`. |
| Incorrect rebase          | Wrong base branch selected     | Abort using `git rebase --abort`.                    |
| Lost commits after rebase | History rewritten              | Recover using `git reflog`.                          |

---

# Remote Repository Issues

| Problem               | Possible Cause                 | Resolution                                                  |
| --------------------- | ------------------------------ | ----------------------------------------------------------- |
| Push rejected         | Remote branch ahead of local   | Pull or fetch latest changes, resolve conflicts, then push. |
| Authentication failed | Invalid credentials or token   | Verify SSH key or Personal Access Token configuration.      |
| Remote not found      | Incorrect remote URL           | Check using `git remote -v`.                                |
| Permission denied     | Insufficient repository access | Verify repository permissions and authentication.           |

---

# Undo & Recovery

| Situation                          | Recommended Action                                     |
| ---------------------------------- | ------------------------------------------------------ |
| Undo unstaged changes              | `git restore <file>`                                   |
| Unstage a file                     | `git restore --staged <file>`                          |
| Undo last commit (keep changes)    | `git reset --soft HEAD~1`                              |
| Undo last commit (unstage changes) | `git reset --mixed HEAD~1`                             |
| Discard last commit and changes    | `git reset --hard HEAD~1` *(use with extreme caution)* |
| Recover lost commits               | `git reflog`                                           |

---

# Stash Issues

| Problem                                 | Resolution        |
| --------------------------------------- | ----------------- |
| Forgot to commit before switching tasks | `git stash`       |
| Restore latest stash                    | `git stash pop`   |
| View saved stashes                      | `git stash list`  |
| Apply stash without deleting it         | `git stash apply` |

---

# Recovery Commands

| Command                            | Purpose                                          |
| ---------------------------------- | ------------------------------------------------ |
| `git reflog`                       | View all HEAD movements and recover lost commits |
| `git log --all --graph --decorate` | Visualize repository history                     |
| `git fsck`                         | Verify repository integrity                      |
| `git show <commit>`                | Inspect a specific commit                        |

---

# Common Error Messages

| Error                         | Meaning                                   | Resolution                                            |
| ----------------------------- | ----------------------------------------- | ----------------------------------------------------- |
| `merge conflict`              | Git cannot merge automatically            | Resolve conflicting files manually.                   |
| `non-fast-forward`            | Remote has newer commits                  | Pull latest changes before pushing.                   |
| `detached HEAD`               | Not currently on a branch                 | Switch to or create a branch.                         |
| `nothing to commit`           | No staged changes                         | Stage files or verify modifications.                  |
| `fatal: not a git repository` | Current directory is not a Git repository | Navigate to the correct repository or initialize Git. |

---

# Debugging Checklist

| Check                | Command                                      |
| -------------------- | -------------------------------------------- |
| Repository status    | `git status`                                 |
| Current branch       | `git branch`                                 |
| Recent commits       | `git log --oneline`                          |
| Remote repositories  | `git remote -v`                              |
| Commit history graph | `git log --graph --oneline --decorate --all` |
| Repository integrity | `git fsck`                                   |

---

# Best Practices

| Practice                               | Benefit                                          |
| -------------------------------------- | ------------------------------------------------ |
| Commit frequently with logical changes | Easier rollback and review                       |
| Pull before pushing                    | Reduces merge conflicts                          |
| Review changes before committing       | Prevents accidental commits                      |
| Use feature branches                   | Keeps the main branch stable                     |
| Avoid force-pushing shared branches    | Prevents accidental history loss                 |
| Keep `.gitignore` updated              | Avoids committing unnecessary or sensitive files |
| Learn `git reflog`                     | Enables recovery from many mistakes              |

---

# Decision Matrix

| Situation                               | Recommended Action                        |
| --------------------------------------- | ----------------------------------------- |
| Work not ready but need to switch tasks | `git stash`                               |
| Wrong commit message                    | `git commit --amend`                      |
| Wrong file staged                       | `git restore --staged`                    |
| Lost commit                             | `git reflog`                              |
| Merge conflict                          | Resolve manually and commit               |
| Push rejected                           | Pull/fetch, resolve conflicts, push again |

---

# Related Documents

| Document      | Purpose               |
| ------------- | --------------------- |
| README.md     | Sprint overview       |
| Dictionary.md | Git terminology       |
| Analogies.md  | Mental models         |
| Cheatsheet.md | Command reference     |
| Interview.md  | Interview preparation |
