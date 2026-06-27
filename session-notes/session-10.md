# Session 09

## Topics

* Program vs Process
* Process Lifecycle
* Process States (R, S, D, T, Z)
* Parent and Child Processes
* Process Tree
* PID and PPID
* systemd as PID 1
* Orphan Processes
* Zombie Processes
* Foreground Processes
* Background Processes
* Terminal Ownership
* jobs, fg and bg Commands
* Linux Signals
* SIGINT
* SIGTERM
* SIGKILL
* SIGSTOP
* SIGCONT
* Process Engineering Principles

---

## Hands-on Discussions

### Discussion 1 — Program vs Process

Objective:

Understand the difference between a program stored on disk and a running process.

Discussion:

* Applications stored on SSD are programs.
* Programs become processes only after execution begins.
* Kernel loads the executable into memory before execution starts.

Key Insight:

A program is passive storage.
A process is an executing instance managed by the kernel.

---

### Discussion 2 — Process Lifecycle

Objective:

Understand how a process is created.

Lifecycle:

```text
Executable (SSD)

↓

Loaded into RAM

↓

Kernel allocates resources

↓

CPU begins execution

↓

Running Process
```

Key Insight:

The kernel is responsible for converting a program into a running process.

---

### Discussion 3 — Process States

Objective:

Understand the major Linux process states.

Covered:

* Running (R)
* Sleeping (S)
* Uninterruptible Sleep (D)
* Stopped (T)
* Zombie (Z)

Key Insights:

* Running processes actively execute or wait for CPU scheduling.
* Sleeping processes wait for an event.
* D state waits for critical hardware I/O.
* Stopped processes are intentionally paused.
* Zombie processes have completed execution but await parent cleanup.

---

### Discussion 4 — Parent and Child Processes

Objective:

Understand Linux process hierarchy.

Hierarchy:

```text
systemd

↓

bash

↓

python

↓

flask
```

Covered:

* PID
* PPID
* Parent-child relationships
* Why Linux maintains a process tree

Key Insight:

Every process has a parent. This enables ownership, cleanup, monitoring and lifecycle management.

---

### Discussion 5 — Orphan Processes

Objective:

Understand orphan process adoption.

Scenario:

```text
bash exits

↓

python continues

↓

systemd adopts python
```

Key Insight:

Linux never allows a running process to exist without a parent.

---

### Discussion 6 — Zombie Processes

Objective:

Understand zombie processes.

Scenario:

```text
Child exits

↓

Parent has not collected exit status

↓

Zombie Process
```

Key Insight:

Zombie processes are already dead.
Only their process table entry remains until the parent performs cleanup.

---

### Discussion 7 — Foreground vs Background Processes

Objective:

Understand terminal ownership.

Covered:

* Foreground process owns terminal.
* Background process executes without owning the terminal.
* Bash regains terminal after background execution.

Commands Discussed:

```bash
jobs

fg

bg
```

Key Insight:

Only one foreground process can own the terminal at a time.

---

### Discussion 8 — Ctrl + Z

Objective:

Understand intentional process suspension.

Flow:

```text
Running Process

↓

Ctrl + Z

↓

SIGSTOP

↓

Stopped State (T)

↓

Bash regains terminal
```

Key Insight:

Ctrl + Z pauses execution.
It does not terminate the process.

---

### Discussion 9 — Linux Signals

Objective:

Understand operating system communication with processes.

Signals Covered:

* SIGINT
* SIGTERM
* SIGKILL
* SIGSTOP
* SIGCONT

Concepts:

* Interrupt
* Graceful shutdown
* Forced termination
* Pause execution
* Resume execution

Key Insight:

Signals provide a standardized mechanism for controlling processes.

---

## Engineering Questions

* Why does every Linux process require a parent?
* Why are orphan processes adopted instead of terminated?
* Why do zombie processes exist?
* Why can only one process own a terminal?
* Why is SIGTERM preferred over SIGKILL?
* Why does Linux separate graceful termination from forced termination?

---

## Engineering Insights

* A process is an executing instance of a program.
* The kernel owns the complete process lifecycle.
* Every process belongs to a hierarchical process tree.
* Orphan adoption prevents unmanaged processes.
* Zombie processes preserve exit status until parent acknowledgement.
* Terminal ownership enables predictable user interaction.
* Background execution improves multitasking.
* Signals standardize process communication.
* Graceful shutdown protects application consistency.
* Forced termination should be the last resort.

---

## Engineering Principles Reinforced

* Resource Management Belongs to the Kernel
* Every Running Process Requires Ownership
* Failure Should Be Isolated
* Graceful Shutdown Before Forced Shutdown
* Explicit Process Lifecycle Management
* Separation of Responsibility

---

## Repository Updates

Updated:

* session-notes/session-09.md
* docs/DICTIONARY.md
* docs/ANALOGIES.md
* docs/ENGINEERING_PRINCIPLES.md

---

## Phase Status

Phase 03 — Linux Fundamentals

Status:

```text
In Progress
```

Completed Topics:

* Linux Architecture
* Linux Boot Process
* GNU
* Shell
* Kernel
* Programs vs Processes
* Process Lifecycle
* Process States
* Parent-Child Relationships
* Process Tree
* Orphan Processes
* Zombie Processes
* Foreground and Background Processes
* Linux Signals

Remaining Topics:

* Linux Filesystem
* File Navigation
* File Manipulation
* Permissions
* Users and Groups
* Package Management
* Networking Basics

---

## Next Session

Planned Topics:

* Linux Filesystem Hierarchy
* Absolute vs Relative Paths
* Navigation Commands
* File Types
* Inodes
* File Manipulation Commands

---

Version: 1.0

Status: Complete