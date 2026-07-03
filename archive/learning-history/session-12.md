# Session 12

## Topics

* Linux Users
* Linux Groups
* Ownership
* Linux Permissions
* Symbolic Permission Representation
* Octal Permissions
* `chmod`
* `chown`
* `chgrp`
* Linux Filesystem Hierarchy (Level 2)
* `/boot`
* `/opt`
* `/run`
* `/media`
* `/mnt`
* `/lib`
* `/lib64`
* `systemd`
* Linux Services
* `systemctl`
* Service States
* Service Dependencies
* `journald`
* `journalctl`
* Log Filtering
* SSH Fundamentals
* SSH Client vs SSH Server
* Local Shell vs Remote Shell

---

## Hands-on Discussions

### Discussion 1 — Users, Groups, Ownership and Permissions

Objective:

Understand how Linux separates identity, accountability, and access.

Discussion:

* Users represent individual identities.
* Groups represent users performing similar responsibilities.
* Ownership establishes accountability.
* Permissions determine access.
* Ownership and permissions are independent concepts.

Key Insight:

Ownership answers **"Who is responsible?"**

Permissions answer **"Who is allowed?"**

---

### Discussion 2 — Linux Permission Model

Objective:

Understand how Linux controls file access.

Discussion:

Linux stores permissions as:

```text
Owner

↓

Group

↓

Others
```

Each category receives:

* Read
* Write
* Execute

Example:

```text
rwxr--r--
```

Key Insight:

Permissions belong to the file itself and travel with the file.

---

### Discussion 3 — Symbolic and Octal Permissions

Objective:

Understand two methods of modifying permissions.

Discussion:

Symbolic:

```bash
chmod u+x file
chmod g+w file
chmod o-r file
```

Octal:

```text
rwx = 7
rw- = 6
r-x = 5
r-- = 4
```

Examples:

```text
700
750
640
```

Key Insight:

Octal permissions compress Linux permission bits into an easily readable numeric format.

---

### Discussion 4 — Users, Groups and Permission Management

Objective:

Understand why Linux groups exist.

Discussion:

Without groups:

* Every permission must be assigned individually.

With groups:

* Add users to the appropriate group.
* Permissions automatically apply.

Example:

Instead of assigning permissions individually to 50 developers:

```text
Developers Group

↓

Add User

↓

Permissions inherited
```

Key Insight:

Groups improve scalability, consistency and administration.

---

### Discussion 5 — Linux Filesystem Hierarchy (Level 2)

Objective:

Understand additional Linux directories and their responsibilities.

Discussion:

Covered:

* `/boot`
* `/opt`
* `/run`
* `/media`
* `/mnt`
* `/lib`
* `/lib64`

Observed:

```text
/lib

↓

Symbolic Link

↓

/usr/lib
```

```text
/lib64

↓

Symbolic Link

↓

/usr/lib64
```

Key Insight:

Modern Linux distributions consolidate many historical directories using symbolic links while maintaining backward compatibility.

---

### Discussion 6 — systemd

Objective:

Understand Linux service management.

Discussion:

* systemd is PID 1.
* It starts Linux services.
* It manages dependencies.
* It supervises services throughout system runtime.

Analogy:

Hotel Operations Manager.

Key Insight:

systemd coordinates services rather than performing the work itself.

---

### Discussion 7 — Linux Services

Objective:

Understand service lifecycle management.

Discussion:

Commands practiced:

```bash
systemctl status
systemctl start
systemctl stop
systemctl restart
systemctl reload
systemctl is-enabled
systemctl list-units
systemctl list-unit-files
```

Discussed:

* Enabled
* Disabled
* Running
* Stopped

Key Insight:

Enabled means **ready to start during boot**.

Running means **currently executing**.

These are different states.

---

### Discussion 8 — Linux Logging

Objective:

Understand how Linux records system events.

Discussion:

Commands:

```bash
journalctl
journalctl -n
journalctl -u
journalctl -b
```

Observed:

* chronological ordering
* timestamps
* service names
* process IDs
* log severity

Analogy:

Hotel incident register.

Key Insight:

Logs provide accountability, auditing and the starting point for troubleshooting.

---

### Discussion 9 — SSH Fundamentals

Objective:

Understand secure remote administration.

Discussion:

Covered:

* Why remote administration exists.
* Authentication.
* Encryption.
* Server identity verification.
* SSH Client.
* SSH Server (`sshd`).
* Local Shell.
* Remote Shell.

Analogy:

Secure hotel intercom.

Key Insight:

SSH securely extends your terminal to another machine while executing commands on the remote system.

---

## Engineering Questions

* Why are ownership and permissions separate concepts?
* Why does Linux manage permissions through groups?
* Why should users receive only the permissions they require?
* Why are services managed by systemd instead of independently?
* Why should services with dependencies start in order?
* Why is logging essential for troubleshooting?
* Why should only required services be exposed to the internet?
* Why does SSH require server identity verification?

---

## Engineering Insights

* Ownership establishes accountability.
* Permissions establish access.
* Groups provide scalable permission management.
* Linux follows the Principle of Least Privilege.
* Symbolic links preserve backward compatibility.
* systemd manages services through dependency-aware orchestration.
* Enabled and Running represent different service states.
* Logs enable auditing, observability and root-cause analysis.
* SSH securely extends a local terminal to a remote Linux shell.

---

## Engineering Principles Reinforced

* Separation of Responsibility
* Accountability vs Access
* Principle of Least Privilege
* Role-Based Access
* Controlled Interfaces
* Dependency Management
* Observability
* Principle of Least Exposure
* Graceful Change

---

## Repository Updates

Updated:

* session-notes/session-12.md
* docs/DICTIONARY.md
* docs/ANALOGIES.md
* docs/ENGINEERING_PRINCIPLES.md
* docs/AI_IN_PRACTICE.md
* docs/PARKING_LOT.md
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

Remaining Topics:

* SSH Lab
* Package Management

---

## Next Session

Planned Topics:

* DevOps / Cloud / AI Infrastructure News
* Knowledge Assessment
* Package Management
* Package Management Lab
* Phase 03 Retrospective
* Repository Cleanup
* Phase Completion

---

Version: 1.0

Status: Complete