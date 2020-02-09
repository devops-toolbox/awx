Role Name
=========

awx: Awx

[![Build Status](https://travis-ci.org/cmihai-ansible/awx.svg?branch=master)](https://travis-ci.org/cmihai-ansible/awx)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.awx](https://galaxy.ansible.com/devopstoolbox.awx)

```bash
ansible-galaxy install devopstoolbox.awx
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
awx_packages_state: present
awx_remove_packages: true
awx_enable_service: true
awx_enable_selinux: true
awx_copy_templates: true
awx_firewall_configure: true
awx_firewall_rules:
  - service: ssh
  - port: 3389
awx_users:
  - user: devops
    group: docker
awx_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install awx on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: awx is configured
      import_role:
        name: devopstoolbox.awx
      vars:
        awx_packages_state: present
        awx_remove_packages: true
        awx_enable_service: true
        awx_enable_selinux: true
        awx_copy_templates: true
        awx_firewall_configure: true
        awx_firewall_rules:
          - service: ssh
          - port: 3389
        awx_users:
          - user: devops
            group: docker
        awx_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: awx
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
