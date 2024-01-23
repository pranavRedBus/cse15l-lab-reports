# **Lab Report 1**

Pranav Reddy Bussannagari
***

# 'cd'

* Changes the directory by getting more/less/equally specific

## Example 1- No Arg

```
# code block
[user@sahara ~/lecture1/messages]$ cd
[user@sahara ~]$ 
```
> Working directory: **`/home/lecture1`**
> 
> I got this output because `cd`, with no commands given, returns the terminal to the `/home` directory, or the most general directory in which the workspace is set up.
> 
> Not an error


## Example 2- Directory

```
# code block
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ 
```
> Working directory: **`/home`**
> 
> I got this output because `cd`, when given a proper directory that is directly below it (accessible 1 folder down), enters that directory.
> 
> Not an error.


## Example 3- File

```
# code block
[user@sahara ~/lecture1]$ cd Hello.java
bash: cd: Hello.java: Not a directory
```
> Working directory: **`/home/lecture1`**
> 
> I got this output since `cd` can only be used to change *directories*, moving from one to another, and a file does not fall into the category of directory.
> 
> Error: the command `cd` does not work in this case, returning a message rather than changing a directory, since `Hello.java` is a file, and one cannot change directories into a file– only other directories.

***


# 'ls'

* Lists all possible paths from given/current location

## Example 1- No arg

```
# code block
[user@sahara ~/lecture1]$ ls
Hello.class  Hello.java  messages  README
```
> Working directory: **`/home/lecture1`**
>
> I got this output because `ls` gives a list of files, folders, and directories that the terminal could next enter, either from the directory/file specified as an argument, or from the working directory if no arguments are passed. In this case, the `lecture1` directory contains `Hello.class`,  `Hello.java`,  `messages`,  and `README` are accessible to the terminal, so they are listed when the command is called.
>
> Not error.


## Example 2- Directory

```
# code block
[user@sahara ~/lecture1]$ ls messages
en-us.txt  es-mx.txt  tel.txt  zh-cn.txt
```
> Working directory: **`/home/lecture1`**
>
> This time, a directory was specified, and since a directory can have multiple files/directories in it, all of those files and other directories are listed by the command.
>
> Not error.


## Example 3- File

```
# code block
[user@sahara ~/lecture1]$ ls Hello.java 
Hello.java
```

***
> Working directory: **`/home/lecture1`**
>
> This time, a file was specified, and since a file only has its contents (itself), its name is the only listed path by the `ls` function.
>
> Not error.


# 'cat'

* Prints the contents of a file (excluding binary files), and concatenates them when given multiple arguments. Does not work with directories.

## Example 1- No arg

```
#code block
[user@sahara ~]$ cat 

```
> Working directory: **`/home`**
>
> The `cat` command concatenates text from files, but since no file was given for it, there was nothing to print, leading to an empty line being printed. If anything is written in this line, cat will output the same written value from the terminal.
>
> Not error.


## Example 2- Directory

```
#code block
[user@sahara ~/lecture1]$ cat messages
cat: messages: Is a directory
```
> Working directory: **`/home/lecture1`**
>
> The `cat` command cannot concatenate directories as there could be multiple files that can be opened from them, and there is no text contained directly under them. Therefore, the terminal would not know what to print, leading to an error.
>
> Error: `cat` returned a message explaining why it cannot concatenate `messages` rather than the contents of the argument since, as mentioned earlier, it is meant to concatenate the text/writing in a file, which it cannot do when provided with a terminal.


## Example 3- File

```
#code block
[user@sahara ~/lecture1]$ cat Hello.java
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOException {
    String content = Files.readString(Path.of(args[0]), StandardCharsets.UTF_8);    
    System.out.println(content);
  }
}
```
> Working directory: **`/home/lecture1`**
>
> The `cat` command concatenates text from files, including code, and so it prints out everything written in the `Hello.java` file after being called.
>
> Not error.
