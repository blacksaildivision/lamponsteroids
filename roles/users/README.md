Users role
==========

This role is responsible for user and group management. It can create and remove groups, create and remove users. 
It also enables sudo for given users.

Variables
---------
Here is the list of configurable variables for this role:

 - `users_groups_to_remove` list of groups that should be removed from the system. By default it's empty. If you wish to remove a group, simply list the group names to remove.
 
 - `users_groups_to_create` list of groups that should be present in the system. By default there are two groups. `wheel` is for enabling sudo for given users, `www` is general role for all webserver related things.
 
 - `users_to_remove` list of users that should be removed from the system. By default it's empty. If you wish to remove some users, simply list their usernames here. 

 - `users_to_create` list of users that should be present in the system. By default it `developer` user is created. It is strongly recommended **NOT** to use default here. Instead create your own user.



How to create your own user?
----------------------------
It is important to create your own user here. Or at least change the password to the default user. You should create your own file with variables or even better, Ansible Vault. 
You can see the example of how to configure the user in `default.yml` file of this role. Each user can have some properties:
 - `name` is the username. By default it is `developer`
 - `password` password for given user. Please refer to this article in order to create user password: [How do I generate encrypted passwords for the user module?](https://docs.ansible.com/ansible/latest/reference_appendices/faq.html#how-do-i-generate-encrypted-passwords-for-the-user-module)
 - `groups` is a list of groups that given user should belong. If you wish to enable sudo for given user, make sure that `wheel` group is on the list.
 - `generate_ssh_key` if set to `yes` it will generate id_rsa key in user `~/.ssh` directory. 
 - `authorized_keys` is a list of authorized keys that should be added to given user. By default it adds your id_rsa key so you will be able to SSH to the machine using this key.
