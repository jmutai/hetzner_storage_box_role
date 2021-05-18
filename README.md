Role Name
=========

Ansible role to install Samba tools and configure mounting of Hetzner Storage box share

Requirements
------------

Requires configured Storage box with username, password and Share URL

Role Variables
--------------

Set below variables in playbook file:

```
    vars:
      storage_box_username:         #Storage box share username
      storage_box_password:         #Storage box share user password
      hetzner_storage_box_fstab:
      - mountpoint: /mnt            #Where samba share is mounted in the server
        mount_system_user: root     #User in the server to mount
        mount_system_group: root    #Server user group managing mount
```

Dependencies
------------

No other role dependency

Example Playbook
----------------

```
---
- name: Include Hetzner storage setup role
  hosts: servers #Server group / IP Address / Server hostname in hosts inventory
  roles:
  - jmutai.hetzner_storage_box_role
  vars:
    storage_box_username: <username>         #Storage box share username
    storage_box_password: <password>        #Storage box share user password
    hetzner_storage_box_fstab:
    - mountpoint: /mnt            #Where samba share is mounted in the server
      mount_system_user: root     #User in the server to mount
      mount_system_group: root    #Server user group managing mount
```

Hosts Inventory example
-----------------------

```
[all:vars]
ansible_user='centos' #change accordingly
ansible_become=yes
ansible_become_method=sudo

[servers]
#List server addresses below, one per line
```

Download role from galaxy
-------------------------

```
ansible-galaxy install jmutai.hetzner_storage_box_role
```

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
