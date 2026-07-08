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
| Immutable Image | Read-only image that never changes after creation.|
| PID 1| The primary process inside a container. The container exits when this process ends.|
| Attached Mode | Docker execution mode where the CLI remains connected to the container's stdout and stderr until the process exits or the user detaches. |
| Detached Mode | Docker execution mode (`-d`) where the container runs in the background and the CLI immediately returns control to the terminal. |
| Logging Driver | Docker component responsible for capturing and managing a container's stdout and stderr streams. |
| OCI Bundle | Standardized package containing a container's configuration and root filesystem passed from containerd to runc. |
| Port Publishing | Mapping a host port to a container port using the `-p` option. |
| Storage Driver | Docker component responsible for managing image layers and each container's writable layer on disk. |