# Session 03

## Topics

- TCP vs UDP
- TCP Reliability
- UDP Characteristics
- Sequence Numbers
- Acknowledgements (ACK)
- Packet Ordering
- Duplicate Packet Detection
- TCP Three-Way Handshake
- TCP Four-Way Connection Termination
- TCP Connection Identification (4-Tuple)
- LISTENING vs ESTABLISHED States
- Ephemeral Ports
- Client and Server Port Allocation

---

## Hands-on Labs

### Lab 1 — DNS Resolution

Commands Used:

```bash
nslookup github.com
```

Observations:

- Verified DNS resolution of `github.com`.
- Identified GitHub's public IP address.
- Identified the configured DNS server.
- Understood that DNS translates human-readable domain names into IP addresses.

---

### Lab 2 — Connectivity Testing

Commands Used:

```bash
ping github.com
```

Observations:

- Verified that `ping` first performs DNS resolution before sending ICMP packets.
- Confirmed that `ping` resolved `github.com` to the same IP returned by `nslookup`.
- Observed successful communication with GitHub.
- Understood packet size, round-trip time (RTT), and packet statistics.
- Discussed the purpose of TTL (Time To Live).

---

### Lab 3 — Inspect Active TCP Connections

Commands Used:

```powershell
Get-NetTCPConnection
```

Observations:

- Observed multiple active TCP connections on the local machine.
- Identified Local Address and Local Port.
- Understood that applications communicate through ports rather than IP addresses alone.
- Learned that Windows assigns ephemeral (temporary) source ports for outgoing connections.

---

### Lab 4 — LISTENING vs ESTABLISHED

Commands Used:

```cmd
netstat -ano
```

Observations:

- Observed TCP sockets in the LISTENING state.
- Observed active ESTABLISHED connections.
- Understood that a listening socket waits for incoming client connections.
- Learned that established connections are created after the TCP three-way handshake.
- Understood that one listening socket can create multiple established connections.

---

### Lab 5 — Observe Live HTTPS Connections

Commands Used:

```powershell
Get-NetTCPConnection | Where-Object {$_.RemotePort -eq 443}
```

Observations:

- Identified a live HTTPS connection to GitHub.
- Verified that GitHub listens on remote port 443.
- Observed Windows assigning a unique ephemeral source port.
- Understood how multiple browser tabs create separate TCP connections using different source ports.
- Verified that a TCP connection is uniquely identified by Source IP, Source Port, Destination IP, and Destination Port.

---

## Engineering Questions

- Why do different applications choose TCP or UDP?
- Why does TCP require acknowledgements?
- Why are sequence numbers necessary?
- Why does TCP require a three-way handshake instead of two?
- Why is a four-way termination used?
- Why does a listening socket not require a remote IP address?
- Why do client applications use ephemeral ports?
- How does a server distinguish millions of simultaneous clients using the same destination port?

---

## Engineering Insights

- Application requirements determine whether TCP or UDP should be used.
- Reliability is a design decision based on business requirements.
- A server continuously listens for new connections while simultaneously serving existing clients.
- TCP connections are uniquely identified using the 4-tuple:
  - Source IP
  - Source Port
  - Destination IP
  - Destination Port
- Operating systems automatically manage ephemeral ports for outgoing client connections.

---

## Questions Parked

- IPv4 vs IPv6
- ICMP
- Packet Fragmentation
- TCP Window Size
- Congestion Control
- Flow Control
- Keep-Alive