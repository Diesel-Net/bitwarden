[![Build Status](https://drone.kiwi-labs.net/api/badges/Diesel-Net/bitwarden/status.svg)](https://drone.kiwi-labs.net/Diesel-Net/bitwarden)

# bitwarden
Sets up bitwarden on Docker Swarm. 

:warning: Warning!
This configuration uses the unofficial backend [vaultwarden](https://github.com/dani-garcia/vaultwarden), formerly known as `bitwarden_rs`.


## Deployments
This application is configured and deployed automatically using [Drone CI](https://github.com/harness/drone), however there might be situations where you would prefer to do this manually. 

You will need to have the [Ansible Vault](https://docs.ansible.com/ansible/latest/user_guide/vault.html#encrypting-content-with-ansible-vault) password file configured on your machine, if there are any vaulted secrets. Please read the relevant ansible documentation on [setting a default password source](https://docs.ansible.com/ansible/latest/user_guide/vault.html#setting-a-default-password-source). If you are trying to reuse this Ansible configuration for your own purposes, then you will need to encrypt all of _your own_ secrets using _your own_ Ansible Vault password and replace those variables in the [Ansible configuration](.ansible).

### Requirements
I recommend [installing Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible) with `pip` (globally) versus other package managers like Apt or Brew. It makes upgrading and using third party modules much easier.
```bash
python3 -m pip install --user ansible
```

### Steps
1. Install roles (dependencies).
   ```bash
   ansible-galaxy install -r .ansible/roles/requirements.yaml -p .ansible/roles --force
   ```
2. Run playbook.
   ```bash
   ansible-playbook .ansible/deploy.yaml -i .ansible/inventory/development
   ```
