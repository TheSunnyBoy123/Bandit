# Level 4 → 5
## Connecting to level
~~~
ssh bandit4@bandit.labs.overthewire.org -p 2220
~~~

## Password to Enter Level
~~~
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
~~~

## Level Explanation
There is a directory `inhere` in the home directory, which contains multiple files.  
Now, only one of these files is human-readable - we need to extract the password for the next level from this. 

## Hints
To get into `inhere` we need to use `cd` to change directory 

One approach is brute force, check each file's content by simply printing it. The output which reads a password will be our answer

Another, more efficient, approach is the `file` command, check this [page](https://www.geeksforgeeks.org/file-command-in-linux-with-examples/) to learn more.  
This approach will also need wildcard symbol (specifically `*`)

## Approach  
The brute force approach should be straight forward, we simply do what we have been doing, using `cat` for each file. Basically executing `cat ./-file0x` (pathname is necessary since filename starts with a hyphen, Level 1→2) for all x from 0 to 9.

Another is executing `file` for all files in the directory to check which contains ASCII text. This command basically goes through some of the initial bytes looking for certain numbers (called magic number) which help identify the file type. We will see more of magic numbers on Level 12 → 13.

For this we will use `file <pathname>` but since we need to go through multiple files, all which have the same path, we can simply execute `file ./*`. In this command, `*` represents that this character can be replaced by any number of characters for matching purposes.

## Solution
~~~
cd inhere
file ./*
cat ./-file07
~~~

## Extracted Password
~~~
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
~~~

## Step-by-Step Guide
This assumes you are connected to `bandit4`, if not follow the connecting to level and the password from the previous level.  

~~~
bandit4@bandit:~$
~~~

Use `cd inhere/` change your working directory to `inhere`

~~~
bandit4@bandit:~$ cd inhere/
bandit4@bandit:~/inhere$
~~~

Now we can check which files are available to us using `ls`
~~~
bandit4@bandit:~/inhere$ ls
-file00  -file02  -file04  -file06  -file08
-file01  -file03  -file05  -file07  -file09
~~~
We can now see that all these files have the path name of the structure `./-file0x` where x varies. To execute a command on all files with a similar name we can use what is called a wildcard symbol.  
So to represent this pathname using `*` we can go for `./*` since all files within this directory will be checked for

~~~
bandit4@bandit:~/inhere$ file ./*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
~~~

Now notice that only `-file07` has the type `ASCII text` in its contents. Now we can check its contents using `cat` like previous levels.

~~~
bandit4@bandit:~/inhere$ cat ./-file07
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
~~~

This final line is our password. To disconnect, use Ctrl+D or the command `logout`.