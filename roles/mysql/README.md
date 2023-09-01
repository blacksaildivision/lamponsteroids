MySQL role
==========

This role will install MySQL Community server, configure the server, setup root account, create databases and users.
It will also install MySQL tuner script and take care of database backup with possible push update to S3 bucket.

Variables
---------
Here is the list of configurable variables for this role:

 - `mysql_version` version of MySQL server that should be installed.
 
 - `mysql_root_password` root password. Create a very strong password and override it in your own variables.
 
 - `mysql_root_host` host of root password. Default is `127.0.0.1` instead of `localhost` due to `skip-name-resolve`.
 
 - `mysql_config_file` path to MySQL server configuration file. Default is `/etc/my.cnf`.
 
 - `mysql_default_configuration` list of configuration variables that should be present in MySQL config file. If you want to override the variables or add your own, use `mysql_user_configuration`.

- `mysql_user_configuration` list of additional configuration that should be present in MySQL config file or override the values set in `mysql_default_configuration`.

- `mysql_group_users` list of users that should be added to mysql group.

- `mysql_databases` dictionary of databases that should be present in the system. Key is the database name. Here is the list of available options:
  - `user` user that should have access to given database.
  - `password` password of the user.
  - `host` host of the user.
  - `tls_requires` requirements for secure transport. The default is `{}`.
  - `backup` when backup is set to yes, additional user with access to selected database will be created.
  - `backup_directory` directory where to store compressed backup files.
  - `backup_directory_owner` owner of the backup directory. `root` is the default.
  - `backup_directory_group` group of the backup directory. `root` is the default.
  - `rotate` number of backup files that should be kept on the server. `30` is default.
  - `s3_bucket` when this variable is set, backup script will try to push compressed dump to S3 bucket. 
 
 - `mysql_backup_user` name of the user for backups. Defaults to `backup`.
 
 - `mysql_backup_user_password` password for backup user.
