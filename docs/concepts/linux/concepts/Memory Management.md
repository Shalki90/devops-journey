# Memory Management

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document explains how Linux manages memory, how processes use RAM, how virtual memory works, the role of swap space, memory allocation mechanisms, and how administrators monitor and troubleshoot memory-related issues.

Memory management is one of the Linux kernel's primary responsibilities and directly impacts system performance, stability, and scalability.

---

# Why Memory Management is Important

Memory management enables Linux to:

* Run multiple applications simultaneously
* Prevent processes from interfering with one another
* Maximize RAM utilization
* Improve application performance
* Protect system stability
* Support virtual memory

---

# Types of Memory

| Memory Type       | Description                             | Speed     | Persistence |
| ----------------- | --------------------------------------- | --------- | ----------- |
| CPU Cache         | Small, high-speed memory inside the CPU | Fastest   | No          |
| RAM               | Main system memory                      | Very Fast | No          |
| Swap              | Disk space used as virtual memory       | Slow      | No          |
| Storage (SSD/HDD) | Permanent data storage                  | Slowest   | Yes         |

---

# Linux Memory Architecture

```text
+----------------------------+
|        User Process        |
+----------------------------+
|      Virtual Memory        |
+----------------------------+
|      Linux Kernel          |
+----------------------------+
|            RAM             |
+----------------------------+
|        Swap Space          |
+----------------------------+
|      Physical Storage      |
+----------------------------+
```

---

# Physical vs Virtual Memory

| Physical Memory (RAM)    | Virtual Memory                                 |
| ------------------------ | ---------------------------------------------- |
| Actual hardware memory   | Logical memory presented to each process       |
| Limited by installed RAM | Larger than physical RAM                       |
| Fast                     | May involve disk access                        |
| Shared by all processes  | Each process has its own virtual address space |

---

# Virtual Memory

Virtual memory allows each process to believe it has its own continuous memory space.

Benefits include:

* Process isolation
* Memory protection
* Efficient RAM utilization
* Larger address space
* Demand paging

---

# Memory Allocation

When an application starts:

```text
Application Starts
        │
Kernel Creates Process
        │
Virtual Memory Allocated
        │
Pages Loaded into RAM
        │
Process Executes
```

The kernel allocates memory only as needed rather than loading the entire application into RAM immediately.

---

# Memory Segments

A typical process memory layout consists of:

```text
+------------------+
| Stack            |
+------------------+
| Heap             |
+------------------+
| BSS              |
+------------------+
| Data Segment     |
+------------------+
| Text (Code)      |
+------------------+
```

| Segment | Purpose                               |
| ------- | ------------------------------------- |
| Text    | Executable program instructions       |
| Data    | Initialized global/static variables   |
| BSS     | Uninitialized global/static variables |
| Heap    | Dynamically allocated memory          |
| Stack   | Function calls, local variables       |

---

# Paging

Linux divides memory into fixed-size **pages**.

Instead of moving entire processes, Linux transfers memory page-by-page between RAM and swap when necessary.

Advantages:

* Efficient memory usage
* Faster allocation
* Better isolation
* Simplified memory management

---

# Swap Space

Swap is disk space used when available RAM becomes insufficient.

```text
RAM Full
    │
Kernel Moves Inactive Pages
    │
Swap Space
```

---

## Advantages

* Prevents immediate crashes
* Supports memory overcommit
* Provides temporary overflow capacity

## Disadvantages

* Much slower than RAM
* Excessive swap usage reduces performance

---

# Memory Cache

Linux uses available RAM as a filesystem cache.

Instead of leaving unused RAM idle, Linux caches frequently accessed files.

Benefits:

* Faster disk access
* Reduced I/O
* Improved overall performance

Cached memory is automatically released when applications require additional RAM.

---

# Out Of Memory (OOM)

When Linux cannot allocate sufficient memory, the **OOM Killer** selects one or more processes to terminate in order to protect overall system stability.

Selection is based on several factors, including memory usage and process priority.

---

# Monitoring Memory

| Command             | Purpose                            |
| ------------------- | ---------------------------------- |
| `free -h`           | Display memory and swap usage      |
| `top`               | Monitor memory usage by process    |
| `htop`              | Interactive process monitor        |
| `vmstat`            | Virtual memory statistics          |
| `cat /proc/meminfo` | Detailed kernel memory information |

---

# Understanding `free -h`

Example:

```text
              total   used   free   shared   buff/cache   available
Mem:           16G     6G      2G       1G          8G         9G
Swap:           2G     0G      2G
```

| Field      | Meaning                                       |
| ---------- | --------------------------------------------- |
| Total      | Installed RAM                                 |
| Used       | Memory currently allocated                    |
| Free       | Completely unused memory                      |
| Buff/Cache | Memory used for caching                       |
| Available  | Memory readily available for new applications |

> **Note:** Low "free" memory is not necessarily a problem if sufficient "available" memory exists.

---

# Memory-Related `/proc` Files

| File                 | Purpose                    |
| -------------------- | -------------------------- |
| `/proc/meminfo`      | Memory statistics          |
| `/proc/swaps`        | Active swap devices        |
| `/proc/<PID>/status` | Process memory information |
| `/proc/vmstat`       | Virtual memory statistics  |

---

# Common Troubleshooting Scenarios

| Problem              | Investigation              | Resolution                                        |
| -------------------- | -------------------------- | ------------------------------------------------- |
| High memory usage    | `top`, `htop`, `free -h`   | Identify memory-intensive processes               |
| Excessive swap usage | `vmstat`, `free -h`        | Reduce memory pressure or add RAM                 |
| OOM events           | `journalctl`, `dmesg`      | Determine why the OOM Killer terminated a process |
| Memory leak          | Long-term monitoring       | Fix application or restart affected service       |
| Slow system          | Check RAM, swap, and cache | Investigate resource contention                   |

---

# Best Practices

| Practice                          | Benefit                            |
| --------------------------------- | ---------------------------------- |
| Monitor memory regularly          | Detect issues early                |
| Investigate increasing swap usage | Prevent performance degradation    |
| Size RAM based on workload        | Improve stability                  |
| Understand cache behavior         | Avoid misinterpreting memory usage |
| Review OOM events after crashes   | Identify underlying memory issues  |

---

# Common Mistakes

| Mistake                                   | Better Practice                                       |
| ----------------------------------------- | ----------------------------------------------------- |
| Assuming low free memory means a problem  | Evaluate available memory and cache usage             |
| Ignoring swap activity                    | Persistent swap usage often indicates memory pressure |
| Clearing cache unnecessarily              | Linux manages cache automatically                     |
| Restarting services without investigation | Identify the root cause first                         |
| Ignoring gradual memory growth            | Monitor for memory leaks over time                    |

---

# Interview Highlights

| Question                                    | Answer                                                                              |
| ------------------------------------------- | ----------------------------------------------------------------------------------- |
| What is virtual memory?                     | A logical memory abstraction that provides each process with its own address space. |
| What is swap?                               | Disk space used as overflow when RAM is insufficient.                               |
| Why does Linux use available RAM for cache? | To improve disk access performance; cache is reclaimed when needed.                 |
| What is the OOM Killer?                     | A kernel mechanism that terminates processes when memory cannot be allocated.       |
| Why can low free memory be normal?          | Linux intentionally uses unused RAM for filesystem caching.                         |

---

# Key Takeaways

| Concept         | Summary                                  |
| --------------- | ---------------------------------------- |
| RAM             | Primary working memory                   |
| Virtual Memory  | Logical address space for processes      |
| Paging          | Memory managed in fixed-size pages       |
| Swap            | Disk-based overflow memory               |
| Cache           | Improves filesystem performance          |
| OOM Killer      | Protects system during memory exhaustion |
| `free -h`       | Quick memory overview                    |
| `/proc/meminfo` | Detailed kernel memory statistics        |

---

# Related Documents

| Document           | Purpose                               |
| ------------------ | ------------------------------------- |
| Linux Overview.md  | Kernel architecture                   |
| Processes.md       | Process execution and lifecycle       |
| File System.md     | Virtual filesystems (`/proc`, `/sys`) |
| Storage.md         | Disks, partitions, and filesystems    |
| Troubleshooting.md | Memory diagnostics                    |
| Cheatsheet.md      | Memory monitoring commands            |
