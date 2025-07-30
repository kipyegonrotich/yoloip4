# Explanation of Terraform-Ansible Integration (Stage Two)

This document explains how Terraform and Ansible work together to automate the provisioning and configuration of the Yolo E-commerce application environment.

## Objective

Automate deployment of the Dockerized app (MongoDB + backend + frontend) using:
- **Terraform** for infrastructure provisioning
- **Ansible** for configuration management and container orchestration

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
