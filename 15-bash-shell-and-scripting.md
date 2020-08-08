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

## Syntax
### Basic Syntax and Special Characters
Scripts require you to follow a standard language syntax. Rules delineate how to define variables and how to construct and format allowed statements, etc. The table lists some special character usages within bash scripts:

 
**Character** 	**Description**
# 	        Used to add a comment, except when used as \#, or as #! when starting a script
\ 	        Used at the end of a line to indicate continuation on to the next line
; 	        Used to interpret what follows as a new command to be executed next
$ 	        Indicates what follows is an environment variable
> 	        Redirect output
>> 	        Append output
< 	        Redirect input
| 	        Used to pipe the result into the next command

 

There are other special characters and character combinations and constructs that scripts understand, such as (..), {..}, [..], &&, ||, ', ", $((...)), some of which we will discuss later.

### Splitting Long Commands Over Multiple Lines
Sometimes, commands are too long to either easily type on one line, or to grasp and understand (even though there is no real practical limit to the length of a command line).  

In this case, the concatenation operator (\), the backslash character, is used to continue long commands over several lines.

Here is an example of a command installing a long list of packages on a system using Debian package management:

`$~/> cd $HOME`
$~/> sudo apt-get install autoconf automake bison build-essential
    chrpath curl diffstat emacs flex gcc-multilib g++-multilib \ 
    libsdl1.2-dev libtool lzop make mc patch \
    screen socat sudo tar texinfo tofrodos u-boot-tools unzip \
    vim wget xterm zip

### Putting Multiple Commands on a Single Line
There are several different ways to do this, depending on what you want to do. The ; (semicolon) character is used to separate these commands and execute them sequentially, as if they had been typed on separate lines. Each ensuing command is executed whether or not the preceding one succeeded.

Thus, the three commands in the following example will all execute, even if the ones preceding them fail:

`$ make ; make install ; make clean`

However, you may want to abort subsequent commands when an earlier one fails. You can do this using the && (and) operator as in:

`$ make && make install && make clean`

If the first command fails, the second one will never be executed. A final refinement is to use the || (or) operator, as in:

`$ cat file1 || cat file2 || cat file3`

### Output Redirection
The > character is used to write output to a file. For example, the following command sends the output of free to /tmp/free.out:

`$ free > /tmp/free.out`

To check the contents of /tmp/free.out, at the command prompt type `cat /tmp/free.out.`

Two > characters (>>) will append output to a file if it exists, and act just like > if the file does not already exist.

### Input Redirection
Just as the output can be redirected to a file, the input of a command can be read from a file. The process of reading input from a file is called input redirection and uses the < character.

The following three commands (using wc to count the number of lines, words and characters in a file) are entirely equivalent and involve input redirection, and a command operating on the contents of a file:

`$ wc < /etc/passwd`
49  105 2678 /etc/passwd

`$ wc /etc/passwd`
49  105 2678 /etcpasswd

`$ cat /etc/passwd | wc`
49  105 2678

### Built-In Shell Commands
Shell scripts execute sequences of commands and other types of statements. These commands can be: 

            * Compiled applications
            * Built-in bash commands
            * Shell scripts or scripts from other interpreted languages, such as perl and Python.

Compiled applications are binary executable files, generally residing on the filesystem in well-known directories such as /usr/bin. Shell scripts always have access to applications such as rm, ls, df, vi, and gzip, which are programs compiled from lower level programming languages such as C.

In addition, bash has many built-in commands, which can only be used to display the output within a terminal shell or shell script. Sometimes, these commands have the same name as executable programs on the system, such as echo which can lead to subtle problems. bash built-in commands include and cd,  pwd, echo, read, logout, printf, let, and ulimit. Thus, slightly different behavior can be expected from the built-in version of a command such as echo as compared to /bin/echo.

### Functions
A function is a code block that implements a set of operations. Functions are useful for executing procedures multiple times, perhaps with varying input variables. Functions are also often called subroutines. Using functions in scripts requires two steps:

            Declaring a function
            Calling a function

The function declaration requires a name which is used to invoke it. The proper syntax is:

function_name () {
   command...
}

For example, the following function is named display:

display () {
   echo "This is a sample function"
}

##  Constructs 
### The if Statement
if TEST-COMMANDS; then CONSEQUENT-COMMANDS; fi

A more general definition is:

if condition
then
       statements
else
       statements
fi
### The elif Statement
You can use the elif statement to perform more complicated tests, and take action appropriate actions. The basic syntax is:

if [ sometest ] ; then
    echo Passed test1 
elif [ somothertest ] ; then
    echo Passed test2 
fi
### Boolean Expressions
**Operator** 	**Operation** 	**Meaning**
&& 	            AND 	        The action will be performed only if both the conditions evaluate to true.
|| 	            OR 	            The action will be performed if any one of the conditions evaluate to true.
! 	            NOT 	        The action will be performed only if the condition evaluates to false. 

### Numerical Tests
You can use specially defined operators with the if statement to compare numbers. The various operators that are available are listed in the table:

 
**Operator** 	**Meaning**
-eq 	        Equal to
-ne 	        Not equal to
-gt 	        Greater than
-lt 	        Less than
-ge 	        Greater than or equal to
-le 	        Less than or equal to

### Arithmetic Expressions
Arithmetic expressions can be evaluated in the following three ways (spaces are important!):

            Using the expr utility
            expr is a standard but somewhat deprecated program. The syntax is as follows:

            `expr 8 + 8`
            `echo $(expr 8 + 8)`
            Using the $((...)) syntax 
            This is the built-in shell format. The syntax is as follows:

            `echo $((x+1))`
            Using the built-in shell command let. The syntax is as follows:

            `let x=( 1 + 2 ); echo $x`

In modern shell scripts, the use of expr is better replaced with var=$((...)).