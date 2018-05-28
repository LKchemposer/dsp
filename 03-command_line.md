# Learn command line

Please follow and complete the free online [Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) or [Codecademy's Learn the Command Line](https://www.codecademy.com/learn/learn-the-command-line). These are helpful tutorials. You should be able to go through these in a couple of hours.

**Note:** Bash is not installed on a PC. Rather, PC users must install Cygwin. Once Cygwin has been installed, the command line interface witll _emulate_ bash. You can find all information regarding Cygwin [here](https://www.cygwin.com/).

---

### Q1.  Cheat Sheet of Commands  

Here's a list of items with which you should be familiar:  
* show current working directory path
* creating a directory
* deleting a directory
* creating a file using `touch` command
* deleting a file
* renaming a file
* listing hidden files
* copying a file from one directory to another

Make a cheat sheet for yourself: a list of at least **ten** commands and what they do.  (Use the 8 items above and add a couple of your own.)

`pwd`: print current directory
`mkdir`: make directory
`rm -r`: remove directory
`touch`: create empty file
`rm`: remove file
`mv`: move/rename file
`ls -a`: list all (including hidden) files
`cp copy_file copy_directory`: copy copy_file to copy_directory
`>`: redirect output of command, overwrite file
`>>`: same as `>`, but append file instead
`<`: redirect input of command
`|`: redirect output of command into another command
`sort`: sort lines of text alphabetically
`uniq`: filter duplicates, alphabetize lines
`grep (-i) (-R(l))`: find text pattern, return lines (case sensitive) (search directory, (return only filename, not lines))
`sep 's/text_find/text_replace(/g)'`: find and replace first instance (globally) text_find and replace with text_replace
`nano`: open text editor
`source`: read text editor file

---

### Q2.  List Files in Unix   

What do the following commands do:  
`ls`  
`ls -a`  
`ls -l`  
`ls -lh`  
`ls -lah`  
`ls -t`  
`ls -Glp`  

`ls`: list files
`ls -a`: list all files
`ls -l`: `ls` in long format
`ls -lh`: `ls -l` with readable file size
`ls -lah`: same as `ls -a` and `ls -lh`
`ls -t`: `ls` with sorted time
`ls -Glp`: `ls -l` with directories in color and with `/`

---

### Q3.  More List Files in Unix  

Explore these other [ls options](http://www.techonthenet.com/unix/basic/ls.php) and pick 5 of your favorites:

`ls -l`
`ls -G`
`ls -t`
`ls -d`
`ls -a`

---

### Q4.  Xargs   

What does `xargs` do? Give an example of how to use it.

`xargs` builds a command pipeline from a standard input as arguments. `xargs` can be used with `find` to replace/remove/etc. files and directories. For example, `find -name "ex" | xargs rm` finds the text ex in the files in current directory and remove them.
 

