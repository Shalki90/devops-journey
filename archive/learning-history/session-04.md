# Session 04

## Topics

- Network Address Translation (NAT)
- Public IP vs Private IP
- Firewall Fundamentals
- Stateless vs Stateful Firewalls
- Firewall Rule Evaluation
- Connection State Tracking
- Reverse Proxy
- Reverse Proxy vs Firewall
- Load Balancer
- Load Balancer Health Checks
- Reverse Proxy vs Load Balancer
- End-to-End Request Journey
- Component Responsibilities

---

## Conceptual Exercises

### Exercise 1 — Firewall Rule Evaluation

Scenarios Discussed:

- Default Deny vs Default Allow
- Rule Ordering
- Allow Rules
- Deny Rules
- Rule Set Organization
- First Match Wins

Observations:

- Firewalls should deny traffic unless explicitly permitted.
- Rule ordering directly affects security.
- Broad allow rules placed before deny rules can unintentionally bypass security.
- Organizing firewall rules into logical groups improves maintainability.

---

### Exercise 2 — Stateful Firewall Thinking

Discussion:

- Should an incoming packet be trusted after the connection expires?

Conclusion:

- Once a connection expires, future packets must be treated as completely new incoming requests.
- Expired state should never be trusted.

---

### Exercise 3 — Reverse Proxy Analogy

Analogy Used:

- Receptionist in a medical clinic.

Responsibilities Identified:

- Verify appointments.
- Decide whether the request can be handled directly.
- Route visitors to the correct doctor.
- Serve common information without disturbing the doctor.
- Hide internal organization from visitors.

Key Insight:

- Reverse proxies manage incoming requests before they reach the application.

---

### Exercise 4 — Load Balancer Analogy

Analogy Used:

- Multiple doctors with identical capabilities.

Responsibilities Identified:

- Check doctor availability.
- Route patients to healthy doctors.
- Distribute workload.
- Prevent one doctor from becoming overloaded.

Key Insight:

- Load balancers improve availability and scalability rather than application functionality.

---

### Exercise 5 — End-to-End Packet Journey

Complete Request Flow Discussed:

1. Client sends request.
2. Request reaches Router.
3. NAT maps Public IP to Private IP.
4. Firewall evaluates security rules.
5. Reverse Proxy receives the request.
6. Load Balancer selects a healthy application instance.
7. Application executes business logic.
8. Response returns through the same path.

Observations:

- Each component owns a single responsibility.
- Components work together as a pipeline.
- Infrastructure should simplify applications, not complicate them.

---

### Exercise 6 — Networking Analogy Mapping

Completed:

- Canonical networking analogy table.
- Canonical reverse proxy analogy.
- Canonical load balancer analogy.

Outcome:

- Established a reusable analogy library for future learning.

---

## Hands-on Labs

No hands-on labs were performed during this session.

Reason:

The session focused on building conceptual understanding of networking infrastructure. Practical exercises will be completed before marking Phase 01 complete.

Planned Labs:

- HTTP Requests using `curl`
- HTTP vs HTTPS
- Local Web Server
- Packet Capture (Optional)

---

## Engineering Questions

- Why is NAT separated from firewall functionality?
- Why should firewalls not perform application routing?
- Why do reverse proxies exist when routers already forward traffic?
- Why is a load balancer separate from the application itself?
- Why should unhealthy servers stop receiving traffic?
- Why do production systems separate responsibilities across infrastructure components?

---

## Engineering Insights

- Every infrastructure component should own a single responsibility.
- Reverse proxies abstract backend infrastructure from clients.
- Load balancers improve scalability by distributing traffic across identical instances.
- Firewalls provide security, not application routing.
- NAT performs address translation, not security enforcement.
- Healthy infrastructure depends on continuous health verification.
- Separating responsibilities simplifies system evolution and maintenance.

---

## Repository Updates

Created:

- `docs/analogies/networking.md`

Updated:

- `curriculum/phase-01-internet-and-networking.md`
- `ENGINEERING_PRINCIPLES.md`
- `AI_IN_PRACTICE.md`

Pending:

- Phase 01 Hands-on Labs
- GitHub Repository Review

---

## Questions Parked

- Reverse Proxy implementations (Nginx, Envoy, HAProxy)
- Load Balancing algorithms
- Session Affinity
- Active vs Passive Health Checks
- Layer 4 vs Layer 7 Load Balancers

---

## Next Session

### Complete Phase 01

Hands-on Labs:

- Inspect HTTP Requests using `curl`
- Compare HTTP vs HTTPS
- Run a Local Web Server
- Observe Packets using Wireshark (Optional)

After successful completion:

- Mark Phase 01 Complete.
- Push repository to GitHub.
- Begin Phase 02 — Git & Version Control.