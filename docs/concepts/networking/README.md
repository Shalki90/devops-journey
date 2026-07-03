# Networking Fundamentals

**Document Version:** 1.0
**Sprint:** 1 — Internet & Networking

---

# Purpose

This document consolidates the **Internet & Networking fundamentals** from the original DevOps Engineering Journey repository into a structured, maintainable format.

It serves as the **entry point for all networking-related knowledge** in this repository.

---

# Source Traceability

This content is migrated from:

* `docs/curriculum/phase-01-internet-and-networking.md`
* `docs/analogies/networking.md`
* `docs/analogies/NETWORKING.md`

All knowledge has been preserved and reorganized without loss.

---

# Learning Objective

The goal of this phase is to develop a **first-principles understanding of how systems communicate over networks**, before moving into tooling like Git, Docker, Kubernetes, and Cloud.

Focus is on understanding **how the Internet works**, not memorization.

---

# Learning Outcomes

By the end of this module, the learner should be able to:

* Explain how devices communicate over a network
* Describe how the Internet is structured
* Understand IP addressing concepts
* Explain DNS resolution flow
* Describe packet-based communication
* Understand routing fundamentals
* Explain the role of protocols
* Differentiate HTTP vs HTTPS
* Understand encryption basics
* Explain public/private key cryptography
* Describe servers and ports
* Understand well-known ports
* Explain browser-server communication
* Describe HTTP request/response lifecycle
* Understand TCP connection lifecycle
* Explain client vs server sockets
* Analyze network traffic using tools

---

# Core Topics

## Internet Fundamentals

* Internet structure
* Client-server model

## Addressing & Routing

* IP Address
* IPv4 basics
* Routing
* Router behavior

## DNS & Name Resolution

* DNS concept
* Domain resolution flow

## Communication Model

* Packets
* Protocols
* TCP vs UDP
* Three-way handshake

## Web Communication

* HTTP
* HTTPS
* HTTP headers
* Request/Response lifecycle

## Infrastructure Concepts

* NAT
* Firewalls
* Load balancers
* Reverse proxy

## System Communication

* Server
* Ports
* Well-known ports
* Listening sockets

## Security Basics

* Encryption
* Plaintext vs ciphertext
* Public/private key cryptography

---

# Hands-on Labs (Source)

Labs are defined in the original curriculum:

📍 `docs/curriculum/phase-01-internet-and-networking.md`

Key lab areas include:

* Network packet analysis
* HTTP request inspection
* TCP connection observation
* DNS resolution tracing
* Traffic inspection tools

(These will later be split into structured `/labs/networking/` in Sprint 1.2)

---

# Analogies (Source Mapped)

Original analogies preserved from:

* `docs/analogies/networking.md`
* `docs/analogies/NETWORKING.md`

These will be reorganized into:

```text
docs/concepts/networking/Analogies.md
```

---

# Concept Organization Strategy

This module will be broken down into:

* Dictionary (terminology)
* Analogies (mental models)
* Cheatsheet (quick reference)
* Troubleshooting (real-world issues)
* Interview (Q&A preparation)
* Labs (hands-on exercises)

This README acts as the **index layer only**.

---

# Relationship to Other Domains

Networking is foundational for:

* Git (remote communication)
* Linux (network stack)
* Docker (container networking)
* Kubernetes (service networking)
* Cloud (VPC, routing, load balancing)
* CI/CD pipelines (deployment communication)

---

# Migration Status

| Component          | Status                |
| ------------------ | --------------------- |
| Curriculum Content | Migrated (structured) |
| Analogies          | Pending split         |
| Dictionary         | Pending extraction    |
| Labs               | Pending restructuring |
| Interview Q&A      | Pending extraction    |

---

# Next Steps (Sprint 1 continuation)

The next migration tasks will be:

1. Extract **Networking Dictionary**
2. Extract **Networking Analogies**
3. Create **Cheatsheet.md**
4. Create **Troubleshooting.md**
5. Create **Interview.md**
6. Split Labs into structured format

---

# Related Documents

* docs/curriculum/phase-01-internet-and-networking.md
* docs/analogies/networking.md
* docs/governance/REPOSITORY_ARCHITECTURE.md
