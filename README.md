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
  become: true
  remote_user: root
  gather_facts: true

  roles:
    - ITM_zimbra_ansible_install

- name: Continue Zimbra Installation
  hosts: remote
  become: true
  remote_user: root
  gather_facts: true

  tasks:
    - include_vars: ITM_zimbra_ansible_install/vars/main.yml

    - name: Configure dnsmasq
      template:
        src: ITM_zimbra_ansible_install/templates/dnsmasq.conf.j2
        dest: /etc/dnsmasq.conf
        owner: root
        group: root
        mode: 644

    - name: Installing Zimbra
      block:
        - name: Configuring /etc/hosts
          lineinfile:
            path: /etc/hosts
            regexp: '^{{ ansible_default_ipv4.address }}.*'
            line: '{{ ansible_default_ipv4.address }} {{ ansible_fqdn }} {{ ansible_hostname }}'
          tags:
            - test

        - name: unarchive zimbra file
          unarchive:
            src: /tmp/zcs/{{ zim_unarchive }}.tgz
            dest: /tmp/zcs
            remote_src: true

        - name: Installing Zimbra Collaboration just the Software
          shell: ./install.sh -s < /tmp/zcs/installZimbra-keystrokes
          args:
            chdir: /tmp/zcs/{{ zim_unarchive }}

        - name: Installing Zimbra Collaboration injecting the configuration
          shell: /opt/zimbra/libexec/zmsetup.pl -c /tmp/zcs/installZimbraScript
    
        - name: Change to zimbra user and execute zmcontrol restart
          shell: su - zimbra -c 'zmcontrol restart'
      when: 
        - ansible_os_family == 'RedHat'
        - ansible_distribution_major_version == '7'

  tasks:
    - include_vars: ITM_zimbra_ansible_install/vars/main.yml

    - name: Configure dnsmasq
      template:
        src: ITM_zimbra_ansible_install/templates/dnsmasq.conf.j2
        dest: /etc/dnsmasq.conf
        owner: root
        group: root
        mode: 644

    - name: Installing Zimbra
      block:
        - name: Configuring /etc/hosts
          lineinfile:
            path: /etc/hosts
            regexp: '^{{ ansible_default_ipv4.address }}.*'
            line: '{{ ansible_default_ipv4.address }} {{ ansible_fqdn }} {{ ansible_hostname }}'
          tags:
            - test

        - name: unarchive zimbra file
          unarchive:
            src: /tmp/zcs/{{ zim_unarchive }}.tgz
            dest: /tmp/zcs
            remote_src: true

        - name: Installing Zimbra Collaboration just the Software
          shell: ./install.sh -s < /tmp/zcs/installZimbra-keystrokes
          args:
            chdir: /tmp/zcs/{{ zim_unarchive }}

        - name: Installing Zimbra Collaboration injecting the configuration
          shell: /opt/zimbra/libexec/zmsetup.pl -c /tmp/zcs/installZimbraScript
    
        - name: Change to zimbra user and execute zmcontrol restart
          shell: su - zimbra -c 'zmcontrol restart'
      when: 
        - ansible_os_family == 'RedHat'
        - ansible_distribution_major_version == '7'
```

Author Information
------------------

Kevyn Perez kperez@itm.gt