# Session 05

## Topics

- HTTP Request and Response
- HTTP Headers
- HTTP Status Codes
- HTTP vs HTTPS
- TLS Handshake Observations
- curl
- Python Built-in HTTP Server
- TCP Socket Programming
- Listening Socket vs Client Socket
- Client Connection Lifecycle
- Persistent Server Design

---

## Hands-on Labs

### Lab 1 — Inspect HTTP Requests using curl

Commands Used:

```powershell
curl.exe -I https://example.com

curl.exe -v https://example.com
```

Observations:

- Observed HTTP response headers returned by the server.
- Identified commonly used headers including:
  - Content-Type
  - Server
  - Date
  - `cf-cache-status`
- Observed that HTTPS communication establishes a TLS connection before the HTTP request is exchanged.
- Observed ALPN negotiation during HTTPS connection establishment.
- Compared verbose (`-v`) output with header-only (`-I`) output.

---

### Lab 2 — Compare HTTP vs HTTPS

Commands Used:

```powershell
curl.exe -v http://example.com

curl.exe -v https://example.com
```

Observations:

- HTTP communicates immediately after the TCP connection is established.
- HTTPS performs a TLS handshake before exchanging HTTP messages.
- Observed communication over port 80 (HTTP) and port 443 (HTTPS).
- Observed TLS negotiation including ALPN.
- Discussed TLS renegotiation and why encrypted sessions may renegotiate security parameters.
- Understood that HTTP data is exchanged only after a secure TLS channel has been established.

---

### Lab 3 — Python Built-in HTTP Server

Commands Used:

```powershell
python -m http.server 8000
```

Observations:

- Started a local HTTP server.
- Verified the server listens on TCP port 8000.
- Accessed the server using a web browser.
- Observed incoming browser requests.
- Verified the listening socket using `netstat`.

---

### Lab 4 — Build a Basic HTTP Server using Python Sockets

Implementation:

- Created a TCP socket.
- Bound the socket to port 8000.
- Started listening for incoming connections.
- Accepted an incoming browser connection.
- Received a raw HTTP request.
- Constructed and returned a valid HTTP response manually.
- Returned HTML content directly to the browser.

Observations:

- Browsers communicate using plain HTTP messages over TCP.
- HTTP requests are human-readable text.
- Browsers successfully render HTML returned by the server.
- A server must return correctly formatted HTTP responses for browsers to understand them.

---

### Lab 5 — Continuous HTTP Server

Implementation:

- Converted the server into a continuously running service using an infinite loop.

Observations:

- The listening socket remains active throughout the server's lifetime.
- Each browser refresh creates a completely new TCP connection.
- Every client connection receives a newly assigned ephemeral source port.
- The server continues listening on the same destination port (8000).
- Client sockets are short-lived while the listening socket is long-lived.
- Observed that only client sockets are closed after serving a request, while the listening socket continues accepting new connections.

---

## Engineering Questions

- Why does HTTPS require TLS before HTTP communication begins?
- Why do servers continue listening after serving a client?
- Why does every browser refresh create a new TCP connection?
- Why does the server keep the same listening port while clients receive new ephemeral ports?
- Why are listening sockets and client sockets separate objects?
- Why do production web servers continuously accept connections instead of terminating after one request?

---

## Engineering Insights

- HTTP is an application protocol built on top of TCP.
- HTTPS secures HTTP by establishing a TLS session before exchanging application data.
- A listening socket accepts incoming connections but does not communicate directly with clients.
- Each accepted client connection receives its own dedicated socket.
- Client connections are temporary, while server sockets remain available for future clients.
- Modern web servers continuously accept new client connections instead of restarting after every request.
- Browsers automatically allocate ephemeral ports for each new TCP connection.
- A TCP connection is created, used, and destroyed for each independent browser request unless persistent connections are explicitly used.

---

## Repository Updates

Updated:

- `curriculum/phase-01-internet-and-networking.md`

Pending:

- Engineering documentation updates.
- GitHub repository push.

---

## Questions Parked

- HTTP/2
- HTTP/3 (QUIC)
- Keep-Alive connections
- Persistent HTTP Connections
- Multi-threaded servers
- Asynchronous web servers

---

## Next Session

### Phase 02 — Git & Version Control

Topics:

- Why Version Control Exists
- Git Fundamentals
- Local Repository
- Working Tree
- Staging Area
- Commit History
- Basic Git Workflow

Hands-on Labs:

- Initialize a Git repository.
- Create the first commit.
- Explore Git history.
- Understand the Git object model.