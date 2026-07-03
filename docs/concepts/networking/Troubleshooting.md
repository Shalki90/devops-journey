# Networking Troubleshooting

**Document Version:** 1.0
**Sprint:** 1 — Internet & Networking

---

# Purpose

This document captures **real-world networking issues and debugging patterns** extracted from the original DevOps Engineering Journey repository.

It focuses on **how to think during failures**, not just commands.

---

# Layered Debugging Approach

| Step | Layer                 | What to Check             | Tools                     |
| ---- | --------------------- | ------------------------- | ------------------------- |
| 1    | Physical/Connectivity | Is the host reachable?    | `ping`, `ip a`            |
| 2    | DNS                   | Can domain resolve?       | `nslookup`, `dig`         |
| 3    | Network Path          | Where is traffic failing? | `traceroute`, `tracepath` |
| 4    | Transport             | Is port open?             | `ss`, `netstat`, `lsof`   |
| 5    | Application           | Is service running?       | `curl`, logs              |
| 6    | Packet Level          | Are packets flowing?      | `tcpdump`, Wireshark      |

---

# Common Issues

## DNS Issues

| Problem              | Cause       | Fix                                      |
| -------------------- | ----------- | ---------------------------------------- |
| Domain not resolving | DNS failure | Check `/etc/resolv.conf`, try `nslookup` |
| Slow resolution      | DNS latency | Use faster DNS (8.8.8.8)                 |
| Wrong IP returned    | Cached DNS  | Flush DNS cache                          |

---

## Connectivity Issues

| Problem                 | Cause                 | Fix                             |
| ----------------------- | --------------------- | ------------------------------- |
| Cannot reach server     | Network down/firewall | Check routing, firewall rules   |
| Intermittent connection | Packet loss           | Check network stability         |
| Timeout errors          | Blocked ports         | Verify firewall/security groups |

---

## Port Issues

| Problem             | Cause               | Fix                       |
| ------------------- | ------------------- | ------------------------- |
| Connection refused  | Service not running | Start service, check logs |
| Port not accessible | Firewall blocking   | Open port in firewall     |
| Wrong port used     | Misconfiguration    | Verify service config     |

---

## HTTP Issues

| Problem          | Cause           | Fix                    |
| ---------------- | --------------- | ---------------------- |
| 404 Not Found    | Wrong endpoint  | Verify URL             |
| 500 Server Error | Backend failure | Check logs             |
| 502 Bad Gateway  | Proxy issue     | Check upstream service |
| Slow response    | Server overload | Scale or optimize      |

---

## Routing Issues

| Problem            | Cause                 | Fix                    |
| ------------------ | --------------------- | ---------------------- |
| No route to host   | Missing route         | Check routing table    |
| Traffic stuck      | Misconfigured gateway | Verify default gateway |
| Asymmetric routing | Bad routing config    | Fix route policies     |

---

# Debugging Patterns

## Pattern 1: "Everything is down"

| Step | Action                       |
| ---- | ---------------------------- |
| 1    | Check local network (`ip a`) |
| 2    | Ping gateway                 |
| 3    | Ping external IP             |
| 4    | Check DNS                    |
| 5    | Check firewall               |

---

## Pattern 2: "Service not reachable"

| Step | Action                |
| ---- | --------------------- |
| 1    | Check service status  |
| 2    | Verify port listening |
| 3    | Check firewall rules  |
| 4    | Test with `curl`      |
| 5    | Inspect logs          |

---

## Pattern 3: "Slow application"

| Step | Action                      |
| ---- | --------------------------- |
| 1    | Check latency (`ping`)      |
| 2    | Check DNS delay             |
| 3    | Check server load           |
| 4    | Analyze packet loss         |
| 5    | Inspect backend performance |

---

# Key Insight

Troubleshooting follows a **top-down approach**:

| Layer          | Focus             |
| -------------- | ----------------- |
| Network        | Connectivity      |
| Transport      | Ports and sockets |
| Application    | Services and APIs |
| Infrastructure | Routing, firewall |
| Packet         | Deep inspection   |

---

# Mental Model

| Symptom          | Likely Layer      |
| ---------------- | ----------------- |
| Cannot connect   | Network / Routing |
| Timeout          | Firewall / Port   |
| Wrong response   | Application       |
| Slow performance | DNS / Latency     |

---

# Related Documents

* Dictionary.md
* Analogies.md
* Cheatsheet.md
* Interview.md
