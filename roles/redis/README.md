Redis role
==========

This role will install and configure Redis server on CentOS.
Redis will be installed in latest version (4.0.1) and will be compiled from source.

What you should know?
---------------------

**Installation**
For installing purpose you need to configure two variables
 - `redis_build_user`
 - `redis_build_group`
 
You should set them to an existing user and group it cannot be root. Compiling software from root account can have serious security impacts.
By default it's set to `developer`. If you are using whole LampOnSteroids project, such user will be created in `centos` role.
If you only use `redis` role, make sure that you set these variables correctly.
