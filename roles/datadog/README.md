Datadog role (Deprecated)
============

** THIS ROLE WILL BE REMOVED SOON **
------------------------------------

This role will install and configure Datadog agent

What you should know?
---------------------

You need to configure two variables for that role:
 - `datadog_key` - API access key from Datadog
 - `datadog_hostname` - Name of the host

Integrations
------------

Here is the list of possible integrations:
 - apache
 - directory
 - http_check
 - mongo
 - mysql
 - nginx
 - ntp
 - php_fpm
 - redisdb
 - system_core

Some of the integrations requires additional configuration. Please refer to `defaults/main.yml` to see what need to be configured.
