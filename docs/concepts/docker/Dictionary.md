# Docker Dictionary

| Term | Definition |
|------|------------|
| Docker | Platform for packaging and running applications in containers. |
| Container | Isolated runtime instance of an image. |
| Image | Read-only blueprint used to create containers. |
| Docker CLI | User interface for Docker commands. |
| Docker Daemon (dockerd) | Background service managing Docker objects. |
| Docker API | API used by the CLI to communicate with dockerd. |
| Docker Go Template | Go template syntax used with `docker inspect -f` to extract specific metadata fields without printing the complete JSON output. |
| containerd | Manages the lifecycle of containers. |
| runc | Low-level OCI runtime that creates Linux containers. |
| Linux Kernel | Shared operating system kernel used by all containers. |
| cgroups | Kernel feature for resource allocation and limits. |
| Namespaces | Kernel feature providing isolation. |
| Writable Layer | Per-container writable layer above image layers. |
| Copy-on-Write | Store only changed data while reusing existing layers. |
| Image Layer | Immutable filesystem layer created during image build. |
| Build Cache | Previously built layers reused to speed builds. |
| Dockerfile | Declarative instructions for building images. |
| Registry | Repository used to store and distribute images. |
| Docker Hub | Public Docker registry. |
| Immutable Image | Read-only image that never changes after creation. |
| PID 1 | The primary process inside a container. The container exits when this process ends. |
| Attached Mode | Docker execution mode where the CLI remains connected to the container's stdout and stderr until the process exits or the user detaches. |
| Detached Mode | Docker execution mode (`-d`) where the container runs in the background and the CLI immediately returns control to the terminal. |
| Logging Driver | Docker component responsible for capturing and managing a container's stdout and stderr streams. |
| OCI Bundle | Standardized package containing a container's configuration and root filesystem passed from containerd to runc. |
| Port Publishing | Mapping a host port to a container port using the `-p` option. |
| Storage Driver | Docker component responsible for managing image layers and each container's writable layer on disk. |
| Build Context | The directory and files sent to Docker during `docker build` that are available to Dockerfile instructions such as `COPY` and `ADD`. |
| Parent Image | The base image referenced by the `FROM` instruction from which a new image is built. |
| Child Image | A newly created image that extends a parent image by adding additional layers or metadata. |
| Image Metadata | Configuration stored inside an image that defines runtime behaviour without modifying the filesystem. |
| Image Filesystem | The collection of immutable filesystem layers that make up the image's file contents. |
| Filesystem Instruction | A Dockerfile instruction that changes the image filesystem by creating a new filesystem layer (for example: `RUN`, `COPY`, `ADD`). |
| Metadata Instruction | A Dockerfile instruction that updates image configuration without modifying the filesystem (for example: `ENV`, `WORKDIR`, `USER`, `CMD`). |
| Temporary Build Container | An ephemeral container created by Docker to execute filesystem-changing Dockerfile instructions during the build process. It is committed into a new image layer and then destroyed. |
| Build Planner | Internal Docker Engine logic that parses the Dockerfile, determines the build sequence, identifies cache reuse opportunities, and coordinates layer creation. |
| Layer Commit | The process of converting the filesystem changes made inside a temporary build container into a new immutable image layer. |
| Cache Hit | Docker successfully reuses an existing image layer because both the Dockerfile instruction and its inputs are unchanged. |
| Cache Miss | Docker rebuilds a layer because the instruction or its inputs differ from a previously cached build. |
| Layer Reuse | Docker's ability to share identical immutable layers across multiple images and containers to reduce storage and build time. |
| FROM | Dockerfile instruction that specifies the parent image and starts a new image build. |
| RUN | Dockerfile instruction that executes commands during image creation and produces a new filesystem layer. |
| COPY | Dockerfile instruction that copies files from the build context into the image filesystem. |
| ADD | Dockerfile instruction similar to `COPY` but with additional capabilities such as automatic archive extraction and remote URL support. |
| WORKDIR | Dockerfile instruction that defines the default working directory for subsequent instructions and container execution. |
| ENV | Dockerfile instruction that defines environment variables stored in the image metadata. |
| USER | Dockerfile instruction that specifies the default user used to execute subsequent instructions and runtime processes. |
| EXPOSE | Dockerfile instruction that documents the network ports the application is expected to listen on. |
| LABEL | Dockerfile instruction used to attach descriptive metadata to an image. |
| CMD | Dockerfile instruction that specifies the default command executed when a container starts if no command is provided at runtime. |
| ENTRYPOINT | Dockerfile instruction that defines the primary executable that always runs when the container starts. |
| HEALTHCHECK | Dockerfile instruction that periodically executes a command inside a running container to determine whether the application is healthy. |
| SHELL | Dockerfile instruction that changes the default shell used for subsequent shell-form instructions. |
| STOPSIGNAL | Dockerfile instruction that specifies which signal Docker sends to PID 1 during graceful container shutdown. |
| ONBUILD | Dockerfile instruction that registers build instructions to be automatically executed when the image is used as the base image for another build. |