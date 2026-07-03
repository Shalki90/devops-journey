# Linux Dictionary

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document provides a structured dictionary of core Linux terminology.

It serves as a quick-reference guide for Linux concepts. Detailed explanations, examples, and practical usage are documented in their respective concept files.

---

# Linux Fundamentals

| Term                         | Definition                                                                                             |
| ---------------------------- | ------------------------------------------------------------------------------------------------------ |
| Linux                        | An open-source Unix-like operating system kernel.                                                      |
| GNU                          | A collection of free software that, together with the Linux kernel, forms a complete operating system. |
| Kernel                       | The core component of the operating system that manages hardware and system resources.                 |
| Distribution (Distro)        | A complete operating system built around the Linux kernel (e.g., Ubuntu, Debian, Fedora).              |
| Shell                        | A command-line interface that allows users to interact with the operating system.                      |
| Terminal                     | An application used to access the shell.                                                               |
| Command Line Interface (CLI) | A text-based interface used to execute commands.                                                       |

---

# File System

| Term                            | Definition                                                      |
| ------------------------------- | --------------------------------------------------------------- |
| Root Directory (`/`)            | The top-level directory of the Linux filesystem hierarchy.      |
| Home Directory                  | Default directory assigned to a user.                           |
| Current Working Directory (PWD) | The directory in which the shell is currently operating.        |
| Absolute Path                   | A path beginning from the root directory (`/`).                 |
| Relative Path                   | A path relative to the current working directory.               |
| File System                     | The method used to organize and store files on storage devices. |
| Mount Point                     | A directory where another filesystem is attached.               |

---

# Files & Directories

| Term                      | Definition                                                               |
| ------------------------- | ------------------------------------------------------------------------ |
| File                      | A unit used to store data.                                               |
| Directory                 | A container that organizes files and subdirectories.                     |
| Hidden File               | A file whose name begins with a dot (`.`).                               |
| Symbolic Link (Soft Link) | A reference that points to another file or directory.                    |
| Hard Link                 | Another directory entry pointing to the same inode as the original file. |
| Inode                     | A filesystem data structure that stores metadata about a file.           |

---

# Users & Permissions

| Term       | Definition                                                               |
| ---------- | ------------------------------------------------------------------------ |
| User       | An account used to access the operating system.                          |
| Group      | A collection of users with shared permissions.                           |
| Root User  | The administrative user with unrestricted system privileges.             |
| Ownership  | The association of a file with a user and group.                         |
| Permission | Rules that determine who can read, write, or execute a file.             |
| `rwx`      | Read, Write, and Execute permission model.                               |
| `chmod`    | Command used to modify file permissions.                                 |
| `chown`    | Command used to change file ownership.                                   |
| `umask`    | Default permission mask applied when creating new files and directories. |

---

# Processes

| Term               | Definition                                                         |
| ------------------ | ------------------------------------------------------------------ |
| Process            | A running instance of a program.                                   |
| PID                | Process Identifier assigned to every running process.              |
| PPID               | Parent Process Identifier.                                         |
| Foreground Process | A process running interactively in the current terminal.           |
| Background Process | A process running independently of the current terminal session.   |
| Daemon             | A background service that runs continuously.                       |
| Zombie Process     | A terminated process whose exit status has not yet been collected. |
| Orphan Process     | A process whose parent has terminated.                             |

---

# System Services

| Term    | Definition                                                          |
| ------- | ------------------------------------------------------------------- |
| Service | A background process managed by the operating system.               |
| Systemd | The default system and service manager on many Linux distributions. |
| Unit    | A configuration object managed by systemd.                          |
| Target  | A logical grouping of systemd units representing a system state.    |

---

# Memory & Storage

| Term           | Definition                                                           |
| -------------- | -------------------------------------------------------------------- |
| RAM            | Primary memory used by running programs.                             |
| Swap           | Disk space used as virtual memory when RAM is insufficient.          |
| Virtual Memory | Memory management technique combining RAM and swap.                  |
| Partition      | A logical division of a storage device.                              |
| Filesystem     | The format used to organize data on storage media (e.g., ext4, XFS). |

---

# Networking

| Term               | Definition                                                    |
| ------------------ | ------------------------------------------------------------- |
| Network Interface  | Hardware or virtual component used for network communication. |
| Hostname           | Human-readable name assigned to a Linux system.               |
| Loopback Interface | Virtual interface used for local communication (`127.0.0.1`). |
| SSH                | Secure Shell protocol for secure remote access.               |

---

# Shell & Scripting

| Term                 | Definition                                                                  |
| -------------------- | --------------------------------------------------------------------------- |
| Bash                 | The most widely used Linux shell.                                           |
| Environment Variable | A named value used by the shell and applications.                           |
| PATH                 | Environment variable that specifies where executable programs are searched. |
| Shell Script         | A file containing shell commands executed sequentially.                     |
| Shebang (`#!`)       | The first line of a script specifying the interpreter to execute it.        |

---

# Package Management

| Term            | Definition                                                  |
| --------------- | ----------------------------------------------------------- |
| Package         | A bundled software application ready for installation.      |
| Package Manager | Tool used to install, update, and remove software packages. |
| Repository      | A server or collection containing software packages.        |
| Dependency      | A software package required by another package.             |

---

# Logging & Scheduling

| Term     | Definition                                                     |
| -------- | -------------------------------------------------------------- |
| Log File | A file containing records of system or application events.     |
| Journal  | Systemd's centralized logging system.                          |
| Cron     | Linux scheduler used to execute recurring tasks automatically. |
| Crontab  | Configuration file defining scheduled cron jobs.               |

---

# Key Insight

| Principle                              | Explanation                                                              |
| -------------------------------------- | ------------------------------------------------------------------------ |
| Everything is a file                   | Linux exposes many system resources through the filesystem.              |
| Small tools working together           | Linux utilities are designed to perform one task well and be composable. |
| Permissions enforce security           | Access control is fundamental to Linux system administration.            |
| Automation is a first-class capability | Shell scripting and scheduling enable efficient system management.       |

---

# Related Documents

| Document              | Purpose                             |
| --------------------- | ----------------------------------- |
| Linux Overview.md     | Linux architecture and ecosystem    |
| File System.md        | Filesystem hierarchy and navigation |
| Permissions.md        | Users, groups, and permissions      |
| Processes.md          | Process management                  |
| Shell.md              | Shell fundamentals                  |
| Shell Scripting.md    | Bash scripting                      |
| Package Management.md | Software installation               |
| Systemd.md            | Services and boot management        |
