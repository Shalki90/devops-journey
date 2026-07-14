# Docker Cheatsheet

| Cheatsheet.md | Frequently used Docker commands, Dockerfile instructions and quick reference |
|---------------|------------------------------------------------------------------------------|

---

# Docker Information

| Command | Purpose | Notes |
|---------|---------|-------|
| `docker --version` | Display installed Docker CLI version. | Verifies Docker CLI installation. |
| `docker info` | Display Docker Client and Docker Engine information. | Useful for verifying Engine status, Storage Driver, Logging Driver, Runtime, Networking, Kernel and Docker Root Directory. |

---

# Images

| Command | Purpose | Notes |
|---------|---------|-------|
| `docker images` | List all locally available images. | Shows images stored on the host. |
| `docker image ls` | List local images. | Modern equivalent of `docker images`. |
| `docker build -t <image-name>:<tag> .` | Build an image from a Dockerfile. | The `.` represents the build context. |
| `docker history <image>` | Display image layer history. | Useful for understanding image construction. |
| `docker image inspect <image>` | Display complete image metadata. | Returns image configuration and metadata in JSON format. |
| `docker rmi <image>` | Remove an image. | Fails if any container still references the image. |

---

# Containers

| Command | Purpose | Notes |
|---------|---------|-------|
| `docker run <image>` | Create and start a new container. | Downloads the image first if not available locally. |
| `docker run -d <image>` | Run a container in Detached Mode. | Returns control to the terminal immediately. |
| `docker run -p <host-port>:<container-port> <image>` | Publish a container port to the host. | Example: `docker run -d -p 8081:80 nginx` |
| `docker ps` | List running containers. | Displays only containers currently running. |
| `docker ps -a` | List all containers. | Displays running and stopped containers. |
| `docker logs <container>` | View container logs. | Shows stdout/stderr captured by Docker's Logging Driver. |
| `docker stop <container>` | Gracefully stop a running container. | Container remains available for restart. |
| `docker start <container>` | Start an existing stopped container. | Reuses the same container and Container ID. |
| `docker restart <container>` | Restart an existing container. | Equivalent to stop followed by start. |
| `docker rm <container>` | Remove a stopped container. | Running containers must be stopped before removal. |
| `docker exec <container> <command>` | Execute a command inside a running container. | Creates a new process inside the existing container. |
| `docker exec -it <container> bash` | Open an interactive Bash shell inside a running container. | Useful for live investigation and troubleshooting. |
| `docker inspect <container>` | Display complete Docker metadata for a container. | Returns detailed JSON describing the container configuration and state. |
| `docker inspect -f "<template>" <container>` | Display only the requested metadata field. | Uses Go template formatting to avoid printing the complete JSON output. |
| `docker top <container>` | Display running processes inside a container. | Shows the container's process list from Docker. |
| `docker stats <container>` | Display live resource utilisation. | Continuously streams CPU, memory, network, block I/O and process statistics until interrupted. |

---

# Dockerfile Instructions

| Instruction | Category | Purpose |
|------------|----------|---------|
| `FROM` | Filesystem | Select the base image. |
| `RUN` | Filesystem | Execute commands while building the image. |
| `COPY` | Filesystem | Copy files into the image. |
| `ADD` | Filesystem | Copy files with additional extraction/URL capabilities. |
| `WORKDIR` | Metadata | Set the default working directory. |
| `ENV` | Metadata | Define environment variables. |
| `USER` | Metadata | Specify the default execution user. |
| `LABEL` | Metadata | Attach descriptive metadata to the image. |
| `EXPOSE` | Metadata | Document the application's listening port. |
| `CMD` | Metadata | Specify the default runtime command. |
| `ENTRYPOINT` | Metadata | Define the primary executable for the container. |
| `HEALTHCHECK` | Metadata | Define how Docker determines container health. |
| `SHELL` | Metadata | Change the shell used by shell-form instructions. |
| `STOPSIGNAL` | Metadata | Define the signal Docker sends during graceful shutdown. |
| `ONBUILD` | Metadata | Register instructions for child image builds. |

---

# Key Notes

| Concept | Summary |
|---------|---------|
| Image | Immutable blueprint used to create containers. |
| Container | Running instance of an image. |
| Dockerfile | Declarative build specification used to create an image. |
| Image Metadata | Runtime behaviour stored inside the image. |
| Image Filesystem | Files physically stored inside the image layers. |
| Temporary Build Container | Ephemeral container used by Docker while executing filesystem instructions during image builds. |
| Build Cache | Docker reuses previously built layers when instructions and build context remain unchanged. |
| Image Reuse | Multiple containers can be created from the same image. |
| Stop vs Remove | Stopping a container does not delete it. |
| Container Removal | Removing a container does not remove its image. |
| Image Dependency | Docker prevents deleting an image while containers still reference it. |
| Port Publishing | Maps a host port to a container port. |
| Detached Mode | Returns control to the terminal while the container continues running. |
| docker exec | Creates additional processes inside an already running container without creating a new container. |
| docker inspect | Metadata inspection command used to examine Docker-managed configuration and state. |
| docker top | Displays the processes currently running inside a container. |
| docker stats | Live monitoring command for container resource utilisation. |
| Investigation Workflow | Typical observation order: `docker ps` → `docker stats` → `docker top` → `docker inspect` → `docker logs`. |
| Docker Build Workflow | `docker build` → Parse Dockerfile → Reuse cache if possible → Temporary build container → Commit layer → Destroy temporary container → Repeat until final image is produced. |