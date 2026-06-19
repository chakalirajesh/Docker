# 🏗 02 - Docker Architecture

> Understanding how Docker works internally.

---

# 📚 Table of Contents

* What is Docker Architecture?
* Why Learn Docker Architecture?
* Docker Architecture Overview
* Docker Client
* Docker Host
* Docker Daemon
* Docker Engine
* Docker Registry
* Docker Objects
* Docker Workflow
* What Happens During docker run?
* Interview Questions
* Summary

---

# 📖 What is Docker Architecture?

Docker Architecture describes how Docker components work together to build, manage, and run containers.

Understanding Docker Architecture helps you:

✅ Troubleshoot Problems

✅ Understand Container Lifecycle

✅ Work with Docker Professionally

✅ Crack DevOps Interviews

---

# 🏗 Complete Docker Architecture

```text
┌─────────────────────────────────────────────────────────────┐
│                      👨‍💻 Developer                         │
└──────────────────────────┬──────────────────────────────────┘
                           │
                           │ Docker Commands
                           ▼
┌─────────────────────────────────────────────────────────────┐
│                     🐳 Docker Client                       │
│       docker build | run | pull | push | ps               │
└──────────────────────────┬──────────────────────────────────┘
                           │
                           │ REST API
                           ▼
┌─────────────────────────────────────────────────────────────┐
│                    ⚙️ Docker Daemon                        │
│                         dockerd                             │
│                                                             │
│  • Builds Images                                            │
│  • Runs Containers                                          │
│  • Creates Networks                                         │
│  • Manages Volumes                                          │
└───────┬─────────────────┬──────────────────┬───────────────┘
        │                 │                  │
        ▼                 ▼                  ▼

┌──────────────┐  ┌──────────────┐  ┌──────────────┐
│    Images    │  │  Containers  │  │   Networks   │
└──────────────┘  └──────────────┘  └──────────────┘

        │
        ▼

┌─────────────────────────────────────────────────────────────┐
│                  🌍 Docker Registry                        │
│          Docker Hub | AWS ECR | GHCR                       │
└─────────────────────────────────────────────────────────────┘
```


---

# 🖥 Docker Client

The Docker Client is the interface used by developers.

Examples:

```bash
docker build
docker run
docker pull
docker push
docker ps
```

### Responsibilities

* Send Commands
* Communicate with Daemon
* Display Results

### Real Example

```bash
docker run nginx
```

The Docker Client sends this request to the Docker Daemon.

---

# ⚙ Docker Daemon

Docker Daemon (`dockerd`) is the brain of Docker.

It runs in the background and manages everything.

### Responsibilities

* Build Images
* Run Containers
* Create Networks
* Manage Volumes
* Pull Images

Verify daemon:

```bash
systemctl status docker
```

---

# 🔧 Docker Engine

Docker Engine consists of:

```text
Docker Client
      │
Docker REST API
      │
Docker Daemon
```

Together they form Docker Engine.

### Docker Engine Responsibilities

* Container Management
* Image Management
* Networking
* Storage

---

# 🏠 Docker Host

Docker Host is the machine where Docker runs.

Examples:

* Ubuntu Server
* EC2 Instance
* Local Laptop
* Virtual Machine

Contains:

* Docker Engine
* Containers
* Images
* Networks
* Volumes

---

# 🌍 Docker Registry

Docker Registry stores Docker Images.

Examples:

* Docker Hub
* Amazon ECR
* GitHub Container Registry

Pull Image:

```bash
docker pull nginx
```

Push Image:

```bash
docker push myimage
```

---

# 📦 Docker Objects

Docker manages several objects.

### Images

Blueprint for containers.

Example:

```bash
docker images
```

---

### Containers

Running instances of images.

Example:

```bash
docker ps
```

---

### Networks

Communication layer.

Example:

```bash
docker network ls
```

---

### Volumes

Persistent storage.

Example:

```bash
docker volume ls
```

---

# 🔄 Docker Workflow

```text
Developer
    │
docker build
    │
    ▼
Docker Image
    │
docker push
    │
    ▼
Registry
    │
docker pull
    │
    ▼
Docker Host
    │
docker run
    │
    ▼
Container
```

---

# 🚀 What Happens During docker run nginx?

Step 1

```bash
docker run nginx
```

Step 2

Docker Client sends request.

↓

Step 3

Docker Daemon checks local image.

↓

Step 4

If image missing:

```bash
docker pull nginx
```

↓

Step 5

Docker creates container.

↓

Step 6

Container starts.

↓

Step 7

Application becomes available.

---

# 🎯 Interview Questions

### What is Docker Architecture?

Docker Architecture is the interaction between Docker Client, Docker Daemon, Docker Host, and Docker Registry.

---

### What is Docker Daemon?

Background service that manages containers, images, networks, and volumes.

---

### What is Docker Client?

Command-line interface used to communicate with Docker.

---

### What is Docker Registry?

A storage location for Docker Images.

---

### What is Docker Engine?

The core runtime that enables containerization.

---

# ⚡ Quick Revision

✅ Docker Client sends commands

✅ Docker Daemon executes commands

✅ Docker Registry stores images

✅ Docker Host runs containers

✅ Docker Engine powers Docker

---

# 📝 Summary

In this module you learned:

* Docker Architecture
* Docker Client
* Docker Daemon
* Docker Engine
* Docker Host
* Docker Registry
* Docker Workflow
* Internal Working of docker run

Understanding Docker Architecture is essential for every DevOps Engineer and Cloud Engineer.
