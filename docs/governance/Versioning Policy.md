# Versioning Policy

**Document Version:** 1.0

---

# Purpose

This document defines the versioning policy for the **DevOps Engineering Journey** repository.

The policy establishes a consistent approach for versioning the repository, documentation, sprint content, laboratories, projects, and reusable assets. It ensures that changes are traceable, meaningful, and easy to understand.

---

# Versioning Philosophy

Version numbers communicate the maturity and significance of changes.

Versioning should:

* Reflect meaningful progress.
* Maintain historical traceability.
* Support continuous improvement.
* Avoid unnecessary version increments.
* Remain simple and predictable.

---

# Repository Versioning

The repository follows **Semantic Versioning (SemVer)**.

Format:

```text
MAJOR.MINOR.PATCH
```

Example:

```text
1.0.0
```

---

# Semantic Version Definitions

| Version Component | Description                                                   | Example |
| ----------------- | ------------------------------------------------------------- | ------- |
| MAJOR             | Significant restructuring or major milestone                  | 2.0.0   |
| MINOR             | New sprint, major documentation, or feature addition          | 1.4.0   |
| PATCH             | Corrections, refinements, typo fixes, formatting improvements | 1.4.3   |

---

# Repository Release Guidelines

| Version | Typical Changes                |
| ------- | ------------------------------ |
| 1.0.0   | Initial repository release     |
| 1.1.0   | Sprint completion              |
| 1.2.0   | New engineering documentation  |
| 1.3.0   | Additional labs or projects    |
| 2.0.0   | Major repository restructuring |

Repository versions should represent meaningful milestones rather than every individual commit.

---

# Document Versioning

Every document begins with:

```text
Document Version: 1.0
```

Subsequent revisions follow the table below.

| Version | Change Type                                    |
| ------- | ---------------------------------------------- |
| 1.0     | Initial complete version                       |
| 1.1     | Minor clarification or formatting improvements |
| 1.2     | Additional examples or explanations            |
| 1.3     | Expanded content without restructuring         |
| 2.0     | Major rewrite or structural redesign           |

Minor typographical corrections do not always require a version change unless the document history is being tracked explicitly.

---

# Sprint Versioning

Each sprint progresses through identifiable stages.

| Stage       | Description                                 |
| ----------- | ------------------------------------------- |
| Planned     | Sprint objectives defined                   |
| In Progress | Learning and documentation underway         |
| Completed   | All planned documentation and labs finished |
| Reviewed    | Content validated and refined               |

Sprint completion should be reflected in the roadmap and project context documents.

---

# Laboratory Versioning

Labs evolve as understanding improves.

| Version | Meaning                                 |
| ------- | --------------------------------------- |
| 1.0     | Initial implementation                  |
| 1.1     | Improved instructions or validation     |
| 1.2     | Additional exercises or troubleshooting |
| 2.0     | Major redesign or expanded scope        |

---

# Project Versioning

Projects should be versioned independently where appropriate.

Suggested milestones:

| Version | Meaning                      |
| ------- | ---------------------------- |
| 0.1     | Initial prototype            |
| 0.5     | Functional implementation    |
| 1.0     | Stable release               |
| 1.1+    | Feature enhancements         |
| 2.0     | Major architectural redesign |

---

# Change Classification

| Change Type              | Version Impact     |
| ------------------------ | ------------------ |
| Typographical correction | Patch or no change |
| Improved explanation     | Minor              |
| New examples             | Minor              |
| New section              | Minor              |
| New sprint               | Repository Minor   |
| Repository restructuring | Repository Major   |

---

# Git Commit Relationship

Versioning complements Git history but does not replace it.

Commit messages should describe individual changes, while version numbers represent meaningful milestones.

Example commit messages:

```text
docs: complete Docker networking documentation

docs: improve Linux troubleshooting guide

feat: add Kubernetes labs

refactor: reorganize governance documents
```

---

# Release Milestones

Suggested repository milestones:

| Version | Milestone                           |
| ------- | ----------------------------------- |
| 1.0.0   | Repository foundation complete      |
| 1.1.0   | Networking completed                |
| 1.2.0   | Git completed                       |
| 1.3.0   | Linux completed                     |
| 1.4.0   | Docker completed                    |
| 1.5.0   | Kubernetes completed                |
| 2.0.0   | Core DevOps learning path completed |

These milestones may evolve as the repository grows.

---

# Version History

Significant version changes should be recorded in a changelog or release notes.

Suggested information:

* Version
* Date
* Summary
* Major additions
* Major improvements
* Breaking structural changes (if any)

---

# Best Practices

* Increment versions only for meaningful changes.
* Keep version numbers consistent across documents.
* Record major milestones clearly.
* Prefer incremental improvements over large undocumented changes.
* Review versions during sprint completion.

---

# Expected Outcomes

Following this versioning policy provides:

* Clear project history
* Traceable documentation evolution
* Predictable repository growth
* Easier collaboration
* Better maintenance
* Professional engineering practices

---

# Related Documents

| Document                   | Purpose                                          |
| -------------------------- | ------------------------------------------------ |
| Repository Standards.md    | Repository-wide standards and conventions        |
| Documentation Standards.md | Documentation formatting and quality guidelines  |
| Engineering Charter.md     | Engineering philosophy and principles            |
| Session Workflow.md        | Standard workflow for learning sessions          |
| Repository Architecture.md | Repository structure and organization            |
| VERSION.md                 | Current repository version and milestone summary |
