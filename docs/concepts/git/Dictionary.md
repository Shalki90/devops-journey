# Git Dictionary

**Document Version:** 1.0
**Sprint:** 2 — Git & Version Control

---

# Purpose

This document provides a structured dictionary of core **Git and Version Control terminology**.

It is designed for quick reference, interview preparation, and foundational understanding.

---

# Core Git Concepts

| Term              | Definition                                                                 |
| ----------------- | -------------------------------------------------------------------------- |
| Git               | A distributed version control system used to track changes in source code. |
| Version Control   | System that records changes to files over time.                            |
| Repository        | A storage location that contains project files and Git history.            |
| Commit            | A snapshot of changes saved in the repository history.                     |
| Staging Area      | Intermediate area where changes are prepared before committing.            |
| Working Directory | The local directory where files are actively edited.                       |

---

# Git Workflow Concepts

| Term   | Definition                                         |
| ------ | -------------------------------------------------- |
| Add    | Command used to move changes to staging area.      |
| Commit | Saves staged changes into repository history.      |
| Push   | Sends local commits to a remote repository.        |
| Pull   | Fetches and merges changes from remote repository. |
| Fetch  | Downloads changes from remote without merging.     |
| Clone  | Creates a local copy of a remote repository.       |

---

# Branching & Merging

| Term           | Definition                                           |
| -------------- | ---------------------------------------------------- |
| Branch         | Independent line of development within a repository. |
| Main Branch    | Primary stable branch of a project.                  |
| Feature Branch | Branch used to develop new features independently.   |
| Merge          | Combining changes from one branch into another.      |
| Rebase         | Reapplying commits on top of another base branch.    |
| Conflict       | Occurs when Git cannot automatically merge changes.  |

---

# Remote Repository Concepts

| Term         | Definition                                      |
| ------------ | ----------------------------------------------- |
| Remote       | A version of the repository hosted on a server. |
| Origin       | Default name for the primary remote repository. |
| Upstream     | The original repository a fork is based on.     |
| Fork         | A personal copy of another repository.          |
| Pull Request | A request to merge changes into a main branch.  |

---

# Git Internals

| Term  | Definition                             |
| ----- | -------------------------------------- |
| SHA   | Unique identifier for Git objects.     |
| Blob  | Stores file content in Git.            |
| Tree  | Represents directory structure in Git. |
| HEAD  | Pointer to the current commit.         |
| Index | Same as staging area.                  |

---

# Key Insight

Git is fundamentally a **content-addressable storage system**.

| Layer             | Meaning                      |
| ----------------- | ---------------------------- |
| Working Directory | Human interaction layer      |
| Staging Area      | Preparation layer            |
| Repository        | Permanent history layer      |
| Objects           | Internal data representation |

---

# Related Documents

* README.md
* Analogies.md (next)
* Cheatsheet.md (next)
* Interview.md (next)
* Troubleshooting.md (next)