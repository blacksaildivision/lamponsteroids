NTP role
==========

This role is responsible for setting system timezone and configuring chrony. 
Please note that it will remove ntp package in favor of chrony. Using two sync tool can cause troubles. 


Variables
---------
Here is the list of configurable variables for this role:

 - `ntp_timezone` by default it's set to **UTC**. It will set system time using `timedatectl` command.
 
 - `ntp_servers` is a list of servers to use in chrony configuration. By default there are time servers from [ntp.org](https://www.ntppool.org) and [time.cloudflare.com](https://www.cloudflare.com/time/)
 