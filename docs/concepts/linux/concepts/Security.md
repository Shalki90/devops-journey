# Security

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document explains Linux security fundamentals, including authentication, authorization, file permissions, privilege escalation, firewalls, SELinux/AppArmor, auditing, software updates, and security best practices.

Understanding Linux security is essential for system administration, DevOps, cloud infrastructure, production operations, and compliance.

---

# What is Linux Security?

Linux security is the practice of protecting a Linux system against unauthorized access, misuse, privilege escalation, malware, and data loss while maintaining system availability and integrity.

Linux security follows the principle of **Defense in Depth**, where multiple security layers work together.

---

# Security Architecture

```text
Users
   │
Authentication
   │
Authorization
   │
Permissions
   │
Kernel Security
   │
Applications
   │
Logging & Auditing
```

---

# Core Security Principles

| Principle            | Description                                       |
| -------------------- | ------------------------------------------------- |
| Least Privilege      | Grant only the minimum required permissions       |
| Defense in Depth     | Multiple independent security layers              |
| Separation of Duties | Divide responsibilities between users and systems |
| Secure Defaults      | Default configuration should be secure            |
| Regular Updates      | Apply security patches promptly                   |
| Auditing             | Record security-related events                    |

---

# Authentication

Authentication verifies a user's identity.

Common authentication methods include:

| Method                            | Description                       |
| --------------------------------- | --------------------------------- |
| Password                          | Traditional login                 |
| SSH Key                           | Public/private key authentication |
| Multi-Factor Authentication (MFA) | Multiple verification methods     |
| LDAP / Active Directory           | Centralized authentication        |

Authentication information is stored in:

| File          | Purpose                   |
| ------------- | ------------------------- |
| `/etc/passwd` | User account information  |
| `/etc/shadow` | Encrypted password hashes |

---

# Authorization

Authorization determines what an authenticated user is allowed to do.

Linux primarily uses:

* User permissions
* Group permissions
* File ownership
* sudo privileges
* Mandatory Access Control (SELinux/AppArmor)

---

# sudo

Instead of logging in as root, administrators temporarily elevate privileges.

Execute a command as root:

```bash
sudo apt update
```

Edit the sudo configuration safely:

```bash
sudo visudo
```

Advantages:

* Accountability
* Reduced risk
* Audit trail
* Controlled privilege escalation

---

# Root User

The root user has unrestricted access to the system.

Best practices:

* Avoid direct root login
* Use sudo instead
* Restrict remote root access
* Protect root credentials

---

# File Permissions

Linux protects files using:

| Permission | Symbol |
| ---------- | ------ |
| Read       | r      |
| Write      | w      |
| Execute    | x      |

Permission groups:

| Group  | Meaning          |
| ------ | ---------------- |
| User   | Owner            |
| Group  | Associated group |
| Others | Everyone else    |

Example:

```text
-rwxr-x---
```

---

# Special Permissions

| Permission | Symbol | Purpose                                      |
| ---------- | ------ | -------------------------------------------- |
| SUID       | s      | Execute with owner's privileges              |
| SGID       | s      | Execute with group's privileges              |
| Sticky Bit | t      | Restrict file deletion in shared directories |

---

# Firewall

A firewall filters network traffic entering and leaving the system.

Common Linux firewall solutions:

| Tool      | Distribution |
| --------- | ------------ |
| nftables  | Modern Linux |
| iptables  | Legacy       |
| firewalld | RHEL family  |
| ufw       | Ubuntu       |

Example:

```bash
sudo ufw status
```

---

# SELinux

SELinux (Security-Enhanced Linux) implements Mandatory Access Control (MAC).

Modes:

| Mode       | Description                       |
| ---------- | --------------------------------- |
| Enforcing  | Policies enforced                 |
| Permissive | Violations logged but not blocked |
| Disabled   | SELinux inactive                  |

Check status:

```bash
getenforce
```

---

# AppArmor

AppArmor provides Mandatory Access Control using application profiles.

Common on:

* Ubuntu
* Debian

Check status:

```bash
aa-status
```

---

# SSH Security

Recommendations:

| Practice                        | Benefit                              |
| ------------------------------- | ------------------------------------ |
| Disable root login              | Prevent direct administrative access |
| Use SSH keys                    | Stronger authentication              |
| Disable password authentication | Reduce brute-force attacks           |
| Change default port (optional)  | Reduce automated scans               |
| Restrict allowed users          | Minimize attack surface              |

---

# Software Updates

Keeping software updated reduces exposure to known vulnerabilities.

Examples:

```bash
sudo apt update
sudo apt upgrade
```

or

```bash
sudo dnf update
```

---

# Auditing

Audit logs record security-related events.

Useful sources:

| Tool                | Purpose                               |
| ------------------- | ------------------------------------- |
| `journalctl`        | System logs                           |
| `/var/log/auth.log` | Authentication events (Debian/Ubuntu) |
| `/var/log/secure`   | Authentication events (RHEL family)   |
| `auditd`            | Security auditing                     |

---

# Password Best Practices

| Recommendation   | Benefit               |
| ---------------- | --------------------- |
| Long passwords   | Stronger security     |
| Unique passwords | Limits compromise     |
| Password manager | Secure storage        |
| MFA              | Additional protection |

---

# Common Security Commands

| Command      | Purpose                    |
| ------------ | -------------------------- |
| `sudo`       | Privilege escalation       |
| `whoami`     | Current user               |
| `id`         | User and group information |
| `passwd`     | Change password            |
| `chmod`      | Change permissions         |
| `chown`      | Change ownership           |
| `getenforce` | SELinux status             |
| `aa-status`  | AppArmor status            |
| `ufw status` | Firewall status            |
| `journalctl` | Security logs              |

---

# Common Troubleshooting

| Problem                   | Investigation                     | Resolution                               |
| ------------------------- | --------------------------------- | ---------------------------------------- |
| Permission denied         | Check ownership and permissions   | Use `ls -l`, `chmod`, or `chown`         |
| sudo not working          | Verify sudoers configuration      | Review with `visudo`                     |
| SSH login failure         | Review SSH configuration and logs | Check keys, permissions, and `sshd`      |
| Firewall blocking traffic | Inspect firewall rules            | Allow required ports                     |
| SELinux/AppArmor denial   | Review audit logs                 | Update or adjust policies if appropriate |

---

# Best Practices

| Practice                          | Benefit                          |
| --------------------------------- | -------------------------------- |
| Apply security updates regularly  | Reduce vulnerabilities           |
| Use least privilege               | Limit damage from compromise     |
| Disable unused services           | Reduce attack surface            |
| Monitor authentication logs       | Detect unauthorized access       |
| Use SSH keys instead of passwords | Improve remote access security   |
| Back up critical data             | Support recovery after incidents |

---

# Common Mistakes

| Mistake                                    | Better Practice                          |
| ------------------------------------------ | ---------------------------------------- |
| Logging in directly as root                | Use `sudo`                               |
| Setting permissions to `777` unnecessarily | Grant only required permissions          |
| Ignoring security updates                  | Patch systems regularly                  |
| Running unnecessary services               | Disable unused services                  |
| Sharing administrator accounts             | Use individual user accounts with `sudo` |

---

# Interview Highlights

| Question                                                         | Answer                                                                    |
| ---------------------------------------------------------------- | ------------------------------------------------------------------------- |
| What is the principle of least privilege?                        | Grant users only the permissions necessary to perform their tasks.        |
| What is the difference between authentication and authorization? | Authentication verifies identity; authorization determines access rights. |
| Why is `sudo` preferred over direct root login?                  | It provides controlled privilege escalation and an audit trail.           |
| What is SELinux?                                                 | A Mandatory Access Control framework that enforces security policies.     |
| What is the purpose of a firewall?                               | To control inbound and outbound network traffic based on defined rules.   |

---

# Key Takeaways

| Concept          | Summary                         |
| ---------------- | ------------------------------- |
| Authentication   | Verify identity                 |
| Authorization    | Control access                  |
| Least Privilege  | Minimize permissions            |
| sudo             | Controlled privilege escalation |
| Firewall         | Network traffic filtering       |
| SELinux/AppArmor | Mandatory Access Control        |
| Auditing         | Record security events          |
| Updates          | Reduce known vulnerabilities    |

---

# Related Documents

| Document            | Purpose                                         |
| ------------------- | ----------------------------------------------- |
| Permissions.md      | Linux permission model                          |
| Users and Groups.md | User and group administration                   |
| SSH.md              | Secure remote access                            |
| Logging.md          | Security and audit logs                         |
| Networking.md       | Network security fundamentals                   |
| Linux for DevOps.md | Security practices in production infrastructure |
