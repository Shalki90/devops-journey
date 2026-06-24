# Session 07

## Topics

* Why Version Control Exists
* Git Fundamentals
* Distributed Version Control
* Repository Structure
* Working Directory
* Staging Area
* Local Repository
* Remote Repository
* Commits
* Commit History
* Git Diff Operations
* Branching
* Branch Isolation
* Fast-Forward Merges
* Merge Conflicts
* Conflict Resolution
* Push
* Fetch
* Pull
* Remote Tracking Branches

---

## Hands-on Labs

### Lab 1 — Working Directory and Staging Area

Objective:

Understand the difference between modified files, staged files, and committed files.

Actions:

Created:

```text
TEST.md
```

Added content:

```text
Git Phase 02 Test
```

Observed:

```bash
git status
```

Added file to staging:

```bash
git add TEST.md
```

Verified staged content:

```bash
git diff --staged
```

Added additional modifications after staging and compared:

```bash
git diff
git diff --staged
```

Key Insight:

The Working Directory and Staging Area are separate states.

A file can contain changes that are partially staged and partially unstaged.

---

### Lab 2 — First Git Commit

Objective:

Create and inspect a commit.

Actions:

Created commit:

```bash
git commit -m "Git learning test"
```

Reviewed history:

```bash
git log --oneline
```

Observations:

A commit creates a permanent snapshot of staged changes.

Each commit receives a unique hash.

Example:

```text
3ed01d8 Git learning test
```

Key Insight:

A commit moves changes from the Staging Area into the Local Repository.

---

### Lab 3 — Restoring Changes

Objective:

Understand how Git restores file states.

Actions:

Modified:

```text
TEST.md
```

Used:

```bash
git restore TEST.md
```

Observations:

Uncommitted changes were discarded.

The file returned to the state stored in the latest commit.

Key Insight:

Git restores from the current commit, not from GitHub.

---

### Lab 4 — Unstaging Changes

Objective:

Separate the Staging Area from the Working Directory.

Actions:

Modified:

```text
TEST.md
```

Staged changes:

```bash
git add TEST.md
```

Removed changes from staging:

```bash
git restore --staged TEST.md
```

Observations:

Changes remained in the Working Directory.

Changes were removed from the Staging Area.

Key Insight:

Unstaging does not discard work.

It only removes changes from the next commit.

---

### Lab 5 — Branch Creation

Objective:

Create an isolated development branch.

Actions:

Created branch:

```bash
git switch -c feature/git-branch-learning
```

Verified branches:

```bash
git branch
```

Created:

```text
BRANCH_TEST.md
```

Committed changes.

Observations:

The new branch contained additional history not present in main.

Key Insight:

Branches are independent lines of development.

---

### Lab 6 — Fast-Forward Merge

Objective:

Merge a branch without creating a merge commit.

Actions:

Switched back to:

```bash
git switch main
```

Merged:

```bash
git merge feature/git-branch-learning
```

Observations:

Git performed a fast-forward merge.

History remained linear.

Example:

```text
main → commit moved forward
```

Key Insight:

A fast-forward merge occurs when no competing history exists.

Git simply moves the branch pointer.

---

### Lab 7 — Merge Conflict Creation

Objective:

Understand why merge conflicts occur.

Actions:

Created branches:

```text
feature-a
feature-b
```

Both branches modified:

```text
TEST.md
```

Different content was committed in each branch.

Attempted merge:

```bash
git merge feature-a
```

Observations:

Git reported:

```text
CONFLICT (content): Merge conflict in TEST.md
```

Conflict markers appeared:

```text
<<<<<<< HEAD
Feature B change
=======
Feature A change
>>>>>>> feature-a
```

Key Insight:

Git cannot determine business intent when the same content is modified differently.

Human intervention is required.

---

### Lab 8 — Merge Conflict Resolution

Objective:

Resolve a merge conflict manually.

Actions:

Edited:

```text
TEST.md
```

Final content:

```text
Feature B change
Feature A change
```

Staged resolution:

```bash
git add TEST.md
```

Completed merge:

```bash
git commit
```

Observations:

Git created a merge commit.

Example:

```text
Merge branch 'feature-a' into feature-b
```

Key Insight:

A merge commit preserves both development histories.

---

### Lab 9 — Push, Fetch, and Pull

Objective:

Understand synchronization between local and remote repositories.

Actions:

Published local commits:

```bash
git push
```

Reviewed tracking information:

```bash
git branch -vv
```

Discussed:

```bash
git fetch
git pull
```

Observations:

Fetch updates knowledge of the remote repository.

Pull updates the local branch using remote changes.

Push publishes local commits to GitHub.

Key Insight:

```text
git fetch
```

does not modify the Working Directory or local branch.

```text
git pull
```

integrates remote changes into the current branch.

---

## Engineering Questions

* Why does Git use a staging area instead of committing directly?
* Why are branches lightweight compared to copying an entire project?
* Why can fast-forward merges avoid creating a merge commit?
* Why can Git merge some changes automatically but not others?
* Why does fetch update remote tracking branches without modifying local branches?
* Why does Git protect uncommitted work during pull operations?

---

## Engineering Insights

* Git is fundamentally a history-management system.
* The Working Directory, Staging Area, and Local Repository are distinct states.
* Commits represent snapshots rather than file differences.
* Branches allow safe experimentation.
* Fast-forward merges preserve linear history.
* Merge commits preserve multiple histories.
* Conflicts occur when Git cannot determine intent.
* Fetch updates remote knowledge.
* Pull integrates remote changes.
* Push publishes local history.

---

## Engineering Principles Reinforced

* Preserve History
* Safe Experimentation
* Incremental Change
* Explicit Review Before Integration
* Human Judgment Over Automation
* Traceability Enables Understanding

---

## Repository Updates

Updated:

* PROJECT_CONTEXT.md
* docs/DICTIONARY.md

Created:

* session-notes/session-07.md

---

## Phase Status

Phase 02 — Git & Version Control

Progress:

* Git fundamentals completed.
* Branching completed.
* Merging completed.
* Conflict resolution completed.
* Push, Fetch, and Pull introduced.

Remaining:

* GitHub Pull Request Workflow
* Tracking Branches
* git revert
* git reset
* git stash
* Advanced Git concepts (optional)

---

## Next Session

* DevOps / Cloud / AI Infrastructure news review
* Complete remaining Git topics
* GitHub Pull Request workflow
* Determine readiness to close Phase 02