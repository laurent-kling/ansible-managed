managed ?
=========

It is a role to create SSH user to manage hosts with Ansible or One Time Password SSH with HashiCorp.

The created user account doesn't have a password.

By default, the user has the full sudo without need to enter a password.

* **Limited** option specifies what command is allowed.

Requirements
------------

* Ubuntu 18.04
* CentOS 7.3

Role Variables
--------------

By default, these 3 variables are used:

1. **manager_local_ssh_key_path**: "~/.ssh/id_rsa.pub"

   The local path of the public SSH key.

2. **managed_name**: managed

   The username used to manage Ansible hosts

3. **managed_generate_local_ssh_key**: False

   Don't generate local SSH key

The additional variables are

* **limited**: True

  Allow only limited command to be executed with sudo without a password.


* **limited_sudo**:  ['reboot','kill']

  List of all command to be executed with sudo without a password

  

Example Playbook
----------------

To installing this role from ansible-galaxy

```bash
ansible-galaxy install laurent_kling.managed
```

Including an example of how to use it with required variables :

```yaml
---
- name: create the user "managed" with sudo without password
  hosts: clients
  become: true

  roles:
    - role: laurent_kling.managed
```

With the **Limited** option to run command "reboot" & "kill" with sudo without a password

```yaml
---
- name: create the user "managed" with sudo without a password for reboot & kill only
  hosts: clients
  become: true

  roles:
    - role: laurent_kling.managed
      limited: True
      limited_sudo:
      - "reboot"
      - "kill"
```

When used in conjunction with the role `laurent_kling.vault-otp` to setup One Time Password SSH with HashiCorp.

```yaml
---
- name: create the user "managed" with full access with OTP SSH with HashiCorp
  hosts: clients
  become: true

  roles:
    - laurent_kling.managed
    - laurent_kling.vault-otp
      vault_addr: https://vault:8200
      ssh_mount_point: ssh
      vault_ca_cert_file: vault.crt
```



License
-------

MIT

Author Information
------------------

[Laurent Kling](https://people.epfl.ch/laurent.kling/?lang=en) @ [EPFL - STI - IT](https://sti-it.epfl.ch/)

## Version

### v1.0.1

*Released: April 21, 2020*

- Don't add default sudo group by OS

### v1.0.0

*Released: April 19, 2020*

- Added limited option
- Correction of the documentation

### v0.0.1

*Released: February 29, 2020*

- Initial release

Dependencies
------------

Fork of create-user-ansible

----------------