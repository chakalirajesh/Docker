# 📦 04 - Docker Containers

> Understanding Docker Containers, Lifecycle, States, and Management.

---

# 📚 Table of Contents

* What is a Docker Container?
* Why Containers?
* Image vs Container
* Container Architecture
* Container Lifecycle
* Container States
* Running Containers
* Managing Containers
* Logs and Troubleshooting
* Interview Questions
* Summary

---

# 📖 What is a Docker Container?

A Docker Container is a lightweight, isolated runtime environment created from a Docker Image.

Containers package everything required to run an application:

* Application Code
* Runtime Environment
* Libraries
* Dependencies
* Configuration Files

Unlike Virtual Machines, containers share the host operating system kernel, making them lightweight and efficient.

---

# ❓ Why Containers?

Containers solve the "Works on My Machine" problem by ensuring applications run consistently across environments.

### Problems Without Containers

❌ Dependency Conflicts

❌ Environment Differences

❌ Slow Deployment

❌ Difficult Scaling

### Benefits of Containers

✅ Fast Startup

✅ Portability

✅ Consistency

✅ Scalability

✅ Resource Efficiency

---

# ⚔ Image vs Container

| Docker Image   | Docker Container |
| -------------- | ---------------- |
| Blueprint      | Running Instance |
| Read-Only      | Read/Write       |
| Static         | Dynamic          |
| Stored on Disk | Runs in Memory   |

### Simple Example

```text
Docker Image  ──►  Docker Container

Blueprint     ──►  House

Class         ──►  Object
```

---

# 🏗 Container Architecture

A container is created from an image.

```text
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ Docker Image │ ─► │ docker run   │ ─► │ Container    │
└──────────────┘    └──────────────┘    └──────────────┘
```

### Explanation

1. Docker reads the image.
2. Docker creates a writable layer.
3. Container starts.
4. Application runs.

---

# 🔄 Container Lifecycle

Containers pass through several states during their lifecycle.

```text
┌─────────┐ ─► ┌─────────┐ ─► ┌─────────┐ ─► ┌─────────┐
│ Created │    │ Running │    │ Stopped │    │ Removed │
└─────────┘    └─────────┘    └─────────┘    └─────────┘
```

### Created

Container exists but has not started.

### Running

Container is actively executing processes.

### Stopped

Container exists but is not running.

### Removed

Container has been deleted permanently.

---

# 🚦 Container States

Docker containers can have different states.

```text
Created ─► Running ─► Paused
              │
              ▼
          Restarting
              │
              ▼
           Exited
              │
              ▼
            Dead
```

Check Container States:

```bash
docker ps -a
```

---

# 🚀 Running Containers

### Run Container

```bash
docker run nginx
```

### Run Container in Background

```bash
docker run -d nginx
```

### Run Container with Name

```bash
docker run --name web-server nginx
```

### Run Container with Port Mapping

```bash
docker run -d -p 80:80 nginx
```

---

# 📋 Managing Containers

### View Running Containers

```bash
docker ps
```

### View All Containers

```bash
docker ps -a
```

### Stop Container

```bash
docker stop container_id
```

### Start Container

```bash
docker start container_id
```

### Restart Container

```bash
docker restart container_id
```

### Remove Container

```bash
docker rm container_id
```

---

# 📜 Viewing Container Logs

Logs help troubleshoot running applications.

### View Logs

```bash
docker logs container_id
```

### Follow Logs

```bash
docker logs -f container_id
```

### Last 50 Lines

```bash
docker logs --tail 50 container_id
```

---

# 💻 Access Container Shell

### Bash Shell

```bash
docker exec -it container_id bash
```

### Alpine Linux Shell

```bash
docker exec -it container_id sh
```

Example:

```bash
docker exec -it nginx-container bash
```

---

# 🎯 Interview Questions

### What is a Docker Container?

A Docker Container is a lightweight isolated runtime environment created from a Docker Image.

---

### Difference Between Image and Container?

Image = Blueprint

Container = Running Instance

---

### How Do You Access a Running Container?

```bash
docker exec -it container_id bash
```

---

### How Do You View Container Logs?

```bash
docker logs container_id
```

---

### What Command Shows Running Containers?

```bash
docker ps
```

---

# ⚡ Quick Revision

✅ Container = Running Instance of Image

✅ Containers are Lightweight

✅ Containers Share Host OS Kernel

✅ docker run Creates Containers

✅ docker exec Accesses Containers

✅ docker logs Shows Logs

---

# 📝 Summary

In this module, you learned:

* What Containers Are
* Image vs Container
* Container Lifecycle
* Container States
* Running Containers
* Managing Containers
* Viewing Logs
* Accessing Container Shell

Docker Containers are the core execution units of the Docker platform and form the foundation of modern containerized applications.
