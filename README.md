## About

Automated provisioning playbooks used to manage production Ubuntu servers for blockchain infrastructure and homelab environments.

### What This Does

- **System Hardening**: Updates packages, configures SSH on custom port (65456)
- **Monitoring Setup**: Installs htop, iotop, iftop, nmon for system observability
- **SSH Key Management**: Deploys authorized keys for secure access
- **Idempotent**: Safe to run multiple times

### Production Use

Used to provision:
- Bare-metal blockchain validator nodes
- VPS instances for various services
- Homelab infrastructure servers

Tested on Ubuntu 20.04, 22.04, and 24.04 LTS.

## Project Structure
```
ansible-bm/
├── inventory/          # Host definitions
├── roles/
│   └── ubuntu/        # Ubuntu-specific tasks
│       ├── tasks/     # Playbook tasks
│       └── files/     # Config files and keys
├── servers.yml        # Full provisioning playbook
└── htopp.yml         # Minimal monitoring install
```

## Usage Examples
```bash
# Full server setup
ansible-playbook -i inventory/hosts.yml servers.yml

# Install monitoring only
ansible-playbook -i inventory/hosts.yml htopp.yml

# Target specific hosts
ansible-playbook -i inventory/hosts.yml servers.yml --limit webservers

# Dry run
ansible-playbook -i inventory/hosts.yml servers.yml --check
```

## Security Notes

- SSH configured on port 65456 (change in `roles/ubuntu/tasks/configuressh.yml`)
- Both key and password authentication enabled (adjust as needed)
- Ensure `authorized_keys` file contains only trusted public keys