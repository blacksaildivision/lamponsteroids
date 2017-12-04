OpenSSL role
============

This role will install latest version of OpenSSL (1.1.0g) on CentOS server.
OpenSSL will be compiled from source.

What you should know?
----------------------

There are two things. First are two variables:
 - `openssl_build_user`
 - `openssl_build_group`
 
You should set them to an existing user and group it cannot be root. Compiling software from root account can have serious security impacts.
By default it's set to `developer`. If you are using whole LampOnSteroids project, such user will be created in `centos` role.
If you only use `openssl` role, make sure that you set these variables correctly.
