# 🌐 07 - Docker Networking

> Learn how containers communicate with each other, the host machine, and external systems using Docker Networking.

---

# 📚 Table of Contents

* What is Docker Networking?
* Why Docker Networking?
* Docker Network Architecture
* Network Drivers
* Bridge Network
* Host Network
* None Network
* Custom Networks
* Container-to-Container Communication
* Port Mapping
* DNS Resolution
* Real-World Networking Architecture
* Best Practices
* Interview Questions
* Summary

---

# 📖 What is Docker Networking?

Docker Networking enables communication between:

* Containers
* Host Machine
* External Networks
* Internet Services

Every container requires networking to:

* Send Requests
* Receive Requests
* Access Databases
* Communicate with APIs

---

# ❓ Why Docker Networking?

Imagine a modern application:

```text
Frontend
   │
Backend
   │
Database
```

All components must communicate.

Docker Networking provides secure and isolated communication between containers.

---

# 🏗 Docker Networking Architecture

```text
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ Container A  │ ─► │ Docker Net   │ ─► │ Container B  │
└──────────────┘    └──────────────┘    └──────────────┘
```

Docker Network acts as the communication layer between containers.

---

# 🚦 Docker Network Drivers

Docker provides multiple network drivers.

| Driver  | Purpose                         |
| ------- | ------------------------------- |
| Bridge  | Default container communication |
| Host    | Uses host network directly      |
| None    | No networking                   |
| Overlay | Multi-host communication        |
| Macvlan | Direct network access           |

Check Available Networks:

```bash
docker network ls
```

---

# 🌉 Bridge Network

Bridge Network is the default Docker network.

When a container starts:

```bash
docker run nginx
```

Docker automatically attaches it to the bridge network.

View Networks:

```bash
docker network ls
```

Inspect Bridge Network:

```bash
docker network inspect bridge
```

Architecture:

```text
┌──────────────┐
│ Container A  │
└───────┬──────┘
        │
        ▼

┌──────────────┐
│ Bridge Net   │
└───────┬──────┘
        │
        ▼

┌──────────────┐
│ Container B  │
└──────────────┘
```

---

# 🖥 Host Network

Host Networking removes network isolation.

Container directly uses host network stack.

Run Container:

```bash
docker run --network host nginx
```

Architecture:

```text
┌──────────────┐    ┌──────────────┐
│ Container    │ ─► │ Host Network │
└──────────────┘    └──────────────┘
```

Benefits:

✅ Better Performance

✅ Lower Latency

Use Cases:

* High Performance Applications
* Monitoring Tools

---

# 🚫 None Network

Containers receive no network connectivity.

Run Container:

```bash
docker run --network none nginx
```

Architecture:

```text
┌──────────────┐
│ Container    │
└──────────────┘

No Network Access
```

Use Cases:

* Security Testing
* Isolated Workloads

---

# 🛠 Custom Networks

Recommended for production environments.

Create Network:

```bash
docker network create app-network
```

Verify:

```bash
docker network ls
```

Run Containers:

```bash
docker run -d --network app-network nginx
```

Architecture:

```text
┌──────────────┐
│ Frontend     │
└──────┬───────┘
       │
       ▼

┌──────────────┐
│ app-network  │
└──────┬───────┘
       │
       ▼

┌──────────────┐
│ Backend      │
└──────────────┘
```

Benefits:

✅ Isolation

✅ Security

✅ DNS Resolution

✅ Service Discovery

---

# 🔄 Container-to-Container Communication

Create Network:

```bash
docker network create demo-network
```

Run Container 1:

```bash
docker run -d \
--name web \
--network demo-network \
nginx
```

Run Container 2:

```bash
docker run -it \
--network demo-network \
busybox
```

Ping Container:

```bash
ping web
```

Docker automatically resolves container names.

---

# 🌍 Port Mapping

Port Mapping exposes container ports to the host machine.

Example:

```bash
docker run -d -p 8080:80 nginx
```

Meaning:

```text
Host Port      Container Port
    8080   ──►      80
```

Architecture:

```text
┌──────────────┐    ┌──────────────┐
│ Browser      │ ─► │ Host:8080    │
└──────────────┘    └──────┬───────┘
                           │
                           ▼

                    ┌──────────────┐
                    │ Container:80 │
                    └──────────────┘
```

---

# 🔍 DNS Resolution

Docker provides built-in DNS.

Containers can communicate using names instead of IP addresses.

Example:

```bash
ping backend
```

Instead of:

```bash
ping 172.18.0.5
```

Benefits:

✅ Easier Communication

✅ Dynamic Service Discovery

✅ No Hardcoded IPs

---

# 🏢 Real-World Architecture

Example: Java Application + PostgreSQL

```text
┌──────────────┐
│ User Browser │
└──────┬───────┘
       │
       ▼

┌──────────────┐
│ Java App     │
└──────┬───────┘
       │
       ▼

┌──────────────┐
│ PostgreSQL   │
└──────────────┘
```

Docker Network enables communication between Java App and PostgreSQL.

---

# 💡 Best Practices

## Use Custom Networks

```bash
docker network create app-network
```

---

## Avoid Using Default Bridge for Production

Custom networks provide better isolation.

---

## Use Container Names

Good:

```bash
ping postgres
```

Avoid:

```bash
ping 172.18.0.5
```

---

## Expose Only Required Ports

Good:

```bash
docker run -p 8080:80 nginx
```

Avoid exposing unnecessary services.

---

# 🎯 Interview Questions

### What is Docker Networking?

Docker Networking enables communication between containers and external systems.

---

### What is the Default Docker Network?

Bridge Network.

---

### Difference Between Bridge and Host Network?

| Bridge   | Host                 |
| -------- | -------------------- |
| Isolated | Shared Host Network  |
| Default  | Manual Configuration |
| Secure   | Higher Performance   |

---

### How Do Containers Communicate?

Using Docker Networks and DNS-based Service Discovery.

---

### What is Port Mapping?

Exposing container ports to the host machine.

Example:

```bash
docker run -p 8080:80 nginx
```

---

### How Do You Create a Custom Network?

```bash
docker network create app-network
```

---

# ⚡ Quick Revision

✅ Docker Networking Connects Containers

✅ Bridge is Default Network

✅ Host Uses Host Network Stack

✅ None Provides No Connectivity

✅ Custom Networks Are Recommended

✅ Port Mapping Exposes Services

✅ Docker Provides Built-in DNS

---

# 📝 Summary

In this module, you learned:

* Docker Networking Fundamentals
* Network Drivers
* Bridge Network
* Host Network
* None Network
* Custom Networks
* Container Communication
* Port Mapping
* DNS Resolution
* Real-World Architecture

Docker Networking is one of the most important concepts for running multi-container applications and is heavily used in Docker Compose, Kubernetes, and production deployments.
