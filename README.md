# ansible
Automatic provisioning of machines


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