LAMP on Steroids
================

Setup your server quickly with LAMP on Steroids. This repository is dedicated to `CentOS 7` system.
Main goal is to setup working LAMP server with latest versions of available tools. 
Secondary goal is to keep your server secure and up to date. 

How to use?
-----------

Make sure that you have Ansible installed. Minimal version required for the included roles and playbooks is `2.0`.

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

**centos** - Takes care of system settings. Configure yum, yum-cron, update and remove packages. 
It also take cares of groups and users. Enable sudo. Configure secure SSH. Set up firewall based on iptables.

**ntp** - Takes care of system timezone and NTP server. It uses Chrony for using NTP.

**git** - Install latest version of git. 

**httpd** - Install and configure latest version of Apache httpd.

**datadog** - Install and configure datadog agent.

Changelog
---------

You can find changelog on our [GitHub Wiki page](https://github.com/blacksaildivision/lamponsteroids/wiki/Changelog).
