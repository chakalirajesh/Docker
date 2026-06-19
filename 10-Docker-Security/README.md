# 🔒 10 - Docker Security

> Learn how to secure Docker Containers, Images, Registries, and Production Deployments.

---

# 📚 Table of Contents

* What is Docker Security?
* Why Docker Security Matters
* Docker Security Architecture
* Container Security
* Image Security
* Registry Security
* Secrets Management
* Running Containers as Non-Root Users
* Image Scanning
* Security Best Practices
* Common Security Risks
* Interview Questions
* Summary

---

# 📖 What is Docker Security?

Docker Security refers to the practices, tools, and configurations used to protect:

* Containers
* Images
* Registries
* Networks
* Host Systems

The goal is to reduce vulnerabilities and protect applications from unauthorized access.

---

# ❓ Why Docker Security Matters?

Containers share the host operating system kernel.

A compromised container can potentially affect:

* Other Containers
* Host Machine
* Sensitive Data
* Production Systems

Security must be implemented throughout the container lifecycle.

---

# 🏗 Security Architecture

```text
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ Docker Image │ ─► │ Container    │ ─► │ Production   │
└──────────────┘    └──────────────┘    └──────────────┘
        │                   │                   │
        ▼                   ▼                   ▼
 Image Security      Runtime Security    Monitoring
```

---

# 🛡 Container Security

Containers should run with minimum privileges.

Bad:

```bash
docker run nginx
```

Better:

```bash
docker run --read-only nginx
```

Even Better:

```bash
docker run --user 1001 nginx
```

Benefits:

✅ Reduced Attack Surface

✅ Better Isolation

✅ Improved Compliance

---

# 📦 Image Security

Always use trusted images.

Good:

```dockerfile
FROM nginx:1.27
```

Avoid:

```dockerfile
FROM random-image:latest
```

Why?

* Unknown Source
* Potential Malware
* Unverified Updates

---

# 🔍 Image Scanning

Scan images for vulnerabilities.

Docker Scout:

```bash
docker scout quickview nginx
```

View Recommendations:

```bash
docker scout recommendations nginx
```

Benefits:

✅ Detect Vulnerabilities

✅ Security Compliance

✅ Safer Deployments

---

# 🌍 Registry Security

Protect image repositories.

Use:

* Docker Hub Private Repositories
* Amazon ECR
* GitHub Container Registry
* Azure Container Registry

Best Practices:

✅ Private Repositories

✅ Access Control

✅ Role-Based Permissions

✅ Image Scanning

---

# 🔐 Secrets Management

Never store secrets inside Dockerfiles.

Bad:

```dockerfile
ENV DB_PASSWORD=admin123
```

Bad:

```yaml
environment:
  PASSWORD: admin123
```

Better:

```env
DB_PASSWORD=********
```

Production:

* Docker Secrets
* AWS Secrets Manager
* HashiCorp Vault

---

# 👤 Non-Root Containers

By default, many containers run as root.

Check User:

```dockerfile
RUN whoami
```

Create User:

```dockerfile
RUN useradd -m appuser
```

Switch User:

```dockerfile
USER appuser
```

Architecture:

```text
┌──────────────┐    ┌──────────────┐
│ Root User    │    │ Non-Root     │
│ High Risk    │ ─► │ Safer Option │
└──────────────┘    └──────────────┘
```

Benefits:

✅ Reduced Privileges

✅ Better Security

✅ Production Ready

---

# 🚫 Avoid Privileged Containers

Bad:

```bash
docker run --privileged nginx
```

Why?

* Full Host Access
* Increased Risk
* Security Violations

Use only when absolutely necessary.

---

# 🌐 Network Security

Limit exposed ports.

Good:

```bash
docker run -p 8080:80 nginx
```

Avoid:

```bash
docker run -P nginx
```

Use Custom Networks:

```bash
docker network create app-network
```

Benefits:

✅ Isolation

✅ Better Control

✅ Reduced Exposure

---

# 📂 File System Security

Use Read-Only Containers.

```bash
docker run --read-only nginx
```

Mount Only Required Volumes.

```bash
docker run \
-v app_data:/data \
nginx
```

Avoid unnecessary filesystem access.

---

# 🔄 Security Best Practices

### Use Official Images

```dockerfile
FROM nginx:1.27
```

---

### Keep Images Updated

```bash
docker pull nginx
```

---

### Scan Images Regularly

```bash
docker scout quickview nginx
```

---

### Run as Non-Root

```dockerfile
USER appuser
```

---

### Use Secrets Management

Never hardcode credentials.

---

### Limit Container Resources

```bash
docker run -m 512m nginx
```

---

### Remove Unused Resources

```bash
docker system prune
```

---

# ⚠ Common Security Risks

### Running as Root

High privilege access.

---

### Hardcoded Secrets

Passwords exposed in images.

---

### Outdated Images

Known vulnerabilities.

---

### Excessive Privileges

Containers gaining host access.

---

### Public Sensitive Images

Accidental data exposure.

---

# 🏢 Real-World Security Workflow

```text
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ Build Image  │ ─► │ Scan Image   │ ─► │ Push Registry│
└──────────────┘    └──────────────┘    └──────────────┘
                                               │
                                               ▼
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ Monitor      │ ◄─ │ Deploy       │ ◄─ │ Pull Image   │
└──────────────┘    └──────────────┘    └──────────────┘
```

---

# 🎯 Interview Questions

### What is Docker Security?

Docker Security refers to securing containers, images, registries, and runtime environments.

---

### Why Should Containers Run as Non-Root?

To minimize privileges and reduce security risks.

---

### What is Image Scanning?

The process of identifying vulnerabilities inside Docker Images.

---

### What is Docker Scout?

A Docker tool used to scan images and provide security recommendations.

---

### Why Should Secrets Not Be Stored in Dockerfiles?

Because secrets become part of the image and can be exposed.

---

### What is the Risk of Privileged Containers?

They can access host resources and increase attack surface.

---

# ⚡ Quick Revision

✅ Use Official Images

✅ Scan Images Regularly

✅ Run Containers as Non-Root

✅ Avoid Hardcoded Secrets

✅ Use Private Registries

✅ Limit Resource Usage

✅ Use Custom Networks

---

# 📝 Summary

In this module, you learned:

* Docker Security Fundamentals
* Container Security
* Image Security
* Registry Security
* Secrets Management
* Non-Root Containers
* Image Scanning
* Production Security Practices

Docker Security is essential for running secure, reliable, and production-ready containerized applications.
