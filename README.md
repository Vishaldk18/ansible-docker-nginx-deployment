# Ansible Docker Nginx Deployment Automation

## Overview

This project automates application deployment on Ubuntu servers using Ansible.

It performs:

- Common server configuration
- Docker installation and setup
- Docker Hub authentication
- Application container deployment
- Health verification
- Nginx reverse proxy setup

This demonstrates Infrastructure as Code (IaC), configuration management, and DevOps automation best practices.

---

## Architecture

Developer Machine
        |
        v
    Ansible Control Node
        |
        +-------------------------+
        |                         |
        v                         v
 Ubuntu Web Server         Common Managed Server
        |
        v
 Docker Engine
        |
        v
 Application Container
        |
        v
 Nginx Reverse Proxy
        |
        v
 End Users

---

## Features

- Role-based Ansible project structure
- Docker installation automation
- Docker Hub registry authentication
- Container deployment automation
- Health checks using HTTP validation
- Nginx reverse proxy configuration
- Common Linux server provisioning
- Reusable variables using group_vars
- Secure secret handling with Ansible Vault

---

## Tech Stack

- Ansible
- Docker
- Nginx
- Ubuntu
- YAML
- Linux
- Docker Hub

---

## Project Structure

```bash
ansible-docker-project/
│
├── ansible.cfg
├── inventory.ini
├── site.yml
├── group_vars/
│   └── all.yml
│
└── roles/
    ├── common/
    │   └── tasks/
    │       └── main.yml
    │
    ├── docker/
    │   └── tasks/
    │       └── main.yml
    │
    └── nginx/
        └── tasks/
            └── main.yml
```

---

## Prerequisites

Install:

- Ansible
- Python
- Docker SDK for Python

Example:

```bash
sudo apt update
sudo apt install ansible python3-pip -y
pip install docker
ansible-galaxy collection install community.docker
```

---

## Configuration

Update inventory:

```ini
[web]
web-server ansible_host=<SERVER_IP>

[all:vars]
ansible_user=ubuntu
ansible_ssh_private_key_file=~/.ssh/server-key.pem
```

Create vault secrets:

```bash
ansible-vault create group_vars/vault.yml
```

Example:

```yaml
vault_docker_username: your-dockerhub-user
vault_docker_password: your-dockerhub-password
```

---

## Run Deployment

```bash
ansible-playbook site.yml --ask-vault-pass
```

Run specific role:

```bash
ansible-playbook site.yml --tags docker
```

---

## What This Project Demonstrates

- Configuration Management
- Infrastructure Automation
- Container Orchestration Basics
- Reverse Proxy Setup
- Secure Credential Management
- DevOps Deployment Workflow

---

## Future Improvements

- HTTPS with Let's Encrypt
- CI/CD pipeline integration
- Multi-container deployments
- Blue/Green deployment
- Monitoring integration
- Dynamic inventory with AWS

---

## Author

Vishal Khairnar
DevOps / Cloud Engineer
