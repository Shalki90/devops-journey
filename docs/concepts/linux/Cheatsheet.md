# Linux Cheatsheet

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document provides a quick reference for commonly used Linux commands grouped by category.

It is intended for daily system administration, interview preparation, troubleshooting, and rapid revision.

---

# System Information

| Command       | Purpose                               | Example       |
| ------------- | ------------------------------------- | ------------- |
| `uname -a`    | Display kernel and system information | `uname -a`    |
| `hostname`    | Display system hostname               | `hostname`    |
| `hostnamectl` | Display or modify hostname            | `hostnamectl` |
| `date`        | Show current date and time            | `date`        |
| `uptime`      | Show system uptime and load           | `uptime`      |
| `whoami`      | Display current user                  | `whoami`      |
| `id`          | Show user and group IDs               | `id`          |

---

# Navigation

| Command | Purpose                         | Example       |
| ------- | ------------------------------- | ------------- |
| `pwd`   | Print current working directory | `pwd`         |
| `ls`    | List directory contents         | `ls -la`      |
| `cd`    | Change directory                | `cd /var/log` |
| `tree`  | Display directory hierarchy     | `tree`        |

---

# File & Directory Management

| Command    | Purpose                        | Example                |
| ---------- | ------------------------------ | ---------------------- |
| `touch`    | Create an empty file           | `touch notes.txt`      |
| `mkdir`    | Create a directory             | `mkdir projects`       |
| `mkdir -p` | Create nested directories      | `mkdir -p app/config`  |
| `cp`       | Copy files/directories         | `cp file.txt backup/`  |
| `mv`       | Move or rename files           | `mv old.txt new.txt`   |
| `rm`       | Remove files                   | `rm file.txt`          |
| `rm -r`    | Remove directories recursively | `rm -r temp/`          |
| `find`     | Search for files               | `find . -name "*.log"` |
| `locate`   | Quickly find files             | `locate nginx.conf`    |

---

# Viewing File Contents

| Command   | Purpose                        | Example                   |
| --------- | ------------------------------ | ------------------------- |
| `cat`     | Display file contents          | `cat file.txt`            |
| `less`    | View large files interactively | `less /var/log/syslog`    |
| `head`    | Show beginning of a file       | `head -10 file.txt`       |
| `tail`    | Show end of a file             | `tail -20 file.txt`       |
| `tail -f` | Monitor a file in real time    | `tail -f /var/log/syslog` |

---

# Searching & Text Processing

| Command | Purpose                         | Example                      |
| ------- | ------------------------------- | ---------------------------- |
| `grep`  | Search for text patterns        | `grep "error" app.log`       |
| `sort`  | Sort lines                      | `sort names.txt`             |
| `uniq`  | Remove duplicate adjacent lines | `sort file.txt \| uniq`      |
| `wc`    | Count lines, words, characters  | `wc -l file.txt`             |
| `cut`   | Extract fields                  | `cut -d':' -f1 /etc/passwd`  |
| `awk`   | Pattern scanning and processing | `awk '{print $1}' file.txt`  |
| `sed`   | Stream editor                   | `sed 's/old/new/g' file.txt` |

---

# Permissions & Ownership

| Command | Purpose                            | Example                    |
| ------- | ---------------------------------- | -------------------------- |
| `chmod` | Change file permissions            | `chmod 755 script.sh`      |
| `chown` | Change file owner                  | `chown user:user file.txt` |
| `chgrp` | Change file group                  | `chgrp developers app.log` |
| `umask` | Display or set default permissions | `umask 022`                |

---

# User Management

| Command    | Purpose                | Example                         |
| ---------- | ---------------------- | ------------------------------- |
| `useradd`  | Create a user          | `sudo useradd devuser`          |
| `passwd`   | Set or change password | `sudo passwd devuser`           |
| `usermod`  | Modify a user          | `sudo usermod -aG sudo devuser` |
| `userdel`  | Delete a user          | `sudo userdel devuser`          |
| `groupadd` | Create a group         | `sudo groupadd developers`      |
| `groups`   | Display user groups    | `groups`                        |

---

# Process Management

| Command   | Purpose                    | Example        |
| --------- | -------------------------- | -------------- |
| `ps`      | List running processes     | `ps -ef`       |
| `top`     | Real-time process monitor  | `top`          |
| `htop`    | Interactive process viewer | `htop`         |
| `kill`    | Terminate a process        | `kill 1234`    |
| `kill -9` | Force terminate a process  | `kill -9 1234` |
| `pkill`   | Kill by process name       | `pkill nginx`  |
| `jobs`    | View background jobs       | `jobs`         |
| `bg`      | Resume job in background   | `bg %1`        |
| `fg`      | Bring job to foreground    | `fg %1`        |

---

# Services (systemd)

| Command             | Purpose                 | Example                        |
| ------------------- | ----------------------- | ------------------------------ |
| `systemctl status`  | Check service status    | `systemctl status nginx`       |
| `systemctl start`   | Start a service         | `sudo systemctl start nginx`   |
| `systemctl stop`    | Stop a service          | `sudo systemctl stop nginx`    |
| `systemctl restart` | Restart a service       | `sudo systemctl restart nginx` |
| `systemctl enable`  | Enable service at boot  | `sudo systemctl enable nginx`  |
| `systemctl disable` | Disable service at boot | `sudo systemctl disable nginx` |

---

# Memory & Storage

| Command   | Purpose                  | Example           |
| --------- | ------------------------ | ----------------- |
| `free -h` | Display memory usage     | `free -h`         |
| `df -h`   | Show filesystem usage    | `df -h`           |
| `du -sh`  | Show directory size      | `du -sh /var/log` |
| `lsblk`   | List block devices       | `lsblk`           |
| `mount`   | Show mounted filesystems | `mount`           |

---

# Networking

| Command     | Purpose                    | Example                             |
| ----------- | -------------------------- | ----------------------------------- |
| `ip a`      | Show network interfaces    | `ip a`                              |
| `ip route`  | Show routing table         | `ip route`                          |
| `ping`      | Test connectivity          | `ping google.com`                   |
| `ss -tulnp` | Show listening ports       | `ss -tulnp`                         |
| `curl`      | Make HTTP requests         | `curl https://example.com`          |
| `wget`      | Download files             | `wget https://example.com/file.zip` |
| `ssh`       | Connect to a remote system | `ssh user@server`                   |
| `scp`       | Securely copy files        | `scp file.txt user@server:/tmp`     |

---

# Package Management

| Command       | Purpose                       | Example                  |
| ------------- | ----------------------------- | ------------------------ |
| `apt update`  | Update package index          | `sudo apt update`        |
| `apt upgrade` | Upgrade installed packages    | `sudo apt upgrade`       |
| `apt install` | Install package               | `sudo apt install nginx` |
| `apt remove`  | Remove package                | `sudo apt remove nginx`  |
| `yum install` | Install package (RHEL/CentOS) | `sudo yum install nginx` |
| `dnf install` | Install package (Fedora/RHEL) | `sudo dnf install nginx` |

---

# Logs

| Command         | Purpose                 | Example               |
| --------------- | ----------------------- | --------------------- |
| `journalctl`    | View systemd logs       | `journalctl -xe`      |
| `journalctl -u` | View logs for a service | `journalctl -u nginx` |
| `dmesg`         | Display kernel messages | `dmesg`               |

---

# Scheduling

| Command      | Purpose        | Example      |
| ------------ | -------------- | ------------ |
| `crontab -e` | Edit cron jobs | `crontab -e` |
| `crontab -l` | List cron jobs | `crontab -l` |

---

# Common Linux Workflow

| Step                    | Command                 |
| ----------------------- | ----------------------- |
| Check current user      | `whoami`                |
| Check current directory | `pwd`                   |
| List files              | `ls -la`                |
| Navigate                | `cd`                    |
| Create/Edit files       | `touch`, editor         |
| Verify permissions      | `ls -l`                 |
| Monitor processes       | `ps`, `top`             |
| Check logs              | `journalctl`, `tail -f` |
| Check disk & memory     | `df -h`, `free -h`      |

---

# Best Practices

| Practice                                | Benefit                                         |
| --------------------------------------- | ----------------------------------------------- |
| Prefer absolute paths in scripts        | Improves reliability                            |
| Use `sudo` only when required           | Follows the principle of least privilege        |
| Verify commands before using `rm -rf`   | Prevents accidental data loss                   |
| Monitor logs before restarting services | Helps identify root causes                      |
| Learn manual pages (`man`)              | Access authoritative command documentation      |
| Use tab completion                      | Reduces typing errors and improves productivity |

---

# Related Documents

| Document           | Purpose                     |
| ------------------ | --------------------------- |
| README.md          | Sprint overview             |
| Dictionary.md      | Linux terminology           |
| Analogies.md       | Mental models               |
| Interview.md       | Linux interview preparation |
| Troubleshooting.md | Linux debugging guide       |
| `concepts/`        | Detailed Linux concepts     |
