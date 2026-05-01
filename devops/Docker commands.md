# 🐳 Docker Basics – Complete Cheat Sheet

A simple, beginner-friendly reference for Docker commands and concepts.  
This file is meant for quick revision while building and debugging projects.

---

## 📌 What is Docker?

Docker is a containerization platform that allows you to package applications along with their dependencies into lightweight, portable containers.

👉 Instead of “it works on my machine”, Docker ensures:
- Same environment everywhere
- Faster development & deployment
- Isolation between applications

---

## ⚙️ Basic Docker Workflow

1. Pull an image from Docker Hub  
2. Run a container from that image  
3. Interact, debug, and manage it  
4. Stop and remove when done  

---

## 🚀 Docker CLI Cheat Sheet

---

### 📦 1. Container Management

| Action | Command |
|--------|--------|
| List running containers | `docker ps` |
| List all containers | `docker ps -a` |
| Run container | `docker run <image>` |
| Run in background | `docker run -d <image>` |
| Run with name | `docker run -d --name myapp <image>` |
| Run with port mapping | `docker run -p 3000:3000 <image>` |
| Run with env variables | `docker run -e NODE_ENV=prod <image>` |
| Start stopped container | `docker start <container>` |
| Stop container | `docker stop <container>` |
| Restart container | `docker restart <container>` |
| Pause container | `docker pause <container>` |
| Unpause container | `docker unpause <container>` |
| Remove container | `docker rm <container>` |
| Remove running container | `docker rm -f <container>` |

---

### 🖼️ 2. Image Management

| Action | Command |
|--------|--------|
| List images | `docker images` |
| Pull image | `docker pull <image>` |
| Build image | `docker build -t myapp .` |
| Remove image | `docker rmi <image>` |
| Remove all images | `docker rmi $(docker images -q)` |
| Tag image | `docker tag myapp user/myapp:v1` |

---

### 📂 3. Volume & Storage

| Action | Command |
|--------|--------|
| Create volume | `docker volume create myvolume` |
| List volumes | `docker volume ls` |
| Inspect volume | `docker volume inspect myvolume` |
| Remove volume | `docker volume rm myvolume` |
| Mount volume | `docker run -v myvolume:/data <image>` |

---

### 🌐 4. Network Management

| Action | Command |
|--------|--------|
| List networks | `docker network ls` |
| Create network | `docker network create mynet` |
| Inspect network | `docker network inspect mynet` |
| Connect container to network | `docker network connect mynet <container>` |

---

### 🛠️ 5. Logs & Debugging

| Action | Command |
|--------|--------|
| View logs | `docker logs <container>` |
| Follow logs (live) | `docker logs -f <container>` |
| Execute inside container | `docker exec -it <container> bash` |
| Inspect container | `docker inspect <container>` |
| Check resource usage | `docker stats` |
| Show processes | `docker top <container>` |

---

### ⚡ 6. Bulk Cleanup (⚠️ Use Carefully)

#### Stop all running containers
```bash
docker stop $(docker ps -q)
