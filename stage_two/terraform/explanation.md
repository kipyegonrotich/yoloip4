# Explanation of Terraform-Ansible Integration (Stage Two)

This stage demonstrates the use of **Terraform and Ansible** together to deploy the YOLO E-commerce Dockerized application. Unlike Stage One, which uses **Vagrant for provisioning**

## Objective
Automate deployment of the Dockerized app (MongoDB + backend + frontend) using:

- **Terraform** for infrastructure provisioning to orchestrate the deployment workflow triggering **Ansible playbooks** from within Terraform using `local-exec`

- **Ansible** for configuration management and container orchestration

## Project Structure

 stage_two/

├── ansible/

│ ├── inventory.yml

│ ├── playbook.yml

│ └── roles/

│ ├── mongodb/

│ ├── backend/

│ └── frontend/

└── terraform/

└── main.tf

## 🚀 How to Deploy

### 1. Ensure your VM is running (e.g., via Vagrant)

```bash
vagrant  up

```
Navigate to the Terraform directory

```bash

cd  stage_two/terraform
terraform  init
terraform  apply

```

- Verify Deployment
- MongoDB: Port 27017 (internal)
- Backend API: Accessible via port 5000
- Frontend: Accessible via port 3000
- Visit http://127.0.0.1:3000 from the browser.

## How It Works

### Terraform

- Defines a `null_resource` that serves as a trigger.
- Uses `local-exec` to call the Ansible playbook after provisioning is done.

### Ansible

- Executes tasks on the already provisioned VM (Ubuntu 20.04 via Vagrant).
- Installs Docker
- Creates Docker network `app-net`
- Launches containers:
  - MongoDB
  - Backend (Node.js)
  - Frontend (React)

### Trigger Example in `main.tf`

```hcl
resource "null_resource" "ansible_deploy" {
  provisioner "local-exec" {
    command = "ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i ../ansible/inventory.yml ../ansible/playbook.yml"
  }
}
```

## Benefits

- Decouples provisioning from configuration
- Scales well with infrastructure growth
- Makes CI/CD integration easier

## Limitations

- Assumes Vagrant-based environment is already running
- Local `local-exec` assumes host has Ansible installed and can SSH into VM

## Improvements

- Use remote backends for `.tfstate`
- Add dynamic inventory for Ansible
- Integrate with cloud providers like AWS or DigitalOcean for real cloud infrastructure
