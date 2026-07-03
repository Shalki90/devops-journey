# Linux Interview

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document consolidates common Linux interview questions ranging from beginner to intermediate and practical system administration scenarios.

The objective is to understand Linux concepts deeply and explain them confidently with practical examples.

---

# Linux Fundamentals

| Question                                           | Answer                                                                                                                                             |
| -------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| What is Linux?                                     | Linux is an open-source Unix-like operating system kernel that, together with GNU utilities and other software, forms a complete operating system. |
| What is a Linux distribution?                      | A Linux distribution (distro) packages the Linux kernel with utilities, package managers, and applications (e.g., Ubuntu, Debian, Fedora, RHEL).   |
| What is the kernel?                                | The kernel is the core of the operating system responsible for managing CPU, memory, hardware devices, processes, and system calls.                |
| What is the shell?                                 | The shell is a command interpreter that allows users to interact with the operating system.                                                        |
| What is the difference between Terminal and Shell? | A terminal is the application/interface used to access a shell. The shell interprets and executes commands.                                        |

---

# Linux File System

| Question                                            | Answer                                                                                               |
| --------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| What is the root directory?                         | `/` is the top-level directory from which all other directories originate.                           |
| Difference between absolute and relative paths?     | Absolute paths begin from `/`; relative paths begin from the current working directory.              |
| What is an inode?                                   | An inode stores metadata about a file, excluding its filename and contents.                          |
| Difference between a hard link and a symbolic link? | A hard link points to the same inode as the original file. A symbolic link references the file path. |
| Why does Linux use a hierarchical filesystem?       | It provides a standardized, organized structure for storing system and user data.                    |

---

# Users & Permissions

| Question                                | Answer                                                                              |
| --------------------------------------- | ----------------------------------------------------------------------------------- |
| What are file permissions?              | Permissions determine who can read, write, or execute a file or directory.          |
| Explain `rwx`.                          | `r` = Read, `w` = Write, `x` = Execute.                                             |
| What is the root user?                  | The superuser with unrestricted access to the system.                               |
| Difference between `chmod` and `chown`? | `chmod` changes permissions; `chown` changes ownership.                             |
| What is `umask`?                        | It defines the default permissions assigned to newly created files and directories. |

---

# Process Management

| Question                                   | Answer                                                                            |
| ------------------------------------------ | --------------------------------------------------------------------------------- |
| What is a process?                         | A running instance of a program.                                                  |
| What is a PID?                             | A unique Process Identifier assigned by the kernel.                               |
| Difference between a process and a thread? | A process has its own memory space; threads share memory within the same process. |
| What is a daemon?                          | A background process that runs without direct user interaction.                   |
| What is a zombie process?                  | A terminated process whose exit status has not yet been collected by its parent.  |
| What is an orphan process?                 | A process whose parent has exited; it is adopted by the init/systemd process.     |

---

# Memory & Storage

| Question                                         | Answer                                                                                            |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------- |
| What is swap memory?                             | Disk space used as virtual memory when physical RAM is exhausted.                                 |
| Difference between RAM and Swap?                 | RAM is fast physical memory; swap is slower disk-based virtual memory.                            |
| What is mounting?                                | Making a filesystem accessible by attaching it to a directory in the filesystem hierarchy.        |
| Difference between a partition and a filesystem? | A partition is a logical section of a disk; a filesystem defines how data is organized within it. |

---

# Services & Boot Process

| Question                             | Answer                                                                      |
| ------------------------------------ | --------------------------------------------------------------------------- |
| What is systemd?                     | The default system and service manager for many modern Linux distributions. |
| What is a service?                   | A background process managed by the operating system.                       |
| How do you check a service status?   | `systemctl status <service>`                                                |
| How do you enable a service at boot? | `systemctl enable <service>`                                                |

---

# Networking

| Question                                | Answer                                                       |
| --------------------------------------- | ------------------------------------------------------------ |
| How do you check the system IP address? | `ip a`                                                       |
| How do you test connectivity?           | `ping`                                                       |
| How do you check open ports?            | `ss -tulnp`                                                  |
| What is SSH?                            | Secure Shell protocol for encrypted remote access.           |
| Difference between `scp` and `ssh`?     | `ssh` provides remote login; `scp` securely transfers files. |

---

# Shell Scripting

| Question                                | Answer                                                           |
| --------------------------------------- | ---------------------------------------------------------------- |
| What is a shell script?                 | A text file containing shell commands executed sequentially.     |
| What is a shebang?                      | The first line (`#!`) specifying the interpreter for the script. |
| How do you make a script executable?    | `chmod +x script.sh`                                             |
| Why automate tasks using shell scripts? | To reduce manual effort, improve consistency, and save time.     |

---

# Package Management

| Question                                    | Answer                                                           |
| ------------------------------------------- | ---------------------------------------------------------------- |
| What is a package manager?                  | A tool that installs, updates, and removes software packages.    |
| Difference between `apt`, `yum`, and `dnf`? | They are package managers used by different Linux distributions. |
| What is a repository?                       | A collection of software packages available for installation.    |
| What is a dependency?                       | A required package needed by another package.                    |

---

# Logs & Troubleshooting

| Question                                    | Answer                                                                  |
| ------------------------------------------- | ----------------------------------------------------------------------- |
| Where are Linux logs stored?                | Common locations include `/var/log` and the systemd journal.            |
| How do you view systemd logs?               | `journalctl`                                                            |
| How do you monitor a log file in real time? | `tail -f <logfile>`                                                     |
| Why are logs important?                     | They help diagnose failures, monitor system health, and audit activity. |

---

# Practical Scenarios

| Scenario                 | Expected Approach                                                                                            |
| ------------------------ | ------------------------------------------------------------------------------------------------------------ |
| Disk is full             | Use `df -h` and `du -sh` to identify large files/directories, then clean up or expand storage.               |
| High CPU usage           | Identify processes using `top` or `ps`, investigate the cause, and optimize or terminate if appropriate.     |
| High memory usage        | Check `free -h`, inspect processes with `top`, and determine whether swap is being heavily used.             |
| Service is not starting  | Check `systemctl status`, review logs using `journalctl`, verify configuration, and resolve reported errors. |
| Cannot SSH into a server | Verify network connectivity, SSH service status, firewall rules, and authentication credentials.             |

---

# Frequently Asked DevOps Questions

| Question                                       | What the Interviewer Wants to Assess                             |
| ---------------------------------------------- | ---------------------------------------------------------------- |
| Explain the Linux boot process.                | Understanding of system startup and service initialization.      |
| How does Linux manage permissions?             | Knowledge of security fundamentals.                              |
| How do you troubleshoot a server that is slow? | Structured troubleshooting methodology.                          |
| Which Linux commands do you use daily?         | Practical Linux administration experience.                       |
| Why is Linux preferred in cloud environments?  | Understanding of stability, security, automation, and ecosystem. |

---

# Common Mistakes

| Mistake                                             | Better Practice                                                                       |
| --------------------------------------------------- | ------------------------------------------------------------------------------------- |
| Using `chmod 777` indiscriminately                  | Apply the principle of least privilege.                                               |
| Running everything as `root`                        | Use `sudo` only when required.                                                        |
| Ignoring system logs                                | Always inspect logs before making changes.                                            |
| Killing processes without investigation             | Identify the root cause before terminating processes.                                 |
| Executing destructive commands without verification | Review commands carefully, especially those involving `rm`, `dd`, or disk operations. |

---

# Interview Tips

| Recommendation                                   | Benefit                                              |
| ------------------------------------------------ | ---------------------------------------------------- |
| Explain concepts before commands                 | Demonstrates understanding rather than memorization. |
| Use Linux terminology correctly                  | Shows confidence and accuracy.                       |
| Relate answers to practical administration tasks | Highlights real-world experience.                    |
| Follow a structured troubleshooting approach     | Demonstrates problem-solving ability.                |
| Mention security and automation where relevant   | Aligns with DevOps best practices.                   |

---

# Related Documents

| Document           | Purpose                 |
| ------------------ | ----------------------- |
| README.md          | Sprint overview         |
| Dictionary.md      | Linux terminology       |
| Analogies.md       | Mental models           |
| Cheatsheet.md      | Command reference       |
| Troubleshooting.md | Linux debugging guide   |
| `concepts/`        | Detailed Linux concepts |
