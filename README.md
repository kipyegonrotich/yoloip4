# Docker, Ansible and Vagrant: Containerization and Automated Deployment

This project containerizes and automates the deployment of an e-commerce platform called **Yolo**, consisting of:

- A **Node.js backend API**
- A **React frontend application**
- A **MongoDB** database

The solution supports **two deployment options**:

1. **Local Docker Compose-based deployment** (manual)
2. **Ansible + Vagrant automated provisioning and deployment**

---

## Tech Stack Overview

| Tool           | Role                                                                 |
|----------------|----------------------------------------------------------------------|
| Docker         | Containerization of MongoDB, backend, and frontend                   |
| Docker Compose | Orchestration of multi-container environments                        |
| Ansible        | Automated configuration and container deployment on provisioned VMs  |
| Vagrant        | VM provisioning (Ubuntu 20.04)                                       |
| MongoDB        | NoSQL database with persistent volumes                               |
| Node.js        | Backend API                                                          |
| React          | Frontend user interface                                              |

---


## Project Structure
```.
project-root/
├── backend/ # Node.js backend
│ └── Dockerfile
├── client/ # React frontend
│ └── Dockerfile
├── docker-compose.yml # Manual orchestration
├── Vagrantfile # VM provisioning
├── playbook.yml # Main Ansible playbook
├── roles/ # Ansible roles
│ ├── mongodb/
│ ├── backend/
│ └── frontend/
├── explanationIP2.md 
├── explanationIP3.md
└── README.md 
```

---
## Documentation

- [IP 2 Creating a Basic Micro-service - Explanation of steps undertaken to create a Basic Micro-service](./explanationIP2.md)

- [IP 3 Configuration Management - IP3 Configuration Management - Deployment with Ansible and Vagrant ](./explanationIP3.md)
