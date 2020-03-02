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
**General**

- Ansible v. 2.4+.
- Edit the remote group into your inventory host
- RedHat/CentOS 7.x

**Logo**

If you will deploy your own logo, is necessary (more information see the [documentation](http://www.jorgedelacruz.es/2015/09/02/zimbra-cambiar-logo-en-version-open-source-o-network-edition/))

- The application_banner has 200px X 35px pixels and type PNG.
- The login_banner has 440px X 60px pixels and type PNG.

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
- logo: Set to true to deploy your own logo
- url_app: If logo is true, you must specify the full URL when is located the application_banner
- url_login: If logo is true, you must specify the full URL when is located the login banner
- url_redirect: If logo is true, you can change the redirect URL when the app or login banner is clicked (optional)


Main Playbook Examples
-------------
**Deploy zimbra from scratch**

> site.yml


```
---
- name: Execute role(s)
  hosts: remote

  roles:
    - Zimbra_ansible_install_role
```
ansible-playbook site.yml


**If you have a personal logo, you can set the following variables**

> defaults/main.yml


```
---
logo: true
url_app: https://my.images.com/images/application_banner.png
url_login: https://my.images.com/images/login_banner.png
```

**If you want to execute only the procedure to deploy your own logo, with the defaults/main.yml variables**

ansible-playbook site.yml --tags only_logos

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
