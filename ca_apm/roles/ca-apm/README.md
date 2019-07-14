Role Name
=========

This role installs the CA APM Agents (infrastructure and javaagent)

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

At the moment there are no role variables.

Dependencies
------------

At the moment there are no dependencies.

Example Playbook
----------------

---
- hosts: all
  remote_user: roothp
  become: yes
  become_method: sudo
  gather_facts: yes

  vars_files:
    - "{{ playbook_dir }}/../vars/local.yml"
    - "{{ playbook_dir }}/../vars/main.yml"

  tasks:

    - include: "{{ playbook_dir}}/../roles/ca-apm/tasks/machineagent.yml"
      tags:
        - ca-apm
        - machineagent

    - include: "{{ playbook_dir}}/../roles/ca-apm/tasks/javaagent.yml"
      tags:
        - ca-apm
        - javaagent

- name: include restart all tomcats
  include: "{{ playbook_dir}}_restart_all_tomcats_new.yml"

License
-------

BSD

Author Information
------------------

N, Tom <tomchou-n.sana@hpe.com>
Laurisch, Helge (HPE Pointnext External Supplier) <helge.laurisch@hpe.com> 

