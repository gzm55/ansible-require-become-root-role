require_become_root (1.0.3)
===============================

Require the following tasks can `become` as `root` user.

The role outputs two fact variables per host:
- `root_need_become` - if login directly as root, this will set False
- `root_user` - the real root user name, almost always `root`

Requirements
------------

python module
- ansible>=2.0
- jinja2>=2.6

remote command: id

Role Variables
--------------

N/A

Dependencies
------------

N/A

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: gzm55.require_become_root }
      tasks:

         - name: simple become way
           become: True
           become_user: root
           command: exit

         - name: precise become way
           become: "{{ root_need_become }}"
           become_user: "{{ root_user }}"
           vars:
           - ansible_become: "{{ root_need_become }}"
           - ansible_become_user: "{{ root_user }}"
           command: exit

License
-------

BSD
