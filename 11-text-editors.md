# Chapter 11 Text Editors

## Learning Objectives


By the end of this chapter, you should be familiar with:

            - How to create and edit files using the available Linux text editors.
            - nano, a simple text-based editor.
            - gedit, a simple graphical editor.
            - vi and emacs, two advanced editors with both text-based and graphical interfaces.

## Overview of Text Editors in Linux

At some point, you will need to manually edit text files. You might be composing an email off-line, writing a script to be used for bash or other command interpreters, altering a system or application configuration file, or developing source code for a programming language such as C, Python or Java.

Linux administrators may sidestep using a text editor, instead employing graphical utilities for creating and modifying system configuration files. However, this can be more laborious than directly using a text editor, and be more limited in capability. Note that word processing applications (including those that are part of common office application suites) are not really basic text editors; they add a lot of extra (usually invisible) formatting information that will probably render system administration configuration files unusable for their intended purpose. So, knowing how to confidently use one or more text editors is really an essential skill to have for Linux.

By now, you have certainly realized Linux is packed with choices; when it comes to text editors, there are many choices, ranging from quite simple to very complex, including:

            - nano
            - gedit
            - vi
            - emacs.

In this section, we learn first about the nano and gedit editors, which are relatively simple and easy to learn, and then later the more complicated choices, vi and emacs. Before we start, let us take a look at some cases where an editor is not needed.

## Creating Files Without Using an Editor
Sometimes, you may want to create a short file and don't want to bother invoking a full text editor. In addition, doing so can be quite useful when used from within scripts, even when creating longer files. You will no doubt find yourself using this method when you start on the later chapters that cover shell scripting!

If you want to create a file without using an editor, there are two standard ways to create one from the command line and fill it with content.

The first is to use echo repeatedly:

`$ echo line one > myfile`
`$ echo line two >> myfile`
`$ echo line three >> myfile`

Note that while a single greater-than sign (>) will send the output of a command to a file, two of them (>>) will append the new output to an existing file.

The second way is to use cat combined with redirection:

`$ cat << EOF > myfile`
> line one
> line two
> line three
> EOF
$

Both techniques produce a file with the following lines in it:

`line one`
`line two`
`line three`

and are extremely useful when employed by scripts.

## nano and gedit


There are some text editors that are pretty obvious; they require no particular experience to learn and are actually quite capable, even robust. A particularly easy to use one is the text terminal-based editor nano. Just invoke nano by giving a file name as an argument. All the help you need is displayed at the bottom of the screen, and you should be able to proceed without any problem.

As a graphical editor, gedit is part of the GNOME desktop system (kwrite is associated with KDE). The gedit and kwrite editors are very easy to use and are extremely capable. They are also very configurable. They look a lot like Notepad in Windows. Other variants such as kate are also supported by KDE.

### nano
nano is easy to use, and requires very little effort to learn. To open a file, type nano <filename> and press Enter. If the file does not exist, it will be created.

nano provides a two line shortcut bar at the bottom of the screen that lists the available commands. Some of these commands are:
            CTRL-G - Display the help screen.
            CTRL-O - Write to a file.
            CTRL-X - Exit a file.
            CTRL-R - Insert contents from another file to the current buffer.
            CTRL-C - Cancels previous commands.
            
