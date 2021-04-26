# ansible-aos-demo
**Backup Alcatel-lucent Enterprise AOS6 and AOS8 devices.**

Backups are stored in backup folder with a date suffix
- AOS6: CLI connection
- AOS8: REST api

## Steps:
1. Install Python requirements
```python
pip3 install -r requirements.txt
```
2. Install ansible-galaxy role
```ansible
ansible-galaxy role install -r requirements.yml
```
3. Add hosts to inventory.yml file
```yaml
---
all:
  hosts:
    NET-SWI-001:
      ansible_host: <change_me>
      device_vendor: alcatel
      device_os: aos8
```
4. Add credentials in group_vars/all/all.yml
```yaml
---
ale_username: amdin
ale_password: switch
```

## Sample playbook
```ansible
ansible-playbook backup-aos6.yml
ansible-playbook backup-aos8.yml
```

## Note for production:
Use Ansible vault encrypted variables to store credentials
```ansible
ansible-vault encrypt vault.yml
```