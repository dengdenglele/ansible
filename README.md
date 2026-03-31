# Ansible

## Install on Ubuntu
```
sudo apt update && sudo apt install ansible -y
```

## Basic commands
```
# assuming you have created a separate private key for ansible
ssh-keygen -t ed25519 -C "ansible" -f ~/.ssh/ansible
ansible all --key-file ~/.ssh/ansible -i inventory -m ping
```
