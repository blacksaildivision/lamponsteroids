LAMP on Steroids
================

Setup your server quickly with LAMP on Steroids. This repository is dedicated to the `CentOS 7/8` system.
The main goal is to set up a working LAMP server with the latest versions of available tools.
The secondary goal is to keep your server secure and up to date.

How to use?
-----------

Make sure that you have Ansible installed. The minimal version required for the included roles and playbooks is `2.9`.

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

**git** - Compile and install [Git](https://github.com/git/git/tags) from source (2.39.1) 

**nginx** - Compile, install and configure [nginx](https://nginx.org/en/download.html) from source (1.23.2)

**php** - Compile, install and configure [PHP](https://github.com/php/php-src/tags) and tools (8.1.12)

**firewalld** - Setup firewalld as base firewall

**mysql** - Install and configure [MySQL](https://dev.mysql.com/downloads/mysql/) community server (8.0.31). Create databases and users. Install MySQLTuner and set up backups.

**awscli** - Install and configure [AWS CLI](https://github.com/aws/aws-cli/tags) command line tool (2.8.7)

**redis** - Install and configure [Redis](https://redis.io/download) with TLS support (7.0.5)

**nodejs** - Install [NodeJs](https://nodejs.org/en/) and NPM (19.0.0)

**centos** - Takes care of system settings. Set up firewall based on iptables. Disable Transparent Huge Pages.
You can setup logrotate scripts with this role as well.

**httpd** - Compile and configure Apache httpd from source with OpenSSL (2.4.33)

**datadog** - Install and configure DataDog agent with multiple integrations.

**mongodb** - Install and configure MongoDB (3.4.7) with authentication

**letsencrypt** - Install Certbot and obtain certificates from Let's Encrypt

Changelog
---------

You can find changelog on our [GitHub Wiki page](https://github.com/blacksaildivision/lamponsteroids/wiki/Changelog).
