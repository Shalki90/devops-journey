# Docker Interview

## Foundations

- Why was Docker created?
- Containers vs Virtual Machines.
- Why does Docker share the Linux kernel?
- Explain cgroups and namespaces.
- Why does Docker use a daemon?
- Explain Docker CLI -> dockerd -> containerd -> runc -> Kernel.
- Difference between image and container.
- Explain writable layer.
- What is Copy-on-Write?
- Why are images layered?
- Why is build cache important?
- Explain a Dockerfile.
- What is a Docker Registry?
- Why are registries useful in production?
- Explain the complete lifecycle of a Docker container.
- Explain Attached Mode vs Detached Mode.
- Explain Port Publishing (`-p`).
- Explain what happens when `docker stop`, `docker start`, and `docker restart` are executed.
- Why can one image create multiple containers?

---

## Docker Images & Dockerfile

- Explain the complete Docker image build lifecycle.
- Explain what happens internally when `docker build` is executed.
- Explain the role of the Dockerfile parser.
- Explain how Docker decides whether to reuse a cached layer.
- What is a temporary build container?
- Why does Docker destroy the temporary build container after committing a layer?
- Explain the difference between image metadata and image filesystem.
- Explain filesystem instructions vs metadata instructions.
- Explain the purpose of `FROM`.
- Explain the purpose of `RUN`.
- Explain the difference between `COPY` and `ADD`.
- Explain the purpose of `WORKDIR`.
- Explain the purpose of `ENV`.
- Explain the purpose of `USER`.
- Explain the purpose of `LABEL`.
- Explain the purpose of `EXPOSE`.
- Explain the difference between `CMD` and `ENTRYPOINT`.
- Explain why `HEALTHCHECK` exists.
- Explain why `STOPSIGNAL` exists.
- Explain why `SHELL` exists.
- Explain why `ONBUILD` exists.
- Explain how image layers improve efficiency.
- Explain why images are immutable.
- Explain why Dockerfile is declarative instead of procedural.

---

## Engineering Reasoning

- Why are Docker images immutable?
- Why does every container receive its own writable layer instead of writing directly to the image?
- Why did engineers introduce Dockerfile instead of manually creating containers?
- Why are Docker images built using layers?
- Why does Docker use build cache instead of rebuilding every layer?
- Why are Docker registries preferred over manually sharing images?
- Why is the `latest` tag discouraged in production?
- Why does Kubernetes benefit from immutable Docker images?
- Why are images and containers treated as separate objects?
- Why does Docker separate stop, start, restart, and remove into different commands instead of one lifecycle command?
- Why does Docker prevent deleting an image that is still referenced by containers?
- Why does Docker keep stopped containers instead of automatically deleting them?
- Why does Detached Mode exist?
- Why does Docker separate metadata from the filesystem?
- Why does Docker execute filesystem instructions inside temporary build containers?
- Why are metadata instructions stored directly inside the image instead of executing in a build container?
- Why does Docker treat images as build artifacts rather than running systems?
- Why does Docker use exit codes (`0` / non-zero) for `HEALTHCHECK` instead of interpreting application logs?
- Why is graceful shutdown delegated to the application instead of Docker forcibly terminating every process?
- Why is `ONBUILD` useful for organizational standardization?
- Why is `SHELL` configurable instead of being hardcoded?
- Why is Dockerfile considered an engineering specification instead of a deployment script?

---

## Troubleshooting Interview Scenarios

- A container starts successfully and exits after two seconds. Explain your troubleshooting approach.
- An application was rebuilt, but the running container still behaves like the old version. Explain your investigation process.
- `docker --version` works, but `docker info` cannot connect to the Docker Engine. Walk through your troubleshooting approach.
- A container shows **Running** but **Unhealthy**. Explain your troubleshooting process.
- Docker rebuilds every layer even though only one file changed. Explain possible causes.
- A Docker image becomes significantly larger after adding one instruction. How would you investigate?
- A `HEALTHCHECK` reports the container as unhealthy even though the process is still running. Explain why this can happen.
- A container ignores `docker stop` and is eventually killed. Explain what you would investigate.
- A child image unexpectedly executes commands that are not present in its Dockerfile. Explain the cause.
- A `COPY` instruction fails even though the file exists on your computer. Explain your troubleshooting approach.

---

## Engineering Principles Reinforced

- Reuse what already exists; store only what is different.
- Separate responsibilities into independent components.
- Automate repetitive work.
- Preserve immutable artifacts.
- Optimize for reproducibility and consistency.
- Separate build phase from runtime phase.
- Respect ownership and responsibility boundaries.
- Standardize behaviour through centralized definitions.
- Design systems for scalability rather than one-time execution.

---

## Question

A container is reported as "slow". Which Docker commands would you use to investigate, and in what order?

### Expected Discussion

- Verify the container is running.
- Check resource utilisation.
- Inspect running processes.
- Review application logs.
- Inspect container metadata only if configuration verification is required.

### Key Learning

Different Docker commands observe different aspects of a container:

- `docker stats` → Resource utilisation
- `docker top` → Running processes
- `docker logs` → Application output
- `docker inspect` → Docker metadata