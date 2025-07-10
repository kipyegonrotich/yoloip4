# IP2 Yolo E-commerce Platform Containerization

This project containerizes an e-commerce platform consisting of a Node.js backend, a frontend application, and a MongoDB database. 
The setup uses Docker and Docker Compose for orchestration, networking, and persistent data storage.

---

## Project Structure
```.
├── backend/ # Backend Node.js API 
│ └── Dockerfile 
├── client/ # Frontend application 
│ └── Dockerfile 
├── docker-compose.yml # Orchestrates services 
├── explanation.md # Technical documentation and reasoning 
└── README.md 
```
---

## Features

- **Backend API** running on Node.js
- **Frontend** web application
- **MongoDB** database with persistent storage
- **Custom bridge network** for inter-container communication
- **Semantic versioning** of Docker images
- **Clear documentation and good practices**

---

## Prerequisites

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/)

---

## Setup & Usage

Follow the steps below to build and run the application.

## 1 Clone the Repository

```bash
git clone https://github.com/kipyegonrotich/yolo.git
cd yolo
```

## 2 Build and Launch Containers

Use Docker Compose to build images and start all services:
```bash
docker compose up
```
<img width="1855" height="935" alt="websitescreenshot" src="https://github.com/user-attachments/assets/d2a11e5a-13a7-48fd-acb1-1dcea2d9b26a" />

## Docker Compose will:

    Build the backend and frontend images

    Start MongoDB, the backend API, and the frontend

    Create a named volume (mongo_data) for MongoDB persistence

    Create a custom bridge network (mongo-net)

## 3 Access the Application

After all services start successfully:

    Frontend: http://localhost:3000

    Backend API: http://localhost:5000

    MongoDB: Accessible via mongodb://localhost:27017
## Docker Hub Images

Images are tagged and published to Docker Hub:

    Backend Image:
    kipyegonrotich/yolomy-backend:v1.0.0
Backend Image Screenshot
<img width="1855" height="935" alt="backend" src="https://github.com/user-attachments/assets/d75df88c-09bb-45de-bd86-1eae2d73db60" />

    Frontend Image:
    kipyegonrotich/yolomy-frontend:v1.0.0
Frontend Image Screenshot
<img width="1855" height="935" alt="Frontend" src="https://github.com/user-attachments/assets/fc67bf74-0bfa-418c-9803-5167baf369fa" />

## Project Status

- ✅ Docker Compose builds and runs successfully
- ✅ Data persists in MongoDB across container restarts
- ✅ Semantic versioning implemented
- ✅ Good containerization practices followed
