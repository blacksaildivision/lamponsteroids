nginx role
==========

This role will install Nginx http://nginx.org/ server on CentOS.
Nginx will be installed in latest version (1.13.4) and will be compiled from source.

What you should know?
---------------------

**Installation**
For installing purpose you need to configure two variables
 - `nginx_build_user`
 - `nginx_build_group`
 
You should set them to an existing user and group it cannot be root. Compiling software from root account can have serious security impacts.
By default it's set to `developer`. If you are using whole LampOnSteroids project, such user will be created in `centos` role.
If you only use `nginx` role, make sure that you set these variables correctly.

**Configuration**
There is new user created for Apache httpd daemon. If you want to change that, modify following variables:
 - `nginx_user`
 - `nginx_group`
 
nginx will be configured with minimal number of modules required for basic functioning + SSL. Please review and update `nginx_configure_options` variable if you need anything more enabled.

**Servers**
You need to define list of servers that should be present in the system
Full example with all available options:

```
httpd_virtualhosts:
 - {
    server_name: example.com,
    server_aliases: [dev.example.com],
    directory_owner: developer,
    directory_group: "{{ nginx_group }}",
    upstream: ['127.0.0.1:81'],
    server_ip: '23.42.53.64',
    https: yes,
    http2: yes,
    cert_file_path: /etc/letsencrypt/live/example.com/cert.pem,
    cert_key_file_path: /etc/letsencrypt/live/example.com/privkey.pem,
    subdirectory: wp,
    logs: yes,
    htdocs: yes,
    custom_log_if: "$example_com_log",
    rewrites:
      - {
         regex: '^/wp-content/(.*)$',
         replacement: '/content/$1'
    },
    override_location: no,
    proxy_pass: yes,
    proxy_pass_for_php: yes,
    php_status: yes,
    php_status_allowed_ips: ['23.42.53.64'],
    logrotate: yes,
    letsencrypt_integration: yes,
    stub_status: yes
 }
```

**Redirects**

In order to setup redirects you need to adjust `nginx_redirects` variable. Here is an example of redirect:

```
nginx_redirects: 
 - {
   server_name: example.com,
   server_aliases: [www.example.com],
   redirect: 'https://example.com',
 }
```

HTTPS option is also supported here

OpenSSL
-------

This role requires `openssl` role installed. It will install latest version of OpenSSL and Apache HTTPD will be compiled with `--with-openssl` parameter pointing to location where latest version is compiled (/usr/local/openssl)
