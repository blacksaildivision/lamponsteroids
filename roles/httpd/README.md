HTTPD role (Deprecated)
==========

** THIS ROLE WILL BE REMOVED SOON **
------------------------------------

This role will install Apache httpd https://httpd.apache.org/ server on CentOS.
Apache httpd will be installed in 2.4.33 version and will be compiled from source.

What you should know?
---------------------

**Installation**
For installing purpose you need to configure two variables
 - `httpd_build_user`
 - `httpd_build_group`
 
You should set them to an existing user and group it cannot be root. Compiling software from root account can have serious security impacts.
By default it's set to `developer`. If you are using whole LampOnSteroids project, such user will be created in `centos` role.
If you only use `httpd` role, make sure that you set these variables correctly.

**Configuration**
There is new user created for Apache httpd daemon. If you want to change that, modify following variables:
 - `httpd_user`
 - `httpd_group`
 
Apache httpd will be configured with minimal number of modules required for basic functioning + SSL + decoding IP when running with reverse proxy. Please review and update `httpd_active_modules` variable if you need anything more enabled.
By default `httpd_real_ip_recording` is set to `no`. Change it to yes only if it's running behind varnish/nginx/etc.

**VirtualHosts**
You need to define list of VirtualHosts that should be present in the system
Full example with all available options:

```
httpd_virtualhosts:
 - {
    server_name: example.com,
    server_aliases: [dev.example.com],
    directory_owner: developer,
    directory_group: "{{ httpd_group }}",
    subdirectory: wp,
    extra_config: [
        'Alias /wp-content /var/www/example.com/htdocs/content',
        '<Directory "/var/www/example.com/htdocs/content">',
            'Require all granted',
        '</Directory>',
      ],
    php:{
        port: 9000,
        status: yes
    },
    redirect: "https://example2.com",
    redirect_www_to_non_www: yes,
    logs: yes,
    htdocs: yes,
    https: yes,
    cert_file_path: /etc/letsencrypt/live/example.com/cert.pem,
    cert_key_file_path: /etc/letsencrypt/live/example.com/privkey.pem,
    cert_chain_file: /etc/letsencrypt/live/example.com/chain.pem,
    logrotate: yes

 }
```

Alternative host with redirect to different domain. HTTPS option is also supported here. Remember to add "/" at the end of redirect option
```
httpd_virtualhosts:
 - {
    server_name: example.com,
    directory_owner: developer,
    directory_group: "{{ httpd_group }}",
    redirect: "https://google.com/",
    htdocs: no,
    logs: no
 }
```

OpenSSL
-------

This role requires `openssl` role installed. It will install latest version of OpenSSL and Apache HTTPD will be compiled with `--with-ssl` parameter pointing to location where latest version is compiled (/usr/local/openssl)
