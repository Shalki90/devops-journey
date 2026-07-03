# Networking Dictionary

**Document Version:** 1.0
**Sprint:** 1 — Internet & Networking

---

# Purpose

This document provides a structured dictionary of core **networking concepts** extracted from the DevOps Engineering Journey repository.

All definitions are preserved and reformatted into a **table-first structure** for clarity and long-term reference.

---

# Core Networking Dictionary

| Term                     | Definition                                                          |
| ------------------------ | ------------------------------------------------------------------- |
| Network                  | A group of connected devices that can communicate with each other.  |
| Internet                 | A global system of interconnected networks.                         |
| IP Address               | A unique numerical identifier assigned to a device on a network.    |
| IPv4                     | Internet Protocol version 4 using 32-bit addresses.                 |
| IPv6                     | Internet Protocol version 6 using 128-bit addresses.                |
| DNS (Domain Name System) | System that translates domain names into IP addresses.              |
| Domain                   | Human-readable address used to access services (e.g., google.com).  |
| Router                   | A device that forwards data packets between networks.               |
| Routing                  | The process of selecting paths for data to travel across networks.  |
| Packet                   | A small unit of data transmitted over a network.                    |
| Protocol                 | A set of rules that define how data is transmitted between systems. |

---

# Client–Server Model

| Term     | Definition                                                       |
| -------- | ---------------------------------------------------------------- |
| Client   | A device or application that requests services or resources.     |
| Server   | A system that provides services or resources to clients.         |
| Request  | A message sent from client to server asking for data or action.  |
| Response | The reply sent from server to client after processing a request. |

---

# Web Communication

| Term   | Definition                                                       |
| ------ | ---------------------------------------------------------------- |
| HTTP   | Protocol used for communication between web clients and servers. |
| HTTPS  | Secure version of HTTP using encryption (TLS/SSL).               |
| URL    | Uniform Resource Locator used to access resources on the web.    |
| Header | Metadata sent in HTTP requests or responses.                     |
| Body   | The actual data content in a request or response.                |

---

# Transport Layer Concepts

| Term             | Definition                                                            |
| ---------------- | --------------------------------------------------------------------- |
| TCP              | Connection-oriented protocol ensuring reliable data transfer.         |
| UDP              | Connectionless protocol used for fast but less reliable transmission. |
| Port             | Logical endpoint for network communication on a device.               |
| Well-known Ports | Standardized ports (0–1023) used by common services.                  |
| Socket           | Combination of IP address and port for communication endpoint.        |

---

# Security Concepts

| Term        | Definition                                                    |
| ----------- | ------------------------------------------------------------- |
| Encryption  | Process of converting readable data into unreadable format.   |
| Decryption  | Process of converting encrypted data back into readable form. |
| Plaintext   | Original readable data before encryption.                     |
| Ciphertext  | Encrypted unreadable data.                                    |
| Public Key  | Key used to encrypt data in asymmetric encryption.            |
| Private Key | Key used to decrypt data in asymmetric encryption.            |
| TLS         | Protocol that ensures secure communication over a network.    |

---

# Infrastructure Concepts

| Term          | Definition                                                          |
| ------------- | ------------------------------------------------------------------- |
| NAT           | Network Address Translation that maps private IPs to public IPs.    |
| Firewall      | Security system that controls incoming and outgoing traffic.        |
| Load Balancer | System that distributes traffic across multiple servers.            |
| Reverse Proxy | Server that forwards client requests to backend servers.            |
| Proxy         | Intermediate system that relays requests between client and server. |

---

# Key Insight

Networking is fundamentally about:

| Pillar        | Meaning                         |
| ------------- | ------------------------------- |
| Communication | How systems exchange data       |
| Addressing    | How systems identify each other |
| Routing       | How data finds its path         |
| Security      | How data is protected           |
| Transport     | How data is delivered           |

---

# Related Documents

| Document           | Purpose                                  |
| ------------------ | ---------------------------------------- |
| Analogies.md       | Mental models for understanding concepts |
| Cheatsheet.md      | Quick command reference                  |
| Interview.md       | Interview preparation questions          |
| Troubleshooting.md | Real-world problem solving               |
