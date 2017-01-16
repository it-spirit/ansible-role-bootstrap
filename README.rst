spirit.bootstrap
================

Ansible role to bootstrap new servers for it-spirit.

Use this role to do the initial provisioning of your new server.
It will ensure that your software packages are up to date and your system administrators are set up.


Requirements
------------

This role has no requirements.


Role Variables
--------------

Available variables are listed below, along with default values (see `vars/main.yml`).

sysadmins
#########

A list of system administrators to set up.

::

   sysadmins: []
   # - name: username
   #   fullname: User Name
   #   state: present
   #   shell: '/bin/bash'
   #   password: 'secret'
   #   email: username@example.com
   #   ssh_key: 'ssh key'


firewall_allowed_tcp_ports
##########################

This one overrides the default settings from ``geerlingguy.security``.
You can override it within your playbook, group or host variables.

::

   firewall_allowed_tcp_ports:
     - '25'


Dependencies
------------

This role has dependencies to the following roles:

- `geerlingguy.security <https://galaxy.ansible.com/geerlingguy/security/>`_
- `franklinkim.sudo <https://galaxy.ansible.com/franklinkim/sudo/>`_


Example Playbook
----------------

::

   - hosts: all
     vars_files:
       - vars/secrets.yml

     roles:
       - spirit.bootstrap

Inside ``vars/secrets.yml``::

   sysadmins:
     - name: jsmith
       fullname: John Smith
       state: present
       shell: '/bin/bash'
       password: 'hashedpassword'
       email: jsmith@example.org
       ssh_key: 'ssh-rsa ABCDEF00000000... jsmith@example.org'


License
-------

MIT


Author Information
------------------

This role was created 2016-2017 by `it-spirit Software <http://it-spir.it>`_.
