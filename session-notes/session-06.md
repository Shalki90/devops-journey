# Session 06

## Topics

* Wireshark Fundamentals
* Packet Capture
* Network Interface Selection
* ICMP Packet Analysis
* HTTP Packet Analysis
* HTTPS Packet Analysis
* TLS Handshake
* Packet Structure
* Ethernet Frames
* IP Addresses
* TCP Ports
* Encrypted Application Data
* Protocol Layering

---

## Hands-on Labs

### Lab 1 — Capture ICMP Traffic

Objective:

Observe real ICMP Echo Request and Echo Reply packets.

Actions:

* Started packet capture on the Wi-Fi interface.
* Generated traffic using `ping google.com`.
* Applied Wireshark display filter:

```text
icmp
```

Observations:

* Echo Request packets originated from the local machine.
* Echo Reply packets were returned by Google's server.
* Request and Reply packet pairs were visible.
* TTL values differed between request and reply packets.
* Source and destination IP addresses were visible.

Example:

```text
192.168.1.105 → 142.251.220.78
ICMP Echo Request

142.251.220.78 → 192.168.1.105
ICMP Echo Reply
```

Key Insight:

ICMP provides network reachability testing without establishing a TCP connection.

---

### Lab 2 — Capture HTTP Traffic

Objective:

Observe unencrypted HTTP communication.

Actions:

Applied Wireshark display filter:

```text
http
```

Observations:

* HTTP GET requests were visible.
* HTTP responses were visible.
* Status codes such as:

```text
200 OK
404 Not Found
```

were directly readable.

* Request paths were visible.
* Application-layer data was visible.

Key Insight:

HTTP transmits application data in plaintext.

---

### Lab 3 — Capture HTTPS Traffic

Objective:

Observe encrypted HTTPS communication.

Actions:

Applied Wireshark display filter:

```text
tls
```

Observations:

* TLS Client Hello messages were visible.
* TLS Server Hello messages were visible.
* Change Cipher Spec messages were visible.
* Application Data packets were visible.

However:

* HTTP request paths were no longer visible.
* Application content could not be read.
* Payload data appeared encrypted.

Example:

```text
TLSv1.3
Application Data
Encrypted Application Data
```

Key Insight:

HTTPS encrypts application-layer content while still exposing routing information required for packet delivery.

---

## Packet Dissection Exercise

Selected HTTPS packet:

### Ethernet Layer

Source MAC:

```text
74:13:ea:4f:af:c9
```

Destination MAC:

```text
e4:fa:c4:0c:1b:48
```

Observation:

The packet was sent to the local router rather than directly to the destination server.

---

### IP Layer

Source IP:

```text
192.168.1.105
```

Destination IP:

```text
20.184.175.17
```

Observation:

IP addresses remain visible because routers require them for forwarding decisions.

---

### TCP Layer

Source Port:

```text
54335
```

Destination Port:

```text
443
```

Observation:

The client used an ephemeral port while the server listened on HTTPS port 443.

---

### TLS Layer

Observed:

```text
TLSv1.3
Change Cipher Spec
Application Data
Encrypted Application Data
```

Observation:

Application data existed but could not be interpreted without encryption keys.

---

## Engineering Questions

* Why must IP addresses remain visible even when HTTPS is used?
* Why can routers forward encrypted traffic without decrypting it?
* Why are MAC addresses only relevant on the local network?
* Why do applications use ephemeral client ports?
* How does TLS establish encryption keys before application data is transmitted?

---

## Engineering Insights

* Packet captures transform networking theory into observable reality.
* Encryption protects application data, not routing information.
* Routers operate using IP addresses rather than application-layer information.
* HTTPS secures communication without affecting packet forwarding.
* Every packet can be analyzed through layered protocols.
* TCP connections are uniquely identified by source/destination IPs and ports.
* Observability tools provide direct visibility into system behavior.

---

## Engineering Principles Reinforced

* Layered Problem Solving
* End-to-End Identification
* Separation of Responsibilities
* Security Scope
* Visibility Enables Understanding

---

## Repository Updates

Updated:

* docs/curriculum/phase-01-internet-and-networking.md
* docs/ENGINEERING_PRINCIPLES.md
* docs/AI_IN_PRACTICE.md
* docs/ANALOGIES.md

Created:

* session-notes/session-06.md

---

## Phase Status

Phase 01 hands-on labs completed.

Remaining work:

* Documentation updates
* Final Phase 01 review

---

## Next Session

* Officially complete Phase 01
* Review repository structure
* Begin Phase 02 — Git & Version Control