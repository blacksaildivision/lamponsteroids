SSH role
==========

This role hardens SSHD config.


Variables
---------
Here is the list of configurable variables for this role:

 - `ssh_sshd_default_config_options` this is the list of key and values to be set in `/etc/ssh/sshd_config` config file. You should not change it directly. Instead please set `ssh_sshd_user_config_options` variable. 
 
 - `ssh_sshd_user_config_options` by default it's empty. You can add additional options to be set in `/etc/ssh/sshd_config` file or override the values from `ssh_sshd_default_config_options` variable. These two vars will be combined into single variable. 

 - `ssh_sshd_host_keys` list of enabled HostKeys in `/etc/ssh/sshd_config` config file. All other keys not specified here will be removed from config file.oved but it is necessary for Ansible purposes.
