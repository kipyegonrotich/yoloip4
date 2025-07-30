# Stage Two: Terraform-Provisioned Ansible Deployment

This directory contains infrastructure-as-code configurations that provision resources using Terraform and trigger configuration and application deployment using Ansible.

## Overview

- **Terraform** provisions the local Vagrant-based environment (or external VM if adapted).
- **Ansible** is triggered by Terraform via the `null_resource` and `local-exec` provisioner to:
  - Install Docker
  - Deploy MongoDB, backend, and frontend containers
  - Configure networking and volumes

## Files

- `main.tf`: Terraform configuration defining infrastructure and Ansible trigger
- `terraform.tfstate`: Current state of provisioned infrastructure
- `.terraform/`: Terraform plugin binaries and metadata
- `.gitignore`: Specifies which Terraform files to exclude from version control

## Usage

### 1. Initialize Terraform

```bash
terraform init
```

### 2. Apply Infrastructure & Trigger Ansible

```bash
terraform apply
```

### 3. Confirm

- Check the Vagrant VM (if used)
- Use `docker ps` to verify running containers

## Prerequisites

- Vagrant VM is already running (provisioned manually or via Terraform)
- Ansible installed on your local machine
- SSH access is set up from host to guest (e.g., using default Vagrant private key)

## Next Steps

- Add remote backend (e.g., S3) for state management
- Refactor Ansible playbooks and variables for dynamic scalability
