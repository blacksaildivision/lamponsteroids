DNF role
==========

This role is responsible for upgrading, installing and removing packages with DNF package manager. 
It also contains some security checks for GPG validation during package management.
This role also installs `dnf-automatic` to speed up package installation.


Variables
---------
Here is the list of configurable variables for this role:

 - `dnf_packages_to_remove` by default is empty, but you can add the packages you wish to remove here.
 
 - `dnf_packages_to_install` list of additional tools to install. By default it's empty.

 - `dnf_exclude_packages_to_upgrade` packages that will be excluded from upgrades. It is helpful when you wish to manage default packages but for instance you don't want to install new version of MySQL etc. By default there are the packages that are managed by other roles like MongoDB, MySQL and Node.js. All other packages will be updated to latest version.
 