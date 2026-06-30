# AI in Practice

## Purpose

This document captures how engineering concepts are applied in modern AI systems and infrastructure.

The goal is to connect foundational engineering knowledge with real-world AI implementations.

---

| Concept     | AI Application     | Why It Matters     | Domain      |
| --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | ------------------------- |
| Internet    | AI services such as ChatGPT, Claude, Gemini and other LLM platforms are accessed over the Internet.    | Enables global access to AI services.   | Networking  |
| DNS  | AI applications rely on DNS to resolve service domains into IP addresses before communication begins.  | Makes AI services discoverable using human-friendly names.   | Networking  |
| Routing     | Requests to AI services travel through multiple routers and data centers before reaching the hosting infrastructure. | Enables scalable and reliable communication across the Internet.    | Networking  |
| HTTP | Most AI APIs expose REST endpoints over HTTP (e.g., `POST /chat/completions`).    | Provides a standardized method for client-server communication.     | Networking  |
| HTTPS       | AI providers encrypt prompts, responses and authentication tokens using HTTPS.    | Protects user privacy and API credentials during transmission.      | Networking  |
| Public Key Cryptography   | TLS certificates use public key cryptography to establish secure communication between clients and AI services.      | Enables secure and trusted communication.      | Networking  |
| Server      | AI models execute on powerful GPU-equipped servers rather than users' local machines.    | Provides the computational resources required for inference. | Networking  |
| Port | Multiple AI services running on the same machine communicate through different network ports.   | Allows multiple services to coexist on a single machine without conflict.  | Networking  |
| DNS Resolution     | AI clients resolve service domains (e.g., ChatGPT, Claude, Gemini) into IP addresses before sending requests. | Without DNS resolution, AI services cannot be reached over the Internet.   | Networking  |
| Redundancy  | AI platforms deploy multiple servers and regions to continue serving requests when individual machines or data centers fail.       | Ensures high availability and minimizes service disruption for millions of users. | Networking  |
| Network Diagnostics       | Engineers use tools such as `ping`, `nslookup`, and `curl` to verify connectivity before investigating application-level issues.   | Helps isolate networking problems before debugging AI applications or infrastructure.    | Networking  |
| TCP Connection Identification (4-Tuple) | AI inference servers uniquely manage thousands of simultaneous client requests using source/destination IPs and ports.      | Enables scalable request handling across shared infrastructure.     | AI Infrastructure  |
| Listening vs Established Connections    | AI model servers continuously listen for new inference requests while simultaneously serving active clients.  | Forms the basis of scalable AI serving platforms and APIs.   | AI Serving Infrastructure |
| Firewall    | AI infrastructure uses firewalls to restrict access to model servers, databases, and internal services, allowing only authorized traffic. | Prevents unauthorized access while protecting critical AI infrastructure.  | AI Infrastructure  |
| Reverse Proxy      | AI platforms terminate client connections at reverse proxies (such as Nginx or Envoy), which route requests to the appropriate inference service.       | Provides a stable public endpoint while hiding and protecting backend services.   | AI Serving Infrastructure |
| Load Balancer      | AI providers distribute inference requests across many identical model servers using load balancers.   | Prevents overload, improves response time, and enables horizontal scaling. | AI Serving Infrastructure |
| Health Checks      | AI serving platforms continuously monitor model server health and automatically stop routing traffic to unhealthy instances.       | Improves availability and prevents failed inference requests from reaching users. | AI Serving Infrastructure |
| Horizontal Scaling | Large Language Models are typically served by many identical inference servers rather than a single powerful machine.       | Enables systems to handle millions of concurrent requests while remaining highly available.     | AI Infrastructure  |
| Separation of Responsibilities   | Modern AI platforms separate responsibilities across infrastructure components: firewalls secure traffic, reverse proxies route requests, load balancers distribute load, and inference servers execute models. | Simplifies operations, improves scalability, and allows independent evolution of each layer.    | Platform Engineering      |
| HTTP Request Lifecycle    | Every AI API request follows the same lifecycle: client request → TCP connection → HTTP request → inference → HTTP response.       | Understanding this flow simplifies debugging and designing AI services.    | AI Serving Infrastructure |
| HTTP Headers       | AI platforms use HTTP headers to exchange metadata such as authentication tokens, content types, request identifiers, and caching information.   | Enables secure, standardized, and extensible communication between clients and AI services.     | API Design  |
| Long-Running Inference Servers   | AI inference servers remain continuously available, accepting new client requests while previous requests complete independently.  | Enables uninterrupted service for thousands or millions of users.   | AI Serving Infrastructure |
| Ephemeral Client Connections     | Each AI API request is typically served through an independent client connection while the inference service continues listening on a stable endpoint.  | Improves scalability, simplifies connection management, and supports high request volumes.      | AI Infrastructure  |
| Raw Protocol Understanding       | Building a simple HTTP server from raw sockets provides insight into how AI serving frameworks such as FastAPI, Flask, vLLM, Triton Inference Server, and TensorRT-LLM ultimately communicate with clients.     | Understanding lower-level protocols makes higher-level AI infrastructure easier to debug and reason about.    | AI Platform Engineering   |
| Packet Capture     | AI infrastructure engineers use packet capture tools such as Wireshark to inspect network traffic between clients, APIs, reverse proxies, load balancers, and model servers. | Provides direct visibility into how systems behave rather than relying solely on assumptions or logs.  | Observability      |
| TLS Encryption     | AI platforms protect prompts, responses, API keys, and user data using TLS encryption during network transmission.   | Prevents intermediaries from reading application data while still allowing packets to be routed across the Internet. | Security    |
| Visible Metadata vs Encrypted Data      | Even when AI traffic is encrypted, infrastructure components can still observe source IPs, destination IPs, ports, protocols, and packet sizes.  | Explains how networking equipment can forward traffic without accessing protected application content. | Networking  |
| Protocol Layering  | AI requests travel through multiple protocol layers including Ethernet, IP, TCP, TLS, HTTP, and application logic.   | Understanding layered protocols simplifies troubleshooting and infrastructure design.    | Systems Engineering       |
| Network Observability     | AI platform engineers validate connectivity, latency, encryption, routing, and service behavior using network observability tools. | Direct observation reduces guesswork and accelerates troubleshooting.      | Platform Engineering      |
| Request Path Visibility   | AI providers can observe where requests travel through infrastructure without viewing encrypted payload contents.    | Enables routing, monitoring, scaling, and security enforcement while preserving user privacy.   | AI Infrastructure  |
| Permission Auditing   | AI can identify overly permissive files, detect inconsistent permission patterns, and recommend least-privilege configurations.  | Improves security posture and reduces human error.       | Security  |
| Identity & Access Management | AI can analyze user and group memberships to identify excessive privileges or orphaned accounts.     | Supports scalable access governance.       | Infrastructure Security |
| Ownership Analysis    | AI can detect files with incorrect ownership after deployments or migrations and suggest corrective actions.       | Prevents permission-related outages and improves accountability.       | Linux Administration    |
| Log Analysis   | AI can summarize large log datasets, identify recurring failures, correlate events across services, and accelerate root-cause analysis. | Reduces Mean Time To Resolution (MTTR) and improves incident response. | Observability    |
| SSH Security   | AI can detect unusual login patterns, brute-force attempts, impossible travel, and anomalous remote access behaviour.     | Improves infrastructure security and threat detection.   | Security  |
| Service Failure Correlation  | AI can correlate failures across multiple services managed by systemd and suggest probable dependency chains.      | Assists engineers during complex production incidents.   | Infrastructure   |
| Package Management   | Explain dependency trees and package relationships.   | Helps understand complex software ecosystems. | Linux  |
| Dependency Analysis  | Identify missing dependencies and installation order. | Useful during troubleshooting.                | Linux  |
| Repository Selection | Explain repository structure and package sources.     | Helps diagnose installation problems.         | Linux  |

---

Version: 0.4

Status: Living Document
