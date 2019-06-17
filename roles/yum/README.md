Yum role
==========

This role is responsible for updating, installing and removing packages with yum role. 
It also contains some security checks for GPG validation during package management.
This role also installs two helper tools: `yum-cron` and `deltarpm` to speed up package installation.


Variables
---------
Here is the list of configurable variables for this role:

 - `yum_packages_to_remove` by default is empty, but you can add the packages you wish to remove here.

 - `yum_packages_to_install_or_update` packages that will be installed if not present or updated to latest version. By default it's `*` which means that all packages will be updated.
 
 - `yum_exclude_packages_to_install_or_update` packages that will be excluded from updates. It is helpful when you wish to manage small packages but for instance you don't want to install new version of MySQL etc. By default there are the packages that are managed by other roles like MongoDB, MySQL and Node.js.
 