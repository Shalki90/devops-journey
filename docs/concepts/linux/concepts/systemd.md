# systemd

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document explains **systemd**, the default initialization (init) system and service manager for most modern Linux distributions. It covers service management, units, targets, boot dependencies, logging integration, timers, and troubleshooting.

Understanding `systemd` is essential for Linux administration, DevOps, cloud infrastructure, containers, and production troubleshooting.

---

# What is systemd?

**systemd** is the first userspace process started by the Linux kernel.

It always runs as:

```text
PID 1
```

Its primary responsibility is to initialize the operating system and manage all system services throughout the system's lifetime.

---

# Why systemd Exists

systemd provides:

* Fast parallel booting
* Service management
* Dependency resolution
* Logging integration
* Timer management
* Device management
* Resource control
* System state management

---

# Where systemd Fits

```text
Power On
    │
Firmware
    │
GRUB
    │
Linux Kernel
    │
systemd (PID 1)
    │
──────────────────────────────
│        │         │
Network  SSH     Logging
│        │         │
Docker  Cron    Database
│
Applications
```

---

# Responsibilities

| Responsibility        | Description                     |
| --------------------- | ------------------------------- |
| Initialize userspace  | First userspace process         |
| Start services        | Launch system services          |
| Stop services         | Gracefully stop services        |
| Restart services      | Recover failed services         |
| Dependency Management | Start services in correct order |
| Boot Management       | Control boot targets            |
| Logging               | Integrates with journald        |
| Timers                | Alternative to cron             |
| Resource Management   | Control CPU and memory usage    |

---

# Unit Files

systemd manages resources using **Unit Files**.

A unit describes an object managed by systemd.

---

# Common Unit Types

| Unit       | Purpose                    |
| ---------- | -------------------------- |
| `.service` | Background service         |
| `.socket`  | Socket activation          |
| `.target`  | System state               |
| `.mount`   | Mount point                |
| `.timer`   | Scheduled task             |
| `.device`  | Hardware device            |
| `.path`    | Monitor filesystem changes |
| `.swap`    | Swap device                |

---

# Service Lifecycle

```text
Stopped
    │
Start
    │
Running
    │
Restart
    │
Running
    │
Stop
    │
Stopped
```

---

# Managing Services

## Start

```bash
systemctl start nginx
```

---

## Stop

```bash
systemctl stop nginx
```

---

## Restart

```bash
systemctl restart nginx
```

---

## Reload Configuration

```bash
systemctl reload nginx
```

---

## Check Status

```bash
systemctl status nginx
```

---

# Enable vs Start

| Command             | Effect                       |
| ------------------- | ---------------------------- |
| `systemctl start`   | Starts immediately           |
| `systemctl stop`    | Stops immediately            |
| `systemctl restart` | Restarts immediately         |
| `systemctl enable`  | Starts automatically at boot |
| `systemctl disable` | Prevents automatic startup   |

---

# Viewing Services

| Command                     | Purpose              |
| --------------------------- | -------------------- |
| `systemctl list-units`      | Running units        |
| `systemctl list-unit-files` | Installed unit files |
| `systemctl --failed`        | Failed services      |

---

# Service States

| State        | Meaning                      |
| ------------ | ---------------------------- |
| active       | Running correctly            |
| inactive     | Stopped                      |
| failed       | Service encountered an error |
| activating   | Starting                     |
| deactivating | Stopping                     |

---

# Targets

Targets define the desired operating state of the system.

| Target              | Purpose        |
| ------------------- | -------------- |
| `poweroff.target`   | Shut down      |
| `rescue.target`     | Recovery mode  |
| `multi-user.target` | Multi-user CLI |
| `graphical.target`  | GUI mode       |
| `reboot.target`     | Restart        |

View current target:

```bash
systemctl get-default
```

Change default target:

```bash
systemctl set-default multi-user.target
```

---

# Unit Dependencies

systemd starts services based on dependencies.

Example:

```text
Network
    │
SSH
    │
Docker
    │
Application
```

Common dependency directives:

| Directive   | Meaning                   |
| ----------- | ------------------------- |
| `Requires=` | Hard dependency           |
| `Wants=`    | Soft dependency           |
| `After=`    | Start after another unit  |
| `Before=`   | Start before another unit |

---

# Journald Integration

systemd includes its own logging service:

```text
systemd-journald
```

Useful commands:

| Command               | Purpose            |
| --------------------- | ------------------ |
| `journalctl`          | View all logs      |
| `journalctl -b`       | Current boot logs  |
| `journalctl -u nginx` | Logs for a service |
| `journalctl -xe`      | Recent errors      |

---

# Boot Analysis

Measure boot performance:

```bash
systemd-analyze
```

Identify slow services:

```bash
systemd-analyze blame
```

Critical startup chain:

```bash
systemd-analyze critical-chain
```

---

# Timers

Timers are the systemd alternative to `cron`.

Advantages:

* Dependency aware
* Better logging
* Integrated with systemd
* Supports missed executions after downtime

---

# Common Troubleshooting

| Problem                      | Investigation                 | Resolution                        |
| ---------------------------- | ----------------------------- | --------------------------------- |
| Service won't start          | `systemctl status`            | Review status and dependencies    |
| Service repeatedly fails     | `journalctl -u service`       | Check logs and configuration      |
| Slow boot                    | `systemd-analyze blame`       | Optimize or disable slow services |
| Service not starting at boot | `systemctl is-enabled`        | Enable the service                |
| Dependency failure           | `systemctl list-dependencies` | Resolve missing dependency        |

---

# Best Practices

| Practice                                             | Benefit                             |
| ---------------------------------------------------- | ----------------------------------- |
| Use `systemctl` instead of legacy `service` commands | Modern and consistent management    |
| Review logs with `journalctl`                        | Faster troubleshooting              |
| Enable only required services                        | Reduce boot time and attack surface |
| Prefer timers over cron for systemd-managed tasks    | Better integration and logging      |
| Understand service dependencies                      | Prevent startup failures            |

---

# Common Mistakes

| Mistake                               | Better Practice                                              |
| ------------------------------------- | ------------------------------------------------------------ |
| Confusing `start` with `enable`       | Remember: `start` affects now; `enable` affects future boots |
| Killing services directly with `kill` | Use `systemctl stop` when appropriate                        |
| Ignoring failed services              | Investigate using `systemctl status` and `journalctl`        |
| Editing unit files without reloading  | Run `systemctl daemon-reload` after changes                  |
| Disabling essential services          | Verify dependencies before disabling units                   |

---

# Interview Highlights

| Question                                  | Answer                                                                           |
| ----------------------------------------- | -------------------------------------------------------------------------------- |
| What is systemd?                          | The init system and service manager used by most modern Linux distributions.     |
| Why is PID 1 important?                   | It is the first userspace process and manages the entire system lifecycle.       |
| Difference between `start` and `enable`?  | `start` launches a service immediately; `enable` configures it to start at boot. |
| What is a unit file?                      | A configuration file describing an object managed by systemd.                    |
| How do you troubleshoot a failed service? | Use `systemctl status` and `journalctl -u <service>`.                            |

---

# Key Takeaways

| Concept    | Summary                           |
| ---------- | --------------------------------- |
| systemd    | Init system and service manager   |
| PID 1      | First userspace process           |
| Unit       | Object managed by systemd         |
| Service    | Background process                |
| Target     | Desired system state              |
| journalctl | View systemd logs                 |
| systemctl  | Manage services and units         |
| Timer      | Scheduled task managed by systemd |

---

# Related Documents

| Document            | Purpose                                      |
| ------------------- | -------------------------------------------- |
| Boot Process.md     | How Linux starts                             |
| Processes.md        | Process lifecycle                            |
| Logging.md          | System and application logs                  |
| Scheduling.md       | Cron and systemd timers                      |
| Networking.md       | Services dependent on networking             |
| Linux for DevOps.md | systemd in cloud and production environments |
