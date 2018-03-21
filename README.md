Zimbra_ansible_install_role
=========
Install zimbra 8.7 or 8.8 with ansible. You will install with two forms:

- Default
- Using prompt variable with true value. (e.g. -e prompt=true)

Requirements
------------

- Ansible v. 2.4+.
- Edit the remote group into your inventory host
- RedHat/CentOS 7.x

Role Variables
--------------

Edit the variables into vars/main.yml file with:

- srv_hostname: 'fqdn of your machine'
- zim_url: URL for download the zimbra compress file.
- zim_unarchive: This name will be generate automatically from zim_url variable
- zim_short_vs: This variable is used for validate zimbra version
- ip_client: Server IP
- ip_dns: DNS Server IP

Notifications
------------

If you want a notification on Telegram when the ansible process is finished, do this:

Change this variables values from your vars/main.yml file

- token_id: id token from your telegram chat group
- chatid: chat id from your telegram chat group

Then, execute the playbook adding the tg variable with true value. (e.g. -e tg=true)

Author Information
------------------

Kevyn Perez kevynkl2@gmail.com
Cel Number 5412-7538
