# Manipulating Text

## Learning Objectives

            * Display and append to file contents using cat and echo. 
            * Edit and print file contents using sed and awk.
            * Search for patterns using grep.
            * Use multiple other utilities for file and text manipulation.

### cat
cat is short for concatenate and is one of the most frequently used Linux command line utilities. It is often used to read and print files, as well as for simply viewing file contents. To view a file, use the following command: 

$ cat <filename>

For example, cat readme.txt will display the contents of readme.txt on the terminal. However, the main purpose of cat is often to combine (concatenate) multiple files together. You can perform the actions listed in the table using cat.

The tac command (cat spelled backwards) prints the lines of a file in reverse order. Each line remains the same, but the order of lines is inverted. The syntax of tac is exactly the same as for cat, as in:

$ tac file
$ tac file1 file2 > newfile

 
**Command** 	            **Usage**
cat file1 file2 	        Concatenate multiple files and display the output; i.e. the entire content of the first 
                            file is followed by that of the second file
cat file1 file2 > newfile 	Combine multiple files and save the output into a new file
cat file >> existingfile 	Append a file to the end of an existing file
cat > file 	                Any subsequent lines typed will go into the file, until CTRL-D is typed
cat >> file 	            Any subsequent lines are appended to the file, until CTRL-D is typed

### Using cat Interactively
cat can be used to read from standard input (such as the terminal window) if no files are specified. You can use the > operator to create and add lines into a new file, and the >> operator to append lines (or files) to an existing file. We mentioned this when talking about how to create files without an editor.

To create a new file, at the command prompt type cat > <filename> and press the Enter key.

This command creates a new file and waits for the user to edit/enter the text. After you finish typing the required text, press CTRL-D at the beginning of the next line to save and exit the editing.

Another way to create a file at the terminal is cat > <filename> << EOF. A new file is created and you can type the required input. To exit, enter EOF at the beginning of a line.

Note that EOF is case sensitive. One can also use another word, such as STOP.
