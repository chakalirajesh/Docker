# 🛠 Docker Fundamentals Commands

> Frequently used Docker commands for beginners.

---

## Verify Docker Installation

```bash
docker --version
```

```bash
docker info
```

---

## Pull Image

```bash
docker pull nginx
```

```bash
docker pull ubuntu
```

---

## List Images

```bash
docker images
```

---

## Run Container

```bash
docker run nginx
```

Run in Background:

```bash
docker run -d nginx
```

---

## View Running Containers

```bash
docker ps
```

View All Containers:

```bash
docker ps -a
```

---

## Stop Container

```bash
docker stop <container-id>
```

---

## Start Container

```bash
docker start <container-id>
```

---

## Restart Container

```bash
docker restart <container-id>
```

---

## Remove Container

```bash
docker rm <container-id>
```

---

## Remove Image

```bash
docker rmi <image-id>
```

---

## View Logs

```bash
docker logs <container-id>
```

---

## Execute Command Inside Container

```bash
docker exec -it <container-id> bash
```

---

## Cleanup Unused Resources

```bash
docker system prune
```

