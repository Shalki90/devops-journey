# Processes

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document explains how Linux executes programs through processes, how the kernel schedules them, how processes communicate with one another, and how administrators monitor and manage running processes.

Understanding processes is fundamental to Linux administration, troubleshooting, Docker, Kubernetes, and modern DevOps practices.

---

# What is a Process?

A **process** is a running instance of a program.

When a program is executed, the Linux kernel creates a process, allocates resources, assigns it a Process ID (PID), and schedules it for execution.

> **Program:** Static executable stored on disk
> **Process:** Active execution of that program in memory

---

# Program vs Process

| Program                     | Process                   |
| --------------------------- | ------------------------- |
| Stored on disk              | Running in memory         |
| Passive                     | Active                    |
| No CPU usage                | Uses CPU resources        |
| No PID                      | Assigned a PID            |
| Can exist without execution | Exists only while running |

---

# Process Lifecycle

```text
Program
   │
Execute
   │
Created
   │
Ready
   │
Running
   │
Waiting / Sleeping
   │
Running Again
   │
Terminated
```

---

# Process States

| State                     | Description                                                             |
| ------------------------- | ----------------------------------------------------------------------- |
| Running (R)               | Currently executing on a CPU                                            |
| Sleeping (S)              | Waiting for an event or resource                                        |
| Uninterruptible Sleep (D) | Waiting for I/O completion                                              |
| Stopped (T)               | Execution paused                                                        |
| Zombie (Z)                | Process finished execution but parent has not collected its exit status |

---

# Process Architecture

```text
Application
      │
Shell
      │
fork()
      │
exec()
      │
Linux Kernel
      │
Running Process
```

---

# Process Identifiers

Every process has unique identifiers.

| Identifier | Purpose                           |
| ---------- | --------------------------------- |
| PID        | Process Identifier                |
| PPID       | Parent Process Identifier         |
| UID        | User that owns the process        |
| GID        | Group associated with the process |

---

# Parent and Child Processes

Processes create other processes.

```text
systemd (PID 1)
        │
        ├── sshd
        │      └── bash
        │             └── vim
        │
        └── nginx
```

| Process        | Description                |
| -------------- | -------------------------- |
| Parent Process | Creates another process    |
| Child Process  | Created by another process |

---

# Process Creation

Linux primarily uses two system calls.

| System Call | Purpose                                                 |
| ----------- | ------------------------------------------------------- |
| `fork()`    | Creates a new child process                             |
| `exec()`    | Replaces the current process image with another program |

---

# Process Scheduling

The Linux scheduler determines which process gets CPU time.

Goals include:

* Fair CPU allocation
* High responsiveness
* Efficient multitasking
* Maximum CPU utilization

---

# Context Switching

A **context switch** occurs when the CPU stops executing one process and begins executing another.

The kernel saves the current process state and restores the next process.

Although necessary, excessive context switching introduces overhead.

---

# Foreground vs Background Processes

| Foreground              | Background                            |
| ----------------------- | ------------------------------------- |
| Interacts with the user | Runs independently                    |
| Blocks the terminal     | Terminal remains usable               |
| Started normally        | Started using `&` or moved using `bg` |

Example:

```bash
python app.py &
```

---

# Viewing Processes

| Command  | Purpose                    |
| -------- | -------------------------- |
| `ps`     | Display running processes  |
| `ps -ef` | Detailed process list      |
| `top`    | Real-time process monitor  |
| `htop`   | Interactive process viewer |
| `pstree` | Display process hierarchy  |
| `pgrep`  | Find processes by name     |

---

# Process Management

| Command           | Purpose                        |
| ----------------- | ------------------------------ |
| `kill PID`        | Send a signal to a process     |
| `kill -9 PID`     | Forcefully terminate a process |
| `pkill process`   | Kill by process name           |
| `killall process` | Kill all matching processes    |

---

# Linux Signals

Signals allow processes to communicate.

| Signal  | Number | Purpose                                     |
| ------- | ------ | ------------------------------------------- |
| SIGTERM | 15     | Gracefully terminate a process              |
| SIGKILL | 9      | Forcefully terminate a process              |
| SIGINT  | 2      | Interrupt (`Ctrl + C`)                      |
| SIGHUP  | 1      | Reload configuration or terminal disconnect |
| SIGSTOP | 19     | Pause a process                             |
| SIGCONT | 18     | Resume a paused process                     |

---

# Zombie Processes

A zombie process has:

* Completed execution
* Released most resources
* Parent has not collected its exit status

Characteristics:

* Does not consume CPU
* Occupies a PID
* Usually indicates poor process cleanup

---

# Orphan Processes

An orphan process is one whose parent process has terminated.

Linux automatically reassigns orphan processes to **PID 1 (`systemd` or `init`)**, which later collects their exit status.

---

# Process Priority

Linux assigns priorities to processes.

| Value             | Description                         |
| ----------------- | ----------------------------------- |
| Nice Value        | User-controlled scheduling priority |
| Lower nice value  | Higher priority                     |
| Higher nice value | Lower priority                      |

Useful commands:

| Command  | Purpose                              |
| -------- | ------------------------------------ |
| `nice`   | Start a process with a priority      |
| `renice` | Change priority of a running process |

---

# Jobs

Jobs are shell-managed background tasks.

| Command | Purpose                        |
| ------- | ------------------------------ |
| `jobs`  | List background jobs           |
| `bg`    | Resume a job in the background |
| `fg`    | Bring a job to the foreground  |

---

# Resource Monitoring

| Resource          | Commands         |
| ----------------- | ---------------- |
| CPU               | `top`, `htop`    |
| Memory            | `free -h`, `top` |
| Process Tree      | `pstree`         |
| Running Processes | `ps -ef`         |
| Open Files        | `lsof`           |

---

# Common Troubleshooting Scenarios

| Problem                    | Investigation                    | Resolution                                     |
| -------------------------- | -------------------------------- | ---------------------------------------------- |
| High CPU usage             | `top`, `ps`                      | Optimize or terminate the offending process    |
| High memory usage          | `free -h`, `top`                 | Investigate memory leaks or increase resources |
| Zombie processes           | `ps -el`                         | Identify and restart or fix the parent process |
| Service not responding     | `systemctl status`, `journalctl` | Review logs and restart if necessary           |
| Process repeatedly crashes | Check logs and exit codes        | Resolve configuration or application errors    |

---

# Best Practices

| Practice                                                 | Benefit                            |
| -------------------------------------------------------- | ---------------------------------- |
| Use `SIGTERM` before `SIGKILL`                           | Allows graceful shutdown           |
| Monitor long-running processes                           | Detect performance issues early    |
| Understand parent-child relationships                    | Simplifies troubleshooting         |
| Investigate resource spikes before terminating processes | Prevents masking underlying issues |
| Monitor process trees in production                      | Improves system visibility         |

---

# Interview Highlights

| Question                                            | Answer                                                                      |
| --------------------------------------------------- | --------------------------------------------------------------------------- |
| What is a process?                                  | A running instance of a program.                                            |
| Difference between a program and a process?         | A program is stored on disk; a process is executing in memory.              |
| What is PID?                                        | A unique identifier assigned to every running process.                      |
| What is the difference between SIGTERM and SIGKILL? | SIGTERM requests graceful termination; SIGKILL immediately stops a process. |
| What is a zombie process?                           | A terminated process whose parent has not yet collected its exit status.    |
| What is an orphan process?                          | A process whose parent exited; it is adopted by PID 1.                      |

---

# Key Takeaways

| Concept        | Summary                                 |
| -------------- | --------------------------------------- |
| Process        | Running program                         |
| PID            | Process identifier                      |
| PPID           | Parent process identifier               |
| Scheduler      | Allocates CPU time                      |
| Context Switch | CPU changes from one process to another |
| Signal         | Mechanism for process communication     |
| Zombie         | Terminated process awaiting cleanup     |
| Orphan         | Parent terminated; adopted by PID 1     |

---

# Related Documents

| Document             | Purpose                        |
| -------------------- | ------------------------------ |
| Linux Overview.md    | Linux architecture             |
| Shell.md             | Command execution              |
| Systemd.md           | Service and process management |
| Memory Management.md | Process memory allocation      |
| Troubleshooting.md   | Process diagnostics            |
| Cheatsheet.md        | Process management commands    |
