# Ansible

## Install on Ubuntu
```
sudo apt update && sudo apt install ansible -y
```

## Basic commands
```
# assuming you have created a separate private key for ansible
ssh-keygen -t ed25519 -C "ansible" -f ~/.ssh/ansible

# Run ansible command without local ansible.cfg
ansible all --key-file ~/.ssh/ansible -i inventory -m ping
```

## Set defaults in `ansible.cfg`
- Override the default `ansible.cfg` file by creating a local one
```
# View the default ansible.cfg
ls /etc/ansible
cat /etc/ansible/ansible.cfg

# Run ansible command with local ansible.cfg
ansible all -m ping
ansible all --list-hosts
ansible all -m gather_facts
ansible all -m gather_facts --limit <IP address>
```
