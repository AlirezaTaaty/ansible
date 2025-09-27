# Ansible Server Baseline Configuration

A collection of Ansible roles to automate the initial setup and configuration of Ubuntu servers. This project provides essential roles for common server administration tasks, ensuring consistency and reliability across your infrastructure.

## 🚀 Project Overview

This Ansible project includes three core roles that handle fundamental server configuration:

- **Common**: Base system configuration and essential package installation
- **Docker**: Docker engine installation and container runtime setup
- **Nginx**: Web server installation, configuration, and status monitoring

## 📁 Project Structure

```
ansible-server-baseline/
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
│   ├── nginx/                  # Nginx web server management
│   │   ├── tasks/
│   │   ├── handlers/
│   │   ├── templates/
│   │   └── defaults/
├── myplaybook.yml                    # Main playbook
├── ansible.cfg                 # Ansible configuration
└── README.md                   # This file
```

## 🛠️ Available Roles

### 🔧 Common Role
Base system configuration that should be applied to every server:

- System updates and essential package installation
- Timezone configuration
- Hostname setup
- Basic security hardening
- User management
- System monitoring tools

### 🐳 Docker Role
Docker engine and container management:

- Docker CE installation from official repository
- Docker Compose plugin setup
- Docker service configuration
- User group management for Docker access
- Container network setup

### 🌐 Nginx Role
Web server installation and management:

- Nginx installation and configuration

## ⚙️ Prerequisites

Before using this project, ensure you have:

- **Ansible** (version 2.9 or higher)
- **Python** (version 3.6 or higher)
- **SSH access** to target servers with sudo privileges
- **Ubuntu** servers (20.04 LTS or 22.04 LTS tested)

## 🚀 Quick Start

1. **Clone the repository:**
   ```bash
   git clone https://github.com/AlirezaTaaty/ansible.git
   cd ansible
   ```

2. **Configure your inventory:**
   ```bash
   cp inventory/
   # Edit the hosts file with your server IPs/hostnames
   ```

3. **Run the complete setup:**
   ```bash
   ansible-playbook -i inventory/hosts.txt myplaybook.yml
   ```

## 🎯 Usage Examples

### Apply all roles to all servers:
```bash
ansible-playbook -i inventory/hosts.txt myplaybook.yml
```

### Apply specific roles:
```bash
# Only common role
ansible-playbook -i inventory/hosts.txt myplaybook.yml --tags "common"

# Common and Docker roles
ansible-playbook -i inventory/hosts.txt myplaybook.yml --tags "common,docker"


### Dry run (test without changes):
```bash
ansible-playbook -i inventory/hosts.txt myplaybook.yml --check --diff
```

## ⚙️ Customization

### Variables Configuration
Each role has customizable variables. Edit the files in `roles/<role_name>/defaults/main.yml` or use group/host variables:

**Example group variables (`group_vars/all.yml`):**
```yaml
# Common role variables
common_timezone: America/New_York
common_essential_packages:
  - curl
  - wget
  - vim
  - htop
  - git

# Docker role variables
docker_users:
  - deployer
  - admin

# Nginx role variables
nginx_worker_processes: auto
nginx_worker_connections: 1024
```

## 🔒 Security Notes

- Use Ansible Vault for sensitive data (passwords, API keys)
- Regularly update the roles for security patches
- Review and customize firewall rules based on your needs
- Consider using SSH key authentication instead of passwords

## 🤝 Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.
