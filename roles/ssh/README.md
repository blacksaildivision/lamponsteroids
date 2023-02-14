SSH role
==========

This role hardens the SSHD config.


Variables
---------
Here is the list of configurable variables for this role:

- `ssh_sshd_default_config_options` is the list of keys and values to be set in the `/etc/ssh/sshd_config.d/` config
  file. It would be best if you did not change it directly. Instead, please put your config in
  the `ssh_sshd_user_config_options` variable.

- `ssh_sshd_user_config_options` by default it's empty. You can add additional options to be set
  in the `/etc/ssh/sshd_config.d` file or override the values from the `ssh_sshd_default_config_options` variable.
  Ansible will combine these two vars into a single variable.

- `ssh_sshd_host_keys` list of enabled HostKeys in the `/etc/ssh/sshd_config` config file. Ansible will remove all other
  keys not specified here from the config file.
