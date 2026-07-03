# Networking

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document explains how Linux implements and manages networking. It covers network interfaces, IP addressing, routing, DNS configuration, ports, sockets, network services, common commands, troubleshooting, and best practices.

This document focuses on **Linux networking implementation**, not networking theory (covered in Sprint 1).

---

# Scope

| Included                 | Covered in Sprint 1 |
| ------------------------ | ------------------- |
| Linux network interfaces | OSI Model           |
| Interface configuration  | TCP/IP Theory       |
| Routing                  | HTTP/HTTPS          |
| DNS configuration        | DNS Theory          |
| Network services         | Switching           |
| Linux commands           | Routing Theory      |
| Network troubleshooting  | Subnetting          |

---

# Linux Networking Architecture

```text
Application
      │
Socket API
      │
TCP / UDP
      │
IP Layer
      │
Network Interface
      │
NIC Driver
      │
Physical Network
```

---

# Responsibilities of the Linux Networking Stack

| Responsibility        | Description                               |
| --------------------- | ----------------------------------------- |
| Interface Management  | Manage network adapters                   |
| IP Addressing         | Assign IPv4/IPv6 addresses                |
| Routing               | Forward packets                           |
| Name Resolution       | Resolve hostnames                         |
| Socket Communication  | Enable application networking             |
| Firewall Integration  | Filter traffic                            |
| Service Communication | Allow inter-process network communication |

---

# Network Interfaces

A network interface represents a connection between Linux and a network.

Examples:

| Interface | Description                  |
| --------- | ---------------------------- |
| eth0      | Legacy Ethernet interface    |
| ens33     | Predictable Ethernet naming  |
| enp0s3    | PCI-based predictable naming |
| wlan0     | Wireless interface           |
| lo        | Loopback interface           |

---

# Loopback Interface

```text
lo
127.0.0.1
```

Purpose:

* Internal communication
* Local service testing
* Inter-process networking

---

# Viewing Interfaces

| Command               | Purpose                         |
| --------------------- | ------------------------------- |
| `ip addr`             | Display addresses               |
| `ip link`             | Display interfaces              |
| `hostname -I`         | Show assigned IP addresses      |
| `ifconfig` *(legacy)* | Display interface configuration |

---

# IP Address Configuration

Display interface addresses:

```bash
ip addr show
```

Assign an address temporarily:

```bash
sudo ip addr add 192.168.1.100/24 dev eth0
```

Bring interface up:

```bash
sudo ip link set eth0 up
```

Bring interface down:

```bash
sudo ip link set eth0 down
```

---

# Routing

The routing table determines where packets are sent.

View routing table:

```bash
ip route
```

Example:

```text
Destination
        │
Routing Table
        │
Gateway
        │
Network Interface
```

---

# Default Gateway

The default gateway forwards traffic destined for external networks.

View default route:

```bash
ip route
```

Example output:

```text
default via 192.168.1.1 dev eth0
```

---

# DNS Configuration

DNS servers are typically configured in:

```text
/etc/resolv.conf
```

Common commands:

| Command             | Purpose                   |
| ------------------- | ------------------------- |
| `hostname`          | Show hostname             |
| `hostnamectl`       | Configure hostname        |
| `resolvectl status` | Display DNS configuration |

---

# Name Resolution

Linux resolves hostnames using:

```text
Application
      │
/etc/hosts
      │
DNS Resolver
      │
DNS Server
```

---

# Network Ports

Ports identify services running on a host.

| Port | Common Service |
| ---- | -------------- |
| 22   | SSH            |
| 53   | DNS            |
| 80   | HTTP           |
| 443  | HTTPS          |
| 3306 | MySQL          |
| 5432 | PostgreSQL     |

---

# Sockets

A socket is an endpoint for communication between processes.

Relationship:

```text
Application
      │
Socket
      │
TCP / UDP
      │
Network
```

---

# Viewing Listening Services

| Command                    | Purpose                     |
| -------------------------- | --------------------------- |
| `ss -tuln`                 | Display listening sockets   |
| `ss -tulpn`                | Include process information |
| `netstat -tuln` *(legacy)* | List network connections    |

---

# Connectivity Testing

| Command       | Purpose                   |
| ------------- | ------------------------- |
| `ping`        | Test reachability         |
| `traceroute`  | Display network path      |
| `tracepath`   | Lightweight path analysis |
| `curl`        | Test HTTP endpoints       |
| `wget`        | Download content          |
| `nc` (netcat) | Test TCP/UDP ports        |

---

# DNS Troubleshooting

| Command    | Purpose                |
| ---------- | ---------------------- |
| `dig`      | Query DNS records      |
| `nslookup` | Lookup DNS information |
| `host`     | Resolve hostnames      |

---

# Packet Capture

Capture network traffic using:

| Command     | Purpose                     |
| ----------- | --------------------------- |
| `tcpdump`   | Command-line packet capture |
| `Wireshark` | Graphical packet analyzer   |

Example:

```bash
sudo tcpdump -i eth0
```

---

# Firewall Interaction

Linux networking commonly integrates with:

| Tool      | Purpose                      |
| --------- | ---------------------------- |
| iptables  | Legacy packet filtering      |
| nftables  | Modern firewall framework    |
| firewalld | Firewall management service  |
| ufw       | Simplified firewall (Ubuntu) |

---

# Network Configuration

Configuration varies by distribution.

Examples:

| Distribution | Tool                               |
| ------------ | ---------------------------------- |
| Ubuntu       | Netplan                            |
| Debian       | `/etc/network/interfaces` (legacy) |
| RHEL/Fedora  | NetworkManager                     |
| Most Systems | `ip` command                       |

---

# Useful Networking Commands

| Command       | Purpose             |
| ------------- | ------------------- |
| `ip addr`     | IP addresses        |
| `ip route`    | Routing table       |
| `ip link`     | Interface status    |
| `ping`        | Connectivity        |
| `ss -tuln`    | Open ports          |
| `hostnamectl` | Hostname management |
| `curl`        | HTTP testing        |
| `dig`         | DNS queries         |
| `tcpdump`     | Packet capture      |

---

# Common Troubleshooting

| Problem                 | Investigation                   | Resolution                           |
| ----------------------- | ------------------------------- | ------------------------------------ |
| No network connectivity | `ip addr`, `ip route`           | Verify interface, gateway, and cable |
| DNS failures            | `dig`, `resolvectl`             | Verify DNS configuration             |
| Service unreachable     | `ss -tulpn`                     | Confirm service is listening         |
| Packet loss             | `ping`, `traceroute`            | Investigate network path             |
| Slow network            | `tcpdump`, interface statistics | Identify congestion or errors        |

---

# Best Practices

| Practice                                   | Benefit                        |
| ------------------------------------------ | ------------------------------ |
| Use the `ip` command instead of `ifconfig` | Modern and actively maintained |
| Assign static IPs only when required       | Simplifies management          |
| Use meaningful hostnames                   | Eases identification           |
| Monitor open ports                         | Reduce attack surface          |
| Document network changes                   | Improve maintainability        |

---

# Common Mistakes

| Mistake                              | Better Practice                                    |
| ------------------------------------ | -------------------------------------------------- |
| Editing network files without backup | Keep a copy before making changes                  |
| Forgetting the default gateway       | Verify routing configuration                       |
| Leaving unnecessary ports open       | Restrict exposed services                          |
| Assuming DNS is always the issue     | Test IP connectivity first                         |
| Using deprecated tools by default    | Prefer `ip` and `ss` over `ifconfig` and `netstat` |

---

# Interview Highlights

| Question                                               | Answer                                                                            |
| ------------------------------------------------------ | --------------------------------------------------------------------------------- |
| What is the loopback interface?                        | A virtual interface used for communication within the local system (`127.0.0.1`). |
| Difference between `ip addr` and `ifconfig`?           | `ip` is the modern replacement for the legacy `ifconfig` tool.                    |
| How do you view the routing table?                     | `ip route`.                                                                       |
| How do you check listening ports?                      | `ss -tulpn`.                                                                      |
| Which file commonly stores DNS resolver configuration? | `/etc/resolv.conf` (though it may be managed by another service).                 |

---

# Key Takeaways

| Concept           | Summary                         |
| ----------------- | ------------------------------- |
| Network Interface | Connects Linux to a network     |
| IP Address        | Identifies the host             |
| Route             | Determines packet path          |
| Gateway           | Exit point to external networks |
| DNS               | Resolves hostnames              |
| Socket            | Communication endpoint          |
| Port              | Identifies a network service    |
| `ip`              | Primary networking utility      |
| `ss`              | Displays sockets and ports      |

---

# Related Documents

| Document                         | Purpose                                         |
| -------------------------------- | ----------------------------------------------- |
| Boot Process.md                  | Networking during startup                       |
| systemd.md                       | Network-related services                        |
| SSH.md                           | Secure remote access                            |
| Security.md                      | Firewalls and network security                  |
| Linux for DevOps.md              | Networking in containers, cloud, and Kubernetes |
| Sprint 1 – Internet & Networking | Networking concepts and protocols               |
