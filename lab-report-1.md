# `cd` command examples

```
  [user@sahara ~]$ cd
  [user@sahara ~]$ 
```
The working directory is `/home`.
Using `cd` with no arguments changes the directory to the root directory.
This does not result in an error.


```
  [user@sahara ~]$ cd lecture1
  [user@sahara ~/lecture1]$ 
```
The working directory for is `/home`.
Using `cd` with a directory as the argument changes the directory to the directory specified in the argument.
This output is not an error, however, if a directory name is not found inside the working directory, this will result in an error.


```
  [user@sahara ~/lecture1]$ cd Hello.java
  bash: cd: Hello.java: Not a directory
```
The working directory is `/home/lecture1`.
Using `cd` with a file as the argument results in an error because *a file is not a directory*.
This output is an error. It's an error because you cannot `cd` (change directory) into a file (which is not a directory).


# `ls` command examples

```
  [user@sahara ~]$ ls
  lecture1  test.txt
```
The working directory is `/home`.
Using `ls` with no arguments lists all the files and directories inside the working directory.
This output is not an error.


```
  [user@sahara ~]$ ls lecture1
  Hello.class  Hello.java  messages  README
```
The working directory is `/home`.
Using `ls` with a directory as the argument lists all the files and directories inside the directory specified in the argument.
This output is not an error, however, if a directory name is not found inside the working directory, this will result in an error.


```
  [user@sahara ~]$ ls test.txt 
  test.txt
```
The working directory is `/home`.
Using `ls` with a file as the argument returns the name of the file specified in the argument as the output.
This output is not an error, however, if a file name is not found inside the working directory, this will result in an error.


# `cat` command examples

```
  [user@sahara ~]$ cat
  a
  a
  ^C
```
The working directory is `/home`.
Using `cat` with no arguments results in the command line returning any user input until `ctrl + c` is used.
This output is not an error.


```
  [user@sahara ~]$ cat lecture1/
  cat: lecture1/: Is a directory
```
The working directory is `/home`.
Using `cat` with a directory as the argument results in an error because `cat` cannot print the contents of a directory.
This output is an error. `cat` cannot print the contents of a directory.


```
  [user@sahara ~]$ cat test.txt
  test
```
The working directory is `/home`.
Using `cat` with a file as the argument returns the contents of the file specified in the argument.
This output is not an error, however, if a file name is not found inside the working directory, this will result in an error.





