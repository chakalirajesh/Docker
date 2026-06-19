# 📝 05 - Dockerfile

> Learn how to create custom Docker Images using Dockerfiles.

---

# 📚 Table of Contents

* What is a Dockerfile?
* Why Dockerfile?
* Dockerfile Workflow
* Dockerfile Structure
* Dockerfile Instructions
* Building Images
* Multi-Stage Builds
* Best Practices
* Interview Questions
* Summary

---

# 📖 What is a Dockerfile?

A Dockerfile is a text file that contains a set of instructions used to build Docker Images automatically.

Instead of manually configuring an application environment, Dockerfiles allow developers to define the entire build process as code.

### Benefits

✅ Automation

✅ Reproducibility

✅ Consistency

✅ Faster Deployments

✅ Infrastructure as Code

---

# ❓ Why Dockerfile?

Without Dockerfile:

```text id="y79bf9"
Install OS
    │
Install Packages
    │
Copy Application
    │
Configure Environment
    │
Start Application
```

Everything is manual.

With Dockerfile:

```bash id="xuxvzu"
docker build -t myapp .
```

Docker performs all steps automatically.

---

# 🏗 Dockerfile Workflow

```text id="qjg4na"
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│ Dockerfile  │ ─► │ Build Image │ ─► │ Docker Image│
└─────────────┘    └─────────────┘    └─────────────┘
```

Run Image:

```text id="lmb0hy"
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│ Docker Image│ ─► │ docker run  │ ─► │ Container   │
└─────────────┘    └─────────────┘    └─────────────┘
```

---

# 📄 Basic Dockerfile Structure

Example:

```dockerfile
FROM nginx:latest

COPY index.html /usr/share/nginx/html

EXPOSE 80

CMD ["nginx","-g","daemon off;"]
```

Build:

```bash
docker build -t my-nginx .
```

Run:

```bash
docker run -d -p 80:80 my-nginx
```

---

# ⚙ Dockerfile Instructions

## FROM

Defines the base image.

```dockerfile
FROM ubuntu:22.04
```

Every Dockerfile must start with a FROM instruction.

---

## RUN

Executes commands during image creation.

```dockerfile
RUN apt update
```

Example:

```dockerfile
RUN apt update && apt install nginx -y
```

---

## COPY

Copies files from host to image.

```dockerfile
COPY . /app
```

Example:

```dockerfile
COPY app.jar /app/app.jar
```

---

## ADD

Similar to COPY but supports URLs and archive extraction.

```dockerfile
ADD app.tar.gz /app
```

Recommendation:

Use COPY unless ADD features are required.

---

## WORKDIR

Sets the working directory.

```dockerfile
WORKDIR /app
```

All future commands execute inside this directory.

---

## ENV

Defines environment variables.

```dockerfile
ENV APP_ENV=production
```

Example:

```dockerfile
ENV JAVA_HOME=/usr/lib/jvm/java-21
```

---

## EXPOSE

Documents which ports the application uses.

```dockerfile
EXPOSE 8080
```

Example:

```dockerfile
EXPOSE 80
```

---

## CMD

Defines the default command executed when the container starts.

```dockerfile
CMD ["nginx","-g","daemon off;"]
```

Example:

```dockerfile
CMD ["java","-jar","app.jar"]
```

---

## ENTRYPOINT

Defines the main executable.

```dockerfile
ENTRYPOINT ["java","-jar"]
```

Used together with CMD.

Example:

```dockerfile
ENTRYPOINT ["java","-jar"]
CMD ["app.jar"]
```

---

# ☕ Java Application Example

Dockerfile:

```dockerfile
FROM eclipse-temurin:21

WORKDIR /app

COPY target/app.jar app.jar

EXPOSE 8080

CMD ["java","-jar","app.jar"]
```

Build:

```bash
docker build -t java-app .
```

Run:

```bash
docker run -d -p 8080:8080 java-app
```

---

# 🚀 Multi-Stage Builds

Multi-stage builds create smaller production images.

Architecture:

```text id="j1b7zr"
┌──────────────┐    ┌──────────────┐
│ Build Stage  │ ─► │ Runtime Stage│
└──────────────┘    └──────────────┘
```

Example:

```dockerfile
FROM maven:3.9 AS build

WORKDIR /app

COPY . .

RUN mvn clean package

FROM eclipse-temurin:21

COPY --from=build /app/target/app.jar app.jar

CMD ["java","-jar","app.jar"]
```

Benefits:

✅ Smaller Images

✅ Faster Deployment

✅ Better Security

---

# 💡 Best Practices

## Use Official Images

Good:

```dockerfile
FROM nginx:latest
```

---

## Use Small Images

Better:

```dockerfile
FROM alpine
```

---

## Minimize Layers

Good:

```dockerfile
RUN apt update && apt install nginx -y
```

Avoid:

```dockerfile
RUN apt update
RUN apt install nginx -y
```

---

## Use Multi-Stage Builds

Reduces image size significantly.

---

## Use Specific Tags

Good:

```dockerfile
FROM nginx:1.27
```

Avoid:

```dockerfile
FROM nginx:latest
```

for production workloads.

---

# 🎯 Interview Questions

### What is a Dockerfile?

A Dockerfile is a text file containing instructions used to build Docker Images.

---

### What is the Difference Between CMD and ENTRYPOINT?

CMD provides default arguments.

ENTRYPOINT defines the main executable.

---

### Difference Between COPY and ADD?

COPY copies files.

ADD can extract archives and download URLs.

---

### What is a Multi-Stage Build?

A technique used to create smaller production-ready images.

---

### Which Dockerfile Instruction Must Come First?

FROM

---

# ⚡ Quick Revision

✅ Dockerfile = Image Blueprint

✅ FROM Defines Base Image

✅ RUN Executes Commands

✅ COPY Copies Files

✅ WORKDIR Sets Working Directory

✅ EXPOSE Documents Ports

✅ CMD Starts Application

✅ Multi-Stage Builds Reduce Size

---

# 📝 Summary

In this module, you learned:

* What Dockerfiles Are
* Dockerfile Workflow
* Dockerfile Instructions
* Building Images
* Java Dockerfile Example
* Multi-Stage Builds
* Best Practices

Dockerfiles are the foundation of Docker Image creation and are one of the most frequently used components in DevOps workflows.
