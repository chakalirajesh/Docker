# 🐳 01 - Docker Fundamentals

> Learn the foundations of Docker, containerization, and modern application deployment.

---

# 📚 Table of Contents

* What is Docker?
* Why Docker?
* Problems Before Docker
* How Docker Solves These Problems
* Traditional Deployment vs Docker Deployment
* Containers vs Virtual Machines
* Docker Components
* Docker Workflow
* Installing and Verifying Docker
* Running Your First Container
* Essential Docker Commands
* Real-World Use Cases
* Interview Questions
* Quick Revision
* Summary

---

# 📖 What is Docker?

Docker is an open-source containerization platform that enables developers to package applications and all their dependencies into lightweight, portable containers.

A Docker container contains:

* Application Code
* Runtime Environment
* Libraries
* Dependencies
* Configuration Files

Because everything is packaged together, the application behaves the same way everywhere.

### Real-World Example

Imagine developing a Java application.

Without Docker:

* Install Java
* Configure Environment Variables
* Install Dependencies
* Resolve Version Conflicts

With Docker:

```bash
docker run my-java-app
```

The application runs the same way on every machine.

---

# ❓ Why Docker?

Before Docker, developers often faced deployment issues.

### Common Problems

❌ Works on my machine

❌ Dependency conflicts

❌ Different configurations

❌ Different operating systems

❌ Slow deployments

---

# 🚨 Problems Before Docker

```text
Developer Laptop
       │
       ▼
 Works Fine ✅
       │
       ▼
 Testing Server
       │
       ▼
 Fails ❌
       │
       ▼
 Production
       │
       ▼
 Fails ❌
```

### Why Does This Happen?

Different systems have:

* Different Libraries
* Different Runtime Versions
* Different Configurations
* Different Operating Systems

---

# 🚀 How Docker Solves These Problems

Docker packages everything required by the application into a container.

```text
Docker Container
       │
       ├── Developer Laptop ✅
       ├── Testing Server ✅
       ├── Staging Server ✅
       └── Production Server ✅
```

### Docker Philosophy

> Build Once, Run Anywhere

---

# 🏗 Traditional Deployment vs Docker Deployment

## Traditional Deployment

```text
┌─────────────────────┐
│   Application       │
├─────────────────────┤
│   Dependencies      │
├─────────────────────┤
│   Operating System  │
├─────────────────────┤
│   Physical Server   │
└─────────────────────┘
```

### Challenges

* Dependency Conflicts
* Difficult Scaling
* Environment Issues
* High Maintenance

---

## Docker Deployment

```text
┌─────────────────────┐
│   Application       │
├─────────────────────┤
│ Docker Container    │
├─────────────────────┤
│ Docker Engine       │
├─────────────────────┤
│ Host Operating OS   │
├─────────────────────┤
│ Infrastructure      │
└─────────────────────┘
```

### Benefits

✅ Portable

✅ Lightweight

✅ Fast Deployment

✅ Consistent Environments

---

# ⚔ Containers vs Virtual Machines

| Feature        | Containers   | Virtual Machines |
| -------------- | ------------ | ---------------- |
| Startup Time   | Seconds      | Minutes          |
| Size           | MBs          | GBs              |
| Performance    | High         | Moderate         |
| Resource Usage | Low          | High             |
| Guest OS       | Not Required | Required         |
| Portability    | Excellent    | Moderate         |

---

# 🖥 Architecture Comparison

## Virtual Machines

```text
┌──────────────────┐
│ Application A    │
├──────────────────┤
│ Guest OS         │
└──────────────────┘

┌──────────────────┐
│ Application B    │
├──────────────────┤
│ Guest OS         │
└──────────────────┘

     Hypervisor

┌──────────────────┐
│ Host Operating OS│
└──────────────────┘
```

---

## Containers

```text
┌──────────────────┐
│ Container A      │
├──────────────────┤
│ App + Libraries  │
└──────────────────┘

┌──────────────────┐
│ Container B      │
├──────────────────┤
│ App + Libraries  │
└──────────────────┘

   Docker Engine

┌──────────────────┐
│ Host Operating OS│
└──────────────────┘
```

---

# ⚙ Docker Components

## 1. Docker Client

The Docker Client is the command-line tool used to communicate with Docker.

Examples:

```bash
docker run
docker build
docker pull
docker push
```

---

## 2. Docker Daemon

The Docker Daemon runs in the background.

Responsibilities:

* Build Images
* Run Containers
* Manage Networks
* Manage Volumes

---

## 3. Docker Registry

Stores Docker Images.

Examples:

* Docker Hub
* Amazon ECR
* GitHub Container Registry

---

# 🔄 Docker Workflow

```text
┌──────────────┐
│ 👨‍💻 Developer │
└──────┬───────┘
       │ Creates
       ▼
┌──────────────┐
│ Dockerfile   │
└──────┬───────┘
       │ docker build
       ▼
┌──────────────┐
│ Docker Image │
└──────┬───────┘
       │ docker run
       ▼
┌──────────────┐
│ Container    │
└──────────────┘
```

---

# 🧪 Verifying Docker Installation

Check Version:

```bash
docker --version
```

Check Detailed Information:

```bash
docker info
```

Check Running Containers:

```bash
docker ps
```

---

# 🚀 Running Your First Container

Pull Nginx Image:

```bash
docker pull nginx
```

Run Nginx:

```bash
docker run nginx
```

Run in Background:

```bash
docker run -d nginx
```

View Running Containers:

```bash
docker ps
```

---

# 📋 Essential Docker Commands

```bash
docker images
docker ps
docker ps -a
docker pull nginx
docker run nginx
docker stop <container-id>
docker rm <container-id>
docker rmi <image-id>
docker logs <container-id>
docker inspect <container-id>
```

---

# 🌍 Real-World Use Cases

### DevOps

* CI/CD Pipelines
* Infrastructure Automation

### Cloud Computing

* AWS ECS
* AWS EKS
* Kubernetes

### Software Development

* Consistent Development Environments

### Microservices

* Independent Service Deployment

---

# 🎯 Interview Questions

### What is Docker?

Docker is a containerization platform that packages applications and dependencies into portable containers.

### What is a Container?

A lightweight isolated runtime environment used to run applications.

### What is Docker Hub?

A public registry used to store and distribute Docker images.

### Difference Between Container and Virtual Machine?

Containers share the host OS kernel while VMs require a complete guest operating system.

### Why is Docker Popular?

Docker provides consistency, portability, scalability, and faster deployments.

---

# ⚡ Quick Revision

✅ Docker = Containerization Platform

✅ Containers are Lightweight

✅ Build Once, Run Anywhere

✅ Faster than Virtual Machines

✅ Docker Hub Stores Images

✅ Docker Daemon Manages Containers

---

# 📝 Summary

In this module you learned:

* What Docker is
* Why Docker was created
* Problems Docker solves
* Containers vs Virtual Machines
* Docker Components
* Docker Workflow
* Basic Commands
* Real-world Use Cases

Docker is one of the most important technologies in modern DevOps, Cloud Computing, and Software Engineering.
