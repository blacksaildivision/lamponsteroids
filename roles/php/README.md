PHP role
==========

This role will install PHP with FPM mode server on CentOS.
PHP will be installed in latest version (7.2.3) and will be compiled from source.

What you should know?
---------------------

**Installation**
For installing purpose you need to configure two variables
 - `php_build_user`
 - `php_build_group`
 
You should set them to an existing user and group it cannot be root. Compiling software from root account can have serious security impacts.
By default it's set to `developer`. If you are using whole LampOnSteroids project, such user will be created in `centos` role.
If you only use `php` role, make sure that you set these variables correctly.

**FPM**
You need to override `php_fpm_pools` variable. There is only an example pool, but probably it won't suit your needs. 
Good practice is to have one pool per application. Remember that names must be different. 

Also remember to set `user` and `group` to existing values. Like above, if you are using whole project, `developer:www` will exist.
User should be the same use that owns your application files. 

Here is full example with all available options:
```
php_fpm_pools:
 - {
  name: example.com,
  user: developer,
  group: www,
  port: 9000,
  status: yes,
  process_manager: {
    pm: dynamic,
    max_children: 5,
    start_servers: 2,
    min_spare_servers: 1,
    max_spare_servers: 3
  },
  slow_log: "/var/www/example.com/log/php-fpm.slow.log",
  slow_log_timeout: 30s,
  php_admin_flags: [
    { key: log_errors, value: "On" }
  ],
  php_admin_values: [
      { key: error_log, value: /var/www/example.com/log/php-fpm.error.log },
      { key: open_basedir, value: "/var/www/example.com/htdocs:/tmp" },
      { key: disable_functions, value: "exec,passthru,shell_exec,system" }
    ]
 }
```
