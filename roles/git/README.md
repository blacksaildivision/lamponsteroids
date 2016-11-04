GIT role
========

This role will install git https://git-scm.com/ on CentOS server.
Git will be installed in latest version (2.10.2) and will be compiled from source.

What you should know?
----------------------

There are two things. First are two variables:
 - `git_build_user`
 - `git_build_group`
 
You should set the to an existing user and group it cannot be root. Compiling software from root account can have serious security impacts.
By default it's set to `developer`. If you are using whole LampOnSteroids project, such user will be created in `centos` role.
If you only use git role, make sure that you set these variables correctly.

Second thing is `git_disable_in_yum` variable. By default it's set to true. When this flag is set to true, git will be excluded from yum.
It means that you won't be able to execute commands such as `yum install git` or `yum update git`.
In most cases it's OK. If this flag would be set to false, `yum update git` will install latest version of git from CentOS repository (1.8.3.1 or higher) and it will replace compiled version.
However there is a case when you will want to set it to false. If you try to install package that requires particular version of git from CentOS repository, you won't be able to install it. First you would have to disable this feature, update your package and than, probably recompile git.
