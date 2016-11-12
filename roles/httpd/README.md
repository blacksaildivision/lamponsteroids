HTTPD role
==========

This role will install Apache httpd https://httpd.apache.org/ server on CentOS.
Apache httpd will be installed in latest version (2.4.23) and will be compiled from source.

What you should know?
---------------------

**Installation**
For installing purpose you need to configure two variables
 - `httpd_build_user`
 - `httpd_build_group`
 
You should set them to an existing user and group it cannot be root. Compiling software from root account can have serious security impacts.
By default it's set to `developer`. If you are using whole LampOnSteroids project, such user will be created in `centos` role.
If you only use `httpd` role, make sure that you set these variables correctly.