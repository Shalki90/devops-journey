# Analogies

## Purpose

This document captures analogies and mental models that simplify complex engineering concepts.

The goal is to build intuitive understanding through simple real-world comparisons, making concepts easier to remember and explain.

---

| Concept | Analogy | Why It Helps | Domain |
|---------|----------|--------------|--------|
| Engineering Foundation | Building a house before constructing the upper floors. | Strong foundations make everything built later more stable. | Engineering |
| System Design | Planning a city before constructing buildings. | Good systems are designed before implementation begins. | Engineering |
| Internet | A global courier delivery network. | Demonstrates that data travels through multiple intermediate locations before reaching its destination. | Networking |
| DNS | Saving someone's phone number under their name instead of remembering the number. | Humans remember names; computers communicate using IP addresses. | Networking |
| Routing | A courier passing through multiple sorting centers before reaching the destination. | Shows that each router decides only the next hop rather than the complete journey. | Networking |
| Router | A courier sorting center. | Explains how routers forward packets to the next destination. | Networking |
| Server | An apartment building containing multiple residents (applications). | Distinguishes the computer (building) from the services running inside it. | Networking |
| Port | The apartment number identifying the exact resident. | Explains how multiple applications can exist on the same computer. | Networking |
| Protocol | Two people agreeing to speak the same language before starting a conversation. | Illustrates why communication requires agreed rules. | Networking |
| HTTP | A conversation in a public place where anyone nearby can overhear. | Demonstrates that communication is readable during transmission. | Networking |
| HTTPS | A private conversation that outsiders cannot understand. | Explains encrypted communication over the Internet. | Networking |
| Packet Capture | Security Camera Footage | Allows engineers to observe what actually happened instead of relying on assumptions or second-hand reports. | Observability |
| Wireshark | Traffic Control Room Monitor | Provides visibility into the movement of packets across the network in real time. | Observability |
| TLS Encryption | Sealed Envelope | The envelope can be delivered and routed using visible address information, but only the intended recipient can read the contents. | Networking |
| Packet Headers | Shipping Label | Contains routing information needed for delivery even when the package contents remain hidden. | Networking |
| Public Key Cryptography | A public mailbox where anyone can drop a letter, but only the owner can unlock and read it. | Explains how public and private keys work together. | Networking |
| LAN (Private Network) | Apartment Building | Multiple devices communicate within a private environment before reaching the Internet. | Networking |
| Public IP Address | Building Address | Represents the globally reachable address of a private network. | Networking |
| Private IP + Port | Apartment Number | Identifies a specific application running inside a device on the private network. | Networking |
| NAT | Reception / Entry Gate | Translates public addresses into private destinations before forwarding traffic. | Networking |
| Firewall | Security Guard | Examines visitors and enforces security rules before allowing entry. | Networking |
| Firewall Rules | Building Rule Book | Defines which visitors are allowed or denied entry. | Networking |
| Stateful Firewall | Visitor Register / Notebook | Remembers active visitors so repeated checks are unnecessary during an active conversation. | Networking |
| Reverse Proxy | Receptionist | Receives requests first, decides whether to answer directly or forward them to the appropriate application. | Networking |
| Application | Doctor | Performs the actual work requested by the client. | Networking |
| Application Instances | Multiple Doctors | Multiple identical workers increase capacity and availability. | Networking |
| Load Balancer | Receptionist assigning visitors to available doctors | Distributes work across multiple healthy application instances. | Networking |
| Health Check | Receptionist checking whether a doctor is available | Prevents new requests from being routed to unavailable services. | Networking |
| Static Content / Cache | Brochure available at reception | Frequently requested information can be served without disturbing the application. | Networking |
| Infrastructure Abstraction | Apartment renovation while visitors remain unaffected | Internal infrastructure can change without affecting clients. | Networking |
| Listening Port | Open Door | An application is ready to accept new connections. | Networking |
| Closed Port | Closed Door | No application is available to receive requests. | Networking |
| UDP Communication | Window | Information can pass without establishing a formal conversation. | Networking |
| Routing Algorithm | GPS | Chooses the most appropriate path toward the destination. | Networking |
| Routing Table | City Map | Stores known routes used to reach different destinations. | Networking |
| Network Links | Roads | Physical or logical paths that connect systems. | Networking |
| TCP SYN | Ringing the Doorbell | Requests permission to begin communication. | Networking |
| TCP SYN-ACK | Resident saying "Come In" | Accepts the connection request. | Networking |
| TCP Communication | Conversation between visitor and doctor | Represents an established communication session. | Networking |
| TCP Connection Termination | Visitor leaving the building | Gracefully closes an active conversation. | Networking |
| Connection Timeout | Security guard forgetting the visitor | Connection state expires after inactivity. | Networking |
| SSH / Maintenance | Electrician visiting the apartment | Administrative access used for maintenance rather than normal user interaction. | Networking |
| Wrong Port | Visitor going to the wrong apartment | Request reaches the wrong application. | Networking |
| No Service Listening | Apartment not occupied | The destination exists but no application is available to respond. | Networking |
| Listening Socket | Reception desk waiting for visitors | A server continuously waits for new client connections without serving a specific client itself. | Networking |
| Established Connection | Private consultation room | After a visitor is accepted, communication happens in a dedicated space separate from the reception desk. | Networking |
| HTTP Request | Visitor explaining why they came | The client sends its request, including the method, destination, and additional information. | Networking |
| HTTP Response | Doctor providing treatment and instructions | The server returns the requested result along with status information. | Networking |
| Client Ephemeral Port | Temporary visitor badge | Assigned only for the duration of a conversation and changes with each new visit. | Networking |
| Long-Running Server | Reception desk that never closes | The server remains available to accept new clients even after previous conversations end. | Networking |

---

## Notes

- Add analogies only after they have been discussed and validated.
- Prefer simple real-world examples over technical explanations.
- Organize entries by engineering domain.
- Maintain this document as the master index of analogies. Detailed explanations belong in the corresponding files under `docs/analogies/`.

---

Version: 0.4

Status: Living Document