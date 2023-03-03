# Ansible
Automatic Provisioning of validators

![Logo](https://github.com/UniversalDot/documents/blob/master/logo/rsz_jpg-02.jpg)

The following ansible playbooks are used to provision Ubuntu Machine and deploy a universaldot validator to a specified machine. 

Among the tasks performed are the following:
- SSH connection via priv/pub key pairs
- Install updates
- Create new user with admin rights
- Download binary and unzip 
- Start systemctl service

## Commands

Ping all hosts
```
ansible  all -m ping
```

List hosts
```
ansible all  --list-hosts
```

Gather Facts
```
ansible all -m gather_facts
```

Install packages remotely:
```
ansible all -m apt -a name=vim-nox --become --ask-become-pass
```

Install playbooks:
```
ansible-playbook --ask-become-pass install.yml
```

Install playbooks:
```
ansible-playbook --tags mariadb --ask-become-pass install.yml
```

Install when remote_user is specified:
```
ansible-playbook install.yml
```