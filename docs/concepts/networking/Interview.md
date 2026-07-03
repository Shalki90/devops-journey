# Networking Interview

**Document Version:** 1.0
**Sprint:** 1 — Internet & Networking

---

# Purpose

This document consolidates **common networking interview questions and answers** extracted and structured from the original DevOps Engineering Journey repository.

It is designed for **concept clarity + interview readiness**, not memorization.

---

# Core Networking Questions

## Basic Concepts

| Question               | Answer                                                             |
| ---------------------- | ------------------------------------------------------------------ |
| What is a network?     | A group of connected devices that communicate and share resources. |
| What is the Internet?  | A global network of interconnected smaller networks.               |
| What is an IP address? | A unique identifier assigned to a device on a network.             |
| What is DNS?           | A system that translates domain names into IP addresses.           |
| What is a router?      | A device that forwards data between networks.                      |

---

## Client–Server Model

| Question                                   | Answer                                                           |
| ------------------------------------------ | ---------------------------------------------------------------- |
| What is a client?                          | A system that requests data or services.                         |
| What is a server?                          | A system that provides data or services.                         |
| How does client-server communication work? | Client sends request → Server processes → Server sends response. |

---

## HTTP & Web

| Question                           | Answer                                                               |
| ---------------------------------- | -------------------------------------------------------------------- |
| What is HTTP?                      | Protocol used for communication between web clients and servers.     |
| What is HTTPS?                     | Secure version of HTTP using encryption (TLS).                       |
| Difference between HTTP and HTTPS? | HTTPS encrypts data, HTTP does not.                                  |
| What is a request-response cycle?  | The process of client sending request and server returning response. |

---

## TCP / UDP

| Question                        | Answer                                                         |
| ------------------------------- | -------------------------------------------------------------- |
| What is TCP?                    | A reliable connection-oriented protocol.                       |
| What is UDP?                    | A fast, connectionless protocol without guarantee of delivery. |
| Difference between TCP and UDP? | TCP is reliable, UDP is faster but less reliable.              |
| What is a 3-way handshake?      | SYN → SYN-ACK → ACK process for establishing TCP connection.   |

---

## DNS

| Question                                     | Answer                                                                 |
| -------------------------------------------- | ---------------------------------------------------------------------- |
| What happens when you type a URL in browser? | DNS resolves domain → IP → request sent to server → response returned. |
| What is DNS caching?                         | Storing resolved IPs to speed up future requests.                      |

---

## Ports & Networking

| Question                   | Answer                                            |
| -------------------------- | ------------------------------------------------- |
| What is a port?            | A logical endpoint for communication on a device. |
| What are well-known ports? | Standard ports like 80 (HTTP), 443 (HTTPS).       |
| What is a socket?          | Combination of IP address and port number.        |

---

## Security Basics

| Question                         | Answer                                                         |
| -------------------------------- | -------------------------------------------------------------- |
| What is encryption?              | Process of converting readable data into unreadable form.      |
| What is decryption?              | Converting encrypted data back to readable form.               |
| What is TLS?                     | Protocol that secures communication over a network.            |
| What is public-key cryptography? | System using public and private keys for secure communication. |

---

# Scenario-Based Questions

## Scenario 1: Website not loading

| Step               | Explanation                      |
| ------------------ | -------------------------------- |
| Check DNS          | Ensure domain resolves correctly |
| Check connectivity | Use `ping`                       |
| Check routing      | Use `traceroute`                 |
| Check port         | Verify 80/443 availability       |
| Check server       | Ensure backend is running        |

---

## Scenario 2: Slow website

| Possible Cause  | Explanation                       |
| --------------- | --------------------------------- |
| Network latency | High delay in packet transmission |
| DNS delay       | Slow domain resolution            |
| Server overload | Too many requests                 |
| Packet loss     | Data retransmission required      |

---

# Key Insight

Interview understanding is structured around:

| Layer     | Focus                |
| --------- | -------------------- |
| Basics    | Definitions          |
| Flow      | How data moves       |
| Protocols | TCP, UDP, HTTP       |
| Debugging | Real-world scenarios |
| Security  | Encryption and TLS   |

---

# Related Documents

* Dictionary.md
* Analogies.md
* Cheatsheet.md
* Troubleshooting.md (next)
