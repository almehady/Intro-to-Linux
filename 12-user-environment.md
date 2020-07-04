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

