LAMP on Steroids
================

**LAMP On Steroids** contains a set of Ansible roles that help set up a modern RHEL web server. We test it out mainly on
the `RockyLinux 9` system, but it should also work on `CentOS Stream 9` and other RHEL-based systems.
The primary purpose is to set up a working and secure web server for PHP/Node.js applications.

Prerequisites
-------------

You must have the Ansible installed in your system. If you don't have it, please follow this
guide - [Installing Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).

It is best to use the latest version of Ansible. We tested the roles in this repository on Ansible **8.3.0** (core
version **2.15.3**). If you are running an older version, we recommend updating to the newer version of Ansible.

How to use?
-----------

First create your Inventory file. You can work entirely in this repository. Name your Inventory file `hosts` (this file is in .gitignore) and setup all required connections there.

Example Inventory file:
```
[example-host]
192.168.87.87   ansible_ssh_user=vagrant    ansible_ssh_private_key_file="~/.ssh/id_rsa"
```

Next setup your playbook. The easiest way is to copy `playbooks/example-playbook.yml` file and comment out the roles you don't need. All `.yml` files are ignored in `playbooks` directory.

Optionally you can add variable files that will override defaults in roles. All `.yml` files in `vars` directory are in .gitignore

Run following command to execute this playbook:
```
ansible-playbook -i hosts playbooks/YOUR_PLAYBOOK_FILE.yml
```

Some tasks are marked with `healthcheck` tag. They will do some basic checks to see if system is up and running. All tasks should be green. If there are tasks marked as changed, something is not OK.
```
ansible-playbook -i hosts playbooks/YOUR_PLAYBOOK_FILE.yml --tags="healthcheck" 
``` 

Please take a look at `vars/example-vars.yml` file and make sure that you override default developer account password and path to your public key. 
Public key is required for logging in via SSH with RSA keys. Logging with password will be turned off.
Password is required for sudo, if you will set `centos_groups_wheel_password_required` to `yes` (this is default value). Once sudo with password will be available, you must execute playbooks with `-K` argument and pass sudo password:

```
ansible-playbook -i hosts playbooks/YOUR_PLAYBOOK_FILE.yml -K
```

Included roles
--------------
**dnf** - Handle [RockyLinux](https://rockylinux.org/news/) package management, security features, and package installation optimizations.

**users** - Handle users/groups management and enables sudo.

**ssh** - SSHD hardening.

**ntp** - Take care of system timezone and NTP server. It uses Chrony for using NTP.

**openssl** - Compile [OpenSSL](https://github.com/openssl/openssl/tags) from source (3.0.1)

**git** - Compile and install [Git](https://github.com/git/git/tags) from source (2.42.0) 

**nginx** - Compile, install and configure [nginx](https://nginx.org/en/download.html) from source (1.25.2)

**php** - Compile, install and configure [PHP](https://github.com/php/php-src/tags) and tools (8.2.9)

**firewalld** - Setup firewalld as base firewall

**mysql** - Install and configure [MySQL](https://dev.mysql.com/downloads/mysql/) community server (8.0.32). Create databases and users. Install MySQLTuner and set up backups.

**awscli** - Install and configure [AWS CLI](https://github.com/aws/aws-cli/tags) command line tool (2.9.21)

**redis** - Install and configure [Redis](https://redis.io/download) with TLS support (7.0.8)

**nodejs** - Install [NodeJs](https://nodejs.org/en/) and NPM (20.5.1)

**centos** - Takes care of system settings. Set up firewall based on iptables. Disable Transparent Huge Pages.
You can setup logrotate scripts with this role as well.

**httpd** - Compile and configure Apache httpd from source with OpenSSL (2.4.33)

**mongodb** - Install and configure MongoDB (3.4.7) with authentication

**letsencrypt** - Install Certbot and obtain certificates from Let's Encrypt

Changelog
---------

You can find changelog on our [GitHub Wiki page](https://github.com/blacksaildivision/lamponsteroids/wiki/Changelog).
