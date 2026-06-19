# 🗄️ 09 - Docker Registry

> Learn how Docker Images are stored, shared, versioned, and distributed using Docker Registries.

---

# 📚 Table of Contents

* What is a Docker Registry?
* Why Docker Registry?
* Docker Registry Architecture
* Docker Hub
* Private Registries
* Amazon ECR
* Image Push Workflow
* Image Pull Workflow
* Image Versioning
* Registry Security
* Best Practices
* Interview Questions
* Summary

---

# 📖 What is a Docker Registry?

A Docker Registry is a storage and distribution system for Docker Images.

Instead of manually transferring images between servers, Docker Registries allow teams to:

* Store Images
* Share Images
* Version Images
* Deploy Applications

Think of a Docker Registry as GitHub for Docker Images.

---

# ❓ Why Docker Registry?

Imagine you build an image on your laptop.

```bash
docker build -t myapp:v1 .
```

Without a Registry:

❌ Cannot share image easily

❌ Cannot deploy to servers

❌ Difficult version management

With a Registry:

✅ Store Images Centrally

✅ Easy Deployment

✅ Version Control

✅ CI/CD Integration

---

# 🏗️ Docker Registry Architecture

```text
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ Developer    │ ─► │ Registry     │ ─► │ Server       │
└──────────────┘    └──────────────┘    └──────────────┘
```

### Workflow

1. Build Image
2. Push Image
3. Store in Registry
4. Pull Image
5. Run Container

---

# 🌍 Docker Hub

Docker Hub is Docker's default public registry.

Official Website:

```text
https://hub.docker.com
```

Popular Images:

* nginx
* ubuntu
* redis
* mysql
* postgres

Pull Image:

```bash
docker pull nginx
```

Search Images:

```bash
docker search nginx
```

View Local Images:

```bash
docker images
```

---

# 🔐 Login to Docker Hub

Authenticate with Docker Hub.

```bash
docker login
```

Logout:

```bash
docker logout
```

Verify Login:

```bash
docker info
```

---

# 🚀 Push Image Workflow

Before pushing:

```bash
docker images
```

Tag Image:

```bash
docker tag myapp:v1 username/myapp:v1
```

Push Image:

```bash
docker push username/myapp:v1
```

Architecture:

```text
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ Build Image  │ ─► │ Tag Image    │ ─► │ Push Registry│
└──────────────┘    └──────────────┘    └──────────────┘
```

---

# 📥 Pull Image Workflow

Pull Image:

```bash
docker pull username/myapp:v1
```

Run Image:

```bash
docker run username/myapp:v1
```

Architecture:

```text
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ Registry     │ ─► │ Pull Image   │ ─► │ Run Container│
└──────────────┘    └──────────────┘    └──────────────┘
```

---

# 🏢 Private Registries

Organizations often use private registries.

Examples:

* Docker Hub Private Repositories
* Amazon ECR
* GitHub Container Registry (GHCR)
* Azure Container Registry (ACR)
* Harbor

Benefits:

✅ Security

✅ Access Control

✅ Internal Distribution

✅ Compliance

---

# ☁️ Amazon Elastic Container Registry (ECR)

Amazon ECR is AWS's managed Docker Registry service.

Benefits:

* Fully Managed
* High Availability
* IAM Integration
* Secure Storage

Login to ECR:

```bash
aws ecr get-login-password \
| docker login \
--username AWS \
--password-stdin <ecr-url>
```

Push Workflow:

```text
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ Docker Image │ ─► │ Amazon ECR   │ ─► │ ECS / EKS    │
└──────────────┘    └──────────────┘    └──────────────┘
```

---

# 🏷️ Image Versioning

Versioning helps manage releases.

Good Examples:

```bash
myapp:v1.0

myapp:v1.1

myapp:v2.0
```

Avoid:

```bash
myapp:test

myapp:new

myapp:latest
```

for production environments.

---

# 📦 Image Repository Structure

Example:

```text
myapp
│
├── v1.0
├── v1.1
├── v2.0
└── latest
```

---

# 🔒 Registry Security

Security is critical.

Best Practices:

### Use Private Repositories

Protect sensitive images.

---

### Scan Images

Example:

```bash
docker scout quickview nginx
```

---

### Use IAM Policies (AWS ECR)

Restrict access using IAM Roles.

---

### Avoid Storing Secrets

Bad:

```dockerfile
ENV PASSWORD=admin123
```

Good:

Use:

```env
.env
```

or secret management solutions.

---

# 🔄 CI/CD Integration

Typical CI/CD Workflow:

```text
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ Source Code  │ ─► │ Build Image  │ ─► │ Push Registry│
└──────────────┘    └──────────────┘    └──────────────┘
                                               │
                                               ▼
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ ECS / EKS    │ ◄─ │ Pull Image   │ ◄─ │ Registry     │
└──────────────┘    └──────────────┘    └──────────────┘
```

---

# 💡 Best Practices

## Use Version Tags

Good:

```bash
myapp:v1.0
```

---

## Avoid latest in Production

Bad:

```bash
myapp:latest
```

---

## Use Private Registries

Protect internal applications.

---

## Enable Image Scanning

Detect vulnerabilities early.

---

## Remove Old Images

Keep repositories clean.

---

# 🎯 Interview Questions

### What is a Docker Registry?

A storage system used to store and distribute Docker Images.

---

### What is Docker Hub?

Docker Hub is Docker's default public image registry.

---

### What is Amazon ECR?

Amazon Elastic Container Registry is AWS's managed Docker Registry service.

---

### Difference Between Registry and Repository?

Registry:
A service that stores images.

Repository:
A collection of related image versions.

---

### How Do You Push an Image?

```bash
docker tag myapp:v1 username/myapp:v1

docker push username/myapp:v1
```

---

### Why Use Private Registries?

To improve security and control access.

---

# ⚡ Quick Revision

✅ Registry Stores Images

✅ Docker Hub is Public Registry

✅ ECR is AWS Registry

✅ Push Uploads Images

✅ Pull Downloads Images

✅ Version Tags Improve Management

✅ Private Registries Improve Security

---

# 📝 Summary

In this module, you learned:

* What Docker Registries Are
* Docker Hub
* Private Registries
* Amazon ECR
* Push Workflow
* Pull Workflow
* Image Versioning
* Registry Security
* CI/CD Integration

Docker Registries play a critical role in modern DevOps workflows by enabling image sharing, deployment automation, and version management across environments.
