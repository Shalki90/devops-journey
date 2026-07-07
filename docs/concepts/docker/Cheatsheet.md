# Docker Cheatsheet

> Quick reference for frequently used Docker commands learned during hands-on practice.

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

---

# Key Notes

| Concept | Summary |
|---------|---------|
| Image | Immutable blueprint used to create containers. |
| Container | Running instance of an image. |
| Image Reuse | Multiple containers can be created from the same image. |
| Stop vs Remove | Stopping a container does not delete it. |
| Container Removal | Removing a container does not remove its image. |
| Image Dependency | Docker prevents deleting an image while containers still reference it. |
| Port Publishing | Maps a host port to a container port. |
| Detached Mode | Returns control to the terminal while the container continues running. |