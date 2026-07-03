# Linux Troubleshooting

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document provides a structured methodology for diagnosing and resolving common Linux system issues.

Rather than memorizing commands, the goal is to develop a systematic troubleshooting approach that can be applied to production servers, cloud instances, containers, and virtual machines.

---

# Troubleshooting Workflow

| Step | Question                 | Common Commands                      |
| ---- | ------------------------ | ------------------------------------ |
| 1    | What is the symptom?     | Observe error messages and logs      |
| 2    | Is the system reachable? | `ping`, `ssh`                        |
| 3    | Is the service running?  | `systemctl status`                   |
| 4    | Are resources healthy?   | `top`, `free -h`, `df -h`            |
| 5    | What do the logs say?    | `journalctl`, `tail -f`              |
| 6    | What changed recently?   | Configuration, packages, deployments |
| 7    | Verify the fix           | Re-test and monitor                  |

---

# System Health

| Problem           | Possible Cause                       | Resolution                              |
| ----------------- | ------------------------------------ | --------------------------------------- |
| System is slow    | High CPU, memory pressure, disk I/O  | Check `top`, `htop`, `vmstat`, `iostat` |
| High load average | Too many runnable processes          | Identify CPU-intensive processes        |
| System freezing   | Memory exhaustion or hardware issues | Review memory usage and kernel logs     |
| Frequent crashes  | Kernel panic or failing hardware     | Inspect `journalctl` and `dmesg`        |

---

# Filesystem Issues

| Problem              | Possible Cause               | Resolution                                 |
| -------------------- | ---------------------------- | ------------------------------------------ |
| Disk full            | Large logs or unused files   | `df -h`, `du -sh`, remove unnecessary data |
| Cannot create files  | No disk space or permissions | Verify storage and ownership               |
| File not found       | Incorrect path               | Check with `pwd`, `ls`, `find`             |
| Read-only filesystem | Filesystem mounted read-only | Check mount status and system logs         |

---

# Permissions Issues

| Problem                    | Possible Cause                         | Resolution                                           |
| -------------------------- | -------------------------------------- | ---------------------------------------------------- |
| Permission denied          | Missing read/write/execute permissions | Review with `ls -l`; adjust using `chmod` or `chown` |
| Cannot execute script      | Execute bit missing                    | `chmod +x script.sh`                                 |
| Access denied to directory | Incorrect ownership or permissions     | Verify owner, group, and permissions                 |

---

# User & Authentication Issues

| Problem            | Possible Cause                                   | Resolution                                             |
| ------------------ | ------------------------------------------------ | ------------------------------------------------------ |
| Cannot log in      | Incorrect password or locked account             | Verify credentials and account status                  |
| `sudo` not working | User not in sudo group                           | Check group membership                                 |
| SSH login fails    | SSH service down, firewall, authentication issue | Check `systemctl status ssh`, logs, and firewall rules |

---

# Process Issues

| Problem                    | Possible Cause                               | Resolution                                       |
| -------------------------- | -------------------------------------------- | ------------------------------------------------ |
| Process consuming high CPU | Infinite loop or heavy workload              | Inspect using `top`, `ps`; optimize or terminate |
| High memory usage          | Memory leak or excessive workload            | Review `free -h` and process memory usage        |
| Zombie processes           | Parent process has not collected exit status | Restart or investigate the parent process        |
| Process not terminating    | Hung process                                 | Use `kill`, then `kill -9` only if necessary     |

---

# Service Issues

| Problem                      | Possible Cause                    | Resolution                                   |
| ---------------------------- | --------------------------------- | -------------------------------------------- |
| Service failed to start      | Configuration or dependency issue | Check `systemctl status` and `journalctl -u` |
| Service starts then stops    | Runtime error                     | Inspect logs and application configuration   |
| Service not starting at boot | Not enabled                       | `systemctl enable <service>`                 |

---

# Networking Issues

| Problem                     | Possible Cause                           | Resolution                                   |
| --------------------------- | ---------------------------------------- | -------------------------------------------- |
| Cannot reach another server | Network, routing, firewall, DNS          | Use `ping`, `ip a`, `ip route`, `traceroute` |
| DNS resolution fails        | Incorrect DNS configuration              | Verify `/etc/resolv.conf`                    |
| Port not listening          | Service not running                      | Check with `ss -tulnp`                       |
| SSH connection refused      | SSH service stopped or firewall blocking | Verify service and firewall configuration    |

---

# Package Management Issues

| Problem                    | Possible Cause           | Resolution                                  |
| -------------------------- | ------------------------ | ------------------------------------------- |
| Package installation fails | Repository unavailable   | Update repositories and verify connectivity |
| Dependency errors          | Missing packages         | Install required dependencies               |
| Repository errors          | Misconfigured repository | Verify repository configuration             |

---

# Log Analysis

| Command                   | Purpose                           |
| ------------------------- | --------------------------------- |
| `journalctl`              | View system logs                  |
| `journalctl -u nginx`     | View logs for a specific service  |
| `tail -f /var/log/syslog` | Monitor log file in real time     |
| `dmesg`                   | Display kernel messages           |
| `grep ERROR logfile`      | Search logs for specific patterns |

---

# Performance Investigation

| Resource  | Commands                    |
| --------- | --------------------------- |
| CPU       | `top`, `htop`, `uptime`     |
| Memory    | `free -h`, `vmstat`         |
| Disk      | `df -h`, `du -sh`, `lsblk`  |
| Network   | `ip a`, `ss -tulnp`, `ping` |
| Processes | `ps -ef`, `top`, `pgrep`    |

---

# Common Error Messages

| Error                       | Meaning                           | Resolution                         |
| --------------------------- | --------------------------------- | ---------------------------------- |
| `Permission denied`         | Insufficient privileges           | Check permissions and ownership    |
| `No such file or directory` | Incorrect path or missing file    | Verify the file path               |
| `Disk quota exceeded`       | Storage limit reached             | Free space or increase quota       |
| `Connection refused`        | Service unavailable or blocked    | Verify service status and firewall |
| `Command not found`         | Command unavailable or PATH issue | Install package or update PATH     |

---

# Debugging Checklist

| Check               | Command            |
| ------------------- | ------------------ |
| Current user        | `whoami`           |
| Current directory   | `pwd`              |
| Running processes   | `ps -ef`           |
| CPU usage           | `top`              |
| Memory usage        | `free -h`          |
| Disk usage          | `df -h`            |
| Mounted filesystems | `mount`            |
| Network interfaces  | `ip a`             |
| Open ports          | `ss -tulnp`        |
| System logs         | `journalctl`       |
| Kernel logs         | `dmesg`            |
| Service status      | `systemctl status` |

---

# Best Practices

| Practice                              | Benefit                                     |
| ------------------------------------- | ------------------------------------------- |
| Read the complete error message       | Prevents incorrect assumptions              |
| Check logs before restarting services | Identifies root cause                       |
| Investigate before killing processes  | Avoids unnecessary downtime                 |
| Verify permissions first              | Resolves many access-related issues quickly |
| Make one change at a time             | Simplifies root cause analysis              |
| Document the issue and resolution     | Builds reusable operational knowledge       |

---

# Troubleshooting Mindset

| Principle             | Explanation                                                          |
| --------------------- | -------------------------------------------------------------------- |
| Observe before acting | Gather evidence before making changes                                |
| Verify assumptions    | Confirm facts rather than guessing                                   |
| Start simple          | Eliminate basic causes before investigating complex ones             |
| Isolate the problem   | Narrow the scope systematically                                      |
| Confirm the fix       | Ensure the issue is fully resolved and no new issues were introduced |

---

# Related Documents

| Document      | Purpose                     |
| ------------- | --------------------------- |
| README.md     | Sprint overview             |
| Dictionary.md | Linux terminology           |
| Analogies.md  | Mental models               |
| Cheatsheet.md | Linux command reference     |
| Interview.md  | Linux interview preparation |
| `concepts/`   | Detailed Linux concepts     |
| `labs/`       | Hands-on Linux exercises    |
