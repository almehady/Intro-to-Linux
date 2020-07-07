# Chapter 12: User Environment

## Learning Objectives

By the end of this chapter, you should be able to:

            * Use and configure user accounts and user groups.
            * Use and set environment variables.
            * Use the previous shell command history.
            * Use keyboard shortcuts.
            * Use and define aliases.
            * Use and set file permissions and ownership.

### Identifying the Current User
As you know, Linux is a multi-user operating system, meaning more than one user can log on at the same time.

            * To identify the current user, type whoami.
            * To list the currently logged-on users, type who.

Giving who the -a option will give more detailed information.

### User Startup Files


In Linux, the command shell program (generally bash) uses one or more startup files to configure the user environment. Files in the /etc directory define global settings for all users, while initialization files in the user's home directory can include and/or override the global settings.

The startup files can do anything the user would like to do in every command shell, such as:

            * Customizing the prompt
            * Defining command line shortcuts and aliases
            * Setting the default text editor
            * Setting the path for where to find executable programs

### Creating Aliases
You can create customized commands or modify the behavior of already existing ones by creating aliases. Most often, these aliases are placed in your ~/.bashrc file so they are available to any command shells you create. unalias removes an alias.

Typing alias with no arguments will list currently defined aliases.

Please note there should not be any spaces on either side of the equal sign and the alias definition needs to be placed within either single or double quotes if it contains any spaces.


### Adding and Removing Users
Adding a new user is done with useradd and removing an existing user is done with userdel. In the simplest form, an account for the new user bjmoose would be done with:

`$ sudo useradd bjmoose`

Note that for openSUSE, useradd is not in the normal user's PATH, so the command should be:

`$ sudo /usr/sbin/useradd bjmoose`

which, by default, sets the home directory to /home/bjmoose, populates it with some basic files (copied from /etc/skel) and adds a line to /etc/passwd such as:

`bjmoose:x:1002:1002::/home/bjmoose:/bin/bash`

and sets the default shell to /bin/bash. Removing a user account is as easy as typing userdel bjmoose. However, this will leave the /home/bjmoose directory intact. This might be useful if it is a temporary inactivation. To remove the home directory while removing the account one needs to use the -r option to userdel.

Typing id with no argument gives information about the current user, as in:

`$ id`
uid=1002(bjmoose) gid=1002(bjmoose) groups=106(fuse),1002(bjmoose)

### Adding and Removing Groups
Adding a new group is done with groupadd:

$ sudo /usr/sbin/groupadd anewgroup

The group can be removed with:

`$ sudo /usr/sbin/groupdel anewgroup`

Adding a user to an already existing group is done with usermod. For example, you would first look at what groups the user already belongs to:

`$ groups rjsquirrel`
bjmoose : rjsquirrel

and then add the new group:

`$ sudo /usr/sbin/usermod -a -G anewgroup rjsquirrel`

`$ groups rjsquirrel`
rjsquirrel: rjsquirrel anewgroup

These utilities update /etc/group as necessary. Make sure to use the -a option, for append, so as to avoid removing already existing groups. groupmod can be used to change group properties, such as the Group ID (gid) with the -g option or its name with then -n option.

Removing a user from the group is somewhat trickier. The -G option to usermod must give a complete list of groups. Thus, if you do:

`$ sudo /usr/sbin/usermod -G rjsquirrel rjsquirrel`

`$ groups rjsquirrel`
rjsquirrel : rjsquirrel

only the rjsquirrel group will be left.

### The root Account


The root account is very powerful and has full access to the system. Other operating systems often call this the administrator account; in Linux, it is often called the superuser account. You must be extremely cautious before granting full root access to a user; it is rarely, if ever, justified. External attacks often consist of tricks used to elevate to the root account.

However, you can use sudo to assign more limited privileges to user accounts:

           * Only on a temporary basis
           * Only for a specific subset of commands.


### su and sudo
When assigning elevated privileges, you can use the command su (switch or substitute user) to launch a new shell running as another user (you must type the password of the user you are becoming). Most often, this other user is root, and the new shell allows the use of elevated privileges until it is exited. It is almost always a bad (dangerous for both security and stability) practice to use su to become root. Resulting errors can include deletion of vital files from the system and security breaches.

Granting privileges using sudo is less dangerous and is preferred. By default, sudo must be enabled on a per-user basis. However, some distributions (such as Ubuntu) enable it by default for at least one main user, or give this as an installation option.

### Elevating to root Account
To temporarily become the superuser for a series of commands, you can type su and then be prompted for the root password.

To execute just one command with root privilege type sudo <command>. When the command is complete, you will return to being a normal unprivileged user.

sudo configuration files are stored in the /etc/sudoers file and in the /etc/sudoers.d/ directory. By default, the sudoers.d directory is empty.