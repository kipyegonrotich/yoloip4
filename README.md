# IP2 Yolo E-commerce Platform Containerization

This project containerizes an e-commerce platform consisting of a Node.js backend, a frontend application, and a MongoDB database. 
The setup uses Docker and Docker Compose for orchestration, networking, and persistent data storage.

---

## 📦 Project Structure
.
├── backend/ # Backend Node.js API
│ └── Dockerfile
├── client/ # Frontend application
│ └── Dockerfile
├── docker-compose.yml # Orchestrates services
├── .dockerignore
├── explanation.md # Technical documentation and reasoning
└── README.md 

---

## Features

- **Backend API** running on Node.js
- **Frontend** web application
- **MongoDB** database with persistent storage
- **Custom bridge network** for inter-container communication
- **Semantic versioning** of Docker images
- Clear documentation and good practices

---

## Prerequisites

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/)

---

## Setup & Usage

Follow the steps below to build and run the application.

### 1 Clone the Repository

```bash
git clone https://github.com/kipyegonrotich/yolo.git
cd yolo
2 Build and Launch Containers

Use Docker Compose to build images and start all services:
