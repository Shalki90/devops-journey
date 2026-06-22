# Engineering Principles

## Purpose

This document captures timeless engineering principles discovered throughout the learning journey.

These principles are independent of any specific technology and are intended to guide engineering thinking, design decisions, and problem-solving.

---

| Principle | Description | Why It Matters | First Seen |
|-----------|-------------|----------------|------------|
| Understanding over Memorization | Understand why something exists before learning how to use it. | Leads to long-term retention and better problem-solving. | Engineering OS |
| Single Responsibility | Each component should solve one specific problem. | Makes systems easier to understand, maintain and evolve. | Internet & Networking Fundamentals |
| Standardization | Agreed standards allow independently built systems to communicate seamlessly. | Enables interoperability between independently built systems. | Internet & Networking Fundamentals |
| Distributed Decision Making | Large systems scale better when decisions are distributed rather than centralized. | Improves scalability, reliability and fault tolerance. | Internet & Networking Fundamentals |
| Defense in Depth | Security should rely on multiple independent layers rather than a single protection mechanism. | Reduces the impact of a single point of failure. | Internet & Networking Fundamentals |
| Security Scope | Every security mechanism solves a specific problem. Do not expect it to solve problems outside its intended scope. | Encourages choosing the right solution for the right problem. | Internet & Networking Fundamentals |
| Failure-Oriented Thinking | Ask not only "How does it work?" but also "What assumptions does it make?" and "What happens if they fail?" | Builds resilient systems and improves troubleshooting skills. | Internet & Networking Fundamentals |
| Reduce Cognitive Load | Use standards, conventions and predictable designs to minimize the amount of information humans need to remember. | Makes systems easier to learn, use and maintain. | Internet & Networking Fundamentals |
| Redundancy | Critical systems should avoid single points of failure by providing multiple components that can continue serving requests if one component becomes unavailable. | Improves reliability, fault tolerance, and service availability by eliminating single points of failure. | Session 03 - Networking |
| Separate Naming from Routing | DNS resolves names into IP addresses, while routers determine how packets reach those IP addresses. | Separating responsibilities keeps the Internet simpler, scalable, and easier to maintain. | Session 03 - Networking |
| Layered Problem Solving | Troubleshoot systems in dependency order by verifying lower layers before higher layers. | Reduces troubleshooting time by identifying failures systematically instead of guessing. | Session 03 - Networking |
| End-to-End Identification | Every network connection must be uniquely identifiable using source and destination information. | Prevents ambiguity when multiple simultaneous communications exist between systems. | Phase 01 - TCP Connections |
| Separation of Responsibilities | A listening socket accepts new connections, while each established connection handles communication with a single client. | Improves scalability, simplifies system design, and allows servers to serve many clients simultaneously. | Phase 01 - TCP Connections |
| Abstraction | Hide implementation details behind a stable interface so consumers remain unaffected by internal changes. | Allows systems to evolve without breaking clients and reduces coupling between components. | Phase 01 - Reverse Proxy |
| Horizontal Scalability | Increase system capacity by adding more identical components rather than continuously increasing the size of a single component. | Improves scalability, availability, and fault tolerance while avoiding hardware limits. | Phase 01 - Load Balancer |
| Health-Based Decision Making | Make routing and operational decisions using the current health of system components rather than assuming every component is always available. | Prevents failures from propagating to users and improves overall system reliability. | Phase 01 - Load Balancer |
| Transparency to Clients | Infrastructure changes should remain invisible to clients whenever possible. Clients should interact with stable interfaces while the infrastructure evolves behind the scenes. | Enables maintenance, migrations, scaling, and upgrades without impacting consumers. | Phase 01 - Reverse Proxy |
| Stable Service Endpoints | Long-running services should expose stable endpoints while individual client interactions remain temporary. | Allows clients to reliably locate services while enabling the server to continuously accept new work. | Phase 01 - HTTP Servers |
| Connection Lifecycle | Establish, use, and terminate connections as independent units of work rather than assuming communication is permanent. | Simplifies resource management, improves reliability, and enables systems to handle many independent interactions. | Phase 01 - HTTP Servers |
| Stateless Request Handling | Whenever practical, treat each client request as independent of previous requests unless state is explicitly required. | Improves scalability, fault tolerance, and enables systems to distribute work across multiple servers. | Phase 01 - HTTP Servers |

---

## Notes

- Add principles only after they naturally emerge during discussions.
- Principles should be technology-independent whenever possible.
- Prefer timeless engineering wisdom over tool-specific advice.
- If a concept only applies to one technology, it belongs in documentation—not in this file.
- Every principle should be reusable across multiple technologies and domains.

---

Version: 0.3

Status: Living Document