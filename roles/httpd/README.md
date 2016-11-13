HTTPD role
==========

This role will install Apache httpd https://httpd.apache.org/ server on CentOS.
Apache httpd will be installed in latest version (2.4.23) and will be compiled from source.

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
 
Apache httpd will be configured with minimal number of modules. Please review and update `httpd_active_modules` variable if you need anything more enabled.

**VirtualHosts**
You need to define list of VirtualHosts that should be present in the system
Full example with all available options:

```
httpd_virtualhosts:
 - {
    server_name: example.com
    server_alias: dev.example.com
    directory_owner: developer
    directory_group: "{{ httpd_group }}"
    subdirectory: wp
    extra_config: [
        'Alias /wp-content /var/www/example.com/htdocs/content',
        '<Directory "/var/www/example.com/htdocs/content">',
            'Require all granted',
        '</Directory>',
      ],
    php:{
        port: 9000
    } 
 }
```