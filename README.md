# Ansible

This is a Ansible script that is used for automatic provisioning of validators. 

The deployment has been tasted on close to bare metal Ubuntu 20.04 machines. 

The deployment may work on other Linux versions or distributions, but it has not been tested.

![Logo](https://github.com/UniversalDot/documents/blob/master/logo/universaldot-logo/rsz_jpg-02.jpg)

The following ansible playbooks are used to provision Ubuntu Machine and deploy a universaldot validator to a specified machine. 

Among the tasks performed are the following:

**Playbook prep**
- SSH connection via priv/pub key pairs
- Install journald, nginx, set firewall (make sure its enabled in production),
- Generate letsencrypt, dhparams certificate on the server
- Start Journald and Nginx services
  
**Playbook universaldot**
- Install updates
- Create new user with admin rights
- Download binary and unzip 
- Start systemctl service
  
**Playbook key_rotation**
- Generate new key for validator and display on screen
  
**Playbook IPFS**
- Install Docker and Docker Compose
- Clone the Compose Service repository
- Run the IPFS and IPFS-Cluster repositories

## Useful Commands

Ping all hosts
```
ansible  all -m ping
```

List hosts
```
ansible all --list-hosts
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
ansible-playbook universaldot.yml
```

Generate new key-rotation for validator
```
 ansible-playbook key-rotation.yml -e "target=universaldot_validator_02"
 
```

## Configuration

Make sure you edit the configuration in inventory.ini to the correct server settings. 

These include host information for each node as well as general config items.

Make sure to configure the correct **local_node_identity** you are connecting to. 

### Versions:
ansible [core 2.14.2]
  executable location = /opt/homebrew/bin/ansible
  python version = 3.11.2 (main, Feb 16 2023, 02:52:13) [Clang 13.0.0 (clang-1300.0.29.30)] (/opt/homebrew/Cellar/ansible/7.2.0/libexec/bin/python3.11)
  jinja version = 3.1.2