Git role
========

This role will compile and install Git from source code

Variables
---------
Here is the list of configurable variables for this role:

 - `git_version` version of Git to install.

 - `git_install_path` path where Git will be installed. By default it's `/usr/local/git`

 - `git_sources_location` path where Git source code will be downloaded and unpacked. Make sure that `git_build_user` has access to this directory. By default it's `/usr/src`
 
 - `git_build_user` user that will build the Git. It's not compiled as root. By default it's `developer`. If you don't have such user or you wish to provide your own, make sure the user exists.
 
 - `git_build_group` group of the user for the build process. By default it's `developer`.
