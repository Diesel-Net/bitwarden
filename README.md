[![Build Status](https://drone.kiwi-labs.net/api/badges/Diesel-Net/bitwarden/status.svg)](https://drone.kiwi-labs.net/Diesel-Net/bitwarden)

# bitwarden
[vaultwarden](https://github.com/dani-garcia/vaultwarden) (formerly named `bitwarden_rs`) on Docker Swarm


## Deployments
This application is configured and deployed automatically using Drone CI, however there may be situations where you would prefer to configure and deploy the application manually. You will need to have the [ansible-vault](https://docs.ansible.com/ansible/latest/user_guide/vault.html#encrypting-content-with-ansible-vault) password file configured on your machine. Please read the relevant ansible documentation on [setting a default password source](https://docs.ansible.com/ansible/latest/user_guide/vault.html#setting-a-default-password-source). If you are trying to reuse this Ansible configuration for your own purposes, then you will need to encrypt all of _your_ secrets using _your_ ansible vault password.

### Requirements
Recommended way to install Ansible is with `pip` for `Python3.9+`. Ansible `5.0.1` was used at the time of this writing.
```bash
pip3 install --user ansible
```

### Steps
1. Install Ansible Dependencies (external roles)
   ```bash
   ansible-galaxy install -r .ansible/roles/requirements.yaml -p .ansible/roles --force
   ```
2. Configure and Deploy. 
   ```bash
   ansible-playbook .ansible/deploy.yaml -i .ansible/inventory/development
   ```
