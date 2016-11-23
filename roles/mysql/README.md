MySQL role
==========

This role will install MySQL Community server on CentOS 7.
MySQL will be installed in latest version (5.7.16). 

What you should know?
---------------------

**Setting root password**
You must change following variable `mysql_root_password` to your own password. Please use Ansible vault to store it safely.
If you want to change root password, add `mysql_root_old_password` variable with old/current root password. It will log root user with this password and change it to `mysql_root_password`

**Configuration**
There is list of users that should be added to `mysql` group. Default value is `developer`. If you are using entire project, such user is created in `centos` role. If you only use this role, make sure to set it to empty list `[]` or existing user(s).

**Databases**
In order to create databases and assign users to it, please use `mysql_databases` variables. Each item should contain three fields:
- `database` with name of database to create
- `user` with username that will be assigned to this database
- `password` password for the user

Created user will have ALL privileges to created database.
