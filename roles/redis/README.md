Redis role
==========

This role will compile and install [Redis](https://redis.io/). 
Redis will be compiled with TLS support. 

Variables
---------
Here is the list of configurable variables for this role:

 - `redis_version` version of Redis that should be installed.
 - `redis_install_path` path where Redis will be installed.
 - `redis_sources_path` path where Redis source code will be downloaded. 
 - `redis_build_user` user that will build Redis. It's not compiled as root. Default is `developer`. If you don't have such user, or you wish to provide your own, make sure the user exists.
 - `redis_build_group` group of build user. Defaults to `developer`.
 - `redis_database_dir` directory where Redis database files should be stored.
 - `redis_logs_dir` directory where Redis should store logs.
 - `redis_bind` IP address that should be used for bind in Redis.
 - `redis_default_configuration` default, secure configuration for Redis. If you want to override the settings please use `redis_user_configuration` variable. 
 - `redis_user_configuration` configuration that will extend/override config stored in `redis_default_configuration`.
 - `redis_net_core_somaxconn` value for net.core.somaxconn.
 - `redis_overcommit_memory` value for vm.overcommit_memory.
 - `redis_disable_transparent_huge_pages` whether this role should disable Transparent Huge Pages. Defaults to `yes`.

Examples
--------

Following code will change the port under which Redis is running and will turn on active defragmentation. Store it in your onw VAR files.
```yaml
redis_user_configuration:
 port: "1379"
 activedefrag: "no"
```
