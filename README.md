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
├── site.yml                    # Main playbook
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
- Service status monitoring
- Virtual host setup
- SSL/TLS configuration readiness
- Performance tuning

## ⚙️ Prerequisites

Before using this project, ensure you have:

- **Ansible** (version 2.9 or higher)
- **Python** (version 3.6 or higher)
- **SSH access** to target servers with sudo privileges
- **Ubuntu** servers (20.04 LTS or 22.04 LTS tested)

## 🚀 Quick Start

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/ansible-server-baseline.git
   cd ansible-server-baseline
   ```

2. **Configure your inventory:**
   ```bash
   cp inventories/staging/hosts.example inventories/staging/hosts
   # Edit the hosts file with your server IPs/hostnames
   ```

3. **Run the complete setup:**
   ```bash
   ansible-playbook -i inventories/staging/hosts site.yml
   ```

## 🎯 Usage Examples

### Apply all roles to all servers:
```bash
ansible-playbook -i inventories/production/hosts site.yml
```

### Apply specific roles:
```bash
# Only common role
ansible-playbook -i inventories/production/hosts site.yml --tags "common"

# Common and Docker roles
ansible-playbook -i inventories/production/hosts site.yml --tags "common,docker"

# Only Nginx role
ansible-playbook -i inventories/production/hosts site.yml --tags "nginx"
```

### Apply to specific server groups:
```bash
# Apply to web servers only
ansible-playbook -i inventories/production/hosts site.yml --limit webservers

# Apply to a single server
ansible-playbook -i inventories/production/hosts site.yml --limit server1.example.com
```

### Dry run (test without changes):
```bash
ansible-playbook -i inventories/production/hosts site.yml --check --diff
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

### Inventory Setup
Create your inventory files based on environments:

**`inventories/production/hosts`:**
```ini
[webservers]
web1.example.com
web2.example.com

[docker_servers]
docker1.example.com
docker2.example.com

[all:vars]
ansible_user=ubuntu
ansible_ssh_private_key_file=~/.ssh/production_key
```

## 🔒 Security Notes

- Use Ansible Vault for sensitive data (passwords, API keys)
- Regularly update the roles for security patches
- Review and customize firewall rules based on your needs
- Consider using SSH key authentication instead of passwords

## 🤝 Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Support

If you encounter any problems or have questions:

1. Check the [Issues](https://github.com/yourusername/ansible-server-baseline/issues) page
2. Create a new issue with detailed information
3. Contact: your-email@example.com

---

**⭐ If this project helped you, please give it a star on GitHub!**

*Last updated: March 2024*
