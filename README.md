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

# In ansible repo create a local ansible.cfg file
touch ansible.cfg
```

## Run ansible command with local ansible.cfg
```
ansible all -m ping
ansible all --list-hosts
ansible all -m gather_facts
ansible all -m gather_facts --limit <IP address>
```

## Run ansible with elevated ad-hoc commands
- Consult the apt module [documentation](https://docs.ansible.com/projects/ansible/latest/collections/ansible/builtin/apt_module.html)
```
# apt module
ansible all -m apt -a update_cache=true --become --ask-become-pass
ansible all -m apt -a name=vim-nox --become --ask-become-pass
ansible all -m apt -a name=tmux --become --ask-become-pass

# Install multiple packages, comma separated in quotes
ansible all -m apt -a "name=cmatrix,cowsay" --become --ask-become-pass

# Update single package
ansible all -m apt -a 'name=vim state=latest' --become --ask-become-pass

# Update all packages
ansible all -m apt -a 'upgrade=dist' --become --ask-become-pass
```
