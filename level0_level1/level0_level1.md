# Level 0 → 1

## Level Explanation
We have connected to the host and now there is a readme file in the home directory (which is where we are currently logged in) which has the password for the next level.  

We need to get this password extracted from the file and proceed to the next level, which we will then also connect to using ssh

## Hints
To output the contents of a file `cat` is used 

Refer to this documentation for the use of [cat](https://man7.org/linux/man-pages/man1/cat.1.html) to output contents of a file in command line.   


The command to extract the password is of form `cat <filename>`

## Solution
~~~
cat readme
~~~

## Extracted Password
~~~
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
~~~

## Approach  
We need to extract the contents of the file readme (to check if the file is in this directory - use `ls` to list all files in current directory).  

Here on some basic terminal commands to navigate through directories (folders) and files will be used of which, some are listed here

|Command|Use|
|---|---|
|ls|lists all the files in the current directory|
|cd|changes directory to the specified directory|
|pwd|shows the current working directory, can usually also be seen on the left of each newline in shell/terminal (home is represented as `~`)|
|cat|prints the file specified to the standard output (the terminal in our use case)|


For our purpose, we use `cat` with the form `cat <filename>` - giving us `cat readme` from which we then get the password required for the next level.

## Step-by-Step Guide
This assumes you are connected to `bandit0`, if not follow the steps for Level 0

Your command line looks like this
~~~
bandit0@bandit:~$
~~~

To check the files in our current (home) directory we can use `ls`:
~~~
bandit0@bandit:~$ ls
readme
~~~

We can see the file readme listed here, as discussed in the approach section we now need to use the command cat readme.  
An interesting thing to learn here is autocomplete in terminal, once you've typed `cat re`, attempt pressing tab, this will look through the possible filenames and if there is a complete possible, substitute the name.
~~~
bandit0@bandit:~$ cat re
~~~
Press tab
~~~
bandit0@bandit:~$ cat readme
~~~
Press return to execute
~~~
bandit0@bandit:~$ cat readme
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
~~~
This final line is our password. To disconnect use Ctrl+D or the command `logout`.

