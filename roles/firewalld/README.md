firewalld role
========

This role will install and configure firewalld services

Variables
---------
Here is the list of configurable variables for this role:

 - `firewalld_default_zone` zone that should be set for all interfaces. By default it's `dmz` - ssh access only.  

 - `firewalld_incoming_traffic_services` list of services that should be allowed on incoming traffic. Default is HTTP, HTTPS and SSH access.
