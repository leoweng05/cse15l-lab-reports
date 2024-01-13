# Lab Report 1 - Remote Access and FileSystem (Week 1)

## Command `cd`
Argument: None
```
[user@sahara ~]$ cd
[user@sahara ~]$
```
* The working Directory was `/home`.
* It has no output because the command changes the working directory and doesn't have to return anything. Using no arguments meant that it switched the directory to the root, which was `/home`.
* It is not an error.

---
Argument: path to directory
```
[user@sahara ~]$ cd ./lecture1
[user@sahara ~/lecture1]$
```
* The working directory was `/home`
* There is no output, but the prompt changed from `[user@sahara ~]$` to `[user@sahara ~/lecture1]$`. Once again, there is no output because `cd` changed directory to the argument `\lecture1` and did not return anything.
* It is not an error.

---
  Argument: path to file
  ```
  [user@sahara ~/lecture1]$ cd Hello.java
  bash: cd: Hello.java: Not a directory
  [user@sahara ~/lecture1]$
  ```
  * The working directory was `/home/lecture1`
  * This was the output because `cd` can only take no arguments or a path to a directory as an argument, so inputting a path to a file led to this error message.
  * This is an error because the purpose of `cd` is to change directories. As such, it only takes paths to directories for arguments, and in this instance, a path to a file was inputted.

  ## Command `ls`
  Argument: None
  ```
  [user@sahara ~/lecture1]$ ls
  Hello.class  Hello.java  messages  README
  [user@sahara ~/lecture1]$
  ```
  * The working directory was `/home/lecture1`.
  * This was the output because `ls` lists the files and directories. In this case, there were no arguments, so the command listed all items in the current working directory.
  * This is not an error.
 
 ---
  Argument: path to directory
  ```
  [user@sahara ~/lecture1]$ ls ./messages
  en-us.txt  es-mx.txt  fr.txt  zh-cn.txt
  [user@sahara ~/lecture1]$
  ```
  * The working directory was `/home/lecture1`.
  * This was the output because if the argument is a directory, `ls` will list the items in that directory.
  * This is not an error.

 ---
  Argument: path to file
  ```
  [user@sahara ~/lecture1]$ ls Hello.java
  Hello.java[user@sahara ~/lecture1]$
  ```
  * The working directory was `/home/lecture1`.
  * This was the output because the argument was not empty nor a directory, so it just repeated the file name back.
  * This is technically an error because the purpose of `ls` is to list content and files within a directory. Therefore, passing a file as an argument into the command is practically useless.

## Command: `cat`
Argument: None
```
[user@sahara ~/lecture1]$ cat
hi
hi
test
test
[user@sahara ~/lecture1]$
```
* The working directory was `/home/lecture1`.
* This was the output because with no argument, `cat` reads back whatever is inputted in the terminal. Since I typed `hi` and then `test`, the output shows the terminal reading my input back.
* This is an error because the purpose of `cat` is to concatenate the content of files. No files were inputted, and this repetition of input appears to be some kind of default behavior.

---
Argument: path to directory
```
[user@sahara ~/lecture1]$ cat ./messages
cat: ./messages: Is a directory
[user@sahara ~/lecture1]$
```
* The working directory was `/home/lecture1`.
* This was the output because the command arguments are supposed to be files. When a directory is inputted instead, this is the output message.
* This is an error because `cat` concatenates file contents, not directories. Thus, inputting a directory creates an error.

---
Argument: path to file
```
[user@sahara ~/lecture1]$ cat ./messages/fr.txt 
Bonjour le monde
[user@sahara ~/lecture1]$
```
* The working directory was `/home/lecture1`.
* This was the output because when the arguments are files, the content of the files will be listed. `Bonjour le monde` was the content of `fr.txt`, which `cat` successfully outputted.
* This is not an error.
