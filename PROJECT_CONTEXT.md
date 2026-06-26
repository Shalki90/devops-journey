# Project Context

## Purpose

This document preserves the philosophy, context, current progress, repository structure, and working conventions of the DevOps Engineering Journey.

Its purpose is to provide continuity across future conversations without requiring the complete chat history.

This document is intended for both the mentor (ChatGPT) and Future Shalki.

---

# Vision

Build deep expertise in DevOps, Platform Engineering, Cloud, AI Infrastructure, Kubernetes, and modern software engineering while developing the mindset, engineering principles, and decision-making abilities expected of senior engineers and architects.

The objective extends beyond learning tools—it focuses on understanding systems, reasoning about trade-offs, and building engineering intuition that remains valuable for years.

---

# Learning Philosophy

The learning journey follows these principles:

* Foundations before complexity.
* Understand before memorizing.
* Concepts before tools.
* Progressive disclosure.
* Challenge ideas before accepting them.
* Design before implementation.
* Continuous refinement.
* Build to reinforce understanding.
* Learn how modern AI systems apply engineering concepts.
* Every document has a single responsibility.
* No empty artifacts.

---

# Repository Philosophy

The repository is designed as an Engineering Operating System (Engineering OS).

Documentation is treated as an engineering artifact rather than personal notes.

The primary audience is **Future Shalki**.

Recruiters and interviewers are considered a secondary audience for selected artifacts such as projects, labs, architecture, and the repository README.

The repository should evolve into a long-term engineering handbook rather than a collection of learning notes.

GitHub serves as the canonical source of truth for the project.

---

# Repository

GitHub Repository

```text
https://github.com/Shalki90/devops-journey
```

Git operations use SSH authentication.

---

# Documentation Architecture

## Root

* PROJECT_CONTEXT.md
* README.md
* CHANGELOG.md

## docs/

* ENGINEERING_CHARTER.md
* ROADMAP.md
* CURRICULUM.md
* LEARNING_PRINCIPLES.md
* ENGINEERING_PRINCIPLES.md
* DICTIONARY.md
* ANALOGIES.md
* AI_IN_PRACTICE.md
* PARKING_LOT.md

## docs/curriculum/

One document per learning phase.

## docs/analogies/

One analogy document per engineering domain.

## session-notes/

One summary document per completed learning session.

## labs/

Hands-on labs completed throughout the roadmap.

## projects/

Projects built during the roadmap.

---

# Documentation Workflow

During learning:

* 📖 New engineering terms are added to the Dictionary.
* 🏡 Useful analogies are added to Analogies.
* 💡 Timeless engineering lessons are added to Engineering Principles.
* 🤖 Real-world AI implementations are added to AI in Practice.
* ❓ Deferred technical questions are added to Parking Lot.

Documentation should support learning rather than interrupt it.

Reference documents are updated incrementally throughout the journey.

Session notes summarize learning sessions.

Reference documents capture long-term knowledge.

---

# Current Progress

## Phase Status

* ✅ Phase 00 — Engineering OS
* ✅ Phase 01 — Internet & Networking Fundamentals
* ✅ Phase 02 — Git & Version Control
* 🟡 Phase 03 — Linux Fundamentals (In Progress)
* ⬜ Remaining phases not yet started

---

# Recent Milestones

Completed:

* Engineering OS established.
* Documentation architecture finalized.
* Phase 01 conceptual networking completed.
* Phase 01 hands-on networking labs completed.
* Wireshark packet analysis completed.
* Networking analogies library created.
* Engineering principles library established.
* AI in Practice documentation established.
* Session documentation standardized.
* Local Git repository initialized.
* GitHub repository created.
* SSH authentication configured.
* Initial repository successfully pushed to GitHub.
* Git fundamentals completed.
* Working Directory, Staging Area, Local Repository, and Remote Repository understood.
* Git commit lifecycle completed.
* Git history inspection completed.
* Branch creation and branch isolation demonstrated.
* Fast-forward merge demonstrated.
* Merge conflict creation and resolution completed.
* First merge commit created.
* Push, Fetch, and Pull concepts completed.
* Remote tracking branch concepts completed.
* GitHub collaboration workflow understood.
* Pull Request workflow completed.
* git revert completed.
* git reset completed.
* git stash completed.
* Git analogy challenge completed.
* Phase 02 officially completed.

---

# Mentorship Style

Each learning session follows this structure:

1. DevOps / Cloud / AI Infrastructure news discussion.
2. Knowledge assessment for the upcoming topic.
3. Update repository documentation required before the phase/topic.
4. Learning session.
5. Update learning documents during the phase as needed.
6. End-of-session notes.
7. Commit, push, and repository review.

Preference is given to understanding systems rather than completing topics quickly.

---

# Working Conventions

* Use GitHub as the primary repository.
* Keep documentation synchronized with learning progress.
* Avoid redesigning repository structure unless explicitly requested.
* Prefer improving existing documents over creating new ones.
* Build reusable engineering knowledge instead of session-specific notes.
* Every hands-on lab should reinforce conceptual understanding.

---

# Next Planned Work

## Immediate Next Phase

Phase 03 — Linux Fundamentals

Progress:

Completed:
- Linux architecture overview
- GNU
- Shell and Bash
- Linux distributions
- BIOS and UEFI
- GRUB
- initramfs
- Kernel
- User Space vs Kernel Space
- System Calls
- Device Drivers

Upcoming:
- Processes
- Process Lifecycle
- fork()
- exec()
- Scheduling
- Memory Management
- Filesystem
- Services
- Permissions
- Users & Groups
- Logs
---

# Career Target

Primary Target Role:

* Platform Engineer

Secondary Paths:

* Site Reliability Engineer (SRE)
* DevOps Engineer
* AI Infrastructure Engineer

Current Compensation:

* ~20 LPA

Target Timeline:

* Begin interviewing by October.

Long-Term Compensation Goal:

* 30–40+ LPA through demonstrated engineering capability, projects, infrastructure knowledge, and strong interview performance.

---

# Continuing in a New Conversation

When continuing this mentorship in a new conversation:

1. Read PROJECT_CONTEXT.md.
2. Review the latest Session Note.
3. Review docs/ROADMAP.md.
4. Review docs/CURRICULUM.md.
5. Continue from the current phase.

Assume the Engineering OS, documentation architecture, repository conventions, and learning philosophy have already been established.

Do not redesign the repository unless explicitly requested.

---

# Suggested Opening Prompt

We are continuing the DevOps Engineering Journey documented in this repository.

Repository:

https://github.com/Shalki90/devops-journey

Please begin by reading:

1. PROJECT_CONTEXT.md
2. Latest session note
3. docs/ROADMAP.md
4. docs/CURRICULUM.md

Assume the Engineering OS, documentation architecture, repository conventions, and learning philosophy have already been established.

Continue the mentorship from the current phase without redesigning the repository.

When appropriate, recommend updates to:

* Dictionary
* Analogies
* Engineering Principles
* AI in Practice
* Parking Lot
* Curriculum

Always keep documentation synchronized with learning.

---

# Mentorship Rules

## Session Flow

1. Industry News
2. Hands-on Work
3. Documentation Updates
4. Commit
5. Push
6. Repository Review
7. Next Topic

## Documentation Workflow

Before Phase:
- PROJECT_CONTEXT.md
- ROADMAP.md
- Create curriculum file

During Phase:
- Dictionary
- Analogies
- Engineering Principles
- AI in Practice
- Parking Lot

End Session:
- Session Notes

Phase Completion:
- PROJECT_CONTEXT.md
- ROADMAP.md
- Curriculum File

Cleanup:
- Remove temporary artifacts

Version: 0.6

Status: Living Document