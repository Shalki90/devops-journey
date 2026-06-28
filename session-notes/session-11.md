# Session 11

## Topics

* `fork()`
* `exec()`
* Process Scheduling
* Runnable vs Sleeping Processes
* CPU Time Slice (Time Quantum)
* Preemptive Scheduling
* Context Switching
* Process Context
* Virtual Memory
* Process Isolation
* Demand Paging
* Stack vs Heap
* Memory Organization inside a Process
* Process Engineering Principles

---

## Hands-on Discussions

### Discussion 1 — `fork()`

Objective:

Understand how Linux creates a new process.

Discussion:

* Bash receives the user command.
* Bash does **not** become the requested program.
* Bash calls `fork()`.
* `fork()` creates a child process that is initially an almost identical copy of the parent.
* Parent and child receive different PIDs.

Flow:

```text
Bash

↓

fork()

↓

Parent Bash        Child Bash
```

Key Insight:

`fork()` creates a new process. It does not load a new program.

---

### Discussion 2 — `exec()`

Objective:

Understand how Linux starts a new program.

Discussion:

* After `fork()`, the child is still Bash.
* The child executes `exec()`.
* `exec()` replaces the child Bash with Python.
* The PID remains unchanged because the process itself is reused.

Flow:

```text
Child Bash

↓

exec()

↓

Python
```

Key Insight:

`exec()` replaces the program running inside an existing process while preserving its PID.

---

### Discussion 3 — Process Scheduling

Objective:

Understand how Linux shares one CPU among many processes.

Discussion:

* Multiple processes may request CPU time simultaneously.
* Only runnable processes participate in scheduling.
* Sleeping processes are ignored until they wake.
* The scheduler decides which runnable process executes next.

Key Insight:

The scheduler manages CPU fairness by selecting only runnable processes.

---

### Discussion 4 — Time Slice and Preemptive Scheduling

Objective:

Understand why Linux interrupts running processes.

Discussion:

* Linux cannot predict how long a process will execute.
* Allowing one process to run until completion would make the system unresponsive.
* Linux assigns a short CPU time slice.
* After the time slice expires, another runnable process receives CPU time.

Flow:

```text
Python

↓

5 ms

↓

Spotify

↓

5 ms

↓

Chrome

↓

5 ms
```

Key Insight:

Preemptive scheduling keeps the operating system responsive while remaining fair to all runnable processes.

---

### Discussion 5 — Context Switching

Objective:

Understand how interrupted processes resume execution.

Discussion:

* Before switching processes, Linux saves the current execution state.
* This saved execution state is called the **Process Context**.
* When scheduled again, Linux restores the context and continues execution exactly where it stopped.

Analogy:

A bookmark placed inside a book before reading another book.

Key Insight:

Context Switching creates the illusion that every process executes continuously.

---

### Discussion 6 — Virtual Memory

Objective:

Understand why applications never directly access physical RAM.

Discussion:

* Every process receives its own virtual address space.
* Linux hides physical memory from applications.
* The kernel translates virtual addresses into physical memory locations.
* Processes remain isolated from each other.

Key Insight:

Virtual Memory provides isolation, protection and flexibility while allowing every process to believe it owns its own memory.

---

### Discussion 7 — Demand Paging

Objective:

Understand how Linux allocates memory efficiently.

Discussion:

* A process may request large amounts of memory.
* Linux does not immediately allocate all requested physical RAM.
* Physical memory is allocated only when pages are actually accessed.

Example:

```text
Requested:

2 GB

Actually Used:

50 MB

Allocated:

≈50 MB
```

Key Insight:

Demand Paging prevents unnecessary RAM consumption by allocating memory only when required.

---

### Discussion 8 — Stack vs Heap

Objective:

Understand how a process organizes its memory.

Discussion:

Stack:

* Function calls
* Local variables
* Parameters
* Return addresses
* Automatically managed
* Temporary lifetime

Heap:

* Dynamically allocated objects
* Long-lived program data
* Lifetime controlled by the application

Memory Layout:

```text
Program Code

↓

Global Variables

↓

Heap

↑

Free Space

↓

Stack
```

Key Insight:

Linux separates temporary execution data from long-lived program data to optimize performance and memory management.

---

## Engineering Questions

* Why are `fork()` and `exec()` separate system calls?
* Why does Linux create a child process instead of replacing Bash?
* Why should one process never monopolize the CPU?
* Why must Linux save process context during scheduling?
* Why does Linux hide physical memory from applications?
* Why does Demand Paging improve memory utilization?
* Why are Stack and Heap separated instead of sharing one memory region?

---

## Engineering Insights

* Process creation and program execution are independent operations.
* Every command executed from Bash follows the `fork()` → `exec()` model.
* CPU scheduling considers only runnable processes.
* Fair scheduling improves overall system responsiveness.
* Context Switching enables multitasking by preserving execution state.
* Virtual Memory isolates applications and abstracts physical RAM.
* Demand Paging allocates physical memory only when actually needed.
* Stack automatically manages temporary execution data.
* Heap stores dynamically allocated objects whose lifetime is controlled by the program.

---

## Engineering Principles Reinforced

* Separation of Responsibility
* Fair Resource Scheduling
* Execution State Preservation
* Resource Virtualization
* Lazy Resource Allocation
* Lifetime-Based Memory Organization

---

## Repository Updates

Updated:

* session-notes/session-11.md
* docs/DICTIONARY.md
* docs/ANALOGIES.md
* docs/ENGINEERING_PRINCIPLES.md
* docs/PROJECT_CONTEXT.md
* curriculum/phase-03-linux-fundamentals.md

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
* `fork()`
* `exec()`
* Process Scheduling
* Context Switching
* Virtual Memory
* Demand Paging
* Stack vs Heap

Remaining Topics:

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
* SSH
* Package Management

---

## Next Session

Planned Topics:

* Linux Filesystem Hierarchy
* Files and Directories
* Absolute vs Relative Paths
* Device Files
* Inodes
* Hard Links
* Symbolic Links

---

Version: 1.0

Status: Complete