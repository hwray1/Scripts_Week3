# Bash Commands and Scripts

## Commands related to navigating the filesystem

- `touch filename.txt` will create file
- `pwd` - print working directory - or - "where am I?"
- `ls` - list directory contents
- `ls -l` - long list
    - Everything has three types of permissions
        - Read
        - Write
        - Execute: most files you do not want to execute, but do want to execute the script
    - And three groups whose permissions can be controlled
        - Owner
        - Group
        - Others
- [Wikipedia on Unix Permissions](https://en.wikipedia.org/wiki/File_system_permissions#Notation_of_traditional_Unix_permissions)
- la - list with hidden files: ls -a will do this, shows all files, including hidden
- `cd` - change directory
    - will accept absolute or relative paths
- `chmod` - change permissions - specify who (ugo), how (+ or -), and what (rwx)
- `man <command>` - gives us the manual page and options for any Unix command (q will get out of manual page)
- [Notes about command-line navigation](https://github.com/IntroToCompBioLSU-Spr20/Shell_Week2/blob/master/CommandLine_Navigating.md)

## Commands related to files and folders

- `cp` - copies a file
    - `cp originalFile.txt newFile.txt`
- `mv` - moves __or__ renames a file
    - To change location, use paths: `mv myFile.txt ./folder/myFile.txt`
    - To change name, just use different names: `mv myFile.txt newName.txt`
- `cat filename.txt` - view file contents - can be called on multiple files and will conCATenate their contents
    - `cat file1.txt file2.txt file3.txt` will show all files in command line
    - `cat *.txt` shows all text in files with the file ending .txt
- `ls *.txt` show all files that end in .txt
    - `ls ../*.txt` go up one directory then tell me the txt files there (still within the same directory)
- `head -n #` - view the first # of lines of a file
- `tail -n #` - view the last # of lines of a file
- `less` - view the contents of a file a little at a time nice way to scroll through
- `touch filename.txt` - quickly create a new file
- `nano filename.txt` - this is actually an entire text editing program (type text like normal)
    - write out is save and ^=control (^O) exit (^X)
- `wc` - print out the length of a file in lines, words, and characters

```
Practice Exercise

(1) Create a file with the touch command.
(2) Make a copy of the file using cp.
(3) Rename the original version of the file to something else with mv.
(4) Use nano to add different text to each copy and save it.
(5) View the contents of each file with cat.
(6) Check the sizes of each file with wc.
```

- `echo` - prints something to the screen (or elsewhere, as directed)
- `>>` - appends to file
    - `echo "some text here" >> myTextFile.txt`
- `>` - writes to (or over!) file
    - `echo "more text here" > myTextFile.txt`
- __WARNING - BIG WARNING - PAY ATTENTION__ - `rm` _permanently_ removes a file
    - No going back - always use this VERY carefully
    - I know people who've accidentally erased their __entire computers__ using this command
    - `rm -r` recursively removes a directory and everything inside it - even more dangerous than just `rm`!
    - This is the reason permissions are so important. If someone doesn't have write permissions on a file or folder, they shouldn't be able to delete it.
- `mkdir MyDirectory` - create a new (empty) directory (folder)
- `rmdir MyDirectory` - remove an empty directory !!WARNING!!
- wildcards - * is especially useful - matches anything
- `grep` - find only lines matching some particular string

```
Practice Exercise

(1) Create a series of new text files, with some filenams starting with one letter and some starting with another.
(2) Use echo and output redirection (> or >>) to add content to the files.
(3) With one command, list all the files that start with one particular letter.
(4) Make a new directory
(5) Move all files that start with one particular letter into the new directory.
(6) Try to remove that directory with rmdir. Can you?
(7) Extract all the lines from the files you created that contain one particular word of your choosing.
```

- [Notes about editing files and folders from the command line](https://github.com/IntroToCompBioLSU-Spr20/Shell_Week2/blob/master/CommandLine_Editing.md)

## Commands related to the Unix environment

- Can create a variable and assign value using `=`
    - `myVariable=2`
- Can print value of variable using `echo` and starting name with `$`
    - `echo $myVariable`
- `|` - the Unix pipe can be used to send the output of one command into the input of another
    - `history | tail -n 20 >> endOfHistory.txt`

## Introduction to scripts

- What is a script?
  - Fundamentally, a bash script is just a file containing a series of bash commands.
  - Scripts are formatted as text files. But the things in this file are special.
  - The first line of a script file tells the computer in which language (i.e., shell) we're writing our script. This line starts with "#!" - also known as a shebang. The shebang tells Terminal that we're about to indicate which language we're going to use.
  - Follow the shebang with the path to the shell that you'd like to use. Yes, the shell itself is a program!
    - #! /bin/bash
  - Let's start by creating your first script - myScript.sh
    - nano myScript.sh
    - Add the shebang line
    - Add two commands in the body of the file
      - echo "Hello, "$USER"!"
      - echo "I'M A SCRIPT AND I WORK!"


- Scripts contain series of commands
  - This is essentially your first foray into programming.
  - You'll need to think through the steps involved in whatever task you need to complete and then write a command for each step.
  - This ability to break a big problem into individual steps is the most important skill in programming.
  - As an example, let's write a program together to do a basic analysis of a dna sequence. This sequence is already available in the week 5 repository in `dnaSequence.txt`. This is a real sequence from the human genome (at least, some human genomes) and we'd like to count the number of As, Cs, Gs, and Ts that it contains.

- Command-line Arguments
    - To access the argument from inside the script, bash reserves the special variables $1, $2, $3, ...
    - For practice, go back to `myScript.sh` that we created earlier and change `$USER` to `$1`. Now, run it by typing `myScript.sh <YOUR_NAME>`

```
Assignment 3

Will be posted on Jan. 30th
```
