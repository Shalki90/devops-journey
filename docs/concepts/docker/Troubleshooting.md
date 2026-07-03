# Docker Troubleshooting

| Problem | Likely Cause | Resolution |
|---------|--------------|------------|
| docker command fails | dockerd not running | Start Docker service |
| Slow image build | Cache invalidated | Optimize Dockerfile layer order |
| Image pull fails | Network/auth/tag issue | Verify connectivity, credentials and tag |
| Disk usage grows | Writable layer increasing | Use volumes and remove unused containers |
| Container affects itself | Resource exhaustion within cgroup | Investigate processes inside container |
| Host under pressure | No resource limits configured | Apply CPU/Memory limits |
