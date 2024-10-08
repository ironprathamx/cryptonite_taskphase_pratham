# D.1 Learning from Documentation
## Question
The typical need you'll have for documentation is just to figure out how to use all these dang programs, and a specific case of that is figuring out what arguments to specify on the command line. This module will mostly dig into that concept, as a proxy for figuring out how to use the programs in general. Through the rest of the module, you'll go through various ways of asking the environment for help for the programs, but first, we'll dig into the concept of reading documentation.

The correct usage of programs depends, in a large part, in the proper specification of arguments to them. Recall the -a of ls -a in the hidden files challenge of the Basic Commands module: that -a was an argument that told ls to list out hidden files as well as non-hidden files. Because we wanted to list out hidden files, invoking ls with the -a argument was the correct way to use it in our scenario.

The program for this challenge is /challenge/challenge, and you'll need to invoke it properly in order for it to give you the flag. Let's pretend that this is its documentation:

Welcome to the documentation for /challenge/challenge! To properly run this program, you will need to pass it the argument of --giveflag. Good luck!

Given that knowledge, go get the flag!
## Code
```
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{EYJYixhyJ3OPoSo-7ASjCbI3L3Z.dRjM5QDLyUTN0czW}
hacker@man~learning-from-documentation:~$ 
```
## What I learnt
Nothing.

# D.2 Learning Complex Usage 
## Question
While using most commands is straightforward, the usage of some commands can get quite complex. For example, the arguments to commands like sed and awk, which we're definitely not getting into right now, are entire programs in an esoteric programming language! Somewhere on the spectrum between cd and awk are commands that take arguments to their arguments...

This sounds crazy, but you've already encountered this with the find level in Basic Commands. find has a -name argument, and the -name argument itself takes an argument specifying the name to search for. Many other commands are analogous.

Here is this level's documentation for /challenge/challenge:

Welcome to the documentation for /challenge/challenge! This program allows you to print arbitrary files to the terminal, when given the --printfile argument. The argument to the --printfile argument is the path of the flag to read. For example, /challenge/challenge --printfile /challenge/DESCRIPTION.md will print out the description of the level!

Given that documentation, go get the flag!
## Code
```
hacker@man~learning-complex-usage:~$ cd /challende
ssh-entrypoint: cd: /challende: No such file or directory
hacker@man~learning-complex-usage:~$ cd /challenge
hacker@man~learning-complex-usage:/challenge$ ls
DESCRIPTION.md  challenge
hacker@man~learning-complex-usage:/challenge$ ./challenge --printfile ./challenge
Correct argument! Here is the ./challenge file:
#!/opt/pwn.college/bash

if [ "$#" -eq 0 ]
then
	fold -s <<< "Incorrect usage! You must pass an argument to me (read the challenge description for details)."
	exit 1
fi

if [ "$1" != "--printfile" ]
then
	fold -s <<< "Incorrect usage! You passed the wrong argument (read the challenge description for details)."
	exit 2
fi

if [ "$#" -eq 1 ]
then
	fold -s <<< "You must pass a file for --printfile to read!"
	exit 3
fi

echo "Correct argument! Here is the $2 file:"
cat "$2"
hacker@man~learning-complex-usage:/challenge$ cd ..
hacker@man~learning-complex-usage:/$ ls
bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hacker@man~learning-complex-usage:/$ cat flag
cat: flag: Permission denied
hacker@man~learning-complex-usage:/$ cd challenge
hacker@man~learning-complex-usage:/challenge$ ./challenge
Incorrect usage! You must pass an argument to me (read the challenge 
description for details).
hacker@man~learning-complex-usage:/challenge$ ./challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{4K0AoysBsSzGKcTtECVgAt1JXdi.dVjM5QDLyUTN0czW}
hacker@man~learning-complex-usage:/challenge$
```
## What I learnt
To read the content of flag, we have to pass it as an argument to the challenge execution as we can't read it as we lack the permissions. This is a way to access something we don't have perms for.

# D.3 Reading Manuals 
