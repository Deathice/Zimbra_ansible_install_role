Zimbra_ansible_install_role
=========
Install zimbra with ansible

Requirements
------------

- Ansible v. 2.4+.
- Edit the remote group into test/inventory
- Redhat/CentOS 7.x (Minimal installation recomended)

Role Variables
--------------

Edit the variables into vars/main.yml file with:

- pass_config: 'Variable for the password that use the installation.'
- srv_hostname: 'fqdn of your machine'
- zim_url: URL for download the zimbra compress file.
- zim_unarchive: Name of you compress file unarchive
- ip_client: Server IP
- ip_dns: DNS Server IP


Author Information
------------------

Kevyn Perez kevynkl2@gmail.com
