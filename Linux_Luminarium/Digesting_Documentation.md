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
## Question
This level introduces the man command. man is short for manual, and will display (if available) the manual of the command you pass as an argument. For example, let's say we wanted to learn about the yes command (yes, this is a real command):

hacker@dojo:~$ man yes
This will display the manual page for yes, which will look something like this:

YES(1)                           User Commands                          YES(1)

NAME
       yes - output a string repeatedly until killed

SYNOPSIS
       yes [STRING]...
       yes OPTION

DESCRIPTION
       Repeatedly output a line with all specified STRING(s), or 'y'.

       --help display this help and exit

       --version
              output version information and exit

AUTHOR
       Written by David MacKenzie.

REPORTING BUGS
       GNU coreutils online help: <https://www.gnu.org/software/coreutils/>
       Report any translation bugs to <https://translationproject.org/team/>

COPYRIGHT
       Copyright  ©  2020  Free Software Foundation, Inc.  License GPLv3+: GNU
       GPL version 3 or later <https://gnu.org/licenses/gpl.html>.
       This is free software: you are free  to  change  and  redistribute  it.
       There is NO WARRANTY, to the extent permitted by law.

SEE ALSO
       Full documentation <https://www.gnu.org/software/coreutils/yes>
       or available locally via: info '(coreutils) yes invocation'

GNU coreutils 8.32               February 2022                          YES(1)
The important sections are:

NAME(1)                           CATEGORY                          NAME(1)

NAME
	This gives the name (and short description) of the command or
	concept discussed by the page.

SYNOPSIS
	This gives a short usage synopsis. These synopses have a standard
	format. Typically, each line is a different valid invocation of the
	command, and the lines can be read as:

	COMMAND [OPTIONAL_ARGUMENT] SINGLE_MANDATORY_ARGUMENT
	COMMAND [OPTIONAL_ARGUMENT] MULTIPLE_ARGUMENTS...

DESCRIPTION
	Details of the command or concept, with detailed descriptions
	of the various options.

SEE ALSO
	Other man pages or online resources that might be useful.

COLLECTION                        DATE                          NAME(1)
You can scroll around the manpage with your arrow keys and PgUp/PgDn. When you're done reading the manpage, you can hit q to quit.

Manpages are stored in a centralized database. If you're curious, this database lives in the /usr/share/man directory, but you never need to interact with it directly: you just query it using the man command. The arguments to the man command aren't file paths, but just the names of the entries themselves (e.g., you run man yes to look up the yes manpage, rather than man /usr/bin/yes, which would be the actual path to the yes program but would result in man displaying garbage).

The challenge in this level has a secret option that, when you use it, will cause the challenge to print the flag. You must learn this option through the man page for challenge!
## Code
```
hacker@man~reading-manuals:/$ ls
bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hacker@man~reading-manuals:/$ cd challenge
hacker@man~reading-manuals:/challenge$ ./challenge
Incorrect usage! Please read the challenge man page!
hacker@man~reading-manuals:/challenge$ cat challenge
cat: challenge: Permission denied
hacker@man~reading-manuals:/challenge$ man challenge

CHALLENGE(1)                                                                                Challenge Commands                                                                                CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --klxugg NUM
              print the flag if NUM is 714

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                                                                      May 2024                                                                                     CHALLENGE(1)
hacker@man~reading-manuals:/challenge$ challenge option
ssh-entrypoint: challenge: command not found
hacker@man~reading-manuals:/challenge$ ./challenge --klxugg 714
Correct usage! Your flag: pwn.college{klxugMMgfs7m1HqraQOZMLjUioJ.dRTM4QDLyUTN0czW}
hacker@man~reading-manuals:/challenge$ 
```
## What I learnt
In this case, we only got the flag when we enter the correct argument and to know what argument to enter, we have to look up the man page for challenge.

# D.4 Searching Manuals
## Question
You can scroll man pages with the arrow keys (and PgUp/PgDn) and search with /. After searching, you can hit n to go to the next result and N to go to the previous result. Instead of /, you can use ? to search backwards!

Find the option that will give you the flag by reading the challenge man page.
## Code
```
Connected!                                                                        
hacker@man~searching-manuals:~$ cd /challenge
hacker@man~searching-manuals:/challenge$ ls
DESCRIPTION.md  challenge
hacker@man~searching-manuals:/challenge$ man challenge
hacker@man~searching-manuals:/challenge$ /challenge/challenge --tj 
Initializing...
Correct usage! Your flag: pwn.college{ITS6hmVVorh2lrteWVB8qgnMkVv.dVTM4QDLyUTN0czW}
hacker@man~searching-manuals:/challenge$ 
```
## What I learnt
It is same as the last one but we have to search the man page. I couldn't save the page because it got removed when I exited. 

# D.5 Searching for Manuals 
## Question
This level is tricky: it hides the manpage for the challenge by randomizing its name. Luckily, all of the man pages are gathered in a searchable database, so you'll be able to search the man page database to find the hidden challenge man page! To figure out how to search for the right man page, read the man page manpage by doing: man man!

HINT 1: man man teaches you advanced usage of the man command itself, and you must use this knowledge to figure out how to search for the hidden manpage that will tell you how to use /challenge/challenge

HINT 2: though the man page is randomly named, you still actually use /challenge/challenge to get the flag!
## Code
```
Connected!                                                                        
Connected!                                                                        
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:/usr/share/man$ man -k challenge
dqanpwakzd (1)       - print the flag!
hacker@man~searching-for-manuals:/usr/share/man$ /challenge/run
ssh-entrypoint: /challenge/run: No such file or directory
hacker@man~searching-for-manuals:/usr/share/man$ cd /challenge
hacker@man~searching-for-manuals:/challenge$ ls
DESCRIPTION.md  bin  challenge
hacker@man~searching-for-manuals:/challenge$ /challenge/challenge
Incorrect usage! Please read the challenge man page!
hacker@man~searching-for-manuals:/challenge$ /challenge/challenge dqanpwakzd (1)
ssh-entrypoint: syntax error near unexpected token `('
hacker@man~searching-for-manuals:/challenge$ /challenge/challenge dqanpwakzd 
Incorrect usage! Please read the challenge man page!
hacker@man~searching-for-manuals:/challenge$ man -k challenge
dqanpwakzd (1)       - print the flag!
hacker@man~searching-for-manuals:/challenge$ /flag
ssh-entrypoint: /flag: Permission denied
hacker@man~searching-for-manuals:/challenge$ cat /flag
cat: /flag: Permission denied
hacker@man~searching-for-manuals:/challenge$ /challenge/challenge
Incorrect usage! Please read the challenge man page!
hacker@man~searching-for-manuals:/challenge$ man dqanpwakzd

CHALLENGE(1)                                                                                Challenge Commands                                                                                CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --dqanpw NUM
              print the flag if NUM is 211

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                                                                      May 2024                                                                                     CHALLENGE(1)
hacker@man~searching-for-manuals:/challenge$ /challenge/challenge  --dqanpw 211
Correct usage! Your flag: pwn.college{MO2dQq-aLMV1BnDpw1a31Ok49zV.dZTM4QDLyUTN0czW}
hacker@man~searching-for-manuals:/challenge$ 
```
## What I learnt
First I read the manual for man command and I realised that I could put challenge as an argument to man -k, which will search for the keyword challenge through all the manuals and it gave me the output dqanpwakzd. At first, I thought that it was the argument that I had to use with /challenge/challenge to get the flag but it was the manual page, where I will get the right argument to use to get the flag. This question took me a lot of time to solve as going through the man man page took a lot of time.

# D.6 Helpful Programs
## Question
Some programs don't have a man page, but might tell you how to run them if invoked with a special argument. Usually, this argument is --help, but it can often be -h or, in rare cases, -?, help, or other esoteric values like /? (though that latter is more frequently encountered on Windows).

In this level, you will practice reading a program's documentation with --help. Try it out!

## Code
```
Connected!                                                                        
hacker@man~helpful-programs:~$ cd /challenge
hacker@man~helpful-programs:/challenge$ ls
DESCRIPTION.md  challenge
hacker@man~helpful-programs:/challenge$ ./challenge
No options specified.
hacker@man~helpful-programs:/challenge$ /challenge --help
ssh-entrypoint: /challenge: Is a directory
hacker@man~helpful-programs:/challenge$ /challenge/challenge --help 
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:/challenge$ /challenge/challenge --fortune
I do not know where to find in any literature, whether ancient or modern,
any adequate account of that nature with which I am acquainted.  Mythology
comes nearest to it of any.
		-- Henry David Thoreau
hacker@man~helpful-programs:/challenge$ /challenge/challenge -g
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]
a challenge to make you ask for help: error: argument -g/--give-the-flag: expected one argument
hacker@man~helpful-programs:/challenge$ ./challenge -p
The secret value is: 833
hacker@man~helpful-programs:/challenge$ ./challenge -g 833
Correct usage! Your flag: pwn.college{oRy_P8tuMlZ3qWT3AUphltRkXpq.ddjM4QDLyUTN0czW}
```
## What I learnt
Here I also tried the fortune argument because I found it to be interesting. Although I knew that it won't help me solve the challenge. I wanted to see what it would give to me. First, I had to enter the -p argument to get the value for argument -g to get the flag. 

# D.7 Help for Builtins 
## Question
Some commands, rather than being programs with man pages and help options, are built into the shell itself. These are called builtins. Builtins are invoked just like commands, but the shell handles them internally instead of launching other programs. You can get a list of shell builtins by running the builtin help, as so:

hacker@dojo:~$ help
You can get help on a specific one by passing it to the help builtin. Let's look at a builtin that we've already used earlier, cd!

hacker@dojo:~$ help cd
cd: cd [-L|[-P [-e]] [-@]] [dir]
    Change the shell working directory.
    
    Change the current directory to DIR.  The default DIR is the value of the
    HOME shell variable.
...
Some good information! In this challenge, we'll practice using help to look up help for builtins. This challenge's challenge command is a shell builtin, rather than a program. Like before, you need to lookup its help to figure out the secret value to pass to it!
## Code
```
hacker@man~help-for-builtins:~$ cd /challenge
hacker@man~help-for-builtins:/challenge$ ls
DESCRIPTION.md
hacker@man~help-for-builtins:/challenge$ cd ..
khacker@man~help-for-builtins:/$ ls
bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hacker@man~help-for-builtins:/$ ./flag
ssh-entrypoint: ./flag: Permission denied
hacker@man~help-for-builtins:/$ help flag
ssh-entrypoint: help: no help topics match `flag'.  Try `help help' or `man -k flag' or `info flag'.
hacker@man~help-for-builtins:/$ info flag
ssh-entrypoint: info: command not found
hacker@man~help-for-builtins:/$ man flag
No manual entry for flag
hacker@man~help-for-builtins:/$ ./challenge
ssh-entrypoint: ./challenge: Is a directory
hacker@man~help-for-builtins:/$ cd challenge
hacker@man~help-for-builtins:/challenge$ ls
DESCRIPTION.md
hacker@man~help-for-builtins:/challenge$ ls -a
.  ..  .bashrc  .challenge.so  .init  DESCRIPTION.md
hacker@man~help-for-builtins:/challenge$ ./.challenge.so
Segmentation fault
hacker@man~help-for-builtins:/challenge$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune		display a fortune
      --version		display the version
      --secret VALUE	prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "8MvqVvLh".
hacker@man~help-for-builtins:/challenge$ challenge --secret 8MvqVvLh
Correct! Here is your flag!
pwn.college{8MvqVvLh1Xl3yW-GKtXz6FFJkqz.dRTM5QDLyUTN0czW}
```
## What I learnt
I have some silly mistakes here like trying to access /flag by myself. It took me quite a while to realise that I couldn't access it.
