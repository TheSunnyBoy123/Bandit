# Level 0
~~~
ssh bandit0@bandit.labs.overthewire.org -p 2220
cat readme
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
~~~
**Approach**  
ssh command allows us to connect to a SSH sever; -p flag then specifies the port no to be used
cat command outputs contents of a file in the command line
___
# Level 1
~~~
cat ./-
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
~~~
**Approach**  
'-' is a keyword so instead to show this is a directory we use ./ to target this current directory
___
# Level 2
~~~
cat 'spaces in this filename'
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
~~~
**Approach**  
To handle the space in the filename, we add quotes around the name to treat the entire phrase as one name  
___
# Level 3
~~~
cd inhere
ls -a
cat .hidden
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
~~~
**Approach**  
cd changes directory to child directory 'inhere'.  
ls lists the files in current directory, since file is hidden, we use the -a flag to list hidden files as well.
___
# Level 4
~~~
file inhere/*
cat inhere/-file07
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
~~~
**Approach**  
file command lets us determine the type of a file and its content type
___
# Level 5
~~~
cd inhere
find -maxdepth 2 -type f -size 1033c
cat ./maybehere07/.file2
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
~~~

**Approach**  
we use -maxdepth 2 to search all files within a depth of 2  
-type f to search in only files  
-size 1033 to look for files with only this specific size
___
# Level 6
~~~
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
~~~
**Approach**  
we use find from / to look through all files on system  
-user bandit7 to look through files owned by the bandit7 user  
-group bandit6 to look through files owned by the bandit6 group  
-size 33c to look for files with 33 bytes size  
___
# Level 7  
~~~
vim data.txt
/
TESKZC0XvTetK0S9xNwm25STk5iWrBvP
~~~
**Approach**  
We use vim to open the file in a text editor  
then use / to open search dialogue box and look up millionth
___
# Level 8
~~~
sort data.txt | uniq -u
EN632PlfYiZbn3PhVK3XOGSlNInNE00t
~~~
**Approach**  
We use 'uniq -u' to remove all duplicates and print only the strings present once in the file  
'|' allows us to run two commands simulateneously, passing the sorted file from one command to the next command
___
# Level 9
~~~
strings data.txt | grep ==
G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
~~~
**Approach**  
We use 'strings' to print only the text data in the file  
'grep' is used to find lines with multiple '=' char and print only those
___
# Level 10
~~~
base64 -d data.txt
6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
~~~
**Approach**  
Since the file has data encoded in base64, we can use the command 'base64' which then takes a flag  
-d flag is used for decoding and the password is then seen
___
# Level 11
~~~
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
~~~
**Approach**
we use tr to translate the characters by 13, since that's the translation done by Rot13  
the first argument gives the set of source chars and second arg gives the set of target chars
___
# Level 12
~~~
cd /tmp
mktemp -d
cd /tmp/tmp.6oTLNT00QC
cp ~/data.txt .
mv data.txt hexdump_data
xxd -r hexdump_data compressed_data
mv compressed_data compressed_data.gz
gzip -d compressed_data.gz
mv compressed_data compressed_data.bz2
bzip2 -d compressed_data.bz2
mv compressed_data compressed_data.gz
gzip -d compressed_data.gz
tar -xf compressed_data.tar
tar -xf data5.bin
bzip2 -d data6.bin
tar -xf data6.bin.out
mv data8.bin data8.gz
gzip -d data8.gz
cat data8
wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
~~~
**Approach**  
We used /tmp/ directory to store the files that were required temporarily  
We copied 'data.txt' there using cp which takes arguements source file and target dir 
- '.' signifies current dir  

'mv' command allows us to move the file contents to another using which we can change the file type

Using 'xxd -r' we converted hex data to binary 'r' signifies reverse operation 

Checking the data, the starting byte signfied the type of data contained in it  
- gzip: if the header byte is \x1F\x8B\x08 then we know the file type is a gzip
- bzip2: if the header byte is 425a which stands for 'BZ' then we know the file type is a bizp2

The decompression commands are:
~~~
gzip -d data.gz
bzip2 -d data.bz2
~~~
___
# Level 13
~~~
ssh -i sshkey.private bandit14@localhost -p 2220
cd /etc/bandit_pass/
cat bandit14
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
~~~
**Approach**  
We use the ssh command which lets us login to a public server, like we have been doing to start any bandit level.  
This time we use the -i flag to use a private identity/key, this requires an argument of the file with the private key.  
Next we know that after connecting to bandit14 the password is stored in /etc/bandit_pass/ so we cd into the directory and print out the password
___
# Level 14
~~~
telnet localhost 30000
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
~~~
**Approach**  
As we need to submit the password of the current level to localhost (a server) we can use telnet.  
This takes two arguments - host and port
___
# Level 15
~~~
openssl s_client -connect localhost:30001
JQttfApK4SeyHwDlI9SXGR50qclOAil1
~~~
**Approach**  
The problem requires we connect to the server using ssl so we use openssl  
openssl s_client allows us to a server using ssl  
-connect specifies connect using the argument host:port - the details for this are given in the problem.  
___
