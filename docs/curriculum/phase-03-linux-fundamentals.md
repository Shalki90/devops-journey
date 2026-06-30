# Phase 03 — Linux Fundamentals

## Objective

Understand how Linux operates internally, how it manages hardware, processes, memory, filesystems, users, services, logging, and secure remote administration, and why Linux became the foundation of modern servers, cloud platforms, containers, and Kubernetes.

The goal is to understand Linux as an operating system rather than memorize shell commands.

---

## Learning Outcomes

By the end of this phase, I should be able to:

* Explain Linux architecture.
* Explain why Linux dominates modern infrastructure.
* Describe the complete Linux boot process.
* Explain the responsibilities of BIOS/UEFI, GRUB, initramfs, Kernel, and systemd.
* Explain the relationship between GNU, Shell, Bash, and the Kernel.
* Describe how applications interact with the kernel using system calls.
* Explain the purpose of device drivers.
* Explain processes and the Linux process lifecycle.
* Describe fork() and exec().
* Explain process scheduling.
* Explain virtual memory.
* Differentiate between stack and heap memory.
* Explain the Linux filesystem hierarchy.
* Explain inodes.
* Differentiate between hard links and symbolic links.
* Explain Linux permissions.
* Explain ownership.
* Describe Linux users and groups.
* Explain systemd and Linux services.
* Explain Linux logging using journald and journalctl.
* Explain the fundamentals of SSH and secure remote administration.
* Inspect running processes.
* Inspect memory usage.
* Troubleshoot common Linux issues using built-in tools.

---

## Topics

| Status | Topic                              |
| ------ | ---------------------------------- |
| ✅      | Linux Overview                     |
| ✅      | Why Linux Dominates Infrastructure |
| ✅      | GNU                                |
| ✅      | Shell                              |
| ✅      | Bash                               |
| ✅      | Linux Distributions                |
| ✅      | Ubuntu                             |
| ✅      | Rocky Linux                        |
| ✅      | BIOS / UEFI                        |
| ✅      | GRUB                               |
| ✅      | initramfs                          |
| ✅      | Linux Kernel                       |
| ✅      | User Space vs Kernel Space         |
| ✅      | System Calls                       |
| ✅      | Device Drivers                     |
| ✅      | Processes                          |
| ✅      | Process Lifecycle                  |
| ✅      | PID                                |
| ✅      | PPID                               |
| ✅      | fork()                             |
| ✅      | exec()                             |
| ✅      | Process Scheduling                 |
| ✅      | Context Switching                  |
| ✅      | Virtual Memory                     |
| ✅      | Stack vs Heap                      |
| ✅      | Linux Filesystem Hierarchy         |
| ✅      | Files                              |
| ✅      | Directories                        |
| ✅      | Inodes                             |
| ✅      | Hard Links                         |
| ✅      | Symbolic Links                     |
| ✅      | Users                              |
| ✅      | Groups                             |
| ✅      | Ownership                          |
| ✅      | Permissions                        |
| ✅      | systemd                            |
| ✅      | Services                           |
| ✅      | Logs                               |
| ✅      | SSH Fundamentals                   |
| ⬜      | SSH Hands-on                       |
| ✅      | Package Management                 |

---

## Hands-on Labs

| Status | Lab                          | Objective                                                                         |
| ------ | ---------------------------- | --------------------------------------------------------------------------------- |
| ✅      | Linux Filesystem Exploration | Navigate and understand the Linux filesystem hierarchy.                           |
| ✅      | Process Inspection           | Inspect running processes using `ps`, `top`, and `htop`.                          |
| ✅      | Process Management           | Manage processes using `kill`, `pkill`, and signals.                              |
| ✅      | Memory Inspection            | Observe memory utilization and process memory usage.                              |
| ✅      | Files & Directories          | Create, copy, move, and remove files and directories.                             |
| ✅      | Permissions Lab              | Modify permissions using `chmod`.                                                 |
| ✅      | Ownership Lab                | Manage ownership using `chown` and `chgrp`.                                       |
| ✅      | Users & Groups Lab           | Create and manage Linux users and groups.                                         |
| ⬜      | SSH Lab                      | Connect securely to Linux systems using SSH.                                      |
| ✅      | systemd Services             | Inspect, manage, enable, disable, restart, and reload services using `systemctl`. |
| ✅      | Journal Logs                 | Analyze and filter logs using `journalctl`.                                       |
| ✅      | Package Management           | Install, update, and remove packages using APT.                                   |

---

## Architecture Diagrams Built

Throughout this phase, the following conceptual diagrams will be developed.

* Linux Layered Architecture
* Linux Boot Process
* Application → System Call → Kernel → Driver → Hardware
* Linux Process Creation Flow
* Linux Filesystem Hierarchy
* Linux Permission Model (Owner → Group → Others)
* systemd Service Dependency Flow
* SSH Client → Encrypted Connection → SSH Server
* Linux Logging Flow (Service → journald → journalctl)

---

## Engineering Principles Reinforced

During this phase, the following engineering principles were reinforced:

* Single Responsibility
* Separation of Responsibilities
* Layered Problem Solving
* Stable Interfaces
* Abstraction
* Reduce Cognitive Load
* Principle of Least Privilege
* Principle of Least Exposure
* Observability
* Controlled Interfaces
* Dependency Management
* Parallelization of Independent Tasks

---

## Advanced Topics Deferred

The following topics were intentionally deferred because they are not required for the current roadmap stage:

* Linux Kernel Compilation
* Kernel Modules
* Namespaces
* cgroups
* SELinux
* AppArmor
* Advanced Scheduling Algorithms
* Filesystem Driver Development
* Bootloader Customization
* SSH Key-based Authentication
* SSH Agent Forwarding
* SSH Tunneling and Port Forwarding
* Advanced journald Filtering
* Custom Linux Kernels

---

Version: 0.3

Status: ✅ Completed