MongoDB role
==========

This role will install latest version of MongoDB (3.4.0). It will also configure MongoDB and setup users.

What you should know?
---------------------

**Admin password**
Make sure that you will change default admin password - `mongodb_admin_password`. 
`admin` account has highest permissions.

**Databases and users**
This role can also setup databases. Each database will have separate users. Make sure that you configure following variables and change default password:
```
mongodb_databases:
 - {
    user: example,
    password: O14inEDG948dEEg2zcREZB,
    database: example,
    roles: "readWrite,dbAdmin"
 }
```
