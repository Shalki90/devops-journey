# Session 02

## Topics

- Internet Fundamentals
- DNS
- Routing
- HTTP
- HTTPS
- Encryption
- Public & Private Keys
- Ports

---

## Hands-on Labs

| Lab | Observation |
|------|-------------|
| DNS Resolution (`nslookup`) | Observed how `github.com` is resolved into a public IP address before communication begins. Learned that DNS answers "Where is the destination?" |
| Network Connectivity (`ping`) | Verified connectivity to GitHub, observed round-trip latency, packet statistics, and TTL. Learned that routers forward packets using IP addresses rather than domain names. |

---

## Engineering Questions

- Why do computers need IP addresses?
- Why does DNS exist?
- Why are routers distributed?
- Why do protocols exist?
- Why isn't HTTP secure?
- Why was HTTPS introduced?
- Why can't we simply encrypt the key?
- Why do ports exist?

---

## Engineering Principles Reinforced

- Redundancy
- Separate Naming from Routing
- Layered Problem Solving

---

## Key Takeaways

- DNS resolves domain names into IP addresses before communication begins.
- Routers determine the path to an IP address; they do not understand domain names.
- `ping` verifies reachability by sending small test packets and measuring round-trip latency.
- TTL prevents packets from circulating indefinitely due to routing loops.
- Networking commands are engineering observation tools used to answer specific questions rather than commands to memorize.

---

## Questions Parked

- TLS Handshake
- Certificates
- Certificate Authority
- TCP vs UDP
- NAT
- Subnetting

## Documentation Updated

- ENGINEERING_PRINCIPLES.md
- AI_IN_PRACTICE.md
- phase-01-internet-and-networking.md