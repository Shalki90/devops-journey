# File System

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document explains how Linux organizes, stores, and accesses files.

Understanding the filesystem is fundamental because **Linux follows the philosophy that "Everything is a file."** Files, directories, devices, sockets, and many kernel interfaces are exposed through the filesystem.

---

# What is a File System?

A filesystem is the method used by the operating system to organize, store, retrieve, and manage data on storage devices.

It defines:

* How files are named
* How directories are organized
* How data is stored
* How permissions are enforced
* How free space is managed

---

# Linux File System Hierarchy

Linux follows the **Filesystem Hierarchy Standard (FHS)**.

```text
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

---

# Important Directories

| Directory | Purpose                                 | Common Contents                         |
| --------- | --------------------------------------- | --------------------------------------- |
| `/`       | Root of the filesystem                  | Parent of all directories               |
| `/bin`    | Essential user commands                 | ls, cp, mv, cat                         |
| `/sbin`   | Essential system commands               | fsck, reboot                            |
| `/boot`   | Bootloader files                        | Kernel, GRUB                            |
| `/dev`    | Device files                            | sda, tty, null                          |
| `/etc`    | System configuration                    | passwd, hosts, ssh                      |
| `/home`   | User home directories                   | User files                              |
| `/root`   | Root user's home directory              | Administrator files                     |
| `/lib`    | Shared libraries                        | System libraries                        |
| `/media`  | Automatically mounted removable devices | USB drives                              |
| `/mnt`    | Temporary mount point                   | Manual mounts                           |
| `/opt`    | Optional third-party software           | Vendor applications                     |
| `/proc`   | Virtual process filesystem              | CPU, memory, processes                  |
| `/run`    | Runtime information                     | PID files, sockets                      |
| `/srv`    | Service data                            | FTP, HTTP                               |
| `/sys`    | Kernel interface                        | Hardware information                    |
| `/tmp`    | Temporary files                         | Deleted after reboot (varies by distro) |
| `/usr`    | User applications                       | Binaries, documentation                 |
| `/var`    | Variable data                           | Logs, cache, mail                       |

---

# Absolute vs Relative Path

| Absolute Path                   | Relative Path                 |
| ------------------------------- | ----------------------------- |
| Starts from `/`                 | Starts from current directory |
| Independent of current location | Depends on current location   |
| Example: `/home/user/file.txt`  | Example: `documents/file.txt` |

---

# Special Directory Symbols

| Symbol | Meaning           |
| ------ | ----------------- |
| `.`    | Current directory |
| `..`   | Parent directory  |
| `~`    | Home directory    |
| `/`    | Root directory    |

---

# File Types

| File Type         | Description                             |
| ----------------- | --------------------------------------- |
| Regular File      | Stores user or application data         |
| Directory         | Organizes files                         |
| Symbolic Link     | Points to another file                  |
| Hard Link         | Additional reference to the same inode  |
| Character Device  | Character-based hardware interface      |
| Block Device      | Block storage device                    |
| Socket            | Inter-process communication endpoint    |
| Named Pipe (FIFO) | Communication channel between processes |

---

# Inode

An **inode** is a filesystem data structure that stores metadata about a file.

It does **not** store:

* File name
* File path

It **does** store:

| Metadata             |
| -------------------- |
| File size            |
| Owner                |
| Group                |
| Permissions          |
| Creation time        |
| Modification time    |
| Access time          |
| Data block locations |

---

# Directory Structure

Directories contain mappings between:

```
Filename
        ↓
Inode Number
        ↓
Actual Data Blocks
```

---

# Hard Links vs Symbolic Links

| Feature                         | Hard Link | Symbolic Link |
| ------------------------------- | --------- | ------------- |
| Points to                       | Inode     | File path     |
| Cross Filesystems               | No        | Yes           |
| Survives Original File Deletion | Yes       | No            |
| Inode Shared                    | Yes       | No            |

---

# Mounting

Linux combines multiple storage devices into a **single directory tree**.

Instead of assigning drive letters like Windows, filesystems are mounted into directories.

Example:

```
SSD
↓

/mnt/storage
```

---

# Common Mount Points

| Directory | Purpose           |
| --------- | ----------------- |
| `/mnt`    | Temporary mounts  |
| `/media`  | Removable devices |
| `/boot`   | Boot partition    |
| `/`       | Root filesystem   |

---

# Navigation Commands

| Command  | Purpose                     |
| -------- | --------------------------- |
| `pwd`    | Show current directory      |
| `ls`     | List files                  |
| `cd`     | Change directory            |
| `tree`   | Display directory hierarchy |
| `find`   | Search files                |
| `locate` | Quickly locate files        |

---

# File Management Commands

| Command | Purpose                |
| ------- | ---------------------- |
| `touch` | Create empty file      |
| `cp`    | Copy                   |
| `mv`    | Move or rename         |
| `rm`    | Remove                 |
| `mkdir` | Create directory       |
| `rmdir` | Remove empty directory |

---

# Viewing File Contents

| Command   | Purpose             |
| --------- | ------------------- |
| `cat`     | Display entire file |
| `less`    | Interactive viewing |
| `head`    | First lines         |
| `tail`    | Last lines          |
| `tail -f` | Live monitoring     |

---

# Searching Files

| Command   | Purpose                                |
| --------- | -------------------------------------- |
| `find`    | Search by name, type, size, owner      |
| `locate`  | Database-based search                  |
| `which`   | Locate executable                      |
| `whereis` | Locate binaries, source, documentation |

---

# Everything is a File

| Resource                | Example         |
| ----------------------- | --------------- |
| Disk                    | `/dev/sda`      |
| Terminal                | `/dev/tty`      |
| Random Number Generator | `/dev/random`   |
| CPU Information         | `/proc/cpuinfo` |
| Memory Information      | `/proc/meminfo` |
| Kernel Parameters       | `/sys`          |

---

# Best Practices

| Practice                                                    | Benefit                          |
| ----------------------------------------------------------- | -------------------------------- |
| Use absolute paths in scripts                               | Prevents ambiguity               |
| Avoid storing data in `/tmp` permanently                    | Temporary storage may be cleared |
| Keep configuration files in `/etc`                          | Follows Linux standards          |
| Store application logs under `/var/log`                     | Simplifies administration        |
| Understand directory purposes before modifying system files | Reduces accidental system issues |

---

# Common Mistakes

| Mistake                                           | Better Practice                                                        |
| ------------------------------------------------- | ---------------------------------------------------------------------- |
| Confusing `/` with `/root`                        | `/` is the filesystem root; `/root` is the root user's home directory. |
| Using relative paths in automation                | Prefer absolute paths in scripts.                                      |
| Deleting files with `rm -rf` without verification | Confirm the target path before execution.                              |
| Editing configuration files without backup        | Create a backup before making changes.                                 |

---

# Key Takeaways

| Concept              | Summary                                      |
| -------------------- | -------------------------------------------- |
| Filesystem           | Organizes and stores data                    |
| Root (`/`)           | Top of the filesystem hierarchy              |
| FHS                  | Standard directory organization              |
| Inode                | Stores file metadata                         |
| Mounting             | Attaches filesystems into the directory tree |
| Absolute Path        | Starts from `/`                              |
| Relative Path        | Starts from current directory                |
| Everything is a File | Core Linux design philosophy                 |

---

# Related Documents

| Document           | Purpose                               |
| ------------------ | ------------------------------------- |
| Linux Overview.md  | Linux architecture and philosophy     |
| Permissions.md     | File ownership and permissions        |
| Storage.md         | Partitions, filesystems, and disks    |
| Shell.md           | File navigation and shell interaction |
| Cheatsheet.md      | Common filesystem commands            |
| Troubleshooting.md | Filesystem diagnostics and recovery   |
