# SSH

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document explains **SSH (Secure Shell)**, the standard protocol for secure remote administration of Linux systems. It covers SSH architecture, authentication methods, key-based authentication, configuration, file transfer, tunneling, common commands, troubleshooting, and best practices.

SSH is one of the most important tools in Linux administration, DevOps, cloud computing, and infrastructure automation.

---

# What is SSH?

SSH (Secure Shell) is a cryptographic network protocol used to securely connect to and manage remote systems over an untrusted network.

SSH provides:

* Secure remote login
* Encrypted communication
* Secure command execution
* Secure file transfer
* Port forwarding
* Tunneling

Default port:

```text id="8m4k1a"
22/TCP
```

---

# Why SSH Matters

SSH enables administrators to:

* Manage remote Linux servers
* Execute commands securely
* Transfer files
* Automate deployments
* Access cloud virtual machines
* Configure infrastructure

Without SSH, remote administration would require insecure protocols such as Telnet.

---

# SSH Architecture

```text id="pk7q9v"
SSH Client
      │
Encrypted Connection (TCP 22)
      │
SSH Server (sshd)
      │
Authentication
      │
Shell Session
      │
Remote Linux System
```

---

# SSH Components

| Component           | Responsibility              |
| ------------------- | --------------------------- |
| SSH Client          | Initiates remote connection |
| SSH Server (`sshd`) | Accepts SSH connections     |
| Authentication      | Verifies user identity      |
| Encryption          | Protects communication      |
| Shell               | Executes remote commands    |

---

# Authentication Methods

| Method                      | Description                   | Recommended        |
| --------------------------- | ----------------------------- | ------------------ |
| Password Authentication     | User enters password          | No (production)    |
| Public Key Authentication   | Uses SSH key pair             | Yes                |
| Multi-Factor Authentication | SSH + additional verification | Highly Recommended |

---

# SSH Key Pair

SSH key authentication uses two keys.

```text id="z3vkh5"
Private Key
      │
      │ (Never Shared)
      ▼
Public Key
      │
Stored on Remote Server
```

| Key         | Purpose                       |
| ----------- | ----------------------------- |
| Private Key | Remains on the client machine |
| Public Key  | Stored on the remote server   |

---

# Generate an SSH Key

Generate a modern Ed25519 key pair:

```bash id="k2mr8d"
ssh-keygen -t ed25519
```

Or generate an RSA key pair:

```bash id="n9v5fc"
ssh-keygen -t rsa -b 4096
```

Default location:

```text id="m1d7hx"
~/.ssh/
├── id_ed25519
├── id_ed25519.pub
```

---

# Copy Public Key to Remote Server

```bash id="k7x2na"
ssh-copy-id user@server
```

Alternatively, manually append the public key to:

```text id="6rq0jp"
~/.ssh/authorized_keys
```

---

# Connecting to a Remote Server

Basic syntax:

```bash id="0pvf1m"
ssh user@hostname
```

Example:

```bash id="8h6e3w"
ssh ubuntu@192.168.1.10
```

Specify a custom port:

```bash id="vb0o6d"
ssh -p 2222 user@server
```

---

# SSH Configuration

Client configuration file:

```text id="y5o2kg"
~/.ssh/config
```

Example:

```text id="rx7i0e"
Host web-server
    HostName 192.168.1.10
    User ubuntu
    Port 22
    IdentityFile ~/.ssh/id_ed25519
```

Connect using:

```bash id="d4l2se"
ssh web-server
```

---

# SSH Server Configuration

Server configuration file:

```text id="0kt9tw"
/etc/ssh/sshd_config
```

Common settings:

| Directive                | Purpose                                   |
| ------------------------ | ----------------------------------------- |
| `Port`                   | SSH listening port                        |
| `PermitRootLogin`        | Allow or deny root login                  |
| `PasswordAuthentication` | Enable or disable password authentication |
| `PubkeyAuthentication`   | Enable public key authentication          |
| `AllowUsers`             | Restrict permitted users                  |

Restart SSH after configuration changes:

```bash id="rh1p5q"
sudo systemctl restart ssh
```

---

# File Transfer

Securely copy files using `scp`.

Copy a file to a remote server:

```bash id="4jc3df"
scp file.txt user@server:/home/user/
```

Copy a file from a remote server:

```bash id="b9k2uw"
scp user@server:/home/user/file.txt .
```

---

# Synchronizing Files

Use `rsync` over SSH:

```bash id="h6g3yr"
rsync -avz project/ user@server:/opt/project/
```

Benefits:

* Efficient transfers
* Resume interrupted transfers
* Synchronize only changed files

---

# SSH Agent

An SSH agent securely stores decrypted private keys in memory.

Start the agent:

```bash id="v3n5ep"
eval "$(ssh-agent -s)"
```

Add a key:

```bash id="h0w9da"
ssh-add ~/.ssh/id_ed25519
```

---

# Port Forwarding

SSH supports encrypted tunnels.

| Type               | Purpose                        |
| ------------------ | ------------------------------ |
| Local Forwarding   | Access remote services locally |
| Remote Forwarding  | Expose local services remotely |
| Dynamic Forwarding | SOCKS proxy                    |

Example (local forwarding):

```bash id="t8j4mf"
ssh -L 8080:localhost:80 user@server
```

---

# Useful SSH Commands

| Command                 | Purpose                     |
| ----------------------- | --------------------------- |
| `ssh user@host`         | Connect to a remote server  |
| `ssh -p 2222 user@host` | Connect using a custom port |
| `ssh-keygen`            | Generate SSH keys           |
| `ssh-copy-id`           | Install a public key        |
| `scp`                   | Secure file copy            |
| `rsync`                 | Synchronize files over SSH  |
| `ssh-add`               | Add a key to the SSH agent  |

---

# Common Troubleshooting

| Problem              | Investigation                    | Resolution                                                  |
| -------------------- | -------------------------------- | ----------------------------------------------------------- |
| Connection refused   | Check `sshd` status              | Start or restart the SSH service                            |
| Permission denied    | Verify keys and user permissions | Check `authorized_keys` and file permissions                |
| Host key changed     | Validate server identity         | Remove the outdated entry from `known_hosts` if appropriate |
| Authentication fails | Review SSH logs                  | Verify keys, usernames, and configuration                   |
| Timeout              | Test network connectivity        | Check firewall rules and routing                            |

---

# Best Practices

| Practice                                      | Benefit                          |
| --------------------------------------------- | -------------------------------- |
| Use key-based authentication                  | Stronger security than passwords |
| Disable root login                            | Reduce attack surface            |
| Disable password authentication in production | Prevent brute-force attacks      |
| Protect private keys with a passphrase        | Additional security layer        |
| Restrict SSH access using firewalls           | Limit exposure                   |

---

# Common Mistakes

| Mistake                                               | Better Practice                                 |
| ----------------------------------------------------- | ----------------------------------------------- |
| Sharing private keys                                  | Never share private keys                        |
| Logging in directly as root                           | Use a regular user with `sudo`                  |
| Ignoring host key warnings                            | Verify server identity before accepting changes |
| Using weak RSA keys                                   | Prefer Ed25519 or strong RSA keys               |
| Leaving password authentication enabled unnecessarily | Prefer public key authentication                |

---

# Interview Highlights

| Question                                                       | Answer                                                                                                 |
| -------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| What is SSH?                                                   | A secure protocol for remote administration and encrypted communication.                               |
| What is the difference between a public key and a private key? | The public key is shared with the server; the private key remains on the client and must be protected. |
| Where is the SSH server configuration stored?                  | `/etc/ssh/sshd_config`.                                                                                |
| What is `ssh-copy-id` used for?                                | To install a public key into a remote user's `authorized_keys` file.                                   |
| Why is key-based authentication preferred?                     | It is more secure and resistant to brute-force attacks than passwords.                                 |

---

# Key Takeaways

| Concept             | Summary                               |
| ------------------- | ------------------------------------- |
| SSH                 | Secure remote administration protocol |
| SSH Client          | Initiates secure connections          |
| SSH Server (`sshd`) | Accepts incoming SSH connections      |
| Public Key          | Stored on the server                  |
| Private Key         | Stored securely on the client         |
| `authorized_keys`   | Lists trusted public keys             |
| `sshd_config`       | SSH server configuration              |
| `scp` / `rsync`     | Secure file transfer                  |

---

# Related Documents

| Document            | Purpose                                       |
| ------------------- | --------------------------------------------- |
| Networking.md       | Linux networking fundamentals                 |
| Users and Groups.md | User authentication                           |
| Permissions.md      | File permissions for SSH keys                 |
| systemd.md          | Managing the SSH service                      |
| Security.md         | SSH hardening and access control              |
| Linux for DevOps.md | SSH in cloud, automation, and CI/CD workflows |
