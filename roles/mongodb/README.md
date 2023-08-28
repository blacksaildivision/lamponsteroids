MongoDB role
==========

This role will install MongoDB Community server, configure the server, setup admin account, create databases and users.
It will also install take care of database backup with possible push update to S3 bucket.

Variables
---------
Here is the list of configurable variables for this role:

- `mongodb_version` version of MongoDB server that should be installed.

- `mongodb_config_file` path to the `mongod.conf` configuration file.

- `mongodb_admin_password` admin password. Create very strong password. This item should not rely on this role
  default value, you must change it to protect your MongoDB instance.

- `mongodb_backup_user_password` backup user password. This user have minimal permissions granted to perform the backups
  of the database.

- `mongodb_host` host under which the MongoDB will run and be accessible from. The default value is **mongo.local**.
  This role configures MongoDB server with TLS access, so it must be a valid domain.

- `mongodb_databases` dictionary of databases that should be present in the system. Key is the database name. Here is
  the list of available options:
    - `user` user that should have access to given database.
    - `password` password of the user.
    - `roles` list of roles that should be granted to the given user.
    - `backup` (boolean) whether the database should be backed up.
    - `backup_directory` where the backups should be stored.
    - `s3_bucket` name of the s3 bucket. It requires working AWS CLI setup. If present, the backup is uploaded to AWS.
    - `rotate` number of backup files that should be kept on the server. `30` is default.

- `mongodb_tls_csr` minimal data for creating self-signed certificate.
    - `cn` by default it should be the host name.
    - `o` organization for certificate.
    - `ou` organizational unit for certificate.
