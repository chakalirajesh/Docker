# 📦 03 - Docker Images

> Understanding Docker Images, Image Layers, Image Lifecycle, and Best Practices.

---

# 📚 Table of Contents

* What is a Docker Image?
* Why Do We Need Images?
* Docker Image Workflow
* How Docker Images Work
* Docker Image Layers
* Docker Hub
* Docker Image Lifecycle
* Building Custom Images
* Managing Images
* Image Tagging
* Best Practices
* Interview Questions
* Quick Revision
* Summary

---

# 📖 What is a Docker Image?

A Docker Image is a lightweight, read-only, executable package that contains everything required to run an application.

A Docker Image typically contains:

* Application Code
* Runtime Environment
* System Libraries
* Dependencies
* Configuration Files

Think of a Docker Image as a blueprint or template used to create containers.

A container is simply a running instance of an image.

## Real-World Example

```text
Blueprint = Docker Image

House = Docker Container
```

or

```text
Class = Docker Image

Object = Docker Container
```

---

# ❓ Why Do We Need Images?

Before Docker Images:

* Manual Software Installation
* Environment Differences
* Dependency Conflicts
* Deployment Failures

With Docker Images:

✅ Portable

✅ Reusable

✅ Consistent

✅ Fast Deployment

✅ Easy Distribution

---

# 🏗 Docker Image Workflow

```text
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│ Dockerfile  │ ──► │ Build Image │ ──► │ Docker Image│
└─────────────┘     └─────────────┘     └─────────────┘
```

---

# ⚙ How Docker Images Work

When an image is executed:

```text
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│ Docker Image│ ──► │ docker run  │ ──► │ Container   │
└─────────────┘     └─────────────┘     └─────────────┘
```

## Execution Flow

1. Docker reads the image.
2. Docker creates a writable layer.
3. Container is created.
4. Application starts running.

---

# 🧱 Docker Image Layers

Docker Images are built using layers.

Every Dockerfile instruction creates a new layer.

Example:

```dockerfile
FROM ubuntu:22.04

RUN apt update

RUN apt install nginx -y

COPY . /app
```

Layer Structure:

```text
┌─────────────────────┐
│ Application Files   │
├─────────────────────┤
│ Nginx Installation  │
├─────────────────────┤
│ Package Updates     │
├─────────────────────┤
│ Ubuntu Base Image   │
└─────────────────────┘
```

## Benefits of Layers

✅ Faster Builds

✅ Reduced Storage

✅ Layer Reuse

✅ Efficient Downloads

✅ Better Caching

---

# 🌍 Docker Hub

Docker Hub is Docker's default public image registry.

It stores and distributes Docker Images.

Popular Images:

* nginx
* ubuntu
* postgres
* redis
* mysql

Pull Images:

```bash
docker pull nginx

docker pull ubuntu

docker pull postgres
```

Search Images:

```bash
docker search nginx
```

---

# 🔄 Docker Image Lifecycle

```text
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│ Build Image │ ──► │ Push Image  │ ──► │ Registry    │
└─────────────┘     └─────────────┘     └─────────────┘
                                              │
                                              ▼
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│ Run Image   │ ◄── │ Pull Image  │ ◄── │ Docker Host │
└─────────────┘     └─────────────┘     └─────────────┘
```

Lifecycle Steps:

1. Build Image
2. Tag Image
3. Push Image
4. Store in Registry
5. Pull Image
6. Run Container

---

# 🏗 Building Custom Images

Example Dockerfile:

```dockerfile
FROM nginx:latest

COPY index.html /usr/share/nginx/html

EXPOSE 80
```

Build Image:

```bash
docker build -t my-nginx .
```

Verify Image:

```bash
docker images
```

---

# 🛠 Managing Images

List Images:

```bash
docker images
```

Inspect Image:

```bash
docker inspect nginx
```

View Image History:

```bash
docker history nginx
```

Remove Image:

```bash
docker rmi nginx
```

Remove Unused Images:

```bash
docker image prune
```

---

# 🏷 Image Tagging

Tags help identify image versions.

Example:

```bash
docker tag myapp:v1 myapp:latest
```

Tag Flow:

```text
┌─────────────┐     ┌─────────────┐
│ myapp:v1    │ ──► │ myapp:latest│
└─────────────┘     └─────────────┘
```

Examples:

```bash
myapp:v1

myapp:v2

myapp:latest
```

---

# 💡 Best Practices

## Use Official Images

Good:

```dockerfile
FROM nginx:latest
```

---

## Use Lightweight Images

Better:

```dockerfile
FROM alpine
```

---

## Tag Images Properly

Good:

```bash
myapp:v1.0
```

Avoid:

```bash
myapp:test123
```

---

## Remove Unused Images

```bash
docker image prune
```

---

## Minimize Layers

Combine commands when possible:

```dockerfile
RUN apt update && apt install nginx -y
```

---

# 🎯 Interview Questions

### What is a Docker Image?

A Docker Image is a read-only template used to create containers.

---

### Difference Between Image and Container?

Image = Blueprint

Container = Running Instance

---

### What are Docker Image Layers?

Layers are immutable filesystem changes created by Dockerfile instructions.

---

### What is Docker Hub?

Docker Hub is a public registry used to store and distribute Docker Images.

---

### Why Are Layers Important?

Layers improve build speed, caching efficiency, and storage optimization.

---

### Can Multiple Containers Share One Image?

Yes. Multiple containers can be created from the same image.

---

# ⚡ Quick Revision

✅ Image = Blueprint

✅ Container = Running Instance

✅ Dockerfile Creates Images

✅ Images Contain Layers

✅ Docker Hub Stores Images

✅ docker run Creates Containers

✅ Layers Improve Performance

---

# 📝 Summary

In this module, you learned:

* What Docker Images Are
* Why Images Are Important
* Docker Image Workflow
* Docker Image Layers
* Docker Hub
* Image Lifecycle
* Building Custom Images
* Managing Images
* Image Tagging
* Best Practices

Docker Images form the foundation of containerized applications and are one of the most important concepts in Docker.
