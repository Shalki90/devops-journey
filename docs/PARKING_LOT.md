# Parking Lot

## Purpose

This document captures ideas, architectural decisions, and documentation that have been intentionally postponed.

These items are not forgotten—they are deferred until the appropriate stage of the learning journey.

An item should be added only if:

* It requires future discussion or validation.
* It depends on knowledge that has not yet been acquired.
* Creating the associated artifact immediately would violate the **No Empty Artifacts** principle.

---

## Parked Items

| ID    | Item                                | Reason Parked                                                                                                               | Revisit When                                                                             | Status    |
| ----- | ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | --------- |
| P-001 | AI_PLAYBOOK.md                      | AI usage patterns are still evolving. More practical experience is needed before documenting best practices.                | After completing multiple technical phases and real projects.                            | 🟡 Parked |
| P-002 | Design Before Execution             | Potential learning principle that requires further validation across multiple topics before becoming a permanent principle. | When sufficient evidence has been gathered through the learning journey.                 | 🟡 Parked |
| P-003 | Architecture Diagrams               | Diagrams should represent real systems rather than hypothetical designs.                                                    | As real architectures are built throughout the curriculum.                               | 🟡 Parked |
| P-004 | Labs & Projects Handbook            | The structure should emerge naturally from practical work rather than being designed in advance.                            | After completing multiple hands-on labs and projects.                                    | 🟡 Parked |
| P-005 | Resume & Portfolio Guide            | Best practices should be based on completed work rather than assumptions.                                                   | After building a substantial portfolio of projects.                                      | 🟡 Parked |
| P-006 | git cherry-pick                     | Useful but not required for foundational Git proficiency. Better learned after real project collaboration experience.       | After completing Linux and beginning team-style project work.                            | 🟡 Parked |
| P-007 | git rebase                          | Rewrites commit history and requires strong understanding of branches, merges, and shared history.                          | After gaining practical Git experience across multiple projects.                         | 🟡 Parked |
| P-008 | Interactive Rebase                  | Advanced history editing provides little value until working with larger commit histories.                                  | After learning standard rebase and participating in collaborative development workflows. | 🟡 Parked |
| P-009 | Commit Squashing Strategies         | Best understood after experiencing noisy commit histories in real projects.                                                 | During project development and repository maintenance phases.                            | 🟡 Parked |
| P-010 | Git Bisect                          | Requires larger commit histories and realistic debugging scenarios to provide meaningful value.                             | After building projects with significant development history.                            | 🟡 Parked |
| P-011 | Advanced Git Collaboration Patterns | Concepts such as release branches, trunk-based development, and GitFlow are premature without real team workflows.          | During project and platform engineering phases.                                          | 🟡 Parked |

---

## Guidelines

* Park decisions, not everyday tasks.
* Park ideas that are valuable but premature.
* Revisit parked items periodically.
* Remove items once they have been implemented or intentionally discarded.
* Avoid using this document as a to-do list.
* Technical learning questions belong in **QUESTIONS_PARKED.md**, not here.

---

## Recent Additions

### Phase 02 — Git & Version Control

The following Git topics were intentionally deferred:

* git cherry-pick
* git rebase
* Interactive Rebase
* Commit Squashing
* Git Bisect
* Advanced Collaboration Workflows

Reason:

These topics provide the most value after working on larger projects, collaborating with multiple contributors, and managing more complex repository histories. They were intentionally postponed to prioritize strong fundamentals before advanced Git history manipulation techniques.

---

Version: 0.2

Status: Living Document