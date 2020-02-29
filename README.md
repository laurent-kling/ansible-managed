managed ?
=========

It is a role to create ssh only user to manage hosts with Ansible.

The create user account don't have password.

Requirements
------------

* Ubuntu 18.04
* CentOS 7.3

Role Variables
--------------

By default, these 3 variables are used

1. **manager_local_ssh_key_path**: "~/.ssh/id_rsa.pub"

   The local path of the public SSH key.

2. **managed_name**: managed

   The username used to manage Ansible hosts

3. **managed_generate_local_ssh_key**: False

   Don't generate local SSH key

Dependencies
------------

Fork of create-user-ansible

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: managed, managed_name: ansible }

License
-------

MIT

Author Information
------------------

[Laurent Kling](https://people.epfl.ch/laurent.kling/?lang=en) @ [EPFL - STI - IT](https://sti-it.epfl.ch/)

## Version

### v0.0.1

*Released: Februar 29th 2020*

- Initial release