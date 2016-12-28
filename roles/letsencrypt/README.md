Let's Encrypt role
==================

This role will install latest version of Certbot for Let's Encrypt certificates. It will also create certificates for given domains.

What you should know?
---------------------

**Domains**
Make sure that you will change default list of domains for Let's Encrypt certificates - `letsencrypt_domains`. 

Each entry has 3 fields:
```
letsencrypt_domains:
 - {
  webroot_path: /var/www/example.com,
  domains: example.com,
  email_address: admin@example.com
 }
```

 - `webroot_path` here Certbot will create .well-known entry and will test domain status against it. Make sure that this is valid path
 - `domains` domain for creating certificate for
 - `email_address` for this email address you will receive notification about certificates expiration
