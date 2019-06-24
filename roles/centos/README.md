CentOS role
==========

This role will install and configure CentOS to version 7.4
There are multiple tasks and scenarios this role can do:
 - `ssh` - hardening of SSH 
 - `thp` - disable Transparent Huge Pages
 - `logrotate` - manage logrotate scripts
 - `iptables` - create strong and secure firewall
   

What you should change in defaults?
---------------------

Please review briefly `/roles/centos/defaults/main.yml` file. Most of values are set to harden and optimize server.
