ITM_zimbra_ansible_install
=========
Install zimbra.

Requirements
------------

- Ansible v. 2.4+.
- Create a playbook with any name and copy the 'example playbook' content, do it outside of your role.
- Edit the remote group into test/inventory



Role Variables
--------------

Edit the variables into vars/main.yml file with:

- pass_config: 'Variable for the password that use the installation.'
- srv_hostname: 'fqdn of your machine'
- zim_url: URL for download the zimbra compress file.
- zim_unarchive: Name of you compress file unarchive
- ip_client: Server IP
- ip_dns: DNS Server IP


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
```
---
- name: Initializing ITM_zimbra_ansible_install role
  hosts: remote
  become: false
  remote_user: root
  gather_facts: true

  roles:
    - ITM_zimbra_ansible_install


```

Author Information
------------------

Kevyn Perez kperez@itm.gt
