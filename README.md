<h1>Ansible Server Baseline Project</h1>
A collection of Ansible roles to automate the initial setup and configuration of Ubuntu servers upon first login.

<h1>📋 Project Overview</h1>
This Ansible project provides essential baseline configurations for Ubuntu servers, ensuring consistency, security, and proper setup across your infrastructure. The project follows best practices for Ansible role structure and can be easily extended.
<h1>🎯 Purpose</h1>
Automate repetitive server setup tasks including:

* Basic system configuration and package management

* Docker installation and container runtime setup

* Nginx web server status monitoring and management

📁 Project Structure
ansible-baseline/
├── inventories/                 # Inventory files
│   ├── production/             # Production environment
│   └── staging/                # Staging environment
├── roles/
│   ├── common/                 # Base system configuration
│   │   ├── tasks/
│   │   ├── handlers/
│   │   ├── templates/
│   │   └── defaults/
│   ├── docker/                 # Docker installation & configuration
│   │   ├── tasks/
│   │   ├── handlers/
│   │   ├── vars/
│   │   └── defaults/
│   ├── nginx/                  # Nginx status monitoring
│   │   ├── tasks/
│   │   ├── handlers/
│   │   └── defaults/
├── myplaybook.yml                    # Main playbook
├── ansible.cfg                 # Ansible configuration
└── README.md                   # This file

⚙️ Available Roles
🔧 Common Role
Basic system configuration and essential package installation.

Features:

System updates and package cache refresh

Installation of essential utilities (curl, wget, vim, htop, git, etc.)

Timezone configuration

Hostname setup

Basic directory structure creation

🐳 Docker Role
Docker CE installation and basic configuration.

Features:

Docker Community Edition installation

Official Docker repository setup

Docker Compose plugin installation

User group configuration for Docker access

Service management and validation

🌐 Nginx Role
Nginx installation status checking and service management.

Features:

Nginx installation verification

Service status monitoring

Basic configuration validation

Graceful reload handling

🚀 Quick Start
Prerequisites
Ansible 2.9+

Ubuntu 20.04/22.04 servers

SSH access with sudo privileges

