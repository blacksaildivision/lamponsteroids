PHP role
========

This role will compile and install [PHP](https://www.php.net/). 
This role does not directly manage FPM pools. You should set it up using your own custom role or just place a `.conf` file inside `etc/php-fpm.d` directory. 

Variables
---------
Here is the list of configurable variables for this role:

 - `php_version` version of PHP to install.

 - `php_install_path` path where PHP will be installed. By default it's `/usr/local/php`.

 - `php_sources_path` path where PHP source code will be downloaded and unpacked. Make sure that `php_build_user` has access to this directory. By default it's `/usr/src`.
 
 - `php_build_user` user that will build the PHP. It's not compiled as root. By default it's `developer`. If you don't have such user or you wish to provide your own, make sure the user exists.
 
 - `php_build_group` group of the user for the build process. By default it's `developer`.
 
 - `php_configure_options` list of arguments for `./configure` command.
 
 - `php_ini_config_option_php_section` list of options that should be set in main section of php.ini [PHP].

- `php_ini_config_option_opcache_section` list of options that should be set in opcache section of php.ini [opcache]. It
  extends the `_php_ini_config_option_opcache_section_defaults` variable.
 
 - `php_date_timezone` timezone for PHP. By default it's `UTC`.
 
 - `php_mysql_socket` path to MySQL socket file. By default it's `/var/lib/mysql/mysql.sock`.
 
 - `php_extensions` list of extensions that should be installed with PECL and enabled in php.ini file.
 
 - `php_zend_extensions` list of Zend extensions that should be installed with PECL and enabled in php.ini file.
