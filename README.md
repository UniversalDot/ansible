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