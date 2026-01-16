# 🐳 Softy Pinko Docker

Welcome to the **Softy Pinko Docker** project! 🎉 This repository is designed to teach you the fundamentals of Docker containerization. You will learn how to create Docker images, run containers, work with Docker Compose, and deploy multi-container applications. ✨

---

## 📋 Tasks Overview

| Task | Description |
|------|-------------|
| <a href="https://github.com/Schpser/holbertonschool-softy-pinko-docker/tree/main/task0" target="_blank">`task0`</a> | 📜 Create your first Docker image |
| <a href="https://github.com/Schpser/holbertonschool-softy-pinko-docker/tree/main/task1" target="_blank">`task1`</a> | 🧱 Dockerize your application |
| <a href="https://github.com/Schpser/holbertonschool-softy-pinko-docker/tree/main/task2" target="_blank">`task2`</a> | 🏹 Working with Docker Compose |
| <a href="https://github.com/Schpser/holbertonschool-softy-pinko-docker/tree/main/task3" target="_blank">`task3`</a> | 🔢 Multi-stage Docker builds |
| <a href="https://github.com/Schpser/holbertonschool-softy-pinko-docker/tree/main/task4" target="_blank">`task4`</a> | 🎯 Setting up a reverse proxy |
| <a href="https://github.com/Schpser/holbertonschool-softy-pinko-docker/tree/main/task5" target="_blank">`task5`</a> | ✨ Scaling with Docker Compose |
| <a href="https://github.com/Schpser/holbertonschool-softy-pinko-docker/tree/main/task6" target="_blank">`task6`</a> | 🚀 Production deployment configuration |

---

## 🎯 Concepts Covered

- ✅ **Docker Fundamentals**: Understanding containers and images
- ✅ **Dockerfile**: Writing efficient Dockerfiles
- ✅ **Docker Compose**: Multi-container application orchestration
- ✅ **Networking**: Container networking and communication
- ✅ **Volumes**: Data persistence in containers
- ✅ **Reverse Proxy**: Setting up nginx as a reverse proxy
- ✅ **Scaling**: Horizontal scaling with Docker Compose

## 🎓 Learning Objectives

> 💡 By the end of this project, you should be able to:

- 🗣️ Explain what Docker is and why it's useful
- 🔄 Create and build Docker images from Dockerfiles
- ✍️ Run and manage Docker containers
- 🏹 Use Docker Compose for multi-container applications
- ✨ Configure container networking and volumes
- 🔑 Set up reverse proxies with nginx
- 📦 Scale applications using Docker Compose
- 🚀 Deploy containerized applications

## ⚙️ Requirements

### General
-   🐧 Ubuntu 20.04 LTS or later
-   🐳 Docker 20.x.x or later
-   📦 Docker Compose 2.x.x or later
-   ✍️ All files should end with a new line
-   📝 All Dockerfiles must start with a comment explaining their purpose

---

## 🛠️ Setup & Installation

#### 1. Install Docker
```bash
# Update package index
sudo apt-get update

# Install Docker
sudo apt-get install docker.io -y

# Start Docker service
sudo systemctl start docker
sudo systemctl enable docker

# Add user to docker group (optional, to run without sudo)
sudo usermod -aG docker $USER
```

#### 2. Install Docker Compose
```bash
# Install Docker Compose
sudo apt-get install docker-compose -y

# Verify installation
docker-compose --version
```

#### 3. Verify Installation
```bash
# Check Docker version
docker --version

# Test Docker installation
docker run hello-world
```

---

## 🚀 Usage

#### Build Docker Images
```bash
# Navigate to a task directory
cd task0

# Build the Docker image
docker build -t softy-pinko:task0 .
```

#### Run Docker Containers
```bash
# Run a container
docker run -d -p 8080:80 --name softy-pinko softy-pinko:task0

# Check running containers
docker ps

# Stop a container
docker stop softy-pinko

# Remove a container
docker rm softy-pinko
```

#### Docker Compose Commands
```bash
# Start services
docker-compose up -d

# View logs
docker-compose logs -f

# Stop services
docker-compose down

# Rebuild and restart
docker-compose up -d --build
```

---

## 📚 Resources

- [Docker Official Documentation](https://docs.docker.com/)
- [Docker Compose Documentation](https://docs.docker.com/compose/)
- [Dockerfile Best Practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- [Docker Hub](https://hub.docker.com/)

---

**Happy Containerizing! 🎊**