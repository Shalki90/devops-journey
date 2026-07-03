# Content Ownership Matrix

**Document Version:** 1.0

---

# Purpose

This document defines the **canonical location** (Single Source of Truth) for every type of information within the **DevOps Engineering Journey** repository.

Its primary objective is to eliminate duplication, improve maintainability, and ensure that every piece of knowledge has one clearly defined owner.

Whenever information needs to appear in multiple locations, the repository should use **cross-references instead of duplication**.

---

# Repository Principles

The repository follows these ownership principles:

* Every piece of information has one owner.
* Every document has one primary responsibility.
* Every concept has one canonical location.
* Cross-reference instead of copy.
* Documentation is an engineering artifact.
* Session notes are temporary.
* Permanent knowledge belongs in permanent documentation.

---

# Single Source of Truth

Every category of knowledge should have exactly one canonical location.

Other documents should reference that location instead of duplicating content.

---

# Content Ownership Matrix

| Information Type        | Canonical Location          | Referenced From                      |
| ----------------------- | --------------------------- | ------------------------------------ |
| Technology Overview     | README.md                   | Sprint documentation                 |
| Definitions             | Dictionary.md               | Concepts, Interview Notes            |
| Analogies               | Analogies.md                | README, Concepts                     |
| Core Concepts           | Concepts.md                 | README                               |
| Commands                | Cheatsheet.md               | Labs, Troubleshooting                |
| Hands-on Exercises      | labs/                       | README                               |
| Troubleshooting         | Troubleshooting.md          | Labs                                 |
| Best Practices          | Best Practices.md           | Concepts                             |
| Common Mistakes         | Common Mistakes.md          | Labs, Interview Notes                |
| Interview Questions     | Interview Notes.md          | Concepts                             |
| AI Use Cases            | AI in Practice.md           | Concepts                             |
| References              | Resources.md                | README                               |
| Architecture Diagrams   | Architecture.md             | README                               |
| Engineering Principles  | Engineering Principles.md   | Concepts                             |
| Workflow                | Workflow.md                 | README                               |
| Projects                | projects/                   | Portfolio                            |
| Sprint Curriculum       | Curriculum.md               | README                               |
| Session Learning        | Session Notes               | Permanent documentation after review |
| Repository Rules        | Governance                  | Entire repository                    |
| Repository Architecture | docs/architecture/          | Governance                           |
| Repository Decisions    | Repository Migration Log.md | Governance                           |

---

# Information Flow

Knowledge should progress through the repository in a structured manner.

```text
Learning Session

↓

Session Notes

↓

Review

↓

Categorize

↓

Permanent Documentation

↓

Cross-Reference

↓

Long-Term Knowledge Base
```

Session Notes are temporary.

Permanent documentation becomes the official reference.

---

# Ownership Rules

## Definitions

Definitions belong only in:

```text
Dictionary.md
```

Other documents should briefly reference the definition rather than recreate it.

---

## Commands

Commands belong in:

```text
Cheatsheet.md
```

Concept documents should explain commands but avoid maintaining long command reference lists.

---

## Analogies

Analogies belong only in:

```text
Analogies.md
```

Concept documents may reference the analogy without duplicating it.

---

## Troubleshooting

Errors, root causes, and resolutions belong in:

```text
Troubleshooting.md
```

Labs should describe only issues specific to that exercise.

---

## Interview Preparation

Interview-focused material belongs in:

```text
Interview Notes.md
```

Technical documents should remain educational rather than interview-oriented.

---

## AI Examples

AI-assisted workflows belong in:

```text
AI in Practice.md
```

Concept documents should not become collections of AI prompts.

---

## Resources

External links belong in:

```text
Resources.md
```

Avoid scattering URLs throughout multiple documents.

---

# Session Notes Policy

Session Notes serve as a temporary workspace.

They may contain:

* Raw observations
* Questions
* Mistakes
* Discoveries
* Commands
* Personal learning reflections

Before a sprint is completed, valuable knowledge should be migrated into its permanent document.

---

# Permanent Knowledge

Permanent knowledge includes:

* Concepts
* Definitions
* Engineering principles
* Best practices
* Troubleshooting guides
* Commands
* Architecture
* Projects
* Resources

These documents form the long-term engineering knowledge base.

---

# Duplication Policy

Avoid copying information between documents.

Instead:

* Link to the canonical document.
* Reference related topics.
* Summarize only when necessary.
* Expand only when new context is required.

This keeps documentation consistent and easier to maintain.

---

# Cross-Reference Strategy

Every major document should include a **Related Documents** section.

Cross-references should:

* Connect related concepts.
* Encourage exploration.
* Prevent duplicated explanations.
* Improve repository navigation.

---

# Content Lifecycle

Every piece of information follows the same lifecycle.

```text
Learn

↓

Document

↓

Review

↓

Assign Owner

↓

Publish

↓

Cross-Reference

↓

Maintain
```

Ownership is assigned only after the information has been reviewed and placed in its permanent location.

---

# Responsibilities

| Content               | Responsible Document     |
| --------------------- | ------------------------ |
| Repository Governance | Governance documents     |
| Repository Structure  | Architecture documents   |
| Technical Knowledge   | Sprint documentation     |
| Hands-on Practice     | Labs                     |
| Engineering Projects  | Projects                 |
| Automation            | Scripts                  |
| Learning History      | Session Notes            |
| Repository Evolution  | Repository Migration Log |

---

# Expected Outcomes

Following this ownership model ensures:

* One source of truth for every topic.
* Minimal duplication.
* Easier maintenance.
* Better navigation.
* Consistent documentation.
* Scalable repository growth.
* Professional engineering documentation.

---

# Related Documents

| Document                      | Purpose                                     |
| ----------------------------- | ------------------------------------------- |
| Documentation Standards.md    | Defines documentation quality and structure |
| Repository Standards.md       | Repository-wide standards                   |
| Repository Architecture.md    | Repository organization                     |
| Documentation Architecture.md | Documentation organization and lifecycle    |
| Repository Migration Log.md   | Records repository evolution                |
| Engineering Charter.md        | Defines repository engineering philosophy   |
