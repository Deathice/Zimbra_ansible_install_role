![Linux Distro](https://img.shields.io/badge/platform-CentOS%20%7C%20Red%20Hat-blue.svg)
[![Zimbra Version](https://img.shields.io/badge/Zimbra-8.8.15-blue.svg)](https://www.zimbra.com/downloads/zimbra-collaboration-open-source/)

Zimbra_ansible_install_role
=========
With this role, you can install zimbra 8.8.x with ansible choosen one of the following two ways:

- Default
- Using prompt variable with true value. (e.g. -e prompt=true)

Installing the Ansible Role
---------------------------

```
ansible-galaxy install deathice.zimbra_ansible_install_role
```
or

```
git clone https://github.com/Deathice/Zimbra_ansible_install_role.git
```

Requirements
------------

- Ansible v. 2.4+.
- Edit the remote group into your inventory host
- RedHat/CentOS 7.x

Role Variables
--------------

Edit the variables into default/main.yml file with:

- srv_hostname: 'fqdn of your machine'
- zim_url: URL for download the zimbra compress file.
- ip_client: Server IP
- ip_dns: DNS Server IP
- token_id: 'Token ID from telegram'
- chatid: 'Chat ID from telegram'
- timezone: Set the timezone to the system (e.g. America/Guatemala)

Notifications
-------------

If you want a notification on Telegram when the ansible process is finished, do this:

Change this variables values from your default/main.yml file

- token_id: id token from your telegram chat group
- chatid: chat id from your telegram chat group

Then, execute the playbook adding the tg variable with true value. (e.g. -e tg=true)

- If you dont know how to create a telegram bot, see https://core.telegram.org/bots
- If you don know how to get token_id and chat id, see https://stackoverflow.com/questions/32683992/find-out-my-own-user-id-for-sending-a-message-with-telegram-api

## Note
This role not support backward compatibility.


Author Information
------------------

- Kevyn Perez kevynkl2@gmail.com
- Cellphone Number +(502) 5412-7538
- LinkedIn linkedin.com/in/kevyn-perez-marin-a0b198b7
- Ansible Galaxy https://galaxy.ansible.com/deathice
