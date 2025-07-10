# Explanation of steps undertaken to create a Basic Micro-service

This document explains the reasoning behind my implementation of containerizing the e-commerce platform.

---

## 1. Choice of the Base Images

- **MongoDB**
  - Image: `mongo` (I used `mongo` without specifying the tag to default to the latest stable version)
  - MongoDB image optimized for Docker.
  - Actively maintained.
  - Preconfigured for persistence and default ports.

- **Backend**
  - Base Image: Defined in `./backend/Dockerfile` (typically a Node.js alpine variant for smaller image size).
  - `node:alpine` is chosen for the backend to ensure minimal size, faster build times, and security.

- **Frontend**
  - Base Image: Defined in `./client/Dockerfile` 
  - Rationale: Same reason—minimal footprint and fast deployment.
  ---

## 2. Dockerfile Directives

- **Backend and Frontend**
 - For the two Dockerfiles I adopted a similar structure i.e for both Backend and Frontend
  - The `Dockerfiles` uses:
    - `FROM node:alpine` as the base image.
    - `WORKDIR` to set the working directory.
    - `COPY` to bring the application code.
    - `RUN npm install` to install dependencies.
    - `EXPOSE` declares the port.
    - `CMD ["npm", "start"]` to start the server.
 
    ---

## 3. Docker Compose Networking

- **Custom Bridge Network**: `mongo-net`
  - This allows the services to communicate internally via their container names (`mongodb`, `yoloimage`, `yolofrontend`).
- **Ports**
  - MongoDB: `27017`
  - Backend API: `5000`
  - Frontend App: `3000`

 ---

## 4. Docker Compose Volume Definition

- **MongoDB Data Volume**
  - Named volume: `mongo_data`
  - Mounted path: `/data/db`
  - I did this to ensures persistence of product data even after containers are stopped or recreated. 

  ---

## 5. Git Workflow

- **Commits**
  - The repository uses descriptive commits for each step: examples below shows some descriptive commits
 ```bash
  git commit -m "configure docker compose to build image with semantic versioning"
   git commit -m "New change on docker compose not working, revert back"
  git commit -m "Create a Docker file for the frontend services
  git commit -m "Add multistage build to reduce image size"
  git commit -m "Configure the mongodb to point to the correct database name"
   ```
    
- **Branches**
  - All changes committed on the `main` branch for this assignment.
    
- **README**
  - Provides clear setup instructions.

## 6. Successful Running of the Application

- The `docker-compose.yml` file successfully:
  - Builds all images.
  - Launches MongoDB, the backend, and the frontend.
  - Ensures persistence via `mongo_data`.
  - Exposes ports to test the frontend UI and backend API.
  - Application is accessible on:
    - Frontend: `http://localhost:3000`
    - Backend API: `http://localhost:5000`
    ![alt text](dockercomposerunning.png)
    ![alt text](websitescreenshot.png)

- **Debugging Measures**
  - Used `docker logs` to confirm services started correctly.
  - Verified MongoDB connection strings.

  ---

## 7. Good Practices

- **Semantic Versioning**
  - Images are tagged with `v1.0.0` 
  - screnshots of tags shown below
- **Minimal Base Images**
  - All images based on alpine variants.

---
## Screenshot of Deployed Image on DockerHub
![alt text](backend.png)![alt text](Frontend.png)