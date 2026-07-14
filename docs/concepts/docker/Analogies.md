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
| Docker CLI | Receptionist receiving customer requests |
| dockerd | Restaurant Operations Manager coordinating everything |
| containerd | Kitchen Manager supervising food preparation |
| runc | Chef preparing the actual meal |
| Shared Image Layers | One warehouse supplying many lockers |
| Immutable Image | Blueprint kept in a secure cabinet |
| Copy-on-Write | Photocopy a page only when someone writes on it |
| Build Cache | Chef reusing already prepared ingredients |

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
| docker exec | Reception temporarily sending hotel staff into an occupied room. Creates a new process inside an already running container without creating a new room (container). |
| docker inspect | Hotel management system. Retrieves the complete record of a room (container) without entering it. |
| docker inspect -f | Hotel receptionist answering a specific question. Returns only the requested detail from the room record instead of the entire file. |
| docker top | CCTV control room. Allows hotel management to see everyone currently inside a specific room (container). |
| docker stats | Patient vital monitor. Continuously displays the current health metrics of the room (container), such as resource consumption. |

---

# Docker Images & Dockerfile (Module 3)

| Component | Analogy |
|----------|----------|
| Dockerfile | Cake recipe describing how to bake the cake, not the cake itself |
| Docker Image | Finished cake baked from the recipe and ready to be copied many times |
| Image Metadata | Sticky notes attached to the recipe describing how the cake should be served |
| Image Filesystem | Ingredients and cake layers physically present inside the finished cake |
| FROM | Selecting the base cake before adding your own decorations |
| RUN | Chef performing cooking steps while preparing the master cake |
| COPY | Bringing your own ingredients into the kitchen before baking |
| ADD | COPY with additional abilities, like unpacking a gift box before placing it in the kitchen |
| WORKDIR | Chef deciding which kitchen counter all future work will happen on |
| ENV | Kitchen rules written on a whiteboard for every chef to follow |
| USER | Deciding which chef is allowed to perform the remaining work |
| LABEL | Product information sticker attached to the cake box |
| EXPOSE | Restaurant advertising which service window customers should use |
| CMD | Default meal served unless the customer orders something else |
| ENTRYPOINT | Restaurant itself; customers may customise the order but cannot change the restaurant |
| CMD + ENTRYPOINT | Restaurant defines the meal type; customer chooses the toppings |
| HEALTHCHECK | Quality inspector periodically tasting the food and reporting only "Pass" or "Fail" |
| SHELL | Common language spoken by every chef in the kitchen |
| STOPSIGNAL | Fire alarm instructing everyone to close the kitchen safely before leaving |
| ONBUILD | Franchise blueprint automatically executed whenever a new branch restaurant is opened |
| Temporary Build Container | Temporary construction workshop demolished immediately after the building phase finishes |
| Build Cache | Chef reusing previously prepared ingredients instead of cooking everything again |
| Layer Reuse | Reusing already constructed Lego sections instead of rebuilding them |
| Image Immutability | Master blueprint locked inside a vault; every new building starts from a fresh copy |
| Build Context | Delivery truck bringing all available project materials to the construction site |
| Parser | Architect reading the blueprint and preparing the construction plan before any work begins |
| Docker Engine Build Planner | Project manager deciding which construction activities happen first and which existing work can be reused |
| Commit | Taking a photograph of the completed construction stage before starting the next one |