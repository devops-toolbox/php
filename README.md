Role Name
=========

php: Php

[![Build Status](https://travis-ci.org/cmihai-ansible/php.svg?branch=master)](https://travis-ci.org/cmihai-ansible/php)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.php](https://galaxy.ansible.com/devopstoolbox.php)

```bash
ansible-galaxy install devopstoolbox.php
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
php_packages_state: present
php_remove_packages: true
php_enable_service: true
php_enable_selinux: true
php_copy_templates: true
php_firewall_configure: true
php_firewall_rules:
  - service: ssh
  - port: 3389
php_users:
  - user: devops
    group: docker
php_selinux_booleans:
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
- name: Install php on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: php is configured
      import_role:
        name: devopstoolbox.php
      vars:
        php_packages_state: present
        php_remove_packages: true
        php_enable_service: true
        php_enable_selinux: true
        php_copy_templates: true
        php_firewall_configure: true
        php_firewall_rules:
          - service: ssh
          - port: 3389
        php_users:
          - user: devops
            group: docker
        php_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: php
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
