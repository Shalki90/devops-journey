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

### Engineering Reasoning

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

### Troubleshooting Interview Scenarios

- A container starts successfully and exits after two seconds. Explain your troubleshooting approach.
- An application was rebuilt, but the running container still behaves like the old version. Explain your investigation process.
- `docker --version` works, but `docker info` cannot connect to the Docker Engine. Walk through your troubleshooting approach.

### Engineering Principles Reinforced

- Reuse what already exists; store only what is different.
- Separate responsibilities into independent components.
- Automate repetitive work.
- Preserve immutable artifacts.
- Optimize for reproducibility and consistency.