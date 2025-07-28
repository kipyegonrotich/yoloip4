# IP3 Configuration Management - Deployment with Ansible and Vagrant 

This project automates the deployment of a containerized e-commerce dashboard using **Vagrant** and **Ansible**. The app consists of a MongoDB database, a Node.js backend API, and a React frontend.

---

## Stack Summary

- **Vagrant**: Provisions an Ubuntu 20.04 (Jeff Geerlings ubuntu 20.04) virtual machine (VM).
- **Ansible**: Automates container creation and deployment.
- **MongoDB**: Stores the application's data.

---

## Project Structure
```
project-root/
├── Vagrantfile
├── playbook.yml
├── roles/
│ ├── mongodb/
│ │ └── tasks/
│ │ └── main.yml
│ ├── frontend/
│ │ └── tasks/
│ │ └── main.yml
│ └── backend/
│ └── tasks/
│ └── main.yml
├── yolo/
│ ├── backend/ # Node.js backend
│ └── client/ # React frontend
```

---

## Deployment Steps

### 1. Provision the Virtual Machine

Run from the host machine:

```bash
vagrant up 
vagrant provision
```
![alt text](vagrantupsc-1.png)
![alt text](vagrantprovisionsc-1.png)
This will:

    Provision the VM running Ubuntu 20.04

    Install Docker and Ansible

    Prepare the environment for deployment

### 2. Access the Virtual Machine
```bash
vagrant ssh
```
![alt text](vagrantsshsc-1.png)

### 3. Execute the Ansible Playbook

Inside the VM:
```bash
ansible-playbook playbook.yml
```

This playbook will:

    Create a Docker network called app-net.

    Deploy the MongoDB container.

    Deploy the backend Node.js API container.

    Deploy the frontend React container.

Access Points
```
Component	Address
Frontend    http://localhost:3000
Backend     http://localhost:5000
MongoDB     localhost:27017 (Docker internal)
```
Docker Containers
```
Name                Image                               Purpose
mongodb_container   mongo                               NoSQL Database
yolo-backend        kipyegonrotich/yolo-backend:v1.0.0  Backend API
yolofrontend        kipyegonrotich/yolo-frontend:v1.0.0 React App UI
```
![alt text](dockerpssc.png)

### Git Workflow
Commits
Descriptive commits for each step to be able to track progress clearly: examples below shows some descriptive commits
```
git commit -m "deleted original files that existed to allow me create mine"
git commit -m "Created new vagrantfile"
git commit -m "define the roles that will be provisioned"
git commit -m "create tasks under roles for each container and database"
git commit -m "add tasks to the playbook to be executed under roles"
git commit -m "create a task to provision MongoDB database container"
git commit -m "define ansible role that spins up the MongoDB container"
git commit -m "define ansible role that spins up the frontend and backend containers"
git commit -m "add persistency to ensure that the uploaded products are not lost when restarted"
git commit -m "Add screenshot of results from various stages"

```

### Common Troubleshooting

View container logs:

```bash
docker logs mongodb_container
```

Rebuild the frontend image:

```bash
cd yolo/client
docker build -t kipyegonrotich/yolo-frontend:v1.0.0 .
``` 

Remove a crashed container:

```bash
docker rm kipyegonrotich/yolo-backend:v1.0.0

```

Remove an image to rebuild fresh:

```bash
docker rmi kipyegonrotich/yolo-backend:v1.0.0

```

Restart all containers:

```bash
docker restart $(docker ps -q)
```

### Notes

MongoDB uses Docker volumes for persistent storage, so product data remains intact even after halting or restarting Vagrant.

![alt text](websitescreenshot.png)
![alt text](productlist.png)
![alt text](addedproductsc.png)
