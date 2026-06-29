# Dictionary

## Purpose

This document serves as a quick reference for engineering terminology encountered throughout the learning journey.

The objective is to understand concepts rather than memorize definitions. Entries should remain concise and be updated only after the concept has been discussed.

---

| Term | Definition | Domain |
|------|------------|--------|
| Engineering Mindset | Solving problems by understanding why a solution exists before learning how to use it. | Engineering |
| Single Responsibility | The principle that each component should solve one well-defined problem. | Engineering |
| Standardization | Agreeing on common rules so independently built systems can work together. | Engineering |
| Distributed System | A system where multiple independent components work together to achieve a common goal. | Engineering |
| Idempotent | An operation that produces the same final state no matter how many times it is executed with the same input. | Engineering |
| Network | A collection of connected devices that can communicate with one another. | Networking |
| Internet | A global network connecting millions of smaller networks. | Networking |
| IP Address | A unique numeric address used to identify a device on a network. | Networking |
| DNS (Domain Name System) | Converts human-friendly domain names into IP addresses. | Networking |
| Router | A networking device that forwards data towards its destination. | Networking |
| Routing | The process of determining the path data takes across networks. | Networking |
| Packet | A small unit of data transmitted over a network. | Networking |
| Client | A system that requests a service. | Networking |
| Server | A system that provides a service. | Networking |
| Protocol | An agreed set of rules that enables systems to communicate. | Networking |
| HTTP | A protocol used for communication between clients and web servers. | Networking |
| HTTPS | A secure version of HTTP that encrypts communication during transmission. | Networking |
| Encryption | The process of converting readable information into unreadable data. | Networking |
| Plaintext | Readable data before encryption. | Networking |
| Ciphertext | Encrypted data that cannot be understood without the correct key. | Networking |
| Public Key | A publicly shared key used to encrypt information. | Networking |
| Private Key | A secret key used to decrypt information encrypted with its matching public key. | Networking |
| Port | A logical endpoint that directs network traffic to a specific application. | Networking |
| Well-known Ports | Reserved ports (0–1023) commonly assigned to standard Internet services. | Networking |
| Version Control | A system that tracks changes to files over time and preserves their history. | Git |
| Git | A distributed version control system that tracks changes and manages code history. | Git |
| Repository | A storage location containing files and their complete change history. | Git |
| Working Directory | The current files and folders being actively edited on the local machine. | Git |
| Staging Area | A preparation area where selected changes are gathered before creating a commit. | Git |
| Local Repository | The local database that stores commits and project history on a machine. | Git |
| Remote Repository | A repository hosted elsewhere, typically used for collaboration and backup. | Git |
| Commit | A saved snapshot of tracked changes at a specific point in time. | Git |
| Commit Hash | A unique identifier assigned to a commit. | Git |
| Branch | An independent line of development that allows work to be performed safely without affecting other branches. | Git |
| Main Branch | The primary branch that represents the accepted project history. | Git |
| HEAD | A pointer indicating the currently checked-out commit or branch. | Git |
| Merge | The process of combining changes from one branch into another. | Git |
| Fast-Forward Merge | A merge where Git simply moves a branch pointer forward because no divergent history exists. | Git |
| Merge Commit | A commit created to combine two independent histories into one. | Git |
| Merge Conflict | A situation where Git cannot automatically determine how competing changes should be combined. | Git |
| Remote Tracking Branch | A local reference that represents the current known state of a branch on a remote repository. | Git |
| origin | The default name Git uses to refer to a remote repository. | Git |
| origin/main | The local reference representing the last known state of the remote main branch. | Git |
| git add | A command that moves changes from the Working Directory to the Staging Area. | Git |
| git commit | A command that moves staged changes into the Local Repository as a new commit. | Git |
| git push | A command that publishes local commits to a remote repository. | Git |
| git fetch | A command that updates knowledge of the remote repository without changing local branches. | Git |
| git pull | A command that fetches remote changes and integrates them into the current local branch. | Git |
| git restore | A command used to discard changes from the Working Directory. | Git |
| git restore --staged | A command used to remove changes from the Staging Area while keeping them in the Working Directory. | Git |
| Tracking Branch | A local branch configured to follow a corresponding branch on a remote repository. | Git |
| Pull Request (PR)      | A request to merge changes from one branch into another after review and validation.| Git    |
| Code Review  | The process of examining proposed changes before they are merged into a shared branch.       | Git    |
| Collaboration Workflow | A structured process that allows multiple developers to work safely on the same repository.  | Git    |
| Conflict Resolution    | The process of manually deciding how competing changes should be combined when Git cannot determine the correct outcome automatically. | Git    |
| git revert   | A command that creates a new commit which reverses the changes introduced by an earlier commit.     | Git    |
| git reset| A command that moves branch history backward, allowing commits to be removed or rewritten before sharing.| Git    |
| git stash| A command that temporarily stores unfinished work so another task can be performed without creating a commit.     | Git    |
| Stash    | A temporary storage area used to save unfinished changes outside the current Working Directory.     | Git    |
| Shared History| Commit history that has already been published and may be used by other collaborators.       | Git    |
| Private History| Commit history that exists only locally and can be safely rewritten if necessary.  | Git    |
| Diverged Branches      | Branches that contain different commits and therefore require a true merge rather than a fast-forward update.     | Git    |
| GitHub   | A cloud-hosted platform used for storing, collaborating on, and managing Git repositories.   | Git    |
| Repository History     | The complete record of commits, branches, merges, and changes within a repository. | Git    |
| Operating System (OS)   | System software that manages hardware resources and provides common services for applications.     | Linux  |
| Linux     | An operating system built around the Linux kernel, commonly combined with GNU utilities to form a complete operating system.   | Linux  |
| Kernel    | The core component of an operating system that manages hardware resources and provides services to applications through system calls.| Linux  |
| GNU       | A collection of user-space tools and utilities that make a Linux system usable by providing commands, libraries, and standard programs.      | Linux  |
| Shell     | A command interpreter that allows users to interact with the operating system.       | Linux  |
| Bash (Bourne Again Shell)      | A widely used implementation of the Unix shell that interprets user commands and executes programs.       | Linux  |
| Linux Distribution      | A packaged operating system combining the Linux kernel, GNU utilities, package manager, and additional software into a complete system.      | Linux  |
| Ubuntu    | A Debian-based Linux distribution focused on ease of use and broad community support.| Linux  |
| Rocky Linux   | A community-supported enterprise Linux distribution designed for long-term stability and compatibility with Red Hat Enterprise Linux (RHEL). | Linux  |
| BIOS (Basic Input/Output System)   | Firmware that initializes hardware during startup and locates a bootable device.     | Linux  |
| UEFI (Unified Extensible Firmware Interface) | Modern firmware that replaces BIOS and provides a standardized interface between hardware and the operating system during boot.| Linux  |
| Bootloader| Software responsible for locating and loading the operating system kernel into memory during system startup.  | Linux  |
| GRUB (GRand Unified Bootloader)| A widely used Linux bootloader that loads the selected Linux kernel and initramfs into memory before transferring control.     | Linux  |
| initramfs (Initial RAM Filesystem) | A temporary root filesystem loaded into RAM that prepares the system so the Linux kernel can access the real root filesystem.  | Linux  |
| User Space| The area where applications and user programs execute with limited privileges, requiring system calls to access hardware.      | Linux  |
| Kernel Space  | The protected memory region where the operating system kernel executes with full access to hardware and system resources.      | Linux  |
| System Call   | A controlled interface that allows applications in user space to request services from the Linux kernel.  | Linux  |
| Device Driver | A software component that enables the kernel to communicate with a specific hardware device through a standardized interface.  | Linux  |
| Process     | A running instance of a program managed by the Linux kernel.       | Linux  |
| Program     | A passive executable file stored on disk that becomes a process when executed.| Linux  |
| Process Lifecycle| The sequence through which a program is loaded into memory, executed, managed, and terminated by the kernel. | Linux  |
| PID (Process ID)| A unique numerical identifier assigned to every running process.   | Linux  |
| PPID (Parent Process ID)  | The Process ID of the process that created another process.| Linux  |
| Process Tree| A hierarchical structure showing parent-child relationships between processes.| Linux  |
| Process State   | The current execution status of a process (Running, Sleeping, Stopped, Zombie, etc.).   | Linux  |
| Running (R) | A process currently executing or waiting to be scheduled on the CPU.      | Linux  |
| Sleeping (S)| A process waiting for an event before continuing execution.| Linux  |
| Uninterruptible Sleep (D) | A process waiting for critical hardware or I/O operations that cannot safely be interrupted.   | Linux  |
| Stopped (T) | A process intentionally paused, usually by a signal such as SIGSTOP or Ctrl+Z.| Linux  |
| Zombie (Z)  | A process that has completed execution but whose parent has not yet collected its exit status. | Linux  |
| Orphan Process  | A running process whose parent has terminated and has been adopted by systemd (PID 1).  | Linux  |
| Foreground Process| The process that currently owns the terminal and receives user input directly.| Linux  |
| Background Process| A process that executes without owning the terminal, allowing the shell to continue accepting commands.      | Linux  |
| Terminal Ownership| The mechanism through which only one foreground process controls terminal input and output at a time.| Linux  |
| Signal      | A software interrupt sent by the kernel or another process to control process behavior. | Linux  |
| SIGINT      | A signal sent by Ctrl+C requesting that a process interrupt its execution gracefully.   | Linux  |
| SIGTERM     | A graceful termination signal requesting a process to shut down safely and perform cleanup.    | Linux  |
| SIGKILL     | A non-maskable signal that immediately terminates a process without allowing cleanup.   | Linux  |
| SIGSTOP     | A signal that immediately pauses a running process.  | Linux  |
| SIGCONT     | A signal that resumes a previously stopped process.  | Linux  |
| jobs | A shell command that displays processes currently managed by the shell.   | Linux  |
| fg   | A shell command that moves a background or stopped job into the foreground.   | Linux  |
| bg   | A shell command that resumes a stopped process in the background.  | Linux  |
| Filesystem Hierarchy  | The standardized directory structure Linux uses to organize files and resources.     | Linux Filesystem |
| Root Directory (`/`)  | The top-most directory from which every other file and directory originates.  | Linux Filesystem |
| Home Directory (`~`)  | The personal working directory of the currently logged-in user. | Linux Filesystem |
| Current Working Directory (CWD) | The directory in which a process is currently operating. | Linux Filesystem |
| Absolute Path     | A file path beginning from the root directory (`/`) that identifies a location regardless of the current directory.     | Linux Filesystem |
| Relative Path     | A file path interpreted with respect to the current working directory.| Linux Filesystem |
| Parent Directory (`..`)| The directory immediately above the current directory in the filesystem hierarchy.   | Linux Filesystem |
| Current Directory (`.`)| A reference to the directory the process is currently operating in. | Linux Filesystem |
| File Type  | A Linux classification that determines how the kernel interacts with a filesystem object.| Linux Filesystem |
| Character Device  | A device file that transfers data one byte or character at a time (e.g., keyboard, terminal).      | Linux Devices    |
| Block Device      | A device file that transfers data in fixed-size blocks (e.g., SSD, HDD).      | Linux Devices    |
| Inode      | A filesystem metadata structure that uniquely identifies a file and stores its metadata, permissions, ownership, timestamps, and data block locations. It does not store the filename. | Linux Filesystem |
| Hard Link  | An additional directory entry pointing to the same inode as another filename. | Linux Filesystem |
| Symbolic Link (Soft Link)       | A special file that stores the pathname of another file or directory.| Linux Filesystem |
| Broken (Dangling) Symbolic Link | A symbolic link whose target path no longer exists.   | Linux Filesystem |
| `fork()`| A Linux system call that creates a new child process by duplicating the calling process. The child initially starts as an almost identical copy of the parent.  | Linux / Processes |
| `exec()`| A Linux system call that replaces the current program inside an existing process with a new program while keeping the same PID. | Linux / Processes |
| Process Scheduler | The Linux kernel component responsible for deciding which runnable process receives CPU time.| Linux / Kernel    |
| Context Switch    | The operation of saving the execution state (context) of one process and restoring another so multiple processes can share a CPU.      | Linux / Kernel    |
| Virtual Memory    | An abstraction that gives every process its own private address space while hiding physical RAM and protecting processes from each other.  | Linux / Memory    |
| Demand Paging     | A memory management technique where physical memory is allocated only when a process actually accesses a requested memory page. | Linux / Memory    |
| Stack   | The memory region used for temporary data such as function calls, parameters, local variables, and return addresses. It is automatically managed by the operating system. | Linux / Memory    |
| Heap| The memory region used for dynamically allocated, long-lived objects whose lifetime is controlled by the program. | Linux / Memory    |
| user      | An individual account representing a person or service interacting with the Linux system.  | Linux      |
| group     | A collection of users sharing common access requirements to simplify permission management.| Linux      |
| ownership | The association of a file or directory with a user (owner) and a group, establishing accountability.       | Linux      |
| permission| Rules defining which actions (read, write, execute) are allowed for the owner, group, and others.  | Linux      |
| rwx       | Read, Write, and Execute permission model used throughout Linux.   | Linux      |
| octal permissions | Numeric representation of Linux permissions using values 4 (read), 2 (write), and 1 (execute).     | Linux      |
| chmod     | Command used to modify file and directory permissions.     | Linux      |
| chown     | Command used to change the owner (and optionally the group) of a file or directory.| Linux      |
| chgrp     | Command used to change the group ownership of a file or directory. | Linux      |
| systemd   | The init system and service manager responsible for booting Linux, starting services, managing dependencies, and maintaining system state. | Linux      |
| systemctl | Command-line interface used to communicate with systemd and manage services and units.     | Linux      |
| daemon    | A background process that runs continuously and provides system or application services without direct user interaction.   | Linux      |
| unit      | A systemd object representing a resource such as a service, socket, mount point, timer, or target. | Linux      |
| service   | A long-running background process managed by systemd.      | Linux      |
| journald  | The systemd logging service that collects and stores structured system logs.       | Linux      |
| journalctl| Command-line utility used to query, filter, and inspect logs collected by journald.| Linux      |
| log level | Severity classification of a log entry such as DEBUG, INFO, WARNING, ERROR, or CRITICAL.   | Linux      |
| SSH       | Secure Shell protocol used for encrypted remote administration of systems. | Linux / Networking |
| ssh       | SSH client used to establish secure remote shell sessions. | Linux / Networking |
| sshd      | Secure Shell daemon that listens for incoming SSH connections on a Linux server.   | Linux / Networking |
| remote shell      | A shell running on another machine while being securely controlled from a local client.    | Linux / Networking |
| authentication    | The process of verifying the identity of a user before granting access.    | Security   |
| encryption| Converting data into an unreadable format so that only authorized parties can read it.     | Security   |

---

## Notes

- Add entries only after the concept has been discussed and understood.
- Keep definitions concise and focused on understanding.
- Organize terms by engineering domain.
- Avoid turning this document into a glossary copied from the internet.

---

Version: 0.3

Status: Living Document