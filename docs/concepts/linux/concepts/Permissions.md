# Permissions

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document explains the Linux permission model, including ownership, permission bits, numeric notation, special permissions, and common administrative commands.

Linux uses a permission-based security model to control who can access files, directories, and system resources.

---

# Why Permissions Matter

Permissions provide:

* Security
* Access control
* Multi-user isolation
* Protection of system files
* Controlled collaboration

Without permissions, every user could modify or delete every file on the system.

---

# Permission Model

Every filesystem object has:

| Attribute    | Description                    |
| ------------ | ------------------------------ |
| Owner (User) | User who owns the file         |
| Group        | Group associated with the file |
| Others       | Everyone else on the system    |

---

# Permission Types

| Permission | Symbol | Numeric Value | Meaning                                               |
| ---------- | ------ | ------------- | ----------------------------------------------------- |
| Read       | `r`    | 4             | View file contents or list directory contents         |
| Write      | `w`    | 2             | Modify file or create/delete files within a directory |
| Execute    | `x`    | 1             | Execute a file or enter a directory                   |

---

# Permission Layout

Example:

```text
-rwxr-xr--
```

Breakdown:

| Section | Meaning            |
| ------- | ------------------ |
| `-`     | Regular file       |
| `rwx`   | Owner permissions  |
| `r-x`   | Group permissions  |
| `r--`   | Others permissions |

---

# File Types

| Symbol | File Type         |
| ------ | ----------------- |
| `-`    | Regular file      |
| `d`    | Directory         |
| `l`    | Symbolic link     |
| `c`    | Character device  |
| `b`    | Block device      |
| `s`    | Socket            |
| `p`    | Named pipe (FIFO) |

---

# Numeric (Octal) Permissions

Permissions are represented using octal notation.

| Permission | Value |
| ---------- | ----: |
| Read       |     4 |
| Write      |     2 |
| Execute    |     1 |

---

## Common Permission Values

| Numeric | Symbolic    | Meaning                                  |
| ------- | ----------- | ---------------------------------------- |
| 777     | `rwxrwxrwx` | Full permissions for everyone            |
| 755     | `rwxr-xr-x` | Owner full access; others read & execute |
| 750     | `rwxr-x---` | Owner full; group read & execute         |
| 700     | `rwx------` | Owner only                               |
| 644     | `rw-r--r--` | Standard file permissions                |
| 640     | `rw-r-----` | Owner read/write; group read             |
| 600     | `rw-------` | Private file                             |

---

# Directory Permissions

Directory permissions behave differently than file permissions.

| Permission | Effect                                                                |
| ---------- | --------------------------------------------------------------------- |
| Read       | List directory contents                                               |
| Write      | Create, delete, or rename files (subject to ownership and sticky bit) |
| Execute    | Enter the directory and access its contents                           |

---

# Viewing Permissions

| Command         | Purpose                      |
| --------------- | ---------------------------- |
| `ls -l`         | Display permissions          |
| `stat file.txt` | Show detailed metadata       |
| `id`            | Show current user and groups |
| `groups`        | Display group memberships    |

---

# Changing Permissions

## chmod

Changes file or directory permissions.

### Symbolic Mode

| Command               | Result                             |
| --------------------- | ---------------------------------- |
| `chmod u+x script.sh` | Add execute permission to owner    |
| `chmod g-w file.txt`  | Remove write permission from group |
| `chmod o+r file.txt`  | Add read permission to others      |
| `chmod a+r file.txt`  | Add read permission to everyone    |

---

### Numeric Mode

| Command                 | Result                                   |
| ----------------------- | ---------------------------------------- |
| `chmod 755 script.sh`   | Owner full access, others read & execute |
| `chmod 644 file.txt`    | Standard file permissions                |
| `chmod 600 secrets.txt` | Private file                             |

---

# Ownership

Every file has an owner and a group.

Example:

```text
-rw-r--r-- 1 alice developers file.txt
```

| Field      | Meaning |
| ---------- | ------- |
| alice      | Owner   |
| developers | Group   |

---

# Changing Ownership

## chown

| Command                          | Purpose                    |
| -------------------------------- | -------------------------- |
| `chown user file.txt`            | Change owner               |
| `chown user:group file.txt`      | Change owner and group     |
| `chown -R user:group directory/` | Recursive ownership change |

---

## chgrp

| Command                     | Purpose                |
| --------------------------- | ---------------------- |
| `chgrp developers file.txt` | Change group ownership |

---

# Default Permissions (umask)

`umask` removes permission bits from the system defaults when creating new files and directories.

Default maximum permissions:

| Object    | Default |
| --------- | ------- |
| File      | 666     |
| Directory | 777     |

Example:

```text
666
-022
----
644
```

Result:

New file → **644**

---

# Special Permissions

## SUID (Set User ID)

| Purpose                         | Effect                                     |
| ------------------------------- | ------------------------------------------ |
| Execute with owner's privileges | User temporarily gains owner's permissions |

Example:

```bash
chmod u+s file
```

---

## SGID (Set Group ID)

| Purpose                         | Effect                                                         |
| ------------------------------- | -------------------------------------------------------------- |
| Execute with group's privileges | Files created inside a directory inherit the directory's group |

---

## Sticky Bit

Typically applied to shared directories.

Example:

```text
drwxrwxrwt
```

Effect:

Only the file owner (or root) can delete their own files.

Common example:

```text
/tmp
```

---

# Recursive Operations

| Command                          | Purpose                        |
| -------------------------------- | ------------------------------ |
| `chmod -R 755 directory/`        | Change permissions recursively |
| `chown -R user:group directory/` | Change ownership recursively   |

Use recursive commands carefully, especially on system directories.

---

# Best Practices

| Practice                                | Reason                           |
| --------------------------------------- | -------------------------------- |
| Apply the principle of least privilege  | Reduce security risks            |
| Avoid `777` unless absolutely necessary | Prevent unauthorized access      |
| Use groups for shared access            | Simplifies permission management |
| Protect sensitive files with `600`      | Restrict access                  |
| Review permissions regularly            | Maintain system security         |

---

# Common Mistakes

| Mistake                                       | Better Practice                                        |
| --------------------------------------------- | ------------------------------------------------------ |
| Using `chmod 777` to fix every issue          | Identify the actual permission requirement             |
| Running everything as `root`                  | Use `sudo` only when necessary                         |
| Forgetting execute permission on scripts      | Add execute permission using `chmod +x`                |
| Ignoring group permissions                    | Use groups instead of granting permissions to everyone |
| Applying recursive permission changes blindly | Verify the target directory before executing           |

---

# Interview Highlights

| Question                                | Answer                                                                     |
| --------------------------------------- | -------------------------------------------------------------------------- |
| What does `755` mean?                   | Owner: read, write, execute; Group: read & execute; Others: read & execute |
| Difference between `chmod` and `chown`? | `chmod` changes permissions; `chown` changes ownership                     |
| What is `umask`?                        | Default permission mask applied when new files and directories are created |
| What is SUID?                           | Allows execution with the owner's privileges                               |
| Why is `777` discouraged?               | It grants unrestricted access to everyone, increasing security risk        |

---

# Key Takeaways

| Concept                  | Summary                                |
| ------------------------ | -------------------------------------- |
| Owner                    | User who owns the file                 |
| Group                    | Collection of users with shared access |
| Others                   | All remaining users                    |
| `rwx`                    | Read, Write, Execute                   |
| `chmod`                  | Change permissions                     |
| `chown`                  | Change ownership                       |
| `umask`                  | Defines default permissions            |
| SUID / SGID / Sticky Bit | Special permission mechanisms          |

---

# Related Documents

| Document            | Purpose                       |
| ------------------- | ----------------------------- |
| Linux Overview.md   | Linux architecture            |
| File System.md      | Filesystem hierarchy          |
| Users and Groups.md | User and group administration |
| Shell.md            | Command-line operations       |
| Troubleshooting.md  | Permission-related debugging  |
| Cheatsheet.md       | Permission commands           |
