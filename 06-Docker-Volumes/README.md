# 💾 06 - Docker Volumes

> Understanding Persistent Storage in Docker using Volumes and Bind Mounts.

---

# 📚 Table of Contents

* What are Docker Volumes?
* Why Do We Need Volumes?
* Types of Docker Storage
* Volume Architecture
* Named Volumes
* Bind Mounts
* Anonymous Volumes
* Managing Volumes
* Real-World Examples
* Best Practices
* Interview Questions
* Summary

---

# 📖 What are Docker Volumes?

Docker Volumes are the preferred mechanism for persisting data generated and used by Docker containers.

By default, container data is stored inside the writable container layer.

When a container is deleted, all data stored inside that container is lost.

Volumes solve this problem by storing data outside the container lifecycle.

---

# ❓ Why Do We Need Volumes?

Consider a PostgreSQL container.

```bash
docker run postgres
```

The database stores data inside the container.

If the container is removed:

```bash
docker rm postgres-container
```

All database data is lost.

Volumes allow data to survive container deletion.

---

# 🏗 Volume Architecture

```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│  Container   │ ──► │   Volume     │ ◄── │  Host Disk   │
└──────────────┘     └──────────────┘     └──────────────┘
```

### Explanation

* Container writes data.
* Volume stores data.
* Data persists independently of containers.

---

# 📦 Types of Docker Storage

Docker provides three storage mechanisms:

### 1. Named Volumes

Managed by Docker.

### 2. Bind Mounts

Direct mapping to host filesystem.

### 3. Anonymous Volumes

Automatically generated volumes.

---

# 🔹 Named Volumes

Named volumes are managed entirely by Docker.

Create Volume:

```bash
docker volume create postgres_data
```

Run Container with Volume:

```bash
docker run -d \
-v postgres_data:/var/lib/postgresql/data \
postgres
```

Inspect Volume:

```bash
docker volume inspect postgres_data
```

---

# 🔹 Bind Mounts

Bind mounts connect a host directory directly into a container.

Example:

```bash
docker run -d \
-v /home/rajesh/data:/app/data \
nginx
```

Architecture:

```text
┌──────────────┐     ┌──────────────┐
│ Host Folder  │ ──► │  Container   │
└──────────────┘     └──────────────┘
```

Advantages:

* Easy local development
* Direct access to files
* Immediate synchronization

---

# 🔹 Anonymous Volumes

Docker automatically generates volume names.

Example:

```bash
docker run -v /app/data nginx
```

Check Volumes:

```bash
docker volume ls
```

Example Output:

```text
DRIVER    VOLUME NAME
local     8f3d1d7f29
```

---

# 🛠 Managing Volumes

List Volumes:

```bash
docker volume ls
```

Inspect Volume:

```bash
docker volume inspect volume_name
```

Remove Volume:

```bash
docker volume rm volume_name
```

Remove Unused Volumes:

```bash
docker volume prune
```

---

# 🚀 Real-World Example

### PostgreSQL Persistent Storage

Without Volume:

```text
Container Deleted
        │
        ▼
Database Lost ❌
```

With Volume:

```text
Container Deleted
        │
        ▼
Volume Exists
        │
        ▼
Database Preserved ✅
```

Run PostgreSQL with Volume:

```bash
docker run -d \
--name postgres-db \
-v postgres_data:/var/lib/postgresql/data \
postgres
```

---

# 🏢 Production Use Cases

### Databases

* PostgreSQL
* MySQL
* MongoDB

### Logging

* Application Logs
* Audit Logs

### File Uploads

* User Uploads
* Images
* Documents

### Configuration Storage

* Application Configs
* Secrets

---

# ⚡ Volume Lifecycle

```text
┌──────────────┐ ──► ┌──────────────┐ ──► ┌──────────────┐
│ Create       │     │ Attach       │     │ Use          │
└──────────────┘     └──────────────┘     └──────────────┘
                                            │
                                            ▼
┌──────────────┐ ◄── ┌──────────────┐ ◄── ┌──────────────┐
│ Delete       │     │ Detach       │     │ Persist      │
└──────────────┘     └──────────────┘     └──────────────┘
```

---

# 💡 Best Practices

### Use Named Volumes for Production

```bash
docker volume create app_data
```

---

### Avoid Storing Critical Data Inside Containers

Bad:

```bash
docker run postgres
```

Good:

```bash
docker run -v postgres_data:/var/lib/postgresql/data postgres
```

---

### Clean Unused Volumes

```bash
docker volume prune
```

---

### Backup Critical Volumes

Regular backups are essential for production workloads.

---

# 🎯 Interview Questions

### What is a Docker Volume?

A Docker Volume is a persistent storage mechanism that exists independently of containers.

---

### Why Are Volumes Needed?

To preserve data even when containers are deleted.

---

### Difference Between Volume and Bind Mount?

| Volume                     | Bind Mount             |
| -------------------------- | ---------------------- |
| Managed by Docker          | Managed by Host        |
| Portable                   | Host Dependent         |
| Recommended for Production | Useful for Development |

---

### How Do You List Volumes?

```bash
docker volume ls
```

---

### How Do You Remove Unused Volumes?

```bash
docker volume prune
```

---

# ⚡ Quick Revision

✅ Volumes Store Persistent Data

✅ Volumes Survive Container Deletion

✅ Named Volumes Are Preferred

✅ Bind Mounts Connect Host Directories

✅ Databases Should Always Use Volumes

---

# 📝 Summary

In this module, you learned:

* What Docker Volumes Are
* Why Persistent Storage Matters
* Named Volumes
* Bind Mounts
* Anonymous Volumes
* Volume Lifecycle
* Production Use Cases
* Best Practices

Docker Volumes are essential for running stateful applications such as databases, logging systems, and file storage solutions.
