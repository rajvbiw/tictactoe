# TicTacToe CI/CD DevOps Project

## 📌 Project Overview

This project demonstrates a complete CI/CD (Continuous Integration and Continuous Deployment) pipeline using GitHub Actions, Docker, and DockerHub for a TicTacToe web application.

The application source code is containerized using Docker and automatically built and pushed to DockerHub whenever changes are pushed to the `main` branch.

---

# 🚀 Technologies Used

* Docker
* GitHub Actions
* DockerHub
* GitHub

---

# 📂 Project Structure

```bash
tictactoe/
│
├── .github/
│   └── workflows/
│       └── main.yml
│
├── public/
├── server.js
├── Dockerfile
├── package.json
├── README.md
└── tasks.json
```

---

# ⚙️ CI/CD Workflow

The CI/CD pipeline is implemented using GitHub Actions.

## Workflow Steps

1. Developer pushes code to GitHub
2. GitHub Actions workflow automatically triggers
3. Docker image is built
4. Docker image is pushed to DockerHub

---

# 🐳 Docker Setup

## Build Docker Image

```bash
docker build -t tictactoe-app .
```

## Run Docker Container

```bash
docker run -p 3000:3000 tictactoe-app
```

## Open Application

```bash
http://localhost:3000
```

---

# 🔄 GitHub Actions Workflow

The workflow file is located at:

```bash
.github/workflows/main.yml
```

The workflow performs:

* Source code checkout
* DockerHub login
* Docker image build
* Docker image push

---

# 🔐 GitHub Secrets Used

The following GitHub Secrets were configured:

| Secret Name     | Purpose                |
| --------------- | ---------------------- |
| DOCKER_USERNAME | DockerHub Username     |
| DOCKER_PASSWORD | DockerHub Access Token |

---

# 📦 DockerHub Repository

Docker images are automatically pushed to DockerHub after successful workflow execution.

Example:

```bash
docker.io/rajvbiw/tictactoe-app
```

---

# 📖 Read and Learn from Documentation

## Docker Documentation

https://docs.docker.com/

## GitHub Actions Documentation

https://docs.github.com/en/actions

## DockerHub Documentation

https://docs.docker.com/docker-hub/

## Node.js Documentation

https://nodejs.org/en/docs

## GitHub Documentation

https://docs.github.com/

---

# 🎯 What I Learned

* How to containerize applications using Docker
* How to automate workflows using GitHub Actions
* How to build and push Docker images automatically
* How CI/CD pipelines work in real DevOps environments
* How to manage GitHub Secrets securely

---

# ✅ Project Outcome

Successfully implemented a CI/CD pipeline for a TicTacToe web application using:

* Docker
* GitHub Actions
* DockerHub

The pipeline automatically builds and deploys the Docker image whenever code is pushed to the main branch.

---

# 👨‍💻 Author

Raj Birari
