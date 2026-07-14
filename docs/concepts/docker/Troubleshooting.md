# Docker Troubleshooting

| Problem | Likely Cause | Resolution |
|---------|--------------|------------|
| docker command fails | dockerd not running | Start Docker service |
| Slow image build | Cache invalidated | Optimize Dockerfile layer order |
| Image pull fails | Network/auth/tag issue | Verify connectivity, credentials and tag |
| Disk usage grows | Writable layer increasing | Use volumes and remove unused containers |
| Container affects itself | Resource exhaustion within cgroup | Investigate processes inside container |
| Host under pressure | No resource limits configured | Apply CPU/Memory limits |
| Container reports **Unhealthy** | HEALTHCHECK command failing | Verify the healthcheck command, application endpoint and exit codes |
| Image rebuilds completely | Docker Build Cache invalidated | Review Dockerfile instruction order and build context |
| Image unexpectedly grows in size | Large filesystem changes or poor Dockerfile ordering | Reduce unnecessary layers and optimize instruction order |
| Container ignores graceful shutdown | Incorrect or unsupported stop signal | Verify `STOPSIGNAL` and application signal handling |

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

---

## Scenario 4 — Container is running but the application is unhealthy

| Investigation | Reason |
|--------------|--------|
| Does `docker ps` show the container as running? | Confirms the container lifecycle is healthy before investigating the application. |
| Check `docker stats <container>`. | Identifies CPU, memory, network or I/O resource pressure. |
| Check `docker top <container>`. | Verifies the expected application processes are running. |
| Review `docker logs <container>`. | Identifies application startup failures or runtime errors. |
| Use `docker exec -it <container> bash` for further investigation. | Allows inspection of the runtime environment without recreating the container. |
| Use `docker inspect` if configuration verification is required. | Confirms metadata such as ports, environment variables, restart policy and mounts. |

---

## Scenario 5 — Every image layer rebuilds unexpectedly

| Investigation | Reason |
|--------------|--------|
| Was a file copied before dependency installation? | Early filesystem changes invalidate all downstream cache. |
| Did the build context change? | Docker cache depends on instruction inputs as well as the instruction itself. |
| Was the Dockerfile instruction modified? | Any change to an instruction invalidates its cached layer. |
| Check Docker build output. | Confirms exactly where cache reuse stopped. |
| Reorder Dockerfile instructions if appropriate. | Stable instructions should appear before frequently changing instructions. |

---

## Scenario 6 — HEALTHCHECK reports Unhealthy while the container is still running

| Investigation | Reason |
|--------------|--------|
| Is the application process (PID 1) still running? | Running and healthy are different states. |
| Execute the healthcheck command manually inside the container. | Confirms whether the command itself succeeds. |
| Verify the application's health endpoint. | Confirms the application defines health correctly. |
| Check the command's exit code. | Docker only evaluates success (`0`) or failure (non-zero). |
| Review HEALTHCHECK configuration. | Incorrect intervals, retries or commands may produce false failures. |

---

## Scenario 7 — Container does not stop gracefully

| Investigation | Reason |
|--------------|--------|
| Does the application handle Linux signals? | Docker only delivers the signal. The application performs the shutdown. |
| Verify the configured `STOPSIGNAL`. | Confirms Docker is sending the expected signal. |
| Check whether PID 1 is the application. | PID 1 receives the stop signal. |
| Review application shutdown logs. | Confirms whether cleanup routines executed successfully. |
| Verify child processes terminate correctly. | Prevents orphaned processes during shutdown. |

---

## Scenario 8 — Child image behaves unexpectedly during build

| Investigation | Reason |
|--------------|--------|
| Is the parent image using `ONBUILD`? | Child builds automatically execute inherited ONBUILD instructions. |
| Inspect the parent Dockerfile. | Confirms which ONBUILD instructions are registered. |
| Review build logs. | Shows when inherited instructions are triggered. |
| Verify whether inherited behaviour is intentional. | Determines whether ONBUILD is appropriate for the parent image. |