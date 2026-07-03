# Performance Monitoring

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document explains how to monitor and troubleshoot Linux system performance. It covers CPU, memory, disk, filesystem, I/O, processes, networking, load averages, monitoring tools, and common troubleshooting workflows.

Performance monitoring is a core Linux administration and DevOps skill used to diagnose bottlenecks, optimize systems, and maintain production reliability.

---

# What is Performance Monitoring?

Performance monitoring is the continuous observation and analysis of system resources to ensure efficient operation.

It helps administrators:

* Identify bottlenecks
* Detect abnormal resource usage
* Troubleshoot production issues
* Optimize applications
* Maintain system stability
* Plan capacity upgrades

---

# Linux Performance Architecture

```text
                Linux System
                     │
 ┌───────────┬───────────┬───────────┬───────────┐
 │           │           │           │
CPU       Memory      Storage     Network
 │           │           │           │
Processes  Cache      Filesystem  Interfaces
                     │
                 Monitoring Tools
```

---

# Resources to Monitor

| Resource     | Why It Matters              |
| ------------ | --------------------------- |
| CPU          | Processing power            |
| Memory       | RAM utilization             |
| Disk         | Capacity and usage          |
| Disk I/O     | Read/write performance      |
| Network      | Connectivity and throughput |
| Processes    | Resource consumption        |
| Filesystem   | Storage health              |
| Load Average | Overall system workload     |

---

# CPU Monitoring

Useful commands:

| Command  | Purpose                    |
| -------- | -------------------------- |
| `top`    | Real-time CPU usage        |
| `htop`   | Interactive process viewer |
| `mpstat` | CPU statistics             |
| `lscpu`  | CPU information            |
| `uptime` | Load averages              |

Example:

```bash
top
```

---

# Understanding CPU Usage

CPU time is commonly divided into:

| Metric   | Description                 |
| -------- | --------------------------- |
| User     | Application execution       |
| System   | Kernel execution            |
| Idle     | CPU not in use              |
| I/O Wait | Waiting for disk operations |
| Nice     | Low-priority processes      |

---

# Load Average

Load average represents the number of runnable or waiting tasks.

Example:

```bash
uptime
```

Output:

```text
load average: 0.42, 0.35, 0.30
```

Values represent:

| Interval   | Meaning            |
| ---------- | ------------------ |
| 1 minute   | Immediate workload |
| 5 minutes  | Short-term trend   |
| 15 minutes | Long-term trend    |

---

# Memory Monitoring

Useful commands:

| Command             | Purpose                     |
| ------------------- | --------------------------- |
| `free -h`           | Memory usage                |
| `vmstat`            | Virtual memory statistics   |
| `top`               | Process memory              |
| `cat /proc/meminfo` | Detailed memory information |

Example:

```bash
free -h
```

---

# Memory Layout

```text
RAM
├── Kernel
├── Running Processes
├── Buffers
├── Cache
└── Free Memory
```

---

# Swap

Swap is disk space used when RAM becomes insufficient.

View swap usage:

```bash
swapon --show
```

or

```bash
free -h
```

---

# Process Monitoring

Useful commands:

| Command  | Purpose                |
| -------- | ---------------------- |
| `ps aux` | List running processes |
| `top`    | Real-time monitoring   |
| `htop`   | Interactive monitoring |
| `pidof`  | Find process ID        |
| `pgrep`  | Search processes       |

---

# Disk Usage

Check filesystem utilization:

```bash
df -h
```

Example:

| Command  | Purpose          |
| -------- | ---------------- |
| `df -h`  | Filesystem usage |
| `du -sh` | Directory usage  |
| `lsblk`  | Block devices    |

---

# Disk I/O

Disk I/O measures storage performance.

Useful commands:

| Command  | Purpose             |
| -------- | ------------------- |
| `iostat` | Disk statistics     |
| `iotop`  | Disk I/O by process |
| `vmstat` | System activity     |

---

# Network Monitoring

Useful commands:

| Command      | Purpose               |
| ------------ | --------------------- |
| `ip addr`    | Interface information |
| `ss -tulpn`  | Active sockets        |
| `ping`       | Connectivity          |
| `sar -n DEV` | Network statistics    |
| `iftop`      | Bandwidth usage       |

---

# Filesystem Monitoring

Monitor:

* Free space
* Inode usage
* Mount points
* Read/write errors

Useful commands:

```bash
df -i
```

```bash
mount
```

---

# System Information

Useful commands:

| Command       | Purpose            |
| ------------- | ------------------ |
| `hostnamectl` | System information |
| `uname -a`    | Kernel version     |
| `uptime`      | Uptime and load    |
| `date`        | System time        |

---

# Monitoring Workflow

```text
User Reports Issue
        │
Identify Symptoms
        │
CPU?
Memory?
Disk?
Network?
        │
Investigate
        │
Locate Bottleneck
        │
Resolve
        │
Verify
```

---

# Useful Monitoring Commands

| Command     | Purpose                |
| ----------- | ---------------------- |
| `top`       | Overall system usage   |
| `htop`      | Interactive monitoring |
| `free -h`   | Memory                 |
| `df -h`     | Disk usage             |
| `du -sh`    | Directory usage        |
| `vmstat`    | Virtual memory         |
| `iostat`    | Disk performance       |
| `uptime`    | Load average           |
| `ps aux`    | Processes              |
| `ss -tulpn` | Network sockets        |

---

# Common Troubleshooting

| Problem               | Investigation         | Resolution                                                   |
| --------------------- | --------------------- | ------------------------------------------------------------ |
| High CPU usage        | `top`, `htop`         | Identify and optimize busy processes                         |
| High memory usage     | `free`, `ps`, `top`   | Locate memory-intensive applications                         |
| Disk full             | `df`, `du`            | Remove unnecessary files or expand storage                   |
| Slow disk performance | `iostat`, `iotop`     | Investigate I/O bottlenecks                                  |
| Network slowdown      | `ss`, `ping`, `iftop` | Verify connectivity and bandwidth usage                      |
| High load average     | `uptime`, `top`       | Determine whether CPU, memory, or I/O is the limiting factor |

---

# Best Practices

| Practice                                  | Benefit                        |
| ----------------------------------------- | ------------------------------ |
| Monitor systems regularly                 | Detect issues early            |
| Establish performance baselines           | Simplify anomaly detection     |
| Monitor trends instead of isolated values | Better long-term analysis      |
| Investigate root causes                   | Prevent recurring problems     |
| Automate monitoring where appropriate     | Improve operational efficiency |

---

# Common Mistakes

| Mistake                                  | Better Practice                               |
| ---------------------------------------- | --------------------------------------------- |
| Assuming high memory usage is always bad | Consider Linux page cache behavior            |
| Ignoring load average                    | Review it alongside CPU and I/O metrics       |
| Looking at only one metric               | Correlate CPU, memory, disk, and network data |
| Reacting to short-lived spikes           | Analyze sustained trends                      |
| Forgetting historical data               | Compare with normal system behavior           |

---

# Interview Highlights

| Question                                    | Answer                                                                     |
| ------------------------------------------- | -------------------------------------------------------------------------- |
| What does load average represent?           | The average number of runnable or waiting tasks over 1, 5, and 15 minutes. |
| Which command shows memory usage?           | `free -h`.                                                                 |
| Which command displays real-time processes? | `top` or `htop`.                                                           |
| How do you check disk usage?                | `df -h`.                                                                   |
| How do you identify disk I/O bottlenecks?   | Use `iostat` or `iotop`.                                                   |

---

# Key Takeaways

| Concept              | Summary                               |
| -------------------- | ------------------------------------- |
| CPU Monitoring       | Observe processor utilization         |
| Memory Monitoring    | Track RAM and swap usage              |
| Disk Monitoring      | Monitor storage capacity              |
| Disk I/O             | Measure storage performance           |
| Load Average         | Measure system workload               |
| Process Monitoring   | Identify resource-intensive processes |
| Network Monitoring   | Monitor interfaces and traffic        |
| Performance Baseline | Reference point for healthy operation |

---

# Related Documents

| Document             | Purpose                                           |
| -------------------- | ------------------------------------------------- |
| Processes.md         | Understanding running processes                   |
| Memory Management.md | Memory architecture                               |
| Storage.md           | Storage devices and filesystems                   |
| Logging.md           | Correlating performance with logs                 |
| Networking.md        | Network diagnostics                               |
| Linux for DevOps.md  | Performance monitoring in production environments |
