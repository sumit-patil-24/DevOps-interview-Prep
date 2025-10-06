# 🐳 Docker Troubleshooting & Debugging Cheat Sheet

A complete reference guide to identify, debug, and fix common Docker issues.  
Ideal for DevOps engineers and interview preparation.

---

## 🧱 1️⃣ Container Status & Lifecycle

| Command | Description |
|----------|--------------|
| `docker ps` | List running containers |
| `docker ps -a` | List all containers (including stopped) |
| `docker inspect <container>` | Get detailed info (env, network, volumes, image) |
| `docker inspect -f '{{.State.ExitCode}}' <container>` | Check exit code (0=ok, 1=crash, 137=OOM) |

---

## 📜 2️⃣ Logs & Output

| Command | Description |
|----------|--------------|
| `docker logs <container>` | View container logs |
| `docker logs -f <container>` | Follow logs live |
| `docker logs --tail 50 <container>` | Show last 50 lines |
| `docker-compose logs -f` | View live logs for all services |
| `docker-compose logs -f <service>` | View logs for a specific service |

---

## 🧠 3️⃣ Debug Inside Container

| Command | Description |
|----------|--------------|
| `docker exec -it <container> /bin/bash` | Open shell (Ubuntu/Debian) |
| `docker exec -it <container> /bin/sh` | Open shell (Alpine) |
| `docker cp <container>:/path /host/path` | Copy files from container |
| `docker cp /host/path <container>:/path` | Copy files to container |
| `docker run -it ubuntu /bin/bash` | Start a temporary debug container |

---

## 🌐 4️⃣ Networking & Connectivity

| Command | Description |
|----------|--------------|
| `docker network ls` | List networks |
| `docker network inspect <network>` | Inspect network details |
| `docker exec -it <container> ping <other-container>` | Test container connectivity |
| `docker port <container>` | Check exposed ports |
| `curl http://localhost:<port>` | Test connectivity from host |

---

## 💾 5️⃣ Storage & Volumes

| Command | Description |
|----------|--------------|
| `docker volume ls` | List all volumes |
| `docker volume inspect <volume>` | Inspect volume details |
| `docker inspect -f '{{json .Mounts}}' <container>` | View container mounts |

---

## 🧩 6️⃣ Images & Builds

| Command | Description |
|----------|--------------|
| `docker images` | List images |
| `docker image prune` | Remove dangling images |
| `docker history <image>` | See image layer history |
| `docker build -t <name> . --progress=plain` | Verbose build logs |
| `docker inspect <image>` | Inspect image metadata |

---

## ⚙️ 7️⃣ Resource Usage

| Command | Description |
|----------|--------------|
| `docker stats` | Show live CPU/memory/network usage |
| `docker top <container>` | Show processes inside container |
| `docker system df` | Disk usage summary |
| `docker system prune` | Remove unused containers/images/volumes |

---

## 🧱 8️⃣ Docker Compose & Multi-Service Apps

| Command | Description |
|----------|--------------|
| `docker-compose ps` | Show status of all services |
| `docker-compose restart <service>` | Restart a specific service |
| `docker-compose up -d --build` | Rebuild and restart containers |
| `docker-compose exec <service> bash` | Open shell in a running service |

---

## 🔐 9️⃣ Security & Users

| Command | Description |
|----------|--------------|
| `docker exec <container> whoami` | Check running user inside container |
| `docker scan <image>` | Scan image for vulnerabilities |

---

## 🩺 🔟 Quick Troubleshooting Flow

| Problem | Commands / Steps |
|----------|------------------|
| Container won’t start | `docker ps -a`, `docker logs <id>` |
| Port not accessible | `docker port <id>`, `curl localhost:<port>` |
| Container restarts | `docker inspect <id> --format='{{.State.ExitCode}}'` |
| DB connection issues | `docker network inspect <net>`, `ping db` |
| Data not persisting | `docker volume inspect <vol>` |
| Slow build | `docker history <image>` |
| High memory usage | `docker stats`, `docker inspect` |

---

### ✅ **Tips**
- Keep this cheat sheet open in one terminal window while debugging.
- Add aliases for frequent commands in your `.bashrc` or `.zshrc`.
- Combine with `grep`, `jq`, and `less` for faster filtering.

---

**Author:** Sumit Patil  
**Purpose:** For DevOps learning & Docker interview preparation 🚀
