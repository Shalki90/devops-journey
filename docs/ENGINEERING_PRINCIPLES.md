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
| Visibility Enables Understanding | Systems become easier to understand, troubleshoot, and improve when their behavior can be directly observed rather than inferred. | Observability reduces assumptions and allows engineers to validate how systems actually behave. | Phase 01 - Wireshark |
| End-to-End Identification | Every network connection must be uniquely identifiable using source and destination information. | Prevents ambiguity when multiple simultaneous communications exist between systems. | Phase 01 - TCP Connections |
| Separation of Responsibilities | A listening socket accepts new connections, while each established connection handles communication with a single client. | Improves scalability, simplifies system design, and allows servers to serve many clients simultaneously. | Phase 01 - TCP Connections |
| Abstraction | Hide implementation details behind a stable interface so consumers remain unaffected by internal changes. | Allows systems to evolve without breaking clients and reduces coupling between components. | Phase 01 - Reverse Proxy |
| Horizontal Scalability | Increase system capacity by adding more identical components rather than continuously increasing the size of a single component. | Improves scalability, availability, and fault tolerance while avoiding hardware limits. | Phase 01 - Load Balancer |
| Health-Based Decision Making | Make routing and operational decisions using the current health of system components rather than assuming every component is always available. | Prevents failures from propagating to users and improves overall system reliability. | Phase 01 - Load Balancer |
| Transparency to Clients | Infrastructure changes should remain invisible to clients whenever possible. Clients should interact with stable interfaces while the infrastructure evolves behind the scenes. | Enables maintenance, migrations, scaling, and upgrades without impacting consumers. | Phase 01 - Reverse Proxy |
| Stable Service Endpoints | Long-running services should expose stable endpoints while individual client interactions remain temporary. | Allows clients to reliably locate services while enabling the server to continuously accept new work. | Phase 01 - HTTP Servers |
| Connection Lifecycle | Establish, use, and terminate connections as independent units of work rather than assuming communication is permanent. | Simplifies resource management, improves reliability, and enables systems to handle many independent interactions. | Phase 01 - HTTP Servers |
| Stateless Request Handling | Whenever practical, treat each client request as independent of previous requests unless state is explicitly required. | Improves scalability, fault tolerance, and enables systems to distribute work across multiple servers. | Phase 01 - HTTP Servers |
| Separation of Responsibilities | Complex systems are built by dividing responsibilities into independent components that work together.   | Makes systems easier to build, debug, replace, and evolve.       | Linux Boot Process    |
| Layered Architecture      | Systems should be organized into layers where each layer provides services to the one above while hiding internal complexity. | Reduces coupling and allows each layer to evolve independently.  | Linux Architecture    |
| Stable Interfaces, Replaceable Implementations | Components should communicate through well-defined interfaces so implementations can change without affecting the rest of the system. | Enables flexibility, maintainability, and hardware independence. | System Calls & Device Drivers |
| Kernel-Centric Resource Management | The kernel is solely responsible for creating, scheduling, managing, and terminating processes. Applications request resources but never control them directly. | Prevents resource conflicts, maintains security, and ensures fair scheduling across the system. | Phase 03 – Processes       |
| Every Running Process Must Have Ownership  | Every running process must always have a parent. If its parent terminates, `systemd` (PID 1) adopts it.       | Ensures every process remains managed and prevents unmanaged execution.    | Phase 03 – Processes       |
| Failure Isolation     | The failure of an intermediate process should not unnecessarily terminate useful work. Linux adopts orphan processes instead of terminating them.       | Improves reliability and resilience of long-running services.      | Phase 03 – Processes       |
| Graceful Before Forceful Termination       | Always attempt graceful shutdown (`SIGTERM`) before using forceful termination (`SIGKILL`).      | Allows applications to save work, release resources, and exit safely.      | Phase 03 – Signals |
| Terminal Ownership    | Only one foreground process owns the terminal at any given time. Background processes execute without blocking user interaction.   | Ensures predictable interaction between users and running applications.    | Phase 03 – Process Control |
| Separation of Operating System and Application Responsibilities | The operating system manages process lifecycle and resources, while applications determine their own runtime behavior.     | Promotes modularity, stability, and clear separation of concerns.  | Phase 03 – Processes       |
| Signals as Standardized Process Communication   | Linux uses signals as standardized software interrupts to communicate process control requests.  | Provides a consistent and efficient mechanism for controlling running processes.| Phase 03 – Signals |
| Standardized Organization   | Organizing resources using a fixed filesystem hierarchy instead of arbitrary locations.     | Enables portability, troubleshooting, automation, and consistency across Linux systems.    | Filesystem Hierarchy       |
| Context-Based Navigation    | Relative paths allow navigation based on the current working directory instead of repeating full paths.  | Reduces redundancy and simplifies navigation.    | Absolute vs Relative Paths |
| Avoid Repeating Known Information   | The operating system provides shortcuts (`~`, `..`, `.`) because it already knows the current user and current location. | Improves usability while reducing unnecessary repetition.     | Filesystem Navigation      |
| Behavior-Driven Classification      | Objects are classified by how they behave rather than simply how they are stored.   | Allows the kernel to choose the correct operations for regular files, devices, pipes, sockets, and directories. | File Types |
| Separate Identity from Naming       | Linux separates filenames from the file's identity (inode).    | Renaming files becomes inexpensive and enables advanced filesystem features like hard links.    | Inodes     |
| Reference-Based Resource Management | Resources remain allocated while valid references exist rather than being deleted when one name disappears.      | Prevents accidental data loss and enables efficient storage sharing through hard links.    | Hard Links |
| Indirection Through References      | Symbolic links reference another object's location instead of the object itself.    | Enables flexible shortcuts while maintaining filesystem modularity.   | Symbolic Links     |
| Single Responsibility in System Calls | Unix separates process creation (`fork()`) from program execution (`exec()`), with each system call performing one well-defined task.       | Simpler APIs are easier to understand, compose, and maintain.       | Phase 03 – Processes  |
| Fair CPU Scheduling   | CPU time is divided among runnable processes using short time slices instead of allowing one process to monopolize the processor.   | Ensures responsiveness and fairness across the entire operating system.  | Phase 03 – Process Scheduling |
| Execution State Preservation  | The operating system preserves a process's execution context before switching to another process and restores it later.     | Enables multitasking while giving every process the illusion of uninterrupted execution. | Phase 03 – Context Switching  |
| Resource Virtualization       | The operating system presents virtual resources (such as memory) instead of exposing physical hardware directly to applications.    | Provides isolation, protection, flexibility, and portability.       | Phase 03 – Virtual Memory     |
| Lazy Resource Allocation      | Resources should be allocated only when they are actually needed rather than immediately upon request. | Maximizes efficiency and prevents unnecessary resource consumption. | Phase 03 – Demand Paging      |
| Lifetime-Based Memory Organization    | Memory is organized according to object lifetime: temporary data belongs on the Stack, while long-lived dynamic objects belong on the Heap. | Simplifies memory management and optimizes performance.     | Phase 03 – Stack vs Heap      |
| Accountability vs Access     | Ownership establishes accountability; permissions determine access. These are separate concepts.   | Prevents confusion between responsibility and authorization. | Phase 03 – Ownership & Permissions     |
| Principle of Least Privilege | Users should receive only the permissions necessary to perform their responsibilities.      | Reduces accidental damage and limits security risks.  | Phase 03 – Users, Groups & Permissions |
| Role-Based Access     | Users performing similar responsibilities should inherit permissions through groups rather than individual assignments. | Improves scalability and simplifies administration.   | Phase 03 – Groups |
| Separation of Responsibility | Ownership changes should be deliberate administrative actions rather than automatic consequences of permission changes. | Preserves accountability and system integrity. | Phase 03 – Ownership     |
| Observability  | Systems should record sufficient information to understand their behaviour and failures.    | Enables troubleshooting, auditing, and root-cause analysis.  | Phase 03 – Logs   |
| Principle of Least Exposure  | Only expose services that actually require external access.     | Reduces attack surface and improves security.  | Phase 03 – SSH    |
| Controlled Interfaces | Components should communicate through defined interfaces rather than direct access.  | Simplifies maintenance and improves security boundaries.     | Phase 03 – systemd / SSH |
| Dependency Management | Components with dependencies must start in a controlled order while independent components can run in parallel.  | Improves reliability and boot efficiency.      | Phase 03 – systemd       |
| Graceful Change       | Prefer reloading configuration over restarting services when possible. | Minimizes downtime and user disruption. | Phase 03 – Services      |
| Single Source of Truth        | Maintain one authoritative copy of shared resources.       | Simplifies maintenance and updates.         | Phase 03 - Package Manager  |
| Don't Repeat Yourself (DRY)   | Avoid duplicating identical functionality or resources.    | Reduces redundancy and inconsistency.       | Phase 03 - Package Manager   |
| Configuration over Hardcoding | Store configurable behavior outside the application logic. | Makes systems flexible and maintainable.    | Phase 03 - Package Manager   |
| Centralized Maintenance       | Shared resources should be updated in one place.           | One fix benefits every dependent component. | Phase 03 - Package Manager   |

---

## Notes

- Add principles only after they naturally emerge during discussions.
- Principles should be technology-independent whenever possible.
- Prefer timeless engineering wisdom over tool-specific advice.
- If a concept only applies to one technology, it belongs in documentation—not in this file.
- Every principle should be reusable across multiple technologies and domains.

---

Version: 0.4

Status: Living Document