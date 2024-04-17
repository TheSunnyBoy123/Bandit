# Level 0
## Level Explanation
We are given a username `bandit0` and the password `bandit0`. We need to connect to the given host `bandit.labs.overthewire.org` using SSH and port `2000`.  

## Hints
Refer to this documentation of [SSH](https://man7.org/linux/man-pages/man1/ssh.1.html) for the use of `-p` [flag](https://www.ibm.com/docs/pt/aix/7.1?topic=names-command-flags).  

The solution uses the form `ssh <username>@<host> -p <port no.>`

## Password to Start
~~~
bandit0
~~~


## Solution
~~~
ssh bandit0@bandit.labs.overthewire.org -p 2220
~~~



## Approach  
Once your Command Prompt (Windows) / Terminal (Mac and Linux) is open, we can begin using bash commands like `ls`, `cat`, `ssh`, etc. 

The required bash/command line command is `ssh` for this.

`ssh` is a program for logging into a remote machine and for executing commands on a remote machine  
The used command is of form `ssh <username>@<host> -p <port no.>`.  
If a `-p <port no.>` argument is not provided, `ssh` uses the default port `22` so sometimes your attempt to login can fail.

In a command, the parts including and between the angle brackets are supposed to replaced with the expected value. 

Entering the password `bandit0` logs us in now.

## Step-by-step guide
Once your terminal is open, enter
~~~
ssh bandit0@bandit.labs.overthewire.org -p 2220
~~~

You will now see the screen (some lines are removed in this guide for brevity, try looking at the last line in your terminal):
~~~
bandit0@bandit.labs.overthewire.org's password: 
~~~
Type the password `bandit0` which has been provided in the problem. Typing the password in command line does not show up so don't worry if your keypresses don't show. Once done, press enter you will now see
~~~
bandit0@bandit:~$
~~~
This means we are now logged into bandit0 and current able to move through the directories. To check, try running `ls` which will list all the files in the current directory. 
~~~
bandit0@bandit:~$ ls
readme
~~~




