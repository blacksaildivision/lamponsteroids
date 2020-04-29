OpenSSL role
============

This role will compile from source latest version of OpenSSL (1.1.1g) on CentOS 8 server.

Variables
---------
Here is the list of configurable variables for this role:

 - `openssl_version` version of OpenSSL to install.
 
 - `openssl_install_path` path where OpenSSL will be installed. By default it's `/usr/local/openssl`

 - `openssl_sources_location` path where OpenSSL sources will be downloaded and unpacked. Make sure that `openssl_build_user` has access to this directory. By default it's `/usr/src`
 
 - `openssl_build_user` user that will build the OpenSSL. It's not compiled as root. By default it's `developer`. If you don't have such user or you wish to provide your own, make sure the user exists.
 
 - `openssl_build_group` group of the user for the build process. By default it's `developer`.
