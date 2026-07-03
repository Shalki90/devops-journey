# Session 13

## Topics

* Linux Package Management
* Software Packages
* Package Repositories
* Package Metadata
* Package Dependencies
* Shared Libraries
* APT
* `dpkg`
* `apt update`
* `apt search`
* `apt show`
* `apt install`
* `apt remove`
* `apt autoremove`
* Repository Configuration
* Phase 03 Retrospective

---

## Hands-on Discussions

### Discussion 1 — Why Package Managers Exist

**Objective:**

Understand why Linux uses package managers instead of manual software installation.

**Discussion:**

* Software consists of more than executable files.
* Applications depend on libraries, configuration files, metadata, documentation, and installation scripts.
* Manual installation is error-prone and difficult to maintain.
* Package managers automate installation while maintaining system consistency.

**Key Insight:**

Package managers reduce human error by automating software installation and dependency management.

---

### Discussion 2 — Packages and Dependencies

**Objective:**

Understand what a Linux package contains.

**Discussion:**

A package contains:

* Application files
* Metadata
* Version information
* Dependency declarations
* Installation instructions

Dependencies are software components required for another application to function correctly.

Example:

```text
Docker

↓

Requires

↓

Library A

Library B

Library C
```

**Key Insight:**

Packages declare their dependencies rather than containing every required component.

---

### Discussion 3 — APT vs dpkg

**Objective:**

Understand the responsibilities of APT and dpkg.

**Discussion:**

APT:

* Reads repository metadata
* Resolves dependencies
* Downloads packages
* Invokes dpkg

dpkg:

* Installs local `.deb` packages
* Extracts files
* Registers installed software
* Does **not** resolve dependencies

Architecture:

```text
Repository

↓

APT

↓

dpkg

↓

Filesystem
```

**Key Insight:**

Linux separates dependency resolution from package installation.

---

### Discussion 4 — Package Repositories

**Objective:**

Understand where Linux obtains software.

**Discussion:**

Repositories are centralized servers that store:

* Packages
* Metadata
* Version information

Observed:

```text
archive.ubuntu.com

security.ubuntu.com
```

Ubuntu release:

```text
noble
```

Repository configuration:

```text
/etc/apt/sources.list.d/ubuntu.sources
```

**Key Insight:**

APT reads repository configuration rather than hardcoding software sources.

---

### Discussion 5 — Package Index

**Objective:**

Understand what `apt update` actually performs.

**Discussion:**

Command:

```bash
sudo apt update
```

Observed:

* Contacted configured repositories.
* Downloaded package metadata.
* Did **not** install or upgrade software.

Analogy:

Restaurant menu update.

**Key Insight:**

`apt update` synchronizes the local package index with repository metadata.

---

### Discussion 6 — Inspecting Packages

**Objective:**

Understand package metadata.

**Discussion:**

Commands:

```bash
apt search tree

apt show tree
```

Observed:

* Package version
* Dependencies
* Installed size
* Download size
* Maintainer
* Repository source

**Key Insight:**

Package metadata describes how software should be installed before installation begins.

---

### Discussion 7 — Installing and Removing Packages

**Objective:**

Observe the complete package lifecycle.

**Discussion:**

Commands:

```bash
sudo apt install tree

tree --version

which tree

sudo apt remove tree

sudo apt autoremove
```

Observed installation stages:

* Selecting package
* Preparing to unpack
* Unpacking
* Setting up
* Processing triggers

Executable location:

```text
/usr/bin/tree
```

Observed:

`autoremove` removed nothing because no orphaned dependencies existed.

**Key Insight:**

Package installation is a structured workflow rather than simple file copying.

---

### Discussion 8 — Shared Libraries

**Objective:**

Understand why Linux installs shared libraries only once.

**Discussion:**

Instead of duplicating identical libraries:

```text
Application A

↓

Shared Library

↑

Application B
```

Benefits:

* Easier maintenance
* Reduced disk usage
* Single security update
* Consistent behavior

**Key Insight:**

Linux centralizes reusable components to simplify maintenance and improve consistency.

---

### Discussion 9 — Phase 03 Retrospective

**Objective:**

Reflect on the learning outcomes from Linux Fundamentals.

**Discussion:**

Major concepts mastered:

* Linux architecture
* Boot process
* Processes
* Virtual memory
* Filesystem hierarchy
* Users and permissions
* systemd
* Logging
* SSH fundamentals
* Package management

Major engineering themes:

* Separation of Responsibilities
* Single Responsibility
* Dependency Management
* Least Privilege
* Observability
* Layered Architecture

**Key Insight:**

Linux is best understood as a layered engineering system rather than a collection of commands.

---

## Engineering Questions

* Why should package installation be automated?
* Why are dependency resolution and package installation separate responsibilities?
* Why are repositories configurable instead of hardcoded?
* Why does `apt update` download metadata instead of software?
* Why are shared libraries installed only once?
* Why does Linux keep package metadata separate from executable files?

---

## Engineering Insights

* Packages contain software plus metadata.
* Dependencies are declared rather than duplicated.
* APT orchestrates package management.
* dpkg performs package installation.
* Repository configuration is externalized.
* Shared libraries reduce redundancy and simplify maintenance.
* Package managers reinforce Linux's layered architecture.

---

## Engineering Principles Reinforced

* Single Responsibility
* Separation of Responsibilities
* Dependency Management
* Configuration over Hardcoding
* Single Source of Truth
* Don't Repeat Yourself (DRY)
* Layered Architecture
* Controlled Automation

---

## Repository Updates

Updated:

* session-notes/session-13.md
* docs/DICTIONARY.md
* docs/ANALOGIES.md
* docs/ENGINEERING_PRINCIPLES.md
* docs/AI_IN_PRACTICE.md
* docs/PARKING_LOT.md
* curriculum/phase-03-linux-fundamentals.md
* docs/PROJECT_CONTEXT.md
* docs/ROADMAP.md

---

## Phase Status

**Phase 03 — Linux Fundamentals**

Status:

```text
Completed
```

Completed Topics:

* Linux Architecture
* Linux Boot Process
* GNU
* Shell
* Bash
* Linux Distributions
* BIOS / UEFI
* GRUB
* initramfs
* Linux Kernel
* User Space vs Kernel Space
* System Calls
* Device Drivers
* Processes
* Process Lifecycle
* PID & PPID
* fork()
* exec()
* Process Scheduling
* Context Switching
* Virtual Memory
* Demand Paging
* Stack vs Heap
* Linux Filesystem Hierarchy
* Files
* Directories
* Inodes
* Hard Links
* Symbolic Links
* Users
* Groups
* Ownership
* Permissions
* systemd
* Services
* Logs
* SSH Fundamentals
* Package Management

Outstanding (Intentionally Deferred):

* SSH Hands-on Lab

---

## Next Session

**Phase 04 — Networking Fundamentals**

Planned agenda:

* DevOps / Cloud / AI Infrastructure News
* Networking Knowledge Assessment
* Repository Documentation Updates
* Begin Networking Fundamentals

---

Version: 1.0

Status: Complete