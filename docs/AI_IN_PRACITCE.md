# AI in Practice

## Purpose

This document captures how engineering concepts are applied in modern AI systems and infrastructure.

The goal is to connect foundational engineering knowledge with real-world AI implementations.

---

| Concept | AI Application | Why It Matters | Domain |
|---------|----------------|----------------|--------|
| Internet | AI services such as ChatGPT, Claude, Gemini and other LLM platforms are accessed over the Internet. | Enables global access to AI services. | Networking |
| DNS | AI applications rely on DNS to resolve service domains into IP addresses before communication begins. | Makes AI services discoverable using human-friendly names. | Networking |
| Routing | Requests to AI services travel through multiple routers and data centers before reaching the hosting infrastructure. | Enables scalable and reliable communication across the Internet. | Networking |
| HTTP | Most AI APIs expose REST endpoints over HTTP (e.g., `POST /chat/completions`). | Provides a standardized method for client-server communication. | Networking |
| HTTPS | AI providers encrypt prompts, responses and authentication tokens using HTTPS. | Protects user privacy and API credentials during transmission. | Networking |
| Public Key Cryptography | TLS certificates use public key cryptography to establish secure communication between clients and AI services. | Enables secure and trusted communication. | Networking |
| Server | AI models execute on powerful GPU-equipped servers rather than users' local machines. | Provides the computational resources required for inference. | Networking |
| Port | Multiple AI services running on the same machine communicate through different network ports. | Allows multiple services to coexist on a single machine without conflict. | Networking |
| DNS Resolution | AI clients resolve service domains (e.g., ChatGPT, Claude, Gemini) into IP addresses before sending requests. | Without DNS resolution, AI services cannot be reached over the Internet. | Networking |
| Redundancy | AI platforms deploy multiple servers and regions to continue serving requests when individual machines or data centers fail. | Ensures high availability and minimizes service disruption for millions of users. | Networking |
| Network Diagnostics | Engineers use tools such as `ping`, `nslookup`, and `curl` to verify connectivity before investigating application-level issues. | Helps isolate networking problems before debugging AI applications or infrastructure. | Networking |
| TCP Connection Identification (4-Tuple) | AI inference servers uniquely manage thousands of simultaneous client requests using source/destination IPs and ports. | Enables scalable request handling across shared infrastructure. | AI Infrastructure |
| Listening vs Established Connections | AI model servers continuously listen for new inference requests while simultaneously serving active clients. | Forms the basis of scalable AI serving platforms and APIs. | AI Serving Infrastructure |
| Firewall | AI infrastructure uses firewalls to restrict access to model servers, databases, and internal services, allowing only authorized traffic. | Prevents unauthorized access while protecting critical AI infrastructure. | AI Infrastructure |
| Reverse Proxy | AI platforms terminate client connections at reverse proxies (such as Nginx or Envoy), which route requests to the appropriate inference service. | Provides a stable public endpoint while hiding and protecting backend services. | AI Serving Infrastructure |
| Load Balancer | AI providers distribute inference requests across many identical model servers using load balancers. | Prevents overload, improves response time, and enables horizontal scaling. | AI Serving Infrastructure |
| Health Checks | AI serving platforms continuously monitor model server health and automatically stop routing traffic to unhealthy instances. | Improves availability and prevents failed inference requests from reaching users. | AI Serving Infrastructure |
| Horizontal Scaling | Large Language Models are typically served by many identical inference servers rather than a single powerful machine. | Enables systems to handle millions of concurrent requests while remaining highly available. | AI Infrastructure |
| Separation of Responsibilities | Modern AI platforms separate responsibilities across infrastructure components: firewalls secure traffic, reverse proxies route requests, load balancers distribute load, and inference servers execute models. | Simplifies operations, improves scalability, and allows independent evolution of each layer. | Platform Engineering |
| HTTP Request Lifecycle | Every AI API request follows the same lifecycle: client request → TCP connection → HTTP request → inference → HTTP response. | Understanding this flow simplifies debugging and designing AI services. | AI Serving Infrastructure |
| HTTP Headers | AI platforms use HTTP headers to exchange metadata such as authentication tokens, content types, request identifiers, and caching information. | Enables secure, standardized, and extensible communication between clients and AI services. | API Design |
| Long-Running Inference Servers | AI inference servers remain continuously available, accepting new client requests while previous requests complete independently. | Enables uninterrupted service for thousands or millions of users. | AI Serving Infrastructure |
| Ephemeral Client Connections | Each AI API request is typically served through an independent client connection while the inference service continues listening on a stable endpoint. | Improves scalability, simplifies connection management, and supports high request volumes. | AI Infrastructure |
| Raw Protocol Understanding | Building a simple HTTP server from raw sockets provides insight into how AI serving frameworks such as FastAPI, Flask, vLLM, Triton Inference Server, and TensorRT-LLM ultimately communicate with clients. | Understanding lower-level protocols makes higher-level AI infrastructure easier to debug and reason about. | AI Platform Engineering |

---

Version: 0.3

Status: Living Document