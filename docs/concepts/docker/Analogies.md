# Docker Analogies

## Docker
| Component | Analogy |
|----------|----------|
| Linux | School building |
| Docker | Locker management system |
| Container | Individual locker |
| Image | Warehouse containing master toys |
| Writable Layer | Personal items inside one locker |
| Registry | Central warehouse |
| Dockerfile | Instruction manual for building identical lockers |
| Layers | Lego blocks reused across builds |
| Build Cache | Reusing already assembled Lego sections |
| cgroups | Resource budget allocated to each locker |
| Namespaces | Walls separating lockers |
| Docker CLI          | Receptionist receiving customer requests              |
| dockerd             | Restaurant Operations Manager coordinating everything |
| containerd          | Kitchen Manager supervising food preparation          |
| runc                | Chef preparing the actual meal                        |
| Shared Image Layers | One warehouse supplying many lockers                  |
| Immutable Image     | Blueprint kept in a secure cabinet                    |
| Copy-on-Write       | Photocopy a page only when someone writes on it       |
| Build Cache         | Chef reusing already prepared ingredients             |

---

## Docker Runtime Flow (Hotel Analogy)

| Component | Analogy |
|----------|----------|
| User | Hotel guest |
| Docker CLI | Reception receiving the guest's request |
| dockerd | Hotel Operations Manager verifying availability and arranging resources |
| Image | Standard room blueprint available within the hotel |
| containerd | Floor Manager coordinating room allocation, networking, and resources |
| OCI Bundle | Guest check-in file containing room allocation and configuration details |
| runc | Room Manager escorting the guest into the allocated room before leaving |
| Linux Kernel | Hotel Management authorizing room creation and enforcing hotel policies |
| Container | Allocated hotel room prepared for the guest |
| PID 1 | Guest occupying the room |
| Detached Mode | Reception returns to serving other guests while the guest continues staying in the room |
| Port Publishing | Reception explicitly exposing the guest's room number so visitors know where to reach them |
| docker exec | Reception temporarily sending hotel staff into an occupied room | Creates a new process inside an already running container without creating a new room (container). |
| docker inspect | Hotel management system | Retrieves the complete record of a room (container) without entering it. |
| docker inspect -f | Hotel receptionist answering a specific question | Returns only the requested detail from the room record instead of the entire file. |
| docker top | CCTV control room | Allows hotel management to see everyone currently inside a specific room (container). |
| docker stats | Patient vital monitor | Continuously displays the current health metrics of the room (container), such as resource consumption. |