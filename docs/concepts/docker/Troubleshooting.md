# Docker Troubleshooting

| Problem | Likely Cause | Resolution |
|---------|--------------|------------|
| docker command fails | dockerd not running | Start Docker service |
| Slow image build | Cache invalidated | Optimize Dockerfile layer order |
| Image pull fails | Network/auth/tag issue | Verify connectivity, credentials and tag |
| Disk usage grows | Writable layer increasing | Use volumes and remove unused containers |
| Container affects itself | Resource exhaustion within cgroup | Investigate processes inside container |
| Host under pressure | No resource limits configured | Apply CPU/Memory limits |

---

# Investigation Methodology

## Scenario 1 — Container exits immediately

| Investigation | Reason |
|--------------|--------|
| Did the container start successfully? | Confirms Docker architecture is functioning. |
| Did the image exist? | The image must exist if the container started. |
| Did the main application terminate? | A container stops when PID 1 exits. |
| Investigate application logs and startup configuration. | Focus shifts from Docker to the application. |

---

## Scenario 2 — New image behaves like the old version

| Investigation | Reason |
|--------------|--------|
| Was the image rebuilt successfully? | Verify a new image was actually created. |
| Was the correct image deployed? | Wrong tags or versions are common. |
| Was Docker Build Cache reused? | Cached layers may legitimately be reused. |
| Was the Dockerfile updated correctly? | Incorrect COPY order or build context can exclude changes. |
| Was the application source copied into the image? | Ensure modified files are included in the build. |

---

## Scenario 3 — Docker CLI cannot connect to Docker Engine

| Investigation | Reason |
|--------------|--------|
| Does `docker --version` work? | Confirms the Docker CLI is installed correctly. |
| Does `docker info` return client information but fail on the server? | Indicates the CLI is available but cannot communicate with the Docker Engine. |
| Is Docker Desktop / Docker Engine running? | The daemon must be running before it can accept requests. |
| Check `docker context ls`. | Confirms the CLI is targeting the expected Docker Engine endpoint. |
| Verify the named pipe / Docker Engine endpoint exists. | If the endpoint is unavailable, the daemon has not started successfully. |
| Start Docker Desktop or the Docker Engine service, then retry. | Restores communication between the CLI and the daemon. |