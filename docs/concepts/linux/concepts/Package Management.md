# Package Management

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document explains how Linux installs, updates, verifies, and removes software using package management systems. It covers package formats, repositories, dependency management, package managers across major Linux distributions, and best practices for maintaining software.

Understanding package management is fundamental for Linux administration, automation, DevOps, cloud infrastructure, Docker images, and CI/CD pipelines.

---

# What is Package Management?

Package management is the process of installing, updating, configuring, verifying, and removing software in a controlled and repeatable manner.

Instead of manually copying files into the operating system, Linux uses package managers to automate software lifecycle management.

---

# Why Package Management Matters

Package managers provide:

* Centralized software installation
* Dependency management
* Software updates
* Security patching
* Version tracking
* Easy removal of software
* Repository management

Without package managers, administrators would need to manually download, install, configure, and maintain every application.

---

# Package Management Architecture

```text
Application Request
        │
Package Manager
        │
Repository
        │
Download Package
        │
Dependency Resolution
        │
Installation
        │
Configuration
        │
Ready to Use
```

---

# What is a Package?

A package is a compressed archive containing everything required to install an application.

Typically it includes:

* Executable binaries
* Libraries
* Configuration files
* Documentation
* Metadata
* Installation scripts
* Dependency information

---

# Package Formats

| Package Format | Distribution Family                    | Extension   |
| -------------- | -------------------------------------- | ----------- |
| Debian Package | Debian, Ubuntu                         | `.deb`      |
| RPM Package    | RHEL, CentOS, Fedora, Rocky, AlmaLinux | `.rpm`      |
| Source Package | Most Linux distributions               | Source code |

---

# Package Management Ecosystem

| Distribution | Package Manager | Low-Level Tool |
| ------------ | --------------- | -------------- |
| Ubuntu       | apt             | dpkg           |
| Debian       | apt             | dpkg           |
| Fedora       | dnf             | rpm            |
| RHEL         | dnf / yum       | rpm            |
| Rocky Linux  | dnf             | rpm            |
| AlmaLinux    | dnf             | rpm            |

---

# Repositories

A repository is a centralized location that stores software packages.

Repositories provide:

* Software packages
* Updates
* Security patches
* Dependency metadata

---

# Repository Workflow

```text
User
 │
 ▼
Package Manager
 │
 ▼
Configured Repository
 │
 ▼
Download Packages
 │
 ▼
Install
```

---

# Debian-Based Package Management

## Update Repository Metadata

```bash
sudo apt update
```

Downloads the latest package index from configured repositories.

---

## Upgrade Installed Packages

```bash
sudo apt upgrade
```

Installs newer versions of already installed packages.

---

## Full System Upgrade

```bash
sudo apt full-upgrade
```

Allows dependency changes while upgrading packages.

---

## Install a Package

```bash
sudo apt install nginx
```

---

## Remove a Package

```bash
sudo apt remove nginx
```

---

## Remove Including Configuration Files

```bash
sudo apt purge nginx
```

---

## Remove Unused Dependencies

```bash
sudo apt autoremove
```

---

# RPM-Based Package Management

## Install

```bash
sudo dnf install nginx
```

---

## Update Packages

```bash
sudo dnf update
```

---

## Remove

```bash
sudo dnf remove nginx
```

---

## Search

```bash
dnf search nginx
```

---

## List Installed Packages

```bash
dnf list installed
```

---

# Low-Level Package Managers

| Tool | Purpose                           |
| ---- | --------------------------------- |
| dpkg | Install and query `.deb` packages |
| rpm  | Install and query `.rpm` packages |

Example:

```bash
dpkg -i package.deb
```

```bash
rpm -ivh package.rpm
```

Normally, high-level package managers (`apt`, `dnf`) are preferred because they automatically resolve dependencies.

---

# Dependency Management

Applications often require additional libraries or packages to function.

The package manager automatically:

* Detects dependencies
* Downloads required packages
* Installs them in the correct order
* Maintains dependency information

---

# Package Lifecycle

```text
Repository
     │
Install
     │
Configured
     │
Update
     │
Verify
     │
Remove
```

---

# Querying Installed Packages

| Command                | Purpose                                 |
| ---------------------- | --------------------------------------- |
| `apt list --installed` | List installed packages (Debian/Ubuntu) |
| `dpkg -l`              | Query installed `.deb` packages         |
| `dnf list installed`   | List installed packages (RHEL/Fedora)   |
| `rpm -qa`              | Query installed `.rpm` packages         |

---

# Searching for Packages

| Command              | Purpose                    |
| -------------------- | -------------------------- |
| `apt search package` | Search Debian repositories |
| `dnf search package` | Search RPM repositories    |

---

# Package Information

| Command           | Purpose                     |
| ----------------- | --------------------------- |
| `apt show nginx`  | Display package details     |
| `dnf info nginx`  | Display package information |
| `rpm -qi package` | Query RPM metadata          |
| `dpkg -s package` | Query Debian package status |

---

# Repository Configuration

Typical repository configuration files:

| Distribution  | Configuration                                          |
| ------------- | ------------------------------------------------------ |
| Ubuntu/Debian | `/etc/apt/sources.list` and `/etc/apt/sources.list.d/` |
| RHEL/Fedora   | `/etc/yum.repos.d/`                                    |

---

# Package Cache

Package managers maintain a local cache to improve installation speed.

Useful commands:

| Command         | Purpose                         |
| --------------- | ------------------------------- |
| `apt clean`     | Remove downloaded package cache |
| `apt autoclean` | Remove obsolete package files   |
| `dnf clean all` | Clean DNF cache                 |

---

# Software Updates

Two distinct operations are common:

| Operation | Purpose                                      |
| --------- | -------------------------------------------- |
| Update    | Refresh repository metadata                  |
| Upgrade   | Install newer versions of installed packages |

Example:

```bash
sudo apt update
sudo apt upgrade
```

---

# Common Troubleshooting

| Problem                | Investigation                   | Resolution                                         |
| ---------------------- | ------------------------------- | -------------------------------------------------- |
| Package not found      | Verify repository configuration | Update package index or enable required repository |
| Dependency conflict    | Review dependency information   | Resolve conflicting packages                       |
| Repository unavailable | Test network connectivity       | Verify repository URL or mirror                    |
| Broken package         | Use package repair tools        | Reinstall or repair affected packages              |
| Disk space exhausted   | Check filesystem usage          | Remove unnecessary packages or clean cache         |

---

# Best Practices

| Practice                                    | Benefit                               |
| ------------------------------------------- | ------------------------------------- |
| Update package metadata before installation | Ensures latest package information    |
| Apply security updates regularly            | Reduces vulnerabilities               |
| Prefer official repositories                | Improves stability and security       |
| Remove unused packages                      | Reduces attack surface and disk usage |
| Clean package cache periodically            | Frees disk space                      |

---

# Common Mistakes

| Mistake                                         | Better Practice                                  |
| ----------------------------------------------- | ------------------------------------------------ |
| Installing software from untrusted repositories | Prefer official or verified repositories         |
| Running upgrades without reviewing changes      | Understand major package updates before applying |
| Mixing incompatible repositories                | Use repositories intended for your distribution  |
| Ignoring dependency warnings                    | Resolve conflicts before proceeding              |
| Removing packages without checking dependencies | Verify dependent applications first              |

---

# Interview Highlights

| Question                                   | Answer                                                                                     |
| ------------------------------------------ | ------------------------------------------------------------------------------------------ |
| What is a package manager?                 | A tool that installs, updates, verifies, and removes software while managing dependencies. |
| Difference between `apt` and `dpkg`?       | `apt` is a high-level package manager; `dpkg` is the low-level tool for `.deb` packages.   |
| Difference between `dnf` and `rpm`?        | `dnf` resolves dependencies automatically; `rpm` manages individual RPM packages.          |
| What is a repository?                      | A centralized source of software packages and updates.                                     |
| Why run `apt update` before `apt upgrade`? | To refresh repository metadata before installing newer package versions.                   |

---

# Key Takeaways

| Concept         | Summary                                 |
| --------------- | --------------------------------------- |
| Package         | Installable software bundle             |
| Package Manager | Automates software lifecycle management |
| Repository      | Centralized software source             |
| Dependency      | Required supporting package             |
| apt             | Debian/Ubuntu package manager           |
| dnf             | Fedora/RHEL package manager             |
| dpkg            | Low-level Debian package tool           |
| rpm             | Low-level RPM package tool              |

---

# Related Documents

| Document            | Purpose                                                     |
| ------------------- | ----------------------------------------------------------- |
| Boot Process.md     | Software loaded during startup                              |
| systemd.md          | Managing installed services                                 |
| Shell.md            | Executing package management commands                       |
| Networking.md       | Repository access over the network                          |
| Security.md         | Applying security patches                                   |
| Linux for DevOps.md | Package management in CI/CD, Docker, and cloud environments |
