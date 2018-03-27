GIT role
========

This role will install git https://git-scm.com/ on CentOS server.
Git will be installed in latest version (2.16.3) and will be compiled from source.

What you should know?
----------------------

There are two things. First are two variables:
 - `git_build_user`
 - `git_build_group`
 
You should set them to an existing user and group it cannot be root. Compiling software from root account can have serious security impacts.
By default it's set to `developer`. If you are using whole LampOnSteroids project, such user will be created in `centos` role.
If you only use git role, make sure that you set these variables correctly.

OpenSSL
-------

This role requires `openssl` role installed. It will install latest version of OpenSSL and GIT will be configured with `--with-openssl` parameter and compiler flags pointing to location where latest version is compiled (/usr/local/openssl)
