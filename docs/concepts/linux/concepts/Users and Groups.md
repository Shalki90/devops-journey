# Users and Groups

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document explains how Linux manages users and groups, how authentication and authorization work, and how administrators control access to system resources.

Linux is designed as a **multi-user operating system**, allowing multiple users to work securely on the same machine while maintaining isolation through users, groups, and permissions.

---

# Why Users and Groups Exist

Users and groups provide:

* User identification
* Access control
* Resource isolation
* Security
* Shared access through groups
* Accountability and auditing

---

# User Types

| User Type    | Description                            | Examples                     |
| ------------ | -------------------------------------- | ---------------------------- |
| Root User    | Superuser with unrestricted privileges | `root`                       |
| Regular User | Standard user account                  | `alice`, `ubuntu`            |
| System User  | Used by services and applications      | `nginx`, `mysql`, `www-data` |

---

# Root User

The **root** user has unrestricted access to every file, process, and device on the system.

Capabilities include:

* Install software
* Manage users
* Change permissions
* Configure networking
* Mount storage
* Start or stop services
* Modify kernel parameters

> **Best Practice:** Perform routine administration using `sudo` rather than logging in directly as `root`.

---

# User Identity

Every user has a unique numeric identifier.

| Identifier     | Description                        |
| -------------- | ---------------------------------- |
| Username       | Human-readable account name        |
| UID            | User Identifier                    |
| Primary Group  | Default group assigned to the user |
| Home Directory | User's personal workspace          |
| Login Shell    | Default command interpreter        |

Example:

```text
Username : alice
UID      : 1001
Group    : developers
Home     : /home/alice
Shell    : /bin/bash
```

---

# User IDs (UID)

| UID Range                        | Purpose                   |
| -------------------------------- | ------------------------- |
| 0                                | Root user                 |
| 1–999 *(distribution dependent)* | System users and services |
| 1000+                            | Regular users             |

---

# Groups

A group is a collection of users that share common permissions.

Instead of assigning permissions individually, administrators assign permissions to groups.

Example:

```text
developers
├── Alice
├── Bob
└── Charlie
```

---

# Group Types

| Type            | Description                                    |
| --------------- | ---------------------------------------------- |
| Primary Group   | Default group assigned to a user               |
| Secondary Group | Additional groups that grant extra permissions |

---

# Authentication vs Authorization

| Authentication                       | Authorization                   |
| ------------------------------------ | ------------------------------- |
| Verifies identity                    | Determines permitted actions    |
| "Who are you?"                       | "What are you allowed to do?"   |
| Username and password, SSH key, etc. | Linux permissions, ACLs, groups |

---

# Important System Files

| File           | Purpose                           |
| -------------- | --------------------------------- |
| `/etc/passwd`  | User account information          |
| `/etc/shadow`  | Encrypted password information    |
| `/etc/group`   | Group information                 |
| `/etc/gshadow` | Secure group password information |

---

# User Management Commands

| Command  | Purpose                              |
| -------- | ------------------------------------ |
| `whoami` | Display current user                 |
| `id`     | Show UID, GID, and group memberships |
| `groups` | List user's groups                   |
| `who`    | Show logged-in users                 |
| `w`      | Display logged-in users and activity |

---

# Creating Users

| Command            | Purpose                                   |
| ------------------ | ----------------------------------------- |
| `useradd username` | Create a new user                         |
| `adduser username` | Interactive user creation (Debian/Ubuntu) |
| `passwd username`  | Set or change a password                  |

---

# Modifying Users

| Command                     | Purpose                       |
| --------------------------- | ----------------------------- |
| `usermod -aG group user`    | Add user to a secondary group |
| `usermod -s /bin/bash user` | Change login shell            |
| `usermod -d /new/home user` | Change home directory         |

---

# Deleting Users

| Command               | Purpose                        |
| --------------------- | ------------------------------ |
| `userdel username`    | Delete a user account          |
| `userdel -r username` | Delete user and home directory |

---

# Group Management

| Command               | Purpose                  |
| --------------------- | ------------------------ |
| `groupadd developers` | Create a group           |
| `groupdel developers` | Delete a group           |
| `groupmod`            | Modify a group           |
| `gpasswd`             | Manage group memberships |

---

# Switching Users

| Command         | Purpose                                    |
| --------------- | ------------------------------------------ |
| `su username`   | Switch to another user                     |
| `su - username` | Start a full login shell as another user   |
| `sudo command`  | Execute a command with elevated privileges |

---

# Sudo

`sudo` allows authorized users to execute commands with elevated privileges without logging in as the root user.

Advantages:

* Improved security
* Better auditing
* Reduced risk of accidental system changes
* Fine-grained administrative control

---

# Home Directory

Each user typically has a personal home directory.

Example:

| User  | Home Directory |
| ----- | -------------- |
| root  | `/root`        |
| alice | `/home/alice`  |

Home directories store:

* Personal files
* Shell configuration
* SSH keys
* User-specific settings

---

# Environment Variables

Common user-related variables:

| Variable | Description            |
| -------- | ---------------------- |
| `$HOME`  | User's home directory  |
| `$USER`  | Current username       |
| `$SHELL` | Current login shell    |
| `$PATH`  | Executable search path |

---

# User Lifecycle

```text
Create User
      │
Assign Password
      │
Assign Groups
      │
Login
      │
Perform Tasks
      │
Modify Account (if required)
      │
Delete / Disable User
```

---

# Best Practices

| Practice                                | Benefit                        |
| --------------------------------------- | ------------------------------ |
| Use `sudo` instead of direct root login | Improves security and auditing |
| Assign permissions through groups       | Simplifies administration      |
| Follow the principle of least privilege | Reduces security risks         |
| Disable unused accounts                 | Minimizes attack surface       |
| Use strong authentication methods       | Protects user accounts         |
| Review group memberships regularly      | Prevents privilege creep       |

---

# Common Mistakes

| Mistake                                 | Better Practice                                |
| --------------------------------------- | ---------------------------------------------- |
| Logging in as `root` for routine work   | Use `sudo`                                     |
| Giving every user administrative access | Grant only required privileges                 |
| Managing permissions user-by-user       | Use groups whenever possible                   |
| Forgetting to remove inactive users     | Periodically audit user accounts               |
| Sharing user accounts                   | Provide individual accounts for accountability |

---

# Interview Highlights

| Question                                                      | Answer                                                                                     |
| ------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| What is the difference between a user and a group?            | A user is an individual account; a group is a collection of users with shared permissions. |
| What is UID?                                                  | A unique numeric identifier assigned to each user.                                         |
| What is the purpose of `sudo`?                                | To execute commands with elevated privileges without logging in as `root`.                 |
| Which files store user information?                           | `/etc/passwd`, `/etc/shadow`, `/etc/group`, `/etc/gshadow`.                                |
| Why use groups instead of assigning permissions individually? | Groups simplify permission management and improve scalability.                             |

---

# Key Takeaways

| Concept        | Summary                                     |
| -------------- | ------------------------------------------- |
| User           | Individual account on the system            |
| Group          | Collection of users with shared permissions |
| UID            | Numeric user identifier                     |
| Root           | Superuser with unrestricted privileges      |
| `sudo`         | Temporary privilege escalation              |
| Authentication | Verifies identity                           |
| Authorization  | Determines permitted actions                |

---

# Related Documents

| Document                 | Purpose                             |
| ------------------------ | ----------------------------------- |
| Linux Overview.md        | Linux architecture                  |
| Permissions.md           | Ownership and permissions           |
| Shell.md                 | User shell and environment          |
| SSH.md                   | Remote authentication               |
| Environment Variables.md | User environment configuration      |
| Troubleshooting.md       | User and permission troubleshooting |
