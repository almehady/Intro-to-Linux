# Chapter 15 : The Bash Shell and Basic Scripting

## Command Shell Choices
The command interpreter is tasked with executing statements that follow it in the script. Commonly used interpreters include: /usr/bin/perl, /bin/bash, /bin/csh, /usr/bin/python and /bin/sh.

Typing a long sequence of commands at a terminal window can be complicated, time consuming, and error prone. By deploying shell scripts, using the command line becomes an efficient and quick way to launch complex sequences of steps. The fact that shell scripts are saved in a file also makes it easy to use them to create new script variations and share standard procedures with several users.

Linux provides a wide choice of shells; exactly what is available on the system is listed in /etc/shells. Typical choices are:

/bin/sh
/bin/bash
/bin/tcsh
/bin/csh
/bin/ksh
/bin/zsh

Most Linux users use the default bash shell, but those with long UNIX backgrounds with other shells may want to override the default.

## Shell Scripts
Remember from our earlier discussion, a shell is a command line interpreter which provides the user interface for terminal windows. It can also be used to run scripts, even in non-interactive sessions without a terminal window, as if the commands were being directly typed in. For example, typing find . -name "*.c" -ls at the command line accomplishes the same thing as executing a script file containing the lines:

#!/bin/bash
`find . -name "*.c" -ls`

The first line of the script, which starts with #!, contains the full path of the command interpreter (in this case /bin/bash) that is to be used on the file. As we have noted, you have quite a few choices for the scripting language you can use, such as `/usr/bin/perl`, `/bin/csh`, `/usr/bin/python`, etc.

### A Simple bash Script
Let's write a simple bash script that displays a one line message on the screen. Either type:
```
$ cat > hello.sh
#!/bin/bash
echo "Hello Linux Foundation Student"
```

and press ENTER and CTRL-D to save the file, or just create hello.sh in your favorite text editor. Then, type chmod +x hello.sh to make the file executable by all users.

You can then run the script by  typing ./hello.sh or by doing:

`$ bash hello.sh`
Hello Linux Foundation Student

Note: If you use the second form, you do not have to make the file executable.

### Interactive Example Using bash Scripts
Now, let's see how to create a more interactive example using a bash script. The user will be prompted to enter a value, which is then displayed on the screen. The value is stored in a temporary variable, name. We can reference the value of a shell variable by using a $ in front of the variable name, such as $name. To create this script, you need to create a file named getname.sh in your favorite editor with the following content: 
```
#!/bin/bash
# Interactive reading of a variable
echo "ENTER YOUR NAME"
read name
# Display variable input
echo The name given was :$name
```

Once again, make it executable by doing chmod +x getname.sh.

In the above example, when the user types./getname.sh and the script is executed, the user is prompted with the string ENTER YOUR NAME. The user then needs to enter a value and press the Enter key. The value will then be printed out.

Note: The hash-tag/pound-sign/number-sign (#) is used to start comments in the script and can be placed anywhere in the line (the rest of the line is considered a comment). However, note the special magic combination of #!, used on the first line, is a unique exception to this rule.