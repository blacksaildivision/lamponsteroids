Yum role
==========

This role is responsible for updating, installing and removing packages with yum package manager. 
It also contains some security checks for GPG validation during package management.
This role also installs two helper tools: `yum-cron` and `deltarpm` to speed up package installation.


Variables
---------
Here is the list of configurable variables for this role:

 - `yum_packages_to_remove` by default is empty, but you can add the packages you wish to remove here.
 
 - `yum_packages_to_install` list of additional tools to install. `libselinux-python` is required for Ansible roles.

 - `yum_exclude_packages_to_update` packages that will be excluded from updates. It is helpful when you wish to manage default packages but for instance you don't want to install new version of MySQL etc. By default there are the packages that are managed by other roles like MongoDB, MySQL and Node.js. All other packages will be updated to latest version.
 
 - `yum_exclude_packages_to_autoremove` packages that will be excluded from `yum autoremove` command. By default it's `libselinux-python` that is sometimes removed but it is necessary for Ansible purposes.
 
 