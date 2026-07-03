# Scheduling

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document explains how Linux schedules automated tasks using **cron**, **at**, and **systemd timers**. It covers scheduling concepts, configuration files, common commands, scheduling syntax, troubleshooting, and best practices.

Scheduling is fundamental for automation, system maintenance, backups, monitoring, DevOps pipelines, and production operations.

---

# What is Scheduling?

Scheduling is the process of automatically executing commands or scripts at predefined times or intervals.

Instead of manually running repetitive tasks, Linux uses schedulers to automate them.

Typical scheduled tasks include:

* Backups
* Log rotation
* Database maintenance
* System updates
* Monitoring scripts
* Report generation

---

# Scheduling Components

```text
Administrator
       │
       ▼
Scheduler
       │
────────┼────────
│       │       │
cron     at   systemd Timer
│       │       │
Execute Commands / Scripts
```

---

# Linux Scheduling Options

| Scheduler     | Purpose            | Typical Use                   |
| ------------- | ------------------ | ----------------------------- |
| cron          | Recurring tasks    | Daily backups, cleanup jobs   |
| at            | One-time execution | Run a command later           |
| systemd Timer | Modern scheduler   | Service-aware scheduled tasks |

---

# cron

`cron` is the traditional Linux scheduler used to execute recurring tasks.

The daemon responsible for running cron jobs is:

```text
crond
```

or

```text
cron
```

(depending on the Linux distribution)

---

# cron Architecture

```text
crond
   │
Read Crontab
   │
Time Matches?
   │
Execute Command
```

---

# Crontab

Each user can have a personal schedule.

View current crontab:

```bash
crontab -l
```

Edit crontab:

```bash
crontab -e
```

Remove crontab:

```bash
crontab -r
```

---

# Crontab Format

```text
* * * * * command
│ │ │ │ │
│ │ │ │ └── Day of Week (0-7)
│ │ │ └──── Month
│ │ └────── Day of Month
│ └──────── Hour
└────────── Minute
```

---

# Common cron Examples

| Schedule                 | Expression  |
| ------------------------ | ----------- |
| Every minute             | `* * * * *` |
| Every hour               | `0 * * * *` |
| Daily at midnight        | `0 0 * * *` |
| Every Sunday             | `0 0 * * 0` |
| Every Monday at 08:00    | `0 8 * * 1` |
| First day of every month | `0 0 1 * *` |

---

# Example cron Job

```text
0 2 * * * /home/user/backup.sh
```

Runs the backup script every day at **02:00 AM**.

---

# System Crontab

System-wide configuration:

```text
/etc/crontab
```

Additional scheduled jobs:

```text
/etc/cron.daily/

/etc/cron.weekly/

/etc/cron.monthly/

/etc/cron.hourly/
```

---

# at

`at` schedules a command to run **once** at a specified time.

Schedule a task:

```bash
at 14:00
```

List scheduled jobs:

```bash
atq
```

Remove a scheduled job:

```bash
atrm <job-id>
```

---

# systemd Timers

Modern Linux distributions support scheduling through **systemd timers**.

Advantages over cron:

* Dependency-aware
* Better logging
* Integrated with systemd
* Can recover missed executions after reboot

---

# systemd Timer Architecture

```text
Timer Unit
      │
      ▼
systemd
      │
      ▼
Service Unit
      │
      ▼
Application
```

---

# Timer Components

| Component  | Purpose                     |
| ---------- | --------------------------- |
| `.timer`   | Defines the schedule        |
| `.service` | Defines the task to execute |

---

# Managing Timers

List timers:

```bash
systemctl list-timers
```

Start a timer:

```bash
systemctl start backup.timer
```

Enable a timer:

```bash
systemctl enable backup.timer
```

Check status:

```bash
systemctl status backup.timer
```

---

# Comparing Scheduling Methods

| Feature               | cron    | at      | systemd Timer |
| --------------------- | ------- | ------- | ------------- |
| Recurring Tasks       | Yes     | No      | Yes           |
| One-Time Tasks        | No      | Yes     | Possible      |
| Dependency Management | No      | No      | Yes           |
| Integrated Logging    | Limited | Limited | Yes           |
| Service Integration   | No      | No      | Yes           |

---

# Common Commands

| Command                 | Purpose                   |
| ----------------------- | ------------------------- |
| `crontab -e`            | Edit user cron jobs       |
| `crontab -l`            | List cron jobs            |
| `crontab -r`            | Remove cron jobs          |
| `at`                    | Schedule one-time task    |
| `atq`                   | List scheduled `at` jobs  |
| `atrm`                  | Remove scheduled `at` job |
| `systemctl list-timers` | List systemd timers       |

---

# Common Troubleshooting

| Problem                               | Investigation                | Resolution                                |
| ------------------------------------- | ---------------------------- | ----------------------------------------- |
| Cron job not running                  | Verify crontab entry         | Check syntax and logs                     |
| Script works manually but not in cron | Review environment variables | Use absolute paths and required variables |
| Timer not starting                    | `systemctl status`           | Verify timer and service configuration    |
| Incorrect execution time              | Check timezone               | Verify system clock and timezone          |
| Permission denied                     | Check script permissions     | Ensure the script is executable           |

---

# Best Practices

| Practice                                | Benefit                        |
| --------------------------------------- | ------------------------------ |
| Use absolute paths in scheduled jobs    | Avoid path resolution issues   |
| Redirect output to log files            | Simplify troubleshooting       |
| Test scripts manually before scheduling | Catch errors early             |
| Prefer systemd timers on modern systems | Better integration and logging |
| Keep scheduled tasks documented         | Easier maintenance             |

---

# Common Mistakes

| Mistake                                                         | Better Practice                                  |
| --------------------------------------------------------------- | ------------------------------------------------ |
| Assuming cron uses the same environment as an interactive shell | Define required environment variables explicitly |
| Using relative paths                                            | Always use absolute paths                        |
| Ignoring script permissions                                     | Ensure scripts are executable                    |
| Scheduling overlapping jobs                                     | Consider execution time and concurrency          |
| Forgetting to monitor scheduled jobs                            | Review logs regularly                            |

---

# Interview Highlights

| Question                                        | Answer                                                                      |
| ----------------------------------------------- | --------------------------------------------------------------------------- |
| What is cron?                                   | A scheduler for recurring tasks in Linux.                                   |
| What is the difference between `cron` and `at`? | `cron` runs recurring tasks; `at` runs a task once.                         |
| What are systemd timers?                        | A modern scheduling mechanism integrated with systemd services.             |
| Where are system-wide cron jobs configured?     | `/etc/crontab` and `/etc/cron.*` directories.                               |
| Why use absolute paths in cron jobs?            | Cron runs with a minimal environment and may not locate commands in `PATH`. |

---

# Key Takeaways

| Concept        | Summary                                  |
| -------------- | ---------------------------------------- |
| cron           | Traditional recurring scheduler          |
| at             | One-time task scheduler                  |
| systemd Timer  | Modern scheduler integrated with systemd |
| Crontab        | User scheduling configuration            |
| `/etc/crontab` | System-wide schedule                     |
| `.timer`       | systemd scheduling unit                  |
| `.service`     | Task executed by a timer                 |

---

# Related Documents

| Document                  | Purpose                                          |
| ------------------------- | ------------------------------------------------ |
| systemd.md                | Managing systemd timers                          |
| Bash Scripting.md         | Scripts executed by schedulers                   |
| Logging.md                | Monitoring scheduled task output                 |
| Environment Variables.md  | Environment available to scheduled jobs          |
| Performance Monitoring.md | Monitoring long-running scheduled tasks          |
| Linux for DevOps.md       | Scheduling automation in production environments |
