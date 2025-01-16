CHANGELOG
=========

3.2.0
-----

- (BREAKING) php.ini will always be replaced with the php.ini-production during installation.
- (BREAKING) Change how the `[opcache]` section is configured and allow overrides. This also fixes a bug with setting `opcache` settings.
- (BREAKING) Each user in mysql role must have the `salt` parameter.
- (BREAKING) If you have backup enabled in mysql role, you must define `mysql_backup_user_salt` variable. 
- Use FQCNs in dnf role.
- Use handlers instead of tasks for displaying list of upgraded packages in dnf role.
- Update wording and fix typos in dnf role.
- Fix Ansible warning on consecutive calls when private key already exists in users role.
- Fix issue with removing user and groups in users role.
- Update Git to 2.47.1.
- Update nginx to 1.27.3. 
- Update nginx deps libraries - PCRE2 updated to 10.44, OpenSSL updated to 3.4.0, zlib updated to 1.3.1.
- Fix the brotli dependency installation in nginx role. 
- Update PHP to 8.4.2.
- Update composer to the latest version on systems without crontab. 
- Update MySQL to 8.4.3.
- Stop using `mysql_native_password` for root password in mysql role.
- Verify signature of downloaded MySQL RPM.
- Update Python Ansible MySQL plugin from 3.8 to 3.12.
- Update Redis to 7.4.0.
- Increase redis service start timeout.
- Disable TLS1.2 in redis role.
- Update Node.js to 22.12.0.
- Update MongoDB to 8.0.4.
- Execute clean shutdown only when mongod is running in mongodb role.
- Install Python 3.12 on remote to support pymongo and newer version of Ansible in mongodb role.
- Enable auto-restart for mongod in case of failure in mongodb role.
- Add mandatory CA file entry to configuration in mongodb role.
- Disable TLS1.2 in mongodb role.
- Enable backwards-incompatible features after install equal to the installed version in mongodb role.
- Use the certfile in all tasks when connecting to the database in mongodb role.
- Update AWS CLI to 2.22.33.
- Add salt to the mysql users configuration. 
- Update nginx default host configuration to fix http2 warning.
- Remove deprecated centos role.
- Turn on logging of denied packets in firewalld role.
- Enable HTTP/3 in nginx example.
- Add Ansible lint file.

3.1.0
-----

- Add the prerequisites section to the README file and information which version do we use to test the playbooks.
- Remove deprecated datadog role.
- Update GIT to 2.42.0.
- Remove deprecated Ansible `warn` param in git, php, nodejs, mysql, redis, awscli, openssl and nginx roles.
- Update nginx to 1.25.2 compiled with OpenSSL 3.1.2 and zlib 1.3.
- Update PHP to 8.2.9.
- Fix bug on servers where tar command in missing in PHP role.
- Add AVIF support for GD library in PHP role.
- Update Node.js to 20.5.1.
- (BREAKING) Change how the x509 is enabled for given user in MySQL.
- Update MySQL to 8.0.34.
- Fix missing permission for the MySQL backup user.
- Hide passwords in MySQL role output.
- Fix bug with invalid root password in MySQL.
- Fix deprecated innodb_log_file_size in MySQL.
- Fix bug when some of the packages from MySQL repository were not updated along server packages.
- Fix missing perl-diagnostics packages for MySQLTuner.
- Update MongoDB to 7.0.
- (BREAKING) Rewrite the mongodb role.
- Update Redis to 7.2.0.
- Fix bug in redis role on systems where openssl-devel package was missing.
- Update AWS CLI to 2.13.12.
- Restart services when packages where updated but no changes in config files were made.
- Increase redis service start timeout.
- Add full changelog to the repository.

3.0.0
-----

- Change the testing platform from **CentOS 8** to **RockyLinux 9**.
- Update AWS CLI to 2.9.21
- Update git to 2.39.1
- Update MySQL to 8.0.32
- Update nginx to 1.23.3
- Update nodejs to 19.6.0
- Update PHP to 8.2.2
- Update Redis to 7.0.8
- Mark `centos`, `datadog`, `httpd`, `openssl` roles as deprecated. They will be removed in future releases.
- Remove the `local` tag from all roles.
- Move additional rules from `/etc/ssh/sshd_config` to a separate file in the ssh role.
- Add the `.idea` directory to the .gitignore file.
- Change the default password for Redis.
- Fix MySQL, PHP, git, and nginx installation on RockyLinux.
- Fix bug in PHP role when extensions were not properly updated.
- Update the README file about the project.

2.6.0
-----

- Update AWS CLI to 2.4.7, task inclusion optimizations in the awscli role.
- Update GIT to 2.34.1
- Update MySQL to 8.0.27
- Update nginx to 1.21.5
- Change PCRE to PCRE2 in nginx
- Use OpenSSL v3.* instead of v1.* in nginx
- Remove insecure TLSv1 and TLSv1.1 protocols from nginx
- Update node to 17.3.0
- Update OpenSSL to 3.0.1
- Update PHP to 8.0.14
- Update Redis to 6.2.6
- Change hardcoded paths in Redis to configurable paths
- Change HTTP to HTTPS in download paths
- Improvement of the sentence syntax and added links in the README file.
- Redundant VERSIONS removed

2.5.0
-----

* Update OpenSSL to 1.1.1k
* Update GIT to 2.33.0
* Update nginx to 1.21.1 (included OpenSSL version to 1.1.1k and PCRE to 8.45)
* Update PHP to 8.0.9
* New option to add ports alongside the services to the internal zone
* Update MySQL to 8.0.26
* Update AWS CLI to 2.2.31
* Update Redis to 6.2.5
* Update NodeJS to 16.7.0

2.4.0
-----

* Fixes a bug with duplicated values in the list of packages left to update in dnf role
* Adds special local tag which allows skipping certain tasks in local environments without systemd, for instance in WSL
* Update OpenSSL to 1.1.1i
* Update Git to 2.30.1
* Update nginx to 1.19.6
* Update PHP to 8.0.2
* Update composer to version 2
* Update MySQL to 8.0.23
* Update AWS CLI to 2.1.25
* Update Redis to 6.0.10
* Rewrite NodeJs role and update nodejs version to 15.9.0
* Use new naming of repositories in the latest version of CentOS

2.3.0
-----

* Refactor Redis role
* Update Redis to 6.0.6
* Change how Redis is configured
* Add TLS support to Redis
* Handle kernel variables and THP in Redis role
* Fix false failure in PHP role when Zend Extension doesn't have available upgrade
* Fix bug in MySQL backup script when aws command couldn't be found
* Add InnoDB configuration to MySQL defaults

2.2.0
-----

* Update AWS CLI to version 2.0.28
* Add the possibility to allow traffic from selected IP addresses in firewalld role
* Refactor MySQL role
* Update MySQL to 8.0.21
* Change how MySQL configuration is working
* Add SSL connection setup for MySQL
* Change how MySQL tuner is installed, now it's cloned from git repository
* Change how root password is set in MySQL role

2.1.0
-----

* firewalld role added with basic firewall configuration oriented for security
* Roles tested on CentOS 8.2.2004
* Bug with incorrect gpgcheck fixed in DNF role
* git updated to 2.27.0
* nginx updated to 1.19.0 and compiled with OpenSSL 1.1.1g
* OpenSSL updated to 1.1.1g
* PHP updated to 7.4.7
* Bug with failed install task for Zend Extension fixed
* Some typos fixed

2.0.0
-----

* Major change is update CentOS version. Now some roles support only CentOS8 and will **not** work on CentOS7
* yum role has been removed in favor of new dnf role.
* Delta-rpm package is no longer installed since dnf handles delta-rpms on it's own
* yum-cron has been changed to dnf-automatic
* List of additional packages to install is now empty, compared to yum role
* All variables prefix has changed from yum_* to dnf_*
* Git updated to 2.25.2 version
* git role now requires CentOS8
* nginx updated to 1.17.9
* pcre version that is compiled with nginx updated to 8.44
* openssl version that is compiled with nginx updated to 1.1.1e
* nginx role now requires CentOS8
* chrony role now requires CentOS8
* OpenSSL updated to 1.1.1e
* openssl role now requires CentOS8
* PHP updated to 7.4.4
* PHP is now compiled with libzip version shipped with CentOS8 instead of manual compilation
* PHP is compiled with PEAR support
* php role now requires CentOS8
* Adding PHP executables to $PATH and creating systemctl entry is moved from `install.yml` to `shell.yml` file

1.9.1
-----

* Compile PHP with zip extension
* Compile PHP with freetype support

1.9.0
-----

* Rewrite php role
* Update PHP to 7.4.1
* Skip managing php-fpm polls in favor of deployment playbooks/tasks from different role
* Update nginx to 1.17.7
* Add php-fpm integration to nginx
* Add general.conf file with basic definitions for general hosts
* Fix some typos in nginx role

1.8.0
-----

* Update nginx to 1.17.6
* Change how nginx is installed, now it's compiled with latest version of PCRE, Zlib, OpenSSL, Brotli libraries
* Make configuration more easier, fix some defaults and
* Skip managing server {} blocks in favor of deployment playbooks/tasks from different role

1.7.0
-----

* Simplify git role. Now it does not require custom build OpenSSL. `openssl-devel` is used instead
* Update git to 2.24.1
* Fix bug where OpenSSL was not installed properly

1.6.2
-----

* Update OpenSSL to 1.1.1c
* Simplify openssl role

1.6.1
-----

* Simplify ntp role
* Add `time.cloudflare.com` to list of NTP servers

1.6.0
-----

* Create new ssh role for ssh hardening
* Remove ssh related configuration from centos role

1.5.0
-----

* Create new users role for handling the user and groups related tasks
* Remove users/groups related things from centos role
* Fix bug when packages listed in yum role were not installed
* Fix issue when libselinux-python packages required for proper Ansible execution was autoremoved in yum role
* List updated packages in yum role update task

1.4.0
-----

* Create new yum role to handle yum related tasks. It's now easier to manage packages
* Remove yum related things from centos role

1.3.9
-----

* Update git to 2.16.3
* Update Apache httpd to 2.4.33
* Update PHP to 7.2.3
* Add cronjob for updating composer
* Add XDebug PECL extension
* Add jpeg,webp,png support to GD library
* Use native OpenSSL libraries instead of custom one to prevent bug in PEAR installation
* Remove default cache from HTTPD expires module

1.3.8
-----

* Update Apache httpd to 2.4.29
* Fix installation issues with Apache httpd (missing libraries)
* Configure `mod_expires`
* Fix deprecation note about `include` in httpd role
* Add missing `mdadm` package for kernel when using CentOS with RAID in centos role

1.3.7
-----

* Update git to 2.15.1
* Change git installation path to `/usr/local/git`
* Fix OpenSSL issue when compiling git
* Fix deprecation note about `include` in git role
* Add list of links with releases
* Make sure that `openssldir` variable is set to the same version as `prefix` when compiling OpenSSL

1.3.6
-----

* Update OpenSSL to 1.1.0g
* Fix deprecation note about `include` in openssl role

1.3.5
-----

* Fix deprecation note about `include` in ntp role

1.3.4
-----

* Update list of packages to update to match CentOS 7.4
* README file for CentOS role
* Change task order
* Change user list variable from `- {...}` to `-...`
* Fix deprecation note about Ansible `include` statement in CentOS role

1.3.3
-----

* Add multiple integration in `datadog` role
* Update `python-pip` to `python2-pip` in roles using that package
* Update list of non critical packages in `centos` role
* Add `mod_status` support to Apache httpd
* Fix typos
* Add `/status` and `/ping` for PHP-FPM
* Create database user for DataDog in `mysql` and `mongodb` roles

1.3.2
-----

* Add `redis` role

1.3.1
-----

* Add `nginx` role
* Fix getting real IP in Apache when running behind nginx proxy

1.3.0
-----

* Add `openssl` role
* Use latest version of OpenSSL during compilation in following roles: `git`, `httpd`, `php`

1.2.9
-----

* Add logrotate for php error log and slow log in `php` role
* Add option to disable OPcache extension

1.2.8
-----

* Update Git to `2.14.1` version
* Update NodeJs to `8.3.0` version
* Update MongoDB to `3.4.7` version
* Fix warning on MySQL backup script when removing files from empty directory
* Add MongoDB backup script with push to S3

1.2.7
-----

* Update Git to `2.14.0` version
* Update PHP to `7.1.8` version
* Enable and configure OPcache in `php` role
* Enable and configure realpath cache in `php` role

1.2.6
-----

* Update Git to `2.13.4` version
* Fix bug with PHP-FPM (`Primary script unknown`) in `httpd` role
* Update nodejs to `8.2.1` version
* Update MySQL to `5.7.19` version
* Fix broken GPG key in `mysql` role
* Add AWS config and credentials for root user in `awscli` role
* Create backup system with upload to S3 in `mysql` role

1.2.5
-----

* Update Apache httpd to `2.4.27` and APR libraries to `1.6.*` versions
* Configure SSL with HTTP/2 support in `httpd` role
* Add Let's Encrypt integration to `httpd` role
* Add new redirects using `mod_alias` in `httpd` role
* Fix getting real IP address when Apache httpd is running behind proxy like Varnish/Nginx
* Add logrotate support for VirtualHosts in `httpd` role
* Add option to return 403 status when server is called by IP address in `httpd` role

1.2.4
-----

* Fix issue with Perl-GIT in `git` role. With this version you need to login to your server, edit `/etc/yum.conf` file
  and remove `exclude=git*` line. It was added in previous versions, but now it's not longer necessary
* Update git to `2.13.3` version
* Fix name of nodejs repo file in `nodejs` role

1.2.3
-----

* Add logrotate support in `centos` role
* Update packages list in `centos` role
* Fix warning in `ntp` role

1.2.2
-----

* Add `letsencrypt` role
* Fix wrong user in `awscli` role
* Update packages after CentOS 7.3 release
* Update GIT to `2.11.0` version
* Update MySQL to `5.7.17` version

1.2.1
-----

* Add missing `libselinux-python` library to all roles that are using Ansible template module
* Add missing tags in `nodejs` role

1.2.0
-----

* Update Apache HTTPD to `2.4.25`
* Enable GZIP compression in `httpd` role with `mod_deflate`
* Add `setenvif` module to list of modules enabled by default in `httpd` role

1.1.9
-----

* Add `mongodb` role
* Fix issue with task status always change in THP in `centos` role

1.1.8
-----

* Add `php` role
* Fix wrong variable in `httpd` role
* Fix typo in `httpd` role

1.1.7
-----

* Fix issue for not detecting autoremoved and list of updated packages

1.1.6
-----

* Add MySQLTuner tool
* Add option to configure `skip_name_resolve` variable in MySQL

1.1.5
-----

* Add option to setup permanent redirect in `httpd` role
* Add option to turn off logging per VirtualHost in `httpd` role
* Add option to disable creating `htdocs` directory per VirtualHost in `httpd` role

1.1.4
-----

* Add `awscli` role

1.1.3
-----

* Add `mysql` role
* Fix incorrect variable names in `httpd` role

1.1.2
-----

* Add script for disabling transaprent huge pages

1.1.1
-----

* Add `nodejs` role

1.1.0
-----

* Add `datadog` role

1.0.9
-----

* Add `httpd` role
* Fix typos in `git` role

1.0.8
-----

* Add `git` role
* Fix issue with missing `libselinux-python` in `ntp` role
* Fix issue with closed port 22 that prevents git pull from ssh repositories

1.0.7
-----

* Add `iptables` tasks to `centos` role with secure ruleset
* Fix issue with missing `libselinux-python` that prevented copying SSH key to the server

1.0.6
-----

* Show list of packages removed with `yum autoremove`

1.0.5
-----

* Make output of packages remaining for update more pretty

1.0.4
-----

* Disable weak SSH exchange keys and server keys
* Disable unsafe ciphers and MACs
* Turn off PAM-based authentication to fully disable password authentication

1.0.3
-----

* **ntp** role added. It includes system timezone configuration and Chrony NTP server configuration.
* Add `kmod` packages to list of CentOS core packages
* Update REAMDE file with information about SSH and NTP

1.0.2
-----

* Add tasks for securing SSH in CentOS
* Fix typos and wrong tags in users and sudo tasks in CentOS role

1.0.1
-----

* Add tasks for groups management in CentOS
* Add tasks for users management in CentOS
* Add tasks for enabling sudo with or without password
* Add yum-cron on system startup
* Make separate tasks like groups and users to be conditionally included
* Fix typos and code styling

1.0.0
-----

* Initial setup for Ansible
* **centos** role added
* Save list of installed packages
* Configure gpgcheck for yum
* Install delta RPM feature
* Remove unnecessary packages from the system, update core and other packages to latest versions
* Install additional tools like net-tools
* Setup yum-cron
* Monitor for not-updated packages
