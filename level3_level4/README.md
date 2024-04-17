# Level 3 → 4
## Connecting to level
~~~
ssh bandit3@bandit.labs.overthewire.org -p 2220
~~~

## Password to Enter Level
~~~
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
~~~

## Level Explanation
There is a directory `inhere` in the home directory, which contains a hidden file with the password for our next level.

## Hints
To get into `inhere` we need to use `cd` to change directory 

To list hidden files using `ls` we need to use the `-a` flag - `ls -a` lists hidden files

`.` and `..` when using `ls -a` are used to show parent and current directory, these are not the hidden files.

## Approach  
As discussed earlier `cd` allows us to change our working directory (folder in your file explorer/finder).  
For a little more detail on its usage these are some of its flags
|Flag|Usage|
|---|---|
|`cd <path>`|Changes working directory to `path`|
|`cd ..`|Changes working directory to parent directory|
|`cd ~`|Changes working directory to home directory|

Once we have navigated to `inhere` directory, we can see all the files in this directory by using `ls -a`.  

Next using `cat .hidden` we get the password for the next level

## Solution
~~~
cd inhere
ls -a
cat .hidden
~~~

## Extracted Password
~~~
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
~~~

## Step-by-Step Guide
This assumes you are connected to `bandit3`, if not follow the connecting to level and the password from the previous level.  

~~~
bandit3@bandit:~$
~~~

Use `cd inhere/` change your working directory to `inhere`

~~~
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$
~~~

As you can see in the command line, it now reads the working directory as `~/inhere` which means we have entered inhere within our home directory (`~`).  

Simply using `ls` won't work since the file is hidden so instead we use `ls -a` which will list hidden files as well

~~~
bandit3@bandit:~/inhere$ ls -a
.  ..  .hidden
~~~
The `.hidden` file has our password. Like previously, we can now output this using `cat`

~~~
bandit3@bandit:~/inhere$ cat .hidden
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
~~~

This final line is our password. To disconnect, use Ctrl+D or the command `logout`.