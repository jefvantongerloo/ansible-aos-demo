[![Build Status](https://travis-ci.com/jefvantongerloo/ansible-aos-demo.svg?branch=master)](https://travis-ci.com/jefvantongerloo/ansible-aos-demo)

# ansible-aos-demo
**Backup Alcatel-lucent Enterprise AOS6 and AOS8 devices.**

## Overview
Backup all ALE aos6 and aos8 Omniswitch devices using CLI or REST API.
Output connectors can be turned on to store backups to different locations: local, git, ...

**Default transport connection**
- AOS6: CLI connection
- AOS8: REST api

**Output connectors**
- Local
- Git

## Installation
1. Install Python requirements
```python
pip3 install -r requirements.txt
```
2. Install Ansible-galaxy roles
```ansible
ansible-galaxy role install -r requirements.yml
```

3. Install Ansible-galaxy collections
```ansible
ansible-galaxy role install -r requirements.yml
```

### Configuration
1. Add hosts to inventory.yml file
```yaml
---
all:
  hosts:
    NET-SWI-001:
      ansible_host: <change_me>
      device_vendor: alcatel
      device_os: aos8
```
2. Alter credentials in group_vars/all/all.yml
```yaml
---
ale_username: amdin
ale_password: switch
```

3. Select output connectors
```yaml
---
backup_local: true
backup_git: false
```

4. Optional: set git parameters
```yaml
git_token: "<change_me>"
git_username: "<change_me>"
git_url: "<change_me>"
git_branch: "master"
```

5. call playbook from command line
```bash
ansible-playbook backup-all.yml
```

## Note for production:
Use Ansible vault encrypted variables to store credentials
```ansible
ansible-vault encrypt vault.yml
```