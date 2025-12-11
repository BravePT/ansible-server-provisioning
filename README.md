# Ansible Bare Metal Provisioning

Ansible playbooks for automated Ubuntu server provisioning with system updates, SSH configuration, and monitoring tools.

## Features

- System updates and package management
- SSH hardening and key deployment
- Monitoring tools (htop, iotop, iftop, nmon)
- Customizable server configuration

## Prerequisites

- Ansible 2.9+
- SSH access to target servers
- Root or sudo privileges

## Quick Start

1. **Configure inventory:**
   ```bash
   cp inventory/hosts.yml.example inventory/hosts.yml
   # Edit inventory/hosts.yml with your server details
   ```

2. **Configure SSH keys:**
   ```bash
   cp roles/ubuntu/files/authorized_keys.example roles/ubuntu/files/authorized_keys
   # Add your public SSH keys
   ```

3. **Run provisioning:**
   ```bash
   ansible-playbook -i inventory/hosts.yml servers.yml
   ```

## Playbooks

- `servers.yml` - Full server provisioning (updates, SSH config, monitoring)
- `htopp.yml` - Install htop only

## SSH Configuration

Configures SSH with custom port 65456, enables both key and password authentication, and verbose logging. Review `roles/ubuntu/tasks/configuressh.yml` for details.


## License


