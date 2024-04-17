# Level 2 → 3 
## Connecting to level
~~~
ssh bandit2@bandit.labs.overthewire.org -p 2220
~~~

## Password to Enter Level
~~~
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
~~~

## Level Explanation
We have to extract the password from a file with the name `spaces in this filename`

## Hints
Check the behavior for `cat` for multiple arguments

Check this [source](https://www.baeldung.com/linux/bash-escape-characters) for escaping characters (the `\` is the key).

## Solution
~~~
cat 'spaces in this filename'
~~~
or
~~~
cat spaces\ in\ this\ filename'
~~~

## Extracted Password
~~~
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
~~~


## Approach  
Expected `cat` behaviour for commands like `cat a b c d` is it will output the contents of file `a`, `b`, `c` and `d` to standard output.  
Therefore when we use the command `cat spaces in this filename`, the command attempts to find and print 4 files: `spaces`, `in`, `this`, `filename`.  

To solve we can use quotes to specify a single file name like the previous problem or use escape characters which is `\` before the spaces giving us the two solutions.

## Step-by-Step Guide
This assumes you are connected to `bandit2`, if not follow the connecting to level and the password from the previous level.  

~~~
bandit2@bandit:~$
~~~

Use `ls` to see the files in the current directory

~~~
bandit2@bandit:~$ ls
spaces in this filename
~~~

Attempt to print the contents using `cat spaces in this filename`, you will see the expected behavior - cat will attempt to find each of the 4 files and tell you that they can't be found

~~~
bandit2@bandit:~$ cat spaces in this filename
cat: spaces: No such file or directory
cat: in: No such file or directory
cat: this: No such file or directory
cat: filename: No such file or directory
~~~

Now we will instead use quotations to use the entire filename as one continuous string. Alternate solution can also be used

~~~
bandit2@bandit:~$ cat "spaces in this filename"
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
~~~

>Tip: Attempt pressing tab after typing in 3-4 letters of the file name for auto-completion to help.

This final line is our password. To disconnect use Ctrl+D or the command `logout`.

