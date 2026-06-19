# 🚀 13 - Docker Projects

> Apply Docker concepts in real-world projects and build production-ready containerized applications.

---

# 📚 Table of Contents

* Why Docker Projects?
* Project Architecture
* Project 1: Nginx Static Website
* Project 2: Java Application
* Project 3: Java + PostgreSQL
* Project 4: React + Node.js
* Project 5: Monitoring Stack
* Production Best Practices
* Interview Questions
* Summary

---

## 📖 Why Docker Projects?

Learning commands is important.

Building projects is essential.

Projects help you:

✅ Understand Real-World Usage

✅ Improve Problem Solving

✅ Build Portfolio Projects

✅ Prepare for Interviews

✅ Gain Production Experience

---

## 🏗 Docker Project Architecture

```text
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ Frontend     │ ─► │ Backend      │ ─► │ Database     │
└──────────────┘    └──────────────┘    └──────────────┘
```

This is the most common architecture used in modern applications.

---

# 🚀 Project 1: Nginx Static Website

## 📖 Objective

Deploy a static HTML website using Docker.

---

## 📂 Project Structure

```text
project/
│
├── index.html
└── Dockerfile
```

---

## 📝 Dockerfile

```dockerfile
FROM nginx:1.27

COPY index.html /usr/share/nginx/html

EXPOSE 80
```

---

## ⚙ Build Image

```bash
docker build -t static-site .
```

---

## ▶ Run Container

```bash
docker run -d -p 8080:80 static-site
```

---

## 🌐 Access Application

```text
http://localhost:8080
```

---

# ☕ Project 2: Java Application

## 📖 Objective

Containerize a Java Spring Boot application.

---

## 📂 Project Structure

```text
java-app/
│
├── Dockerfile
└── app.jar
```

---

## 📝 Dockerfile

```dockerfile
FROM eclipse-temurin:21

WORKDIR /app

COPY app.jar app.jar

EXPOSE 8080

CMD ["java","-jar","app.jar"]
```

---

## ⚙ Build Image

```bash
docker build -t java-app .
```

---

## ▶ Run Application

```bash
docker run -d -p 8080:8080 java-app
```

---

## 🏗 Architecture

```text
┌──────────────┐    ┌──────────────┐
│ Browser      │ ─► │ Java App     │
└──────────────┘    └──────────────┘
```

---

# 🗄 Project 3: Java + PostgreSQL

## 📖 Objective

Deploy a Java application with a PostgreSQL database using Docker Compose.

---

## 📂 Project Structure

```text
project/
│
├── Dockerfile
├── docker-compose.yml
└── app.jar
```

---

## 📝 docker-compose.yml

```yaml
services:

  app:
    build: .

    ports:
      - "8080:8080"

    depends_on:
      - postgres

  postgres:
    image: postgres:16

    environment:
      POSTGRES_DB: selfos
      POSTGRES_USER: selfos
      POSTGRES_PASSWORD: selfos123

    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

---

## ▶ Start Application

```bash
docker compose up -d
```

---

## 🏗 Architecture

```text
┌──────────────┐    ┌──────────────┐
│ Java App     │ ─► │ PostgreSQL   │
└──────────────┘    └──────────────┘
```

---

# ⚛ Project 4: React + Node.js

## 📖 Objective

Containerize a Full Stack Application.

---

## 🏗 Architecture

```text
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ React        │ ─► │ Node.js API  │ ─► │ MongoDB      │
└──────────────┘    └──────────────┘    └──────────────┘
```

---

## 📂 Project Structure

```text
project/
│
├── frontend/
├── backend/
└── docker-compose.yml
```

---

## ▶ Run Project

```bash
docker compose up -d
```

---

# 📊 Project 5: Monitoring Stack

## 📖 Objective

Monitor Docker Containers using Prometheus and Grafana.

---

## 🏗 Architecture

```text
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ Containers   │ ─► │ Prometheus   │ ─► │ Grafana      │
└──────────────┘    └──────────────┘    └──────────────┘
```

---

## 📂 Project Structure

```text
monitoring/
│
├── prometheus.yml
├── docker-compose.yml
└── grafana/
```

---

## ▶ Start Monitoring

```bash
docker compose up -d
```

---

# 🏢 Production Best Practices

## 🔒 Security

* Use Official Images
* Scan Images
* Avoid Running as Root
* Store Secrets Securely

---

## 💾 Storage

* Use Named Volumes
* Backup Critical Data
* Avoid Storing Data in Containers

---

## 🌐 Networking

* Use Custom Networks
* Limit Exposed Ports
* Separate Internal Services

---

## 📊 Monitoring

* Enable Logging
* Use Prometheus
* Use Grafana Dashboards

---

## 🚀 CI/CD

```text
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ Source Code  │ ─► │ Build Image  │ ─► │ Push Registry│
└──────────────┘    └──────────────┘    └──────────────┘
                                              │
                                              ▼
                                       ┌──────────────┐
                                       │ Deployment   │
                                       └──────────────┘
```

---

# 🎯 Interview Questions

## What is the Best Beginner Docker Project?

A static website using Nginx.

---

## Why Use Docker Compose?

To manage multi-container applications.

---

## Which Docker Project is Most Common in Industry?

Application + Database architecture.

Example:

```text
Frontend → Backend → Database
```

---

## Why Use Volumes in Projects?

To persist data beyond container lifecycle.

---

## Why Use Custom Networks?

For secure container communication.

---

# ⚡ Quick Revision

✅ Static Website Project

✅ Java Application Project

✅ Java + PostgreSQL Project

✅ React + Node.js Project

✅ Monitoring Stack Project

✅ Production Best Practices

---

# 📝 Summary

In this module, you learned:

* Docker Project Design
* Nginx Deployment
* Java Application Deployment
* Docker Compose Projects
* Full Stack Applications
* Monitoring Stack
* Production Best Practices

These projects demonstrate practical Docker skills and help build a strong DevOps portfolio for interviews and real-world deployments.
