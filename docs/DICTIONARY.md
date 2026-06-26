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
| Pull Request (PR)      | A request to merge changes from one branch into another after review and validation.                                                   | Git    |
| Code Review            | The process of examining proposed changes before they are merged into a shared branch.                                                 | Git    |
| Collaboration Workflow | A structured process that allows multiple developers to work safely on the same repository.                                            | Git    |
| Conflict Resolution    | The process of manually deciding how competing changes should be combined when Git cannot determine the correct outcome automatically. | Git    |
| git revert             | A command that creates a new commit which reverses the changes introduced by an earlier commit.                                        | Git    |
| git reset              | A command that moves branch history backward, allowing commits to be removed or rewritten before sharing.                              | Git    |
| git stash              | A command that temporarily stores unfinished work so another task can be performed without creating a commit.                          | Git    |
| Stash                  | A temporary storage area used to save unfinished changes outside the current Working Directory.                                        | Git    |
| Shared History         | Commit history that has already been published and may be used by other collaborators.                                                 | Git    |
| Private History        | Commit history that exists only locally and can be safely rewritten if necessary.                                                      | Git    |
| Diverged Branches      | Branches that contain different commits and therefore require a true merge rather than a fast-forward update.                          | Git    |
| GitHub                 | A cloud-hosted platform used for storing, collaborating on, and managing Git repositories.                                             | Git    |
| Repository History     | The complete record of commits, branches, merges, and changes within a repository.                                                     | Git    |
| Operating System (OS)                        | System software that manages hardware resources and provides common services for applications.                                               | Linux  |
| Linux                                        | An operating system built around the Linux kernel, commonly combined with GNU utilities to form a complete operating system.                 | Linux  |
| Kernel                                       | The core component of an operating system that manages hardware resources and provides services to applications through system calls.        | Linux  |
| GNU                                          | A collection of user-space tools and utilities that make a Linux system usable by providing commands, libraries, and standard programs.      | Linux  |
| Shell                                        | A command interpreter that allows users to interact with the operating system.                                                               | Linux  |
| Bash (Bourne Again Shell)                    | A widely used implementation of the Unix shell that interprets user commands and executes programs.                                          | Linux  |
| Linux Distribution                           | A packaged operating system combining the Linux kernel, GNU utilities, package manager, and additional software into a complete system.      | Linux  |
| Ubuntu                                       | A Debian-based Linux distribution focused on ease of use and broad community support.                                                        | Linux  |
| Rocky Linux                                  | A community-supported enterprise Linux distribution designed for long-term stability and compatibility with Red Hat Enterprise Linux (RHEL). | Linux  |
| BIOS (Basic Input/Output System)             | Firmware that initializes hardware during startup and locates a bootable device.                                                             | Linux  |
| UEFI (Unified Extensible Firmware Interface) | Modern firmware that replaces BIOS and provides a standardized interface between hardware and the operating system during boot.              | Linux  |
| Bootloader                                   | Software responsible for locating and loading the operating system kernel into memory during system startup.                                 | Linux  |
| GRUB (GRand Unified Bootloader)              | A widely used Linux bootloader that loads the selected Linux kernel and initramfs into memory before transferring control.                   | Linux  |
| initramfs (Initial RAM Filesystem)           | A temporary root filesystem loaded into RAM that prepares the system so the Linux kernel can access the real root filesystem.                | Linux  |
| User Space                                   | The area where applications and user programs execute with limited privileges, requiring system calls to access hardware.                    | Linux  |
| Kernel Space                                 | The protected memory region where the operating system kernel executes with full access to hardware and system resources.                    | Linux  |
| System Call                                  | A controlled interface that allows applications in user space to request services from the Linux kernel.                                     | Linux  |
| Device Driver                                | A software component that enables the kernel to communicate with a specific hardware device through a standardized interface.                | Linux  |


---

## Notes

- Add entries only after the concept has been discussed and understood.
- Keep definitions concise and focused on understanding.
- Organize terms by engineering domain.
- Avoid turning this document into a glossary copied from the internet.

---

Version: 0.3

Status: Living Document