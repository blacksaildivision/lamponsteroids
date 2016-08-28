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
ansible-playbook -i hosts playbooks/YOUR_PLAYBOOK_FILE.yml --tags="healtcheck" 
``` 

Included roles
--------------

**centos** - Take care of system settings. Configure yum, yum-cron, update and remove packages.

Changelog
---------

You can find changelog on our [GitHub Wiki page](https://github.com/blacksaildivision/lamponsteroids/wiki/Changelog).
