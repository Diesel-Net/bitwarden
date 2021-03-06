[![Build Status](https://drone.kiwi-labs.net/api/badges/Diesel-Net/bitwarden/status.svg)](https://drone.kiwi-labs.net/Diesel-Net/bitwarden)

# bitwarden
Sets up bitwarden on Docker Swarm. 

:warning: this configuration uses an unofficial backend implementation [vaultwarden](https://github.com/dani-garcia/vaultwarden), formerly known as `bitwarden_rs`


## Deployments
This application is configured and deployed automatically with [Drone CI](https://github.com/harness/drone) and [Ansible](https://github.com/ansible/ansible), however there might be situations where you would prefer to run the Ansible playbooks manually. 

If [Ansible Vault](https://docs.ansible.com/ansible/latest/user_guide/vault.html#encrypting-content-with-ansible-vault) is being used then you will need to have the password file installed on your machine. Please read the relevant ansible documentation on [setting a default password source](https://docs.ansible.com/ansible/latest/user_guide/vault.html#setting-a-default-password-source).

If you are trying to reuse this Ansible configuration for _your own_ purposes, then you will need to encrypt all of _your own_ secrets using _your own_ Ansible Vault password and replace those variables in the [Ansible configuration](.ansible) after forking/cloning.

### Requirements
I recommend [installing Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible) with `pip` (globally) versus other package managers like `apt` or `brew`. It makes upgrading and using third party modules much easier. If you are on Windows, I would also recommend installing Ansible onto the WSL filesystem instead of the Windows filesytem. 
```bash
python3 -m pip install --user ansible
```

### Steps
1. Install [Ansible roles](https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html) (playbook dependencies). This will download the roles defined in [requirements.yaml](.ansible/roles/requirements.yaml) and place them into `.ansible/roles` for you.
   ```bash
   ansible-galaxy install -r .ansible/roles/requirements.yaml -p .ansible/roles --force
   ```
2. Run [Ansible playbook](https://docs.ansible.com/ansible/latest/user_guide/playbooks_intro.html) against the `development` inventory.
   ```bash
   ansible-playbook .ansible/deploy.yaml -i .ansible/inventories/development
   ```
