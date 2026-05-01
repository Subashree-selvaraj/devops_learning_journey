# 🐳 Docker Basics – Complete Cheat Sheet

A beginner → intermediate level Docker reference file.  
This README covers **most commonly used Docker commands, concepts, and workflows** needed for real-world development and DevOps basics.

---

## 📌 What is Docker?

Docker is a containerization platform that allows you to package applications with all dependencies into **portable, lightweight containers**.

### 🚀 Why Docker?

- Works the same across all environments  
- Eliminates "works on my machine" problem  
- Faster setup & deployment  
- Isolation between applications  

---

## ⚙️ Basic Workflow

1. Pull an image  
2. Run a container  
3. Debug & interact  
4. Stop & remove  

---

## 🚀 Docker CLI Cheat Sheet

---

## 📦 1. Container Management

| Action | Command |
|--------|--------|
| List running containers | `docker ps` |
| List all containers | `docker ps -a` |
| Run container | `docker run <image>` |
| Run in background | `docker run -d <image>` |
| Run with name | `docker run -d --name myapp <image>` |
| Run with port mapping | `docker run -p 3000:3000 <image>` |
| Run with env variables | `docker run -e NODE_ENV=prod <image>` |
| Start container | `docker start <container>` |
| Stop container | `docker stop <container>` |
| Restart container | `docker restart <container>` |
| Pause container | `docker pause <container>` |
| Unpause container | `docker unpause <container>` |
| Remove container | `docker rm <container>` |
| Force remove | `docker rm -f <container>` |
| Rename container | `docker rename old new` |

---

## 🔄 2. Container Interaction

| Action | Command |
|--------|--------|
| Execute command inside container | `docker exec -it <container> bash` |
| Attach to container | `docker attach <container>` |
| Copy host → container | `docker cp file.txt <container>:/app` |
| Copy container → host | `docker cp <container>:/app/file.txt .` |

---

## 🖼️ 3. Image Management

| Action | Command |
|--------|--------|
| List images | `docker images` |
| Pull image | `docker pull <image>` |
| Build image | `docker build -t myapp .` |
| Remove image | `docker rmi <image>` |
| Tag image | `docker tag myapp user/myapp:v1` |
| Push image | `docker push user/myapp` |
| Login Docker Hub | `docker login` |

---

## 🧱 4. Image Advanced

| Action | Command |
|--------|--------|
| Save image | `docker save -o myimage.tar <image>` |
| Load image | `docker load -i myimage.tar` |
| Image history | `docker history <image>` |
| Inspect image | `docker inspect <image>` |

---

## 📂 5. Volumes & Storage

| Action | Command |
|--------|--------|
| Create volume | `docker volume create myvolume` |
| List volumes | `docker volume ls` |
| Inspect volume | `docker volume inspect myvolume` |
| Remove volume | `docker volume rm myvolume` |
| Mount volume | `docker run -v myvolume:/data <image>` |

---

## 🌐 6. Network Management

| Action | Command |
|--------|--------|
| List networks | `docker network ls` |
| Create network | `docker network create mynet` |
| Inspect network | `docker network inspect mynet` |
| Connect container | `docker network connect mynet <container>` |
| Disconnect container | `docker network disconnect mynet <container>` |

---

## 🛠️ 7. Logs & Debugging

| Action | Command |
|--------|--------|
| View logs | `docker logs <container>` |
| Follow logs | `docker logs -f <container>` |
| Inspect container | `docker inspect <container>` |
| Show processes | `docker top <container>` |
| Resource usage | `docker stats` |
| Container changes | `docker diff <container>` |

---

## ⚡ 8. System & Cleanup

⚠️ Use carefully

| Action | Command |
|--------|--------|
| Stop all containers | `docker stop $(docker ps -q)` |
| Remove all containers | `docker rm -f $(docker ps -aq)` |
| Remove all images | `docker rmi $(docker images -q)` |
| Disk usage | `docker system df` |
| Clean unused data | `docker system prune` |
| Full cleanup | `docker system prune -a` |
| Remove unused volumes | `docker volume prune` |
| Remove unused networks | `docker network prune` |

---

## 📄 9. Dockerfile Basics

| Instruction | Purpose |
|------------|--------|
| FROM | Base image |
| WORKDIR | Working directory |
| COPY | Copy files |
| RUN | Execute commands |
| CMD | Default command |
| EXPOSE | Define port |

### Example Dockerfile

```dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD ["npm", "start"]
