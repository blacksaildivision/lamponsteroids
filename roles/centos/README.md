CentOS role
==========

This role will install and configure CentOS to version 7.4
There are multiple tasks and scenarios this role can do:
 - `groups` - create groups for users
 - `users` - create users with SSH keys
 - `sudo` - enable sudo group
 - `ssh` - hardening of SSH 
 - `thp` - disable Transparent Huge Pages
 - `logrotate` - manage logrotate scripts
 - `iptables` - create strong and secure firewall
   

What you should change in defaults?
---------------------

Please review briefly `/roles/centos/defaults/main.yml` file. Most of values are set to harden and optimize server. You will probably want to change `centos_users_available` with list of users that will be created on the server.
Don't forget to add `wheel` group if you need sudo power for given user. Also generate safe password and store it inside ansible-vault for best security.
