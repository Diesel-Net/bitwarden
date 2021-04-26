[![Build Status](https://drone-ci.hopto.org/api/badges/Diesel-Net/bitwarden/status.svg)](https://drone-ci.hopto.org/Diesel-Net/bitwarden)

# bitwarden
Sets up [bitwarden_rs](https://github.com/dani-garcia/bitwarden_rs) on the internal network.

# Notes
- [traefik v2 labels](https://github.com/dani-garcia/bitwarden_rs/wiki/Proxy-examples#traefik-v1-labels-migrated-to-traefik-v2)

## Requirements
- Ansible 2.10+

## Installing Dependencies
```bash
ansible-galaxy install -r .ansible/roles/requirements.yaml -p .ansible/roles --force
```

## Deploy to Docker Swarm
```bash
ansible-playbook .ansible/deploy.yaml -i .ansible/inventory/production/hosts --vault-id ~/.tokens/master_id
```
