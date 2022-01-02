[![Build Status](https://drone.kiwi-labs.net/api/badges/Diesel-Net/bitwarden/status.svg)](https://drone.kiwi-labs.net/Diesel-Net/bitwarden)

# bitwarden
[vaultwarden](https://github.com/dani-garcia/vaultwarden) (formerly named `bitwarden_rs`) on Docker Swarm


## Manual Deployments
This application is automatically configured and deployed using Drone CI, however you may use these commands to manually deploy or test changes if needed.

### Requirements
Recommended way to install Ansible is with `pip` for `Python3.9+`. Ansible `5.0.1` was used at the time of this writing.
```bash
pip3 install --user ansible
```

1. Install Ansible Dependencies (external roles)
   ```bash
   ansible-galaxy install -r .ansible/roles/requirements.yaml -p .ansible/roles --force
   ```
2. Configure and Deploy. You will need to have the ansible-vault password file configured on your machine. Please read the relevant [ansible documentation](https://docs.ansible.com/ansible/latest/user_guide/vault.html#setting-a-default-password-source) for more information.
   ```bash
   ansible-playbook .ansible/deploy.yaml -i .ansible/inventory/development
   ```
