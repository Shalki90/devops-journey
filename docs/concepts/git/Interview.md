# Git Interview

**Document Version:** 1.0
**Sprint:** 2 — Git & Version Control

---

# Purpose

This document consolidates Git interview questions ranging from beginner to intermediate and practical DevOps scenarios.

The objective is to understand **why Git works the way it does**, not simply memorize commands.

---

# Beginner Questions

| Question                                       | Answer                                                                                                                           |
| ---------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| What is Git?                                   | Git is a distributed version control system used to track changes in source code and collaborate efficiently.                    |
| What is Version Control?                       | A system that records changes to files over time, allowing rollback, comparison, and collaboration.                              |
| Why do we use Git?                             | To track changes, collaborate safely, maintain history, recover previous versions, and support parallel development.             |
| What is the difference between Git and GitHub? | Git is the version control software. GitHub is a cloud platform that hosts Git repositories and provides collaboration features. |
| What is a repository?                          | A repository is the complete collection of project files and Git history.                                                        |

---

# Git Workflow

| Question                          | Answer                                                                   |
| --------------------------------- | ------------------------------------------------------------------------ |
| What is the Working Directory?    | The location where files are created and modified before staging.        |
| What is the Staging Area?         | A temporary area where selected changes are prepared before committing.  |
| What is a Commit?                 | A snapshot of the staged changes stored permanently in Git history.      |
| Explain the Git workflow.         | Working Directory → Staging Area → Local Repository → Remote Repository. |
| Why does Git have a staging area? | It allows selective commits instead of committing every modified file.   |

---

# Branching & Merging

| Question                  | Answer                                                                                                 |
| ------------------------- | ------------------------------------------------------------------------------------------------------ |
| What is a branch?         | An independent line of development.                                                                    |
| Why use feature branches? | To isolate development without affecting the stable branch.                                            |
| What is merging?          | Combining the history of one branch into another.                                                      |
| What is rebasing?         | Replaying commits on top of another branch to create a linear history.                                 |
| Merge vs Rebase?          | Merge preserves branch history. Rebase creates a cleaner, linear history by rewriting commit ancestry. |
| What is a merge conflict? | A conflict that occurs when Git cannot automatically combine changes made to the same part of a file.  |

---

# Remote Repositories

| Question                           | Answer                                                                                                       |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| What is origin?                    | The default name for the primary remote repository.                                                          |
| What is upstream?                  | The original repository from which a fork was created.                                                       |
| Difference between fetch and pull? | Fetch downloads changes only. Pull performs fetch followed by merge (or rebase, depending on configuration). |
| Difference between clone and pull? | Clone creates a complete local repository. Pull updates an existing local repository.                        |

---

# Git Internals

| Question                         | Answer                                                                                         |
| -------------------------------- | ---------------------------------------------------------------------------------------------- |
| What is HEAD?                    | A reference pointing to the currently checked-out commit or branch.                            |
| What is a SHA hash?              | A unique identifier used by Git to identify commits and other objects.                         |
| What are Git objects?            | Git stores data as blobs (file contents), trees (directories), commits, and tags.              |
| Does Git store file differences? | Internally, Git stores snapshots of project states, with optimizations for storage efficiency. |
| Why is Git called distributed?   | Every clone contains the complete repository history, allowing work without a central server.  |

---

# Practical Scenarios

| Scenario                              | Expected Approach                                                                                                              |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| You committed to the wrong branch     | Create a new branch if needed, or move the commit using `git cherry-pick`/`git reset` depending on whether it has been pushed. |
| You accidentally deleted a file       | Restore it from the latest commit using `git restore` or retrieve it from history.                                             |
| A push is rejected                    | Pull or fetch the latest changes, resolve conflicts if necessary, then push again.                                             |
| You need to temporarily switch tasks  | Use `git stash` to save uncommitted work, then restore it later.                                                               |
| A teammate force-pushed to the remote | Fetch the latest state, inspect history carefully, and coordinate before rewriting local history.                              |

---

# Command-Based Questions

| Question                      | Expected Command                  |
| ----------------------------- | --------------------------------- |
| View repository status        | `git status`                      |
| View commit history           | `git log --oneline`               |
| Create and switch to a branch | `git switch -c feature-name`      |
| Stage all changes             | `git add .`                       |
| Undo staging                  | `git restore --staged <file>`     |
| Show differences              | `git diff`                        |
| Push a new branch             | `git push -u origin feature-name` |

---

# Frequently Asked DevOps Interview Questions

| Question                                                       | What the Interviewer Wants to Assess                     |
| -------------------------------------------------------------- | -------------------------------------------------------- |
| Describe your Git workflow.                                    | Practical development experience.                        |
| How do you resolve merge conflicts?                            | Collaboration and troubleshooting skills.                |
| How do you recover a deleted commit?                           | Knowledge of Git history and recovery.                   |
| When would you use rebase instead of merge?                    | Understanding of clean commit history.                   |
| How do multiple developers work on the same repository safely? | Branching strategy and collaboration practices.          |
| Why should commits be small and focused?                       | Maintainability, reviewability, and rollback capability. |

---

# Common Mistakes

| Mistake                           | Better Practice                               |
| --------------------------------- | --------------------------------------------- |
| Committing directly to `main`     | Use feature branches and Pull Requests.       |
| Large unrelated commits           | Create small, logical commits.                |
| Poor commit messages              | Write meaningful, descriptive messages.       |
| Forgetting to pull before pushing | Synchronize with the remote first.            |
| Force-pushing shared branches     | Avoid unless coordinated with the team.       |
| Committing secrets or credentials | Use `.gitignore` and secret management tools. |

---

# Interview Tips

| Recommendation                   | Benefit                                              |
| -------------------------------- | ---------------------------------------------------- |
| Explain concepts before commands | Demonstrates understanding rather than memorization. |
| Use real project examples        | Shows practical experience.                          |
| Draw the Git workflow if needed  | Communicates mental models clearly.                  |
| Understand Git internals         | Helps answer advanced questions confidently.         |
| Practice resolving conflicts     | Common practical interview exercise.                 |

---

# Related Documents

| Document           | Purpose                    |
| ------------------ | -------------------------- |
| README.md          | Sprint overview            |
| Dictionary.md      | Git terminology            |
| Analogies.md       | Mental models              |
| Cheatsheet.md      | Command reference          |
| Troubleshooting.md | Git debugging and recovery |
