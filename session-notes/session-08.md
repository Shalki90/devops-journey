# Session 08

## Topics

* Remote Repositories
* Remote Tracking Branches
* Fetch vs Pull
* Local vs Remote Main Branch
* Tracking Branches
* Merge Conflict Resolution
* Fast-Forward Merges
* Merge Commits
* Git Revert
* Git Reset
* Git Stash
* Pull Request Workflow
* Git Collaboration Model
* Git Book Analogy
* Git Engineering Principles

---

## Hands-on Labs

### Lab 1 — Fast-Forward Merge

Objective:

Understand how Git performs a merge when no divergent history exists.

Actions:

* Created a feature branch.
* Added a new file.
* Committed changes.
* Switched back to main.
* Merged feature branch.

Commands:

```bash
git switch -c feature/git-branch-learning

echo "test" > BRANCH_TEST.md

git add .
git commit -m "Add branch test file"

git switch main

git merge feature/git-branch-learning
```

Observations:

* No merge commit was created.
* Git simply moved the branch pointer forward.

Key Insight:

A fast-forward merge occurs when main has not diverged from the feature branch.

---

### Lab 2 — Branch Isolation

Objective:

Understand that branches maintain independent histories.

Actions:

* Created multiple branches.
* Modified the same file differently.
* Observed different file contents between branches.

Observations:

* Changes made in one branch did not automatically appear in another.
* Each branch maintained its own history.

Key Insight:

Branches provide safe isolation for development work.

---

### Lab 3 — Merge Conflict Creation

Objective:

Intentionally create a merge conflict.

Actions:

Feature A:

```bash
echo "Feature A change" > TEST.md
git add .
git commit -m "Feature A modifies TEST.md"
```

Feature B:

```bash
echo "Feature B change" > TEST.md
git add .
git commit -m "Feature B modifies TEST.md"
```

Attempted merge:

```bash
git merge feature-a
```

Result:

```text
CONFLICT (content): Merge conflict in TEST.md
```

Observations:

Git could not determine which modification should win.

Key Insight:

Conflicts occur when Git cannot automatically combine competing changes.

---

### Lab 4 — Conflict Resolution

Objective:

Resolve a merge conflict manually.

Observed file:

```text
<<<<<<< HEAD
Feature B change
=======
Feature A change
>>>>>>> feature-a
```

Actions:

Edited file:

```text
Feature B change
Feature A change
```

Resolved:

```bash
git add TEST.md
git commit
```

Result:

```text
Merge branch 'feature-a' into feature-b
```

Key Insight:

Conflict resolution is a human decision rather than a Git decision.

---

### Lab 5 — Push, Fetch and Pull Reasoning

Objective:

Understand synchronization between local and remote repositories.

Concepts Discussed:

```text
GitHub main
origin/main
local main
```

Observations:

* GitHub main represents the actual remote repository.
* origin/main represents local knowledge of the remote repository.
* main represents the local working branch.

Key Insight:

Git tracks multiple versions of reality simultaneously.

---

### Lab 6 — Git Revert Mental Model

Objective:

Understand safe history correction.

Book Analogy:

```text
Chapter 4 published
Chapter 4 contains mistakes
Publish Chapter 5 that undoes Chapter 4
```

Command:

```bash
git revert <commit>
```

Observations:

* Original history remains intact.
* New history explicitly documents the correction.

Key Insight:

Revert preserves shared history.

---

### Lab 7 — Git Reset Mental Model

Objective:

Understand history rewriting.

Book Analogy:

```text
Chapter 4 never published
Chapter 4 is bad
Throw it away
Rewrite Chapter 4
```

Command:

```bash
git reset
```

Observations:

* History can be rewritten safely before sharing.

Key Insight:

Reset is appropriate for unpublished work.

---

### Lab 8 — Git Stash Mental Model

Objective:

Temporarily pause unfinished work.

Book Analogy:

```text
Unfinished Chapter 5
Urgent correction required in Chapter 2

Put Chapter 5 into a drawer
Fix Chapter 2
Return later
```

Command:

```bash
git stash
```

Observations:

* Work can be safely stored.
* Context switching becomes easier.

Key Insight:

Stash preserves incomplete work without committing it.

---

## Git Analogy Challenge

Created a complete book-writing analogy for Git concepts.

Covered:

* Repository
* Branch
* Commit
* Merge
* Conflict
* Revert
* Reset
* Stash
* Fetch
* Pull
* Push
* Pull Request

Result:

Created:

```text
docs/analogies/GIT.md
```

---

## Engineering Questions

* Why does Git preserve multiple views of repository state simultaneously?
* Why is revert safer than reset for shared history?
* Why should developers avoid committing directly to main?
* Why are pull requests valuable even when code works correctly?
* Why does conflict resolution require human judgment?

---

## Engineering Insights

* History is an engineering asset.
* Isolation reduces risk.
* Shared history should be treated carefully.
* Git is primarily a history-management system.
* Branches enable safe experimentation.
* Pull requests improve quality before integration.
* Revert preserves trust in shared repositories.
* Reset is safe only when history has not been shared.
* Stash enables efficient context switching.
* Remote tracking branches provide awareness without modification.

---

## Engineering Principles Reinforced

* History Is Valuable
* Isolation Reduces Risk
* Shared History Requires Discipline
* Review Before Integration
* Safe Experimentation
* Explicit Change Management

---

## Repository Updates

Updated:

* PROJECT_CONTEXT.md
* docs/ROADMAP.md
* docs/DICTIONARY.md
* docs/ANALOGIES.md
* docs/PARKING_LOT.md

Created:

* docs/analogies/GIT.md
* docs/curriculum/phase-02-git-and-version-control.md
* session-notes/session-08.md

---

## Phase Status

Phase 02 — Git & Version Control

Status:

```text
Completed
```

Completed Topics:

* Git Fundamentals
* Repository Structure
* Working Directory
* Staging Area
* Local Repository
* Remote Repository
* Commits
* Branches
* Merging
* Merge Conflicts
* Conflict Resolution
* Push
* Fetch
* Pull
* Tracking Branches
* Pull Request Workflow
* Git Revert
* Git Reset
* Git Stash

---

## Next Session

Phase 03 — Linux Fundamentals

Planned Topics:

* Why Linux Dominates Infrastructure
* Linux Architecture
* Linux Filesystem
* Files and Directories
* Navigation Commands
* File Manipulation Commands
* Permissions
* Users and Groups
* Processes
* Package Management

---

Version: 1.0

Status: Complete
