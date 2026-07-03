# Linux Overview

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document introduces Linux as an operating system, explains its architecture, major components, distributions, and why it has become the foundation of modern DevOps, Cloud Computing, Containers, and Platform Engineering.

---

# What is Linux?

Linux is an **open-source Unix-like operating system kernel** created by Linus Torvalds in 1991.

By itself, Linux refers only to the **kernel**. A complete Linux operating system combines the Linux kernel with GNU utilities, system libraries, package managers, desktop/server applications, and additional software provided by a Linux distribution.

---

# Linux Architecture

```
+--------------------------------------+
|            Applications              |
+--------------------------------------+
|              Shell (Bash)            |
+--------------------------------------+
|          System Libraries            |
+--------------------------------------+
|          Linux Kernel                |
+--------------------------------------+
|              Hardware                |
+--------------------------------------+
```

---

# Linux Components

| Component        | Responsibility                                                   |
| ---------------- | ---------------------------------------------------------------- |
| Hardware         | CPU, RAM, Storage, Network, and other physical devices.          |
| Kernel           | Manages hardware resources and provides system services.         |
| System Libraries | Allow applications to communicate with the kernel.               |
| Shell            | Accepts user commands and executes them.                         |
| Applications     | User programs such as editors, browsers, databases, and servers. |

---

# What is the Kernel?

The **kernel** is the core of the operating system.

It acts as an intermediary between hardware and software.

---

## Kernel Responsibilities

| Responsibility         | Description                                          |
| ---------------------- | ---------------------------------------------------- |
| Process Management     | Creates, schedules, and terminates processes.        |
| Memory Management      | Allocates and manages RAM and virtual memory.        |
| Device Management      | Communicates with hardware through device drivers.   |
| File System Management | Reads and writes data on storage devices.            |
| Networking             | Handles network communication.                       |
| Security               | Enforces permissions, authentication, and isolation. |

---

# User Space vs Kernel Space

| User Space                       | Kernel Space                     |
| -------------------------------- | -------------------------------- |
| Applications execute here.       | Kernel executes here.            |
| Limited privileges.              | Full hardware access.            |
| Cannot directly access hardware. | Controls hardware resources.     |
| Safer environment.               | Protected operating system core. |

---

# System Calls

Applications cannot directly access hardware.

Instead, they request services from the kernel using **system calls**.

```
Application
      │
System Call
      │
Linux Kernel
      │
Hardware
```

Examples include:

* Opening files
* Reading data
* Creating processes
* Allocating memory
* Network communication

---

# What is GNU?

GNU is a collection of open-source software tools that complement the Linux kernel.

Common GNU utilities include:

* `ls`
* `cp`
* `mv`
* `grep`
* `sed`
* `awk`
* `bash`

Without GNU tools, Linux would provide only the kernel and would not be a complete operating system for general use.

---

# Linux Distributions

A Linux distribution packages the Linux kernel with software, package managers, utilities, and configuration tools.

---

## Popular Distributions

| Distribution                    | Primary Use                         |
| ------------------------------- | ----------------------------------- |
| Ubuntu                          | General purpose, cloud, development |
| Debian                          | Stable servers                      |
| Red Hat Enterprise Linux (RHEL) | Enterprise environments             |
| Rocky Linux                     | Enterprise RHEL-compatible systems  |
| AlmaLinux                       | Enterprise RHEL-compatible systems  |
| Fedora                          | Latest technologies and development |
| Arch Linux                      | Advanced users and customization    |
| Alpine Linux                    | Lightweight containers              |

---

# Linux File Hierarchy

Everything begins at the **root directory (`/`)**.

Examples:

| Directory | Purpose                         |
| --------- | ------------------------------- |
| `/home`   | User home directories           |
| `/etc`    | Configuration files             |
| `/var`    | Variable data such as logs      |
| `/bin`    | Essential user commands         |
| `/usr`    | User applications and libraries |
| `/opt`    | Optional third-party software   |
| `/tmp`    | Temporary files                 |
| `/dev`    | Device files                    |
| `/proc`   | Process and kernel information  |
| `/boot`   | Bootloader and kernel files     |

---

# Why Linux Dominates DevOps

| Area        | Reason                                           |
| ----------- | ------------------------------------------------ |
| Cloud       | Most cloud servers run Linux.                    |
| Containers  | Docker containers use Linux kernel features.     |
| Kubernetes  | Kubernetes worker nodes predominantly run Linux. |
| Automation  | Shell scripting is native to Linux.              |
| Open Source | Large ecosystem and community support.           |
| Performance | Efficient resource utilization.                  |
| Stability   | Designed for long-running production systems.    |
| Security    | Strong permission model and regular updates.     |

---

# Advantages of Linux

| Advantage        | Explanation                                      |
| ---------------- | ------------------------------------------------ |
| Open Source      | Source code is publicly available.               |
| Stable           | Suitable for long-running production workloads.  |
| Secure           | Strong user, group, and permission model.        |
| Portable         | Runs on many hardware architectures.             |
| Scalable         | Suitable for embedded devices to supercomputers. |
| Scriptable       | Extensive automation capabilities.               |
| Community Driven | Continuous improvements from a global community. |

---

# Linux Philosophy

| Principle                | Meaning                                                                               |
| ------------------------ | ------------------------------------------------------------------------------------- |
| Everything is a file     | Devices, processes, and many system resources are represented through the filesystem. |
| Small tools, one job     | Utilities are designed to perform one task well.                                      |
| Compose tools            | Combine simple commands using pipes and redirection.                                  |
| Automate repetitive work | Prefer scripting over manual repetition.                                              |

---

# Linux in the DevOps Stack

```
Application
      │
Docker
      │
Kubernetes
      │
Linux
      │
Cloud Infrastructure
      │
Physical Hardware
```

Linux forms the foundation on which modern DevOps technologies operate.

---

# Key Takeaways

| Concept          | Summary                                                                            |
| ---------------- | ---------------------------------------------------------------------------------- |
| Linux            | An open-source Unix-like kernel.                                                   |
| GNU/Linux        | The complete operating system formed by combining the Linux kernel with GNU tools. |
| Kernel           | Manages hardware and system resources.                                             |
| Shell            | Interface between the user and the operating system.                               |
| Distribution     | A packaged Linux operating system with tools and software.                         |
| System Calls     | Mechanism through which applications interact with the kernel.                     |
| Linux Philosophy | Simplicity, modularity, automation, and composability.                             |

---

# Related Documents

| Document              | Purpose                                   |
| --------------------- | ----------------------------------------- |
| File System.md        | Linux filesystem hierarchy and navigation |
| Shell.md              | Shell architecture and command execution  |
| Processes.md          | Process lifecycle and management          |
| Memory Management.md  | Memory and virtual memory concepts        |
| Package Management.md | Installing and managing software          |
| Systemd.md            | Services and boot process                 |
| Dictionary.md         | Linux terminology                         |
| Analogies.md          | Linux mental models                       |
