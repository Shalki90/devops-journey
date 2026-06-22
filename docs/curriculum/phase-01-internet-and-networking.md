# Phase 01 — Internet & Networking Fundamentals

## Objective

Understand how computers communicate over networks and how modern Internet communication works before learning tools such as Git, Docker, Kubernetes, and Cloud platforms.

The goal is to develop strong first-principles understanding rather than memorize networking terminology.

---

## Learning Outcomes

By the end of this phase, I should be able to:

- Explain how devices communicate across networks.
- Describe how the Internet is organized.
- Explain the purpose of IP addresses.
- Explain how DNS resolves domain names.
- Describe how packets travel across networks.
- Explain the role of routers.
- Understand why protocols exist.
- Differentiate between HTTP and HTTPS.
- Explain the basics of encryption.
- Describe public and private key cryptography.
- Explain the purpose of servers and ports.
- Understand well-known ports.
- Explain how browsers communicate with web servers.
- Explain how HTTP requests and responses are exchanged.
- Explain how a server listens for incoming TCP connections.
- Understand the lifecycle of client and server sockets.

---

## Topics

| Status | Topic |
|--------|-------|
| ✅ | Internet |
| ✅ | Network |
| ✅ | IP Address |
| ✅ | DNS |
| ✅ | Routing |
| ✅ | Router |
| ✅ | Packet |
| ✅ | Protocol |
| ✅ | HTTP |
| ✅ | HTTPS |
| ✅ | Encryption |
| ✅ | Plaintext vs Ciphertext |
| ✅ | Public Key Cryptography |
| ✅ | Server |
| ✅ | Port |
| ✅ | Well-known Ports |
| ✅ | TCP vs UDP |
| ✅ | TCP Three-Way Handshake |
| ✅ | NAT |
| ✅ | Firewalls |
| ✅ | Load Balancers |
| ✅ | Reverse Proxy |
| ✅ | HTTP Request & Response |
| ✅ | HTTP Headers |
| ✅ | Client-Server Communication |
| ✅ | Listening Socket vs Client Socket |
| ✅ | Persistent Server Design |

---

## Hands-on Labs

| Status | Lab | Objective |
|--------|-----|-----------|
| ✅ | DNS Resolution (`nslookup`) | Observe how a domain name resolves to an IP address. |
| ✅ | Network Connectivity (`ping`) | Verify connectivity, observe latency, packet statistics, and TTL. |
| ✅ | Inspect TCP Connections (`Get-NetTCPConnection`, `netstat`) | Observe active TCP connections, listening sockets, established connections, ephemeral ports, and HTTPS connections. |
| ✅ | Inspect HTTP Requests (`curl`) | Observe HTTP request and response headers and compare client/server communication. |
| ✅ | Compare HTTP vs HTTPS | Observe differences in communication, TLS negotiation, encryption, and HTTP headers. |
| ✅ | Local Web Server | Build a Python HTTP server, inspect listening sockets, receive HTTP requests, send HTTP responses, and observe client connections. |
| ✅ | Packet Capture (Wireshark - Optional) | Deferred to a future session. |

---

## Mini Projects

Projects completed during this phase.

- Built a basic HTTP server using Python's `http.server` module.
- Built a minimal HTTP server directly using Python sockets.
- Implemented a continuously running TCP server capable of serving multiple client connections sequentially.
- Observed browser-generated HTTP requests and manually returned valid HTTP responses.

---

## Engineering Principles Reinforced

During this phase, the following engineering principles were reinforced:

- Single Responsibility
- Standardization
- Distributed Decision Making
- Defense in Depth
- Security Scope
- Failure-Oriented Thinking
- Reduce Cognitive Load
- Redundancy
- Separate Naming from Routing
- Layered Problem Solving
- End-to-End Identification
- Separation of Responsibilities
- Stable Service Endpoints
- Short-Lived Client Connections

---

## Related Documentation

- `docs/DICTIONARY.md`
- `docs/ANALOGIES.md`
- `docs/ENGINEERING_PRINCIPLES.md`
- `docs/AI_IN_PRACTICE.md`
- `docs/PARKING_LOT.md`

---

## Completion Criteria

This phase is complete when I can:

- Explain every networking concept without referring to notes.
- Demonstrate the concepts using practical examples.
- Troubleshoot basic networking problems.
- Teach the concepts using simple analogies.
- Complete all hands-on labs.

---

Version: 0.2

Status: ✅ Completed