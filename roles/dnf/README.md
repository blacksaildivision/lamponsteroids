DNF role
==========

This role is responsible for upgrading, installing, and removing packages with the DNF package manager.
It also contains some security checks for GPG validation during package management.
This role also installs `dnf-automatic` to speed up package installation.


Variables
---------
Here is the list of configurable variables for this role:

- `dnf_packages_to_install` list of additional tools to install. By default, it's empty.

- `dnf_exclude_packages_to_upgrade` packages that DNF will exclude from upgrades. This is helpful when you wish to manage default packages but don't want to install a new version of MySQL, etc. All MySQL, MongoDB, and Node.js packages will be excluded by default as they are managed from different roles in this project. DNF will update all other packages to the latest version.

- `dnf_packages_to_remove` is empty by default, but you can add the packages you wish to remove here.
