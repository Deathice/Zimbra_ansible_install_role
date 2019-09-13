Zimbra_ansible_install_role
=========
Install zimbra 8.8.x with ansible. You will install with two forms:

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
- ip_client: Server IP
- ip_dns: DNS Server IP
- token_id: 'Token id of telegram'
- chatid: 'Chat id of telegram'
- timezone: timezone for configure the system (e.g. America/Guatemala)

Notifications
-------------

If you want a notification on Telegram when the ansible process is finished, do this:

Change this variables values from your vars/main.yml file

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
