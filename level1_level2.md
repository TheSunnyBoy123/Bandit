# Level 1 → 2
## Connecting to level
~~~
ssh bandit1@bandit.labs.overthewire.org -p 2220
~~~

## Password to Enter Level
~~~
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
~~~

## Level Explanation
We have to extract the password from a file with the name `-`

## Hints
The simple solution `cat -` does not work since the bash understands the `-` here as a flag, try specifying this as a filename instead.

Alternate solution is to use the pathname (the directory + filename which specifies this file).

Try putting the filename in quotations

## Solution
~~~
cat '-'
~~~
or
~~~
cat ./-
~~~

## Extracted Password
~~~
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
~~~

## Approach  
`-` is a special character which is used to choose flags for a command.  

So to instead show we are referring to a file with the name `-` we can put it within quotations. This shows that the characters within the quotations are simply the name of a file

If we instead use the pathname for this file which is `./-`, we also avoid the confusion.

## Step-by-Step Guide
This assumes you are connected to `bandit1`, if not follow the connecting to level and the password from the previous level.  

~~~
bandit1@bandit:~$
~~~

Use `ls` to see the files in the current directory

~~~
bandit1@bandit:~$ ls
-
~~~

Attempt to print the contents like the previous level, using `cat -`, you will see no output as expected, a flag is being waited for

~~~
bandit1@bandit:~$ cat -

~~~

Press `Ctrl+C` to exit the current dialogue. Now we will specify the pathname `./-` here `.` stands for the current working directory. Alternate solution can also be used

~~~
bandit1@bandit:~$ cat ./-
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
~~~
This final line is our password. To disconnect use Ctrl+D or the command `logout`.