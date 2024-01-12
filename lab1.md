# Lab Report 1 - Remote Access and FileSystem (Week 1)

## Command `cd`
No Arguments:
```
[user@sahara ~]$ cd
[user@sahara ~]$
```
* The working Directory was `/home`.
* It has no output because the command changes the working directory and doesn't have to return anything. Using no arguments meant that it switched the directory to the root, which was `/home`.
* It is not an error.

Path to directory:
```
[user@sahara ~]$ cd ./lecture1
[user@sahara ~/lecture1]$
```
* The working directory was `/home`
* There is no output, but the prompt changed from `[user@sahara ~]$` to `[user@sahara ~/lecture1]$`. Once again, there is no output because `cd` changed directory to the argument `\lecture1` and did not return anything.
* It is not an error.

  Path to file:
  ```
  [user@sahara ~/lecture1]$ cd Hello.java
  bash: cd: Hello.java: Not a directory
  [user@sahara ~/lecture1]$
  ```
  * The working directory was `/home/lecture1`
  * The output was `bash: cd: Hello.java: Not a directory`. This was the output because `cd` can only take no arguments or a path to a directory as an argument, so inputting a path to a file led to this error message.
  * This is an error because the purpose of `cd` is to change directories. As such, it only takes paths to directories for arguments, and in this instance, a path to a file was inputted.
