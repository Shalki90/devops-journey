# Networking Cheatsheet

**Document Version:** 1.0
**Sprint:** 1 — Internet & Networking

---

# Purpose

This document provides a **quick reference guide** for commonly used networking commands, tools, and troubleshooting utilities.

It is designed for fast recall during practice, interviews, and real-world debugging.

---

# IP & Connectivity Commands

| Command      | Purpose                           | Example                 |
| ------------ | --------------------------------- | ----------------------- |
| `ip a`       | Show IP addresses on interfaces   | `ip a`                  |
| `ifconfig`   | Legacy network interface info     | `ifconfig`              |
| `ping`       | Check connectivity to a host      | `ping google.com`       |
| `traceroute` | Trace packet route to destination | `traceroute google.com` |
| `tracepath`  | Alternative route tracing tool    | `tracepath google.com`  |

---

# DNS Commands

| Command    | Purpose                  | Example               |
| ---------- | ------------------------ | --------------------- |
| `nslookup` | Query DNS records        | `nslookup google.com` |
| `dig`      | Advanced DNS lookup tool | `dig google.com`      |
| `host`     | Simple DNS lookup        | `host google.com`     |

---

# Network Connections & Ports

| Command   | Purpose                       | Example          |
| --------- | ----------------------------- | ---------------- |
| `netstat` | Show network connections      | `netstat -tulnp` |
| `ss`      | Modern socket statistics tool | `ss -tulnp`      |
| `lsof -i` | List processes using network  | `lsof -i :80`    |

---

# HTTP & Web Debugging

| Command   | Purpose                 | Example                         |
| --------- | ----------------------- | ------------------------------- |
| `curl`    | Send HTTP requests      | `curl https://example.com`      |
| `wget`    | Download files from web | `wget https://example.com/file` |
| `curl -I` | Fetch headers only      | `curl -I https://google.com`    |

---

# Packet Analysis Tools

| Command     | Purpose                 | Example           |
| ----------- | ----------------------- | ----------------- |
| `tcpdump`   | Capture network packets | `tcpdump -i eth0` |
| `wireshark` | GUI packet analyzer     | (open GUI tool)   |

---

# Routing & Interface Info

| Command    | Purpose               | Example    |
| ---------- | --------------------- | ---------- |
| `ip route` | Show routing table    | `ip route` |
| `route -n` | Display routing table | `route -n` |

---

# System Networking

| Command       | Purpose             | Example            |
| ------------- | ------------------- | ------------------ |
| `hostname -I` | Show system IP      | `hostname -I`      |
| `nmcli`       | Network manager CLI | `nmcli dev status` |

---

# Common Debugging Flow

| Step | Action                          |
| ---- | ------------------------------- |
| 1    | Check IP configuration (`ip a`) |
| 2    | Test connectivity (`ping`)      |
| 3    | Check DNS (`nslookup`)          |
| 4    | Trace route (`traceroute`)      |
| 5    | Check ports (`ss -tulnp`)       |
| 6    | Inspect traffic (`tcpdump`)     |

---

# Key Insight

Networking debugging follows a layered approach:

| Layer        | Focus          |
| ------------ | -------------- |
| Connectivity | ping, ip       |
| Resolution   | DNS tools      |
| Transport    | ports, sockets |
| Application  | HTTP tools     |
| Packet level | tcpdump        |

---

# Related Documents

* Dictionary.md
* Analogies.md
* Interview.md (next)
* Troubleshooting.md (next)
