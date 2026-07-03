# Storage

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document explains how Linux manages persistent storage, including disks, partitions, filesystems, mounting, Logical Volume Manager (LVM), RAID concepts, and storage monitoring.

Understanding Linux storage is essential for system administration, cloud infrastructure, virtualization, containers, and production troubleshooting.

---

# Storage Hierarchy

```text
Application
      │
Filesystem
      │
Partition / Logical Volume
      │
Disk
      │
Storage Controller
      │
Physical Storage
```

---

# Storage Components

| Component     | Responsibility                   |
| ------------- | -------------------------------- |
| Physical Disk | Stores persistent data           |
| Partition     | Logical division of a disk       |
| Filesystem    | Organizes stored data            |
| Mount Point   | Makes a filesystem accessible    |
| Block Device  | Interface used to access storage |
| LVM           | Flexible storage management      |
| RAID          | Redundancy and performance       |

---

# Storage Types

| Type            | Description                     | Advantages              | Limitations        |
| --------------- | ------------------------------- | ----------------------- | ------------------ |
| HDD             | Mechanical spinning disk        | Low cost, high capacity | Slower performance |
| SSD             | Flash-based storage             | Fast, reliable          | Higher cost per GB |
| NVMe SSD        | PCIe-based SSD                  | Extremely fast          | More expensive     |
| Network Storage | Storage accessed over a network | Shared access           | Network dependency |

---

# Block Devices

Linux treats storage devices as **block devices**.

Examples:

| Device         | Description                                     |
| -------------- | ----------------------------------------------- |
| `/dev/sda`     | First SATA/SCSI disk                            |
| `/dev/sdb`     | Second SATA/SCSI disk                           |
| `/dev/nvme0n1` | First NVMe SSD                                  |
| `/dev/vda`     | First virtual disk (common in virtual machines) |

View available block devices:

```bash
lsblk
```

---

# Partitions

A partition divides a physical disk into logical sections.

Example:

```text
Disk (/dev/sda)

├── /dev/sda1
├── /dev/sda2
└── /dev/sda3
```

Benefits:

* Multiple operating systems
* Separate system and user data
* Easier backups
* Improved management

---

# Partition Tables

| Type | Description            | Maximum Disk Size   | Maximum Partitions   |
| ---- | ---------------------- | ------------------- | -------------------- |
| MBR  | Legacy partition table | ~2 TB               | 4 primary partitions |
| GPT  | Modern partition table | >9 ZB (theoretical) | 128+ partitions      |

GPT is recommended for modern systems.

---

# Filesystems

A filesystem determines how data is organized and stored.

| Filesystem | Characteristics                   | Typical Usage                 |
| ---------- | --------------------------------- | ----------------------------- |
| ext4       | Stable, widely used               | General-purpose Linux systems |
| XFS        | High-performance, scalable        | Enterprise servers            |
| Btrfs      | Snapshots, compression, checksums | Advanced storage management   |
| FAT32      | Cross-platform compatibility      | USB drives                    |
| exFAT      | Large removable storage           | Flash drives and SD cards     |
| NTFS       | Windows filesystem                | Dual-boot and external drives |

---

# Formatting a Filesystem

Formatting prepares a partition for use.

Common commands:

```bash
mkfs.ext4 /dev/sdb1
```

```bash
mkfs.xfs /dev/sdb1
```

**Warning:** Formatting erases existing data.

---

# Mounting

A filesystem must be mounted before it can be accessed.

Example:

```text
Disk
   │
Partition
   │
Filesystem
   │
Mounted at
   │
/data
```

Mount manually:

```bash
mount /dev/sdb1 /data
```

Unmount:

```bash
umount /data
```

---

# Mount Points

| Directory | Typical Purpose         |
| --------- | ----------------------- |
| `/`       | Root filesystem         |
| `/boot`   | Boot partition          |
| `/home`   | User data               |
| `/mnt`    | Temporary manual mounts |
| `/media`  | Removable media         |

---

# Persistent Mounts

Persistent mounts are configured in:

```text
/etc/fstab
```

Example:

```text
UUID=abcd1234   /data   ext4   defaults   0   2
```

Advantages:

* Automatic mounting during boot
* Consistent configuration
* Easier administration

---

# UUID

Each filesystem has a unique identifier.

View UUIDs:

```bash
blkid
```

Using UUIDs is preferred over device names because device names may change after reboot.

---

# Disk Usage Commands

| Command  | Purpose                  |
| -------- | ------------------------ |
| `df -h`  | Display filesystem usage |
| `du -sh` | Display directory size   |
| `lsblk`  | List block devices       |
| `blkid`  | Display filesystem UUIDs |
| `mount`  | Show mounted filesystems |

---

# LVM (Logical Volume Manager)

LVM provides flexible storage management.

Benefits:

* Resize volumes
* Create snapshots
* Combine multiple disks
* Simplify storage expansion

Architecture:

```text
Physical Disk
      │
Physical Volume (PV)
      │
Volume Group (VG)
      │
Logical Volume (LV)
      │
Filesystem
```

---

# RAID Overview

RAID combines multiple disks for redundancy or performance.

| RAID Level | Purpose                  | Fault Tolerance                         |
| ---------- | ------------------------ | --------------------------------------- |
| RAID 0     | Performance              | None                                    |
| RAID 1     | Mirroring                | One disk failure                        |
| RAID 5     | Performance + redundancy | One disk failure                        |
| RAID 6     | Extra redundancy         | Two disk failures                       |
| RAID 10    | Performance + redundancy | Multiple failures (depending on layout) |

---

# Storage Monitoring

| Command    | Purpose                  |
| ---------- | ------------------------ |
| `df -h`    | Filesystem utilization   |
| `du -sh`   | Directory usage          |
| `lsblk`    | Block devices            |
| `mount`    | Mounted filesystems      |
| `iostat`   | Disk I/O statistics      |
| `smartctl` | Disk health (SMART data) |

---

# Common Storage Issues

| Problem                 | Possible Cause            | Resolution                                             |
| ----------------------- | ------------------------- | ------------------------------------------------------ |
| Disk full               | Large files or logs       | Use `df -h` and `du -sh` to identify usage             |
| Filesystem not mounting | Incorrect `fstab` entry   | Verify UUID, mount point, and filesystem type          |
| Read-only filesystem    | Filesystem errors         | Check logs and run filesystem repair if appropriate    |
| Device not detected     | Hardware or driver issue  | Verify with `lsblk`, `dmesg`, and hardware connections |
| Slow disk performance   | Failing disk or heavy I/O | Review `iostat`, SMART data, and application workload  |

---

# Best Practices

| Practice                                         | Benefit                                         |
| ------------------------------------------------ | ----------------------------------------------- |
| Use GPT for new disks                            | Supports larger disks and more partitions       |
| Mount filesystems using UUID                     | Prevents issues caused by changing device names |
| Monitor disk usage regularly                     | Avoid unexpected outages                        |
| Separate system and application data             | Simplifies maintenance and recovery             |
| Back up data before repartitioning or formatting | Prevents accidental data loss                   |

---

# Common Mistakes

| Mistake                            | Better Practice                                |
| ---------------------------------- | ---------------------------------------------- |
| Filling the root filesystem        | Monitor usage and separate data volumes        |
| Using device names in `/etc/fstab` | Use UUIDs instead                              |
| Formatting the wrong partition     | Verify the target device before running `mkfs` |
| Ignoring SMART warnings            | Replace failing disks proactively              |
| Mounting without testing `fstab`   | Validate configuration before rebooting        |

---

# Interview Highlights

| Question                             | Answer                                                                         |
| ------------------------------------ | ------------------------------------------------------------------------------ |
| What is a filesystem?                | A structure that organizes and manages data on storage devices.                |
| Difference between MBR and GPT?      | GPT supports larger disks and more partitions than MBR.                        |
| What is mounting?                    | Attaching a filesystem to the Linux directory hierarchy.                       |
| Why use UUID instead of `/dev/sda1`? | UUIDs remain consistent even if device names change.                           |
| What is LVM?                         | A storage management layer that enables flexible volume creation and resizing. |
| What is RAID?                        | A method of combining multiple disks for redundancy, performance, or both.     |

---

# Key Takeaways

| Concept      | Summary                               |
| ------------ | ------------------------------------- |
| Block Device | Linux interface to storage hardware   |
| Partition    | Logical section of a disk             |
| Filesystem   | Organizes stored data                 |
| Mount        | Makes a filesystem accessible         |
| UUID         | Persistent filesystem identifier      |
| LVM          | Flexible logical storage management   |
| RAID         | Storage redundancy and/or performance |
| `/etc/fstab` | Persistent mount configuration        |

---

# Related Documents

| Document             | Purpose                       |
| -------------------- | ----------------------------- |
| Linux Overview.md    | Linux architecture            |
| File System.md       | Filesystem hierarchy          |
| Memory Management.md | Virtual memory and swap       |
| Boot Process.md      | Storage during system startup |
| Troubleshooting.md   | Storage diagnostics           |
| Cheatsheet.md        | Storage management commands   |
