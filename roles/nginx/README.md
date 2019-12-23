nginx role
==========

This role will compile and install [nginx](https://nginx.org/). 
Nginx is compiled with latest version of OpenSSL, Brotli, Zlib and PCRE. 
This role does not directly manage the server {} blocks. You should set it up using your own custom role or just place a `.conf` file inside `sites-enabled` directory. 

Variables
---------
Here is the list of configurable variables for this role:

 - `nginx_version` version of nginx to install.

 - `nginx_install_path` path where nginx will be installed. By default it's `/usr/local/nginx`.

 - `nginx_sources_path` path where nginx source code will be downloaded and unpacked. Make sure that `nginx_build_user` has access to this directory. By default it's `/usr/src`.
 
 - `nginx_build_user` user that will build the nginx. It's not compiled as root. By default it's `developer`. If you don't have such user or you wish to provide your own, make sure the user exists.
 
 - `nginx_build_group` group of the user for the build process. By default it's `developer`.

 - `nginx_pcre_version` version of PCRE to download and compile with nginx. It will not override PCRE binaries on CentOS.
 
 - `nginx_openssl_version` version of OpenSSL to download and compile with nginx. It will not override OpenSSL binaries on CentOS.
 
 - `nginx_zlib_version` version of Zlib to download and compile with nginx. It will not override Zlib binaries on CentOS.
 
 - `nginx_configure_options` list of arguments for `./configure` command.
 
 - `nginx_conf_path` path to `nginx.conf` file. By default it is `/usr/local/nginx/conf/nginx.conf`.
 
 - `nginx_pid_file_path` path to nginx PID file. By default it is `/usr/local/nginx/logs/nginx.pid`.
 
 - `nginx_user` user that should run nginx process. By default it is `nginx`.
 
 - `nginx_group` group of the user that should run nginx process. By default it is `www`.
 
 - `nginx_df_file_path` Diffie-Hellman group file location. By default it is `/etc/ssl/certs/dhparam.pem`.
