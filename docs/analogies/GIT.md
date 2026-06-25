# Git Analogies

## Purpose

This document maps real-world analogies to Git concepts used throughout the DevOps learning roadmap.

The goal is not to memorize commands, but to understand the responsibility of each Git component through familiar real-world scenarios.

> **Learning Principle:** One analogy should represent one primary Git concept.

---

# Canonical Git Analogies

| Analogy                                            | Git Concept            | Explanation                                                                          |
| -------------------------------------------------- | ---------------------- | ------------------------------------------------------------------------------------ |
| Book                                               | Repository             | The complete collection of chapters together with its revision history.              |
| Official Published Book                            | Main Branch            | The accepted version that readers consume.                                           |
| Personal Draft Copy                                | Branch                 | An isolated copy where work can safely continue without affecting the official book. |
| Desk                                               | Working Directory      | The place where active writing and editing occurs.                                   |
| Stack of Pages Ready for Submission                | Staging Area           | Selected changes prepared for inclusion in the next revision.                        |
| Personal Revision Archive                          | Local Repository       | The author's private record of all saved revisions.                                  |
| Publishing House Archive                           | Remote Repository      | The shared repository where official revisions are stored.                           |
| Saving a New Revision                              | Commit                 | Creates a permanent snapshot of the current work.                                    |
| Revision Number                                    | Commit Hash            | Uniquely identifies a specific revision in history.                                  |
| Bookmark Showing Current Chapter                   | HEAD                   | Indicates the current position being edited.                                         |
| Writing Chapter 5 Separately                       | Branching              | Allows development to continue independently from the main book.                     |
| Approved Chapter Inserted into Official Book       | Merge                  | Combines completed work into the main branch.                                        |
| Chapter Added Without Extra Editorial Work         | Fast-Forward Merge     | The official book simply advances because no conflicting history exists.             |
| Editorial Record of Combining Drafts               | Merge Commit           | Documents the integration of multiple histories.                                     |
| Two Authors Rewrite the Same Paragraph Differently | Merge Conflict         | Git cannot automatically decide which change should win.                             |
| Editor Chooses Final Wording                       | Conflict Resolution    | A human decides how competing changes should be combined.                            |
| Submit Draft for Editorial Review                  | Pull Request           | Proposed changes are reviewed before entering the official book.                     |
| Check Library Catalog for New Editions             | git fetch              | Learn about remote updates without modifying the local copy.                         |
| Bring Home the Latest Edition                      | git pull               | Fetch and integrate remote changes into the local branch.                            |
| Send Your New Edition to the Publisher             | git push               | Publish local commits to the remote repository.                                      |
| Mark Pages for Inclusion in Next Revision          | git add                | Move changes from the Working Directory to the Staging Area.                         |
| Publish a New Draft Revision                       | git commit             | Save staged work into the Local Repository.                                          |
| Remove Pages from Submission Stack                 | git restore --staged   | Remove changes from the Staging Area while keeping the work.                         |
| Throw Away Unsaved Edits                           | git restore            | Discard changes from the Working Directory.                                          |
| Publish Chapter 5 that Reverses Chapter 4          | git revert             | Create a new revision that undoes a previous published change.                       |
| Tear Out Unpublished Chapter 4 and Rewrite It      | git reset              | Move history backward as if the bad revision never happened.                         |
| Put Unfinished Chapter in a Drawer                 | git stash              | Temporarily save unfinished work and restore it later.                               |
| Official Publishing House Copy                     | origin/main            | The latest known state of the remote main branch.                                    |
| Library Catalog Reference                          | Remote Tracking Branch | Local knowledge of the remote repository's current state.                            |
| Personal Draft Following Official Book             | Tracking Branch        | A local branch configured to follow a remote branch.                                 |

---

# Engineering Principles Learned

## 1. History Is Valuable

Git is not merely a storage tool.

Its primary purpose is preserving history so changes can be understood, reviewed, and recovered.

Examples:

* Commits
* Commit History
* Revert
* Merge Commits

---

## 2. Isolation Reduces Risk

Work should be performed independently before integration.

Examples:

* Branches
* Pull Requests
* Feature Development

This allows experimentation without damaging the official history.

---

## 3. Shared History Requires Discipline

Once work has been shared, history should be treated carefully.

Examples:

* Prefer `git revert` over `git reset` for published changes.
* Review changes before merging.
* Resolve conflicts intentionally.

---

## 4. Build Mental Models

The goal of these analogies is to develop intuition.

When encountering a Git workflow, the real-world analogy should make the responsibility of each command immediately understandable.

Examples:

* Branch = Personal Draft Copy
* Commit = Revision
* Merge = Insert Approved Chapter
* Revert = Publish a Correction Chapter
* Stash = Put Work in a Drawer

---

# Future Analogy Files

This format will also be used for:

* `docs/analogies/linux.md`
* `docs/analogies/docker.md`
* `docs/analogies/kubernetes.md`
* `docs/analogies/cloud.md`

---

Version: 0.1

Status: Living Document