# **Lab Report 1 by Pranav Redbus**
***

# cd


## Example 1- No Arg

'''
# code block
[user@sahara ~/lecture1/messages]$ cd
[user@sahara ~]$ 
'''


## Example 2- Directory

'''
# code block
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ 
'''


## Example 3- File

'''
# code block
[user@sahara ~/lecture1]$ cd Hello.java
bash: cd: Hello.java: Not a directory
'''

***


# ls


## Example 1- No arg

'''
# code block
[user@sahara ~/lecture1]$ ls
Hello.class  Hello.java  messages  README
'''


## Example 2- Directory

'''
# code block
[user@sahara ~/lecture1]$ ls messages
en-us.txt  es-mx.txt  tel.txt  zh-cn.txt
'''


## Example 3- File

'''
# code block
[user@sahara ~/lecture1]$ ls Hello.java 
Hello.java
'''

***


# cat


## Example 1- No arg

'''
#code block
[user@sahara ~]$ cat 

'''


## Example 2- Directory

'''
#code block
[user@sahara ~/lecture1]$ cat messages
cat: messages: Is a directory
'''


## Example 3- File

'''
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
'''
