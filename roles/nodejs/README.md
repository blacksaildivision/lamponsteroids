Node.js role
============

This role will install [Node.js](https://nodejs.org/en/) and configured global packages.

Variables
---------
Here is the list of configurable variables for this role:

- `nodejs_version` version of Node.JS to install.

- `nodejs_global_packages` list of packages that should be installed globally using NPM. By default, the list is empty.
