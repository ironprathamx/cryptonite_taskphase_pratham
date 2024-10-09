# F.1 Redirecting output
## Question 
First, let's look at redirect stdout to files. You can accomplish this with the > character, as so:

hacker@dojo:~$ echo hi > asdf
This will redirect the output of echo hi (which will be hi) to the file asdf. You can then use a program such as cat to output this file:

hacker@dojo:~$ cat asdf
hi
In this challenge, you must use this input redirection to write the word PWN (all uppercase) to the filename COLLEGE (all uppercase).
## Code
```
hacker@piping~redirecting-output:~$ cd /
hacker@piping~redirecting-output:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@piping~redirecting-output:/$ cd challenge
hacker@piping~redirecting-output:/challenge$ ls
DESCRIPTION.md  run
hacker@piping~redirecting-output:/challenge$ ./run
First, let's look at redirect stdout to files.
You can accomplish this with the `>` character, as so:

```console
hacker@dojo:~$ echo hi > asdf


This will redirect the output of `echo hi` (which will be `hi`) to the file 
`asdf`.
You can then use a program such as `cat` to output this file:

console
hacker@dojo:~$ cat asdf
hi


In this challenge, you must use this input redirection to write the word `PWN` 
(all uppercase) to the filename `COLLEGE` (all uppercase).
hacker@piping~redirecting-output:/challenge$ echo PWN > COLLEGE
ssh-entrypoint: COLLEGE: Permission denied
hacker@piping~redirecting-output:/challenge$ cd ..
hacker@piping~redirecting-output:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@piping~redirecting-output:/$ ./flag
ssh-entrypoint: ./flag: Permission denied
hacker@piping~redirecting-output:/$ cat flag
cat: flag: Permission denied
hacker@piping~redirecting-output:/$ echo PWN > COLLEGE
ssh-entrypoint: COLLEGE: Permission denied
hacker@piping~redirecting-output:/$ cd challenge
hacker@piping~redirecting-output:/challenge$ echo PWN > COLLEGE
ssh-entrypoint: COLLEGE: Permission denied
hacker@piping~redirecting-output:/challenge$ touch COLLEGE
touch: cannot touch 'COLLEGE': Permission denied
hacker@piping~redirecting-output:/challenge$ cd
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{MeAtubN7QKE5aaYZVo6ehJB8lS0.dRjN1QDLyUTN0czW}
```
## What I learnt
I learnt that I can only make changes in my home directory and not in the root directory.

# F.2 Redirecting more output 
## Question
Aside from redirecting the output of echo, you can, of course, redirect the output of any command. In this level, /challenge/run will once more give you a flag, but only if you redirect its output to the file myflag. Your flag will, of course, end up in the myflag file!

You'll notice that /challenge/run will still happily print to your terminal, despite you redirecting stdout. That's because it communicates its instructions and feedback over standard error, and only prints the flag over standard out!
## Code
```
hacker@piping~redirecting-more-output:~$ /challenge/run
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[FAIL] You did not satisfy all the execution requirements.
[FAIL] Specifically, you must fix the following issue:
[FAIL]   You have not redirected anything for this process' stdout.
hacker@piping~redirecting-more-output:~$ ls /challenge
DESCRIPTION.md  chio.py  run
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ /challenge/flag
ssh-entrypoint: /challenge/flag: No such file or directory
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{sR-AySoZV5EXh1gl5NhT0Amv4O5.dVjN1QDLyUTN0czW}
```
## What I learnt
Nothing.

# F.3 Appending output
## Question
A common use-case of output redirection is to save off some command results for later analysis. Often times, you want to do this in aggregate: run a bunch of commands, save their output, and grep through it later. In this case, you might want all that output to keep appending to the same file, but > will create a new output file every time, deleting the old contents.

You can redirect input in append mode using >> instead of >, as so:

hacker@dojo:~$ echo pwn > outfile
hacker@dojo:~$ echo college >> outfile
hacker@dojo:~$ cat outfile
pwn
college
hacker@dojo:$
To practice, run /challenge/run with an append-mode redirect of the output to the file /home/hacker/the-flag. The practice will write the first half of the flag to the file, and the second half to stdout if stdout is redirected to the file. If you properly redirect in append-mode, the second half will be appended to the first, but if you redirect in truncation mode (>), the second half will overwrite the first and you won't get the flag!

Go for it now!
## Code
```
hacker@piping~appending-output:~$ touch the-flag
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!
hacker@piping~appending-output:~$ cat the-flag
 | 
\|/ This is the first half:
 v 
pwn.college{o-dB0IK-MHqedO_O-JVCmLdnln_.ddDM5QDLyUTN0czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
```
## What I learnt
I learnt how to append. 

# F.4 Redirecting errors
## Question
Just like standard output, you can also redirect the error channel of commands. Here, we'll learn about File Descriptor numbers. A File Descriptor (FD) is a number the describes a communication channel in Linux. You've already been using them, even though you didn't realize it. We're already familiar with three:

FD 0: Standard Input
FD 1: Standard Output
FD 2: Standard Error
When you redirect process communication, you do it by FD number, though some FD numbers are implicit. For example, a > without a number implies 1>, which redirects FD 1 (Standard Output). Thus, the following two commands are equivalent:

hacker@dojo:~$ echo hi > asdf
hacker@dojo:~$ echo hi 1> asdf
Redirecting errors is pretty easy from this point. If you have a command that might produce data via standard error (such as /challenge/run), you can do:

hacker@dojo:~$ /challenge/run 2> errors.log
That will redirect standard error (FD 2) to the errors.log file. Furthermore, you can redirect multiple file descriptors at the same time! For example:

hacker@dojo:~$ some_command > output.log 2> errors.log
That command will redirect output to output.log and errors to errors.log.

Let's put this into practice! In this challenge, you will need to redirect the output of /challenge/run, like before, to myflag, and the "errors" (in our case, the instructions) to instructions. You'll notice that nothing will be printed to the terminal, because you have redirected everything! You can find the instructions/feedback in instructions and the flag in myflag when you successfully pull this off!
## Code
```
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{kcoCI4yIBtng7IJsiPYizzF7p2h.ddjN1QDLyUTN0czW}
```
## What I learnt
Nothing.

# F.5 Redirecting input
## Question
Just like you can redirect output from programs, you can redirect input to programs! This is done using <, as so:

hacker@dojo:~$ echo yo > message
hacker@dojo:~$ cat message
yo
hacker@dojo:~$ rev < message
oy
You can do interesting things with a lot of different programs using input redirection! In this level, we will practice using /challenge/run, which will require you to redirect the PWN file to it and have the PWN file contain the value COLLEGE! To write that value to the PWN file, recall the prior challenge on output redirection from echo!
## Code
```
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ challenge/run < pwn
ssh-entrypoint: pwn: No such file or directory
hacker@piping~redirecting-input:~$ challenge/run < PWN
ssh-entrypoint: challenge/run: No such file or directory
hacker@piping~redirecting-input:~$ ls
COLLEGE  Desktop  PWN  hi  instructions  myflag  not-the-flag  the-flag
hacker@piping~redirecting-input:~$ challenge/run < /~/PWN
ssh-entrypoint: /~/PWN: No such file or directory
hacker@piping~redirecting-input:~$ challenge/run < ~/PWN
ssh-entrypoint: challenge/run: No such file or directory
hacker@piping~redirecting-input:~$ /challenge/run < ~/PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{cGxGYc8XwLjgGyh8orxPbAdhgCe.dBzN1QDLyUTN0czW}
```
## What I learnt
The mistakes I made here are embarassing. 

# F.6 Grepping stored results
## Question
You know how to run commands, how to redirect their output (e.g., >), and how to search through the resulting file (e.g., grep). Let's put this together!

In preparation for more complex levels, we want you to:

Redirect the output of /challenge/run to /tmp/data.txt.
This will result in a hundred thousand lines of text, with one of them being the flag, in /tmp/data.txt.
Grep that for the flag!
## Code
```
hacker@piping~grepping-stored-results:~$ /challenge/run >  /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ greap flag  /tmp/data.txt
ssh-entrypoint: greap: command not found
hacker@piping~grepping-stored-results:~$ grep flag  /tmp/data.txt
[FLAG] Here is your flag:
flagstone
flagship's
camouflage's
flagellums
flagrantly
flagella
flagships
flagging
flagstaff's
flagellation's
flags
flag
flagstone's
flagellated
camouflage
flagship
persiflage
flagellation
flagrant
flag's
flagged
flagellum's
flagons
flagon
flagstaffs
flagellating
persiflage's
flagellum
flagon's
flagpole
conflagration
flagpole's
conflagration's
flagstones
flagstaff
unflagging
conflagrations
flagellate
flagpoles
flagellates
camouflaging
camouflages
camouflaged
hacker@piping~grepping-stored-results:~$ grep pwn.college  /tmp/data.txt
pwn.college{QeqtYkzkitijDNQeG9vmrltK2kf.dhTM4QDLyUTN0czW}
```
## What I learnt
Nothing.

# F.7 Grepping live output
## Question
It turns out that you can "cut out the middleman" and avoid the need to store results to a file, like you did in the last level. You can use this using the | (pipe) operator. Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the command to the right of the pipe. For example:

hacker@dojo:~$ echo no-no | grep yes
hacker@dojo:~$ echo yes-yes | grep yes
yes-yes
hacker@dojo:~$ echo yes-yes | grep no
hacker@dojo:~$ echo no-no | grep no
no-no
Now try it for yourself! /challenge/run will output a hundred thousand lines of text, including the flag. Grep for the flag!
## Code
```
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{IlZiicMD5Wisa1GCm80L2tAL9AF.dlTM4QDLyUTN0czW}
```
## What I learnt
Nothing.

# F.8 Grepping errors
## Question
You know how to redirect errors to a file, and you know how to pipe output to another program, such as grep. But what if you wanted to grep through errors directly?

The > operator redirects a given file descriptor to a file, and you've used 2> to redirect fd 2, which is standard error. The | operator redirects only standard output to another program, and there is no 2| form of the operator! It can only redirect standard output (file descriptor 1).

Luckily, where there's a shell, there's a way!

The shell has a >& operator, which redirects a file descriptor to another file descriptor. This means that we can have a two-step process to grep through errors: first, we redirect standard error to standard output (2>& 1) and then pipe the now-combined stderr and stdout as normal (|)!

Try it now! Like the last level, this level will overwhelm you with output, but this time on standard error. Grep through it to find the flag!
## Code
```
hacker@piping~grepping-errors:~$ /challenge/run 
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...

[FAIL] You did not satisfy all the execution requirements.
[FAIL] Specifically, you must fix the following issue:
[FAIL]   stderr of this process does not appear to be a pipe!
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{A-lyvbItDGbjVMnyc4O3nuuHf1d.dVDM5QDLyUTN0czW}
```
## What I learnt
Here, we convert standard error to standard output using 2>&1. This is necessary to read through it meaningfully. 

# F.9 Duplicated piped data with tee
## Question
When you pipe data from one command to another, you of course no longer see it on your screen. This is not always desired: for example, you might want to see the data as it flows through between your commands to debug unintended outcomes (e.g., "why did that second command not work???").

Luckily, there is a solution! The tee command, named after a "T-splitter" from plumbing pipes, duplicates data flowing through your pipes to any number of files provided on the command line. For example:

hacker@dojo:~$ echo hi | tee pwn college
hi
hacker@dojo:~$ cat pwn
hi
hacker@dojo:~$ cat college
hi
hacker@dojo:~$
As you can see, by providing two files to tee, we ended up with three copies of the piped-in data: one to stdout, one to the pwn file, and one to the college file. You can imagine how you might use this to debug things going haywire:
hacker@dojo:~$ command_1 | command_2
Command 2 failed!
hacker@dojo:~$ command_1 | tee cmd1_output | command_2
Command 2 failed!
hacker@dojo:~$ cat cmd1_output
Command 1 failed: must pass --succeed!
hacker@dojo:~$ command_1 --succeed | command_2
Commands succeeded!
Now, you try it! This process' /challenge/pwn must be piped into /challenge/college, but you'll need to intercept the data to see what pwn needs from you!
## Code
```
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee /challenge/college
Processing...
You are trying to use 'tee' *instead* of /challenge/college. Use it *between* 
/challenge/pwn and /challenge/college!
You must pipe the output of /challenge/pwn into /challenge/college (or 'tee' 
for debugging).
hacker@piping~duplicating-piped-data-with-tee:~$ touch output.txt
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee output.txt | /challenge/college
Processing...
WARNING: you are overwriting file output.txt with tee's output...

The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ 
hacker@piping~duplicating-piped-data-with-tee:~$ cat output.txt
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "oiVHAeZ9"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret oiVHAeZ9 | /challenge/college 
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{oiVHAeZ9fTIxjzVwHQJdM0M1tnK.dFjM5QDLyUTN0czW}
```
## What I learnt
Here, I got the output stored in a separate txt file, through which I realised what the correct argument was, using which I got the flag.

# F.10 Writing to multiple programs 
## Question
Okay, so you can duplicate data to two files with tee:

hacker@dojo:~$ echo HACK | tee THE > PLANET
hacker@dojo:~$ cat THE
HACK
hacker@dojo:~$ cat PLANET
HACK
hacker@dojo:~$
And you've used tee to duplicate data to a file and a command:

hacker@dojo:~$ echo HACK | tee THE | cat
HACK
hacker@dojo:~$ cat THE
HACK
hacker@dojo:~$
But what about duplicating to two commands? As tee says in its manpage, it's designed to write to files and to standard output:

TEE(1)                           User Commands                          TEE(1)

NAME
       tee - read from standard input and write to standard output and files
Luckily, Linux follows the philosophy that "everything is a file". This is, the system strives to provide file-like access to most resources, including the input and output of running programs! The shell follows this philosophy, allowing you to, for example, use any utility that takes file arguments on the command line (such as tee) and hook it up to the input or output side of a program!

This is done using what's called Process Substitution. If you write an argument of >(rev), bash will run the rev command (this command reads data from standard input, reverses its order, and writes it to standard output!), but hook up its input to a temporary file that it will create. This isn't a real file, of course, it's what's called a named pipe, in that it has a file name:

hacker@dojo:~$ echo >(rev)
/dev/fd/63
hacker@dojo:~$
Where did /dev/fd/63 come from? bash replaced >(rev) with the path of the named pipe file that's hooked up to rev's input! While the command is running, writing to this file will pipe data to the standard input of the command. Typically, this is done using commands that take output files as arguments (like tee):

hacker@dojo:~$ echo HACK | rev
KCAH
hacker@dojo:~$ echo HACK | tee >(rev)
HACK
KCAH
Above, the following sequence of events took place:

bash started up the rev command, hooking a named pipe (presumably /dev/fd/63) to rev's standard input
bash started up the tee command, hooking a pipe to its standard input, and replacing the first argument to tee with /dev/fd/63. tee never even saw the argument >(rev); the shell substituted it before launching tee
bash used the echo builtin to print HACK into tee's standard input
tee read HACK, wrote it to standard output, and then wrote it to /dev/fd/63 (which is connected to rev's stdin)
rev read HACK from its standard input, reversed it, and wrote KCAH to standard output
Now it's your turn! In this challenge, we have /challenge/hack, /challenge/the, and /challenge/planet. Run the /challenge/hack command, and duplicate its output as input to both the /challenge/the and the /challenge/planet commands!
## Code
```
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >( /challenge/the ) >( /challenge/planet )
This secret data must directly and simultaneously make it to /challenge/the and 
/challenge/planet. Don't try to copy-paste it; it changes too fast.
332431313290312665
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{QFpvtQSndSY_Q9mzRGzhab51m4d.dBDO0UDLyUTN0czW}
hacker@piping~writing-to-multiple-programs:~$
```
## What I learnt
We can't use piping effectively here because it can only send output to one file at a time but we need to send the output to two.

# F.11 Split piping stderr and stdout
## Question 
Now, let's put your knowledge together. You must master the ultimate piping task: redirect stdout to one program and stderr to another.

The challenge here, of course, is that the | operator links the stdout of the left command with the stdin of the right command. Of course, you've used 2>&1 to redirect stderr into stdout and, thus, pipe stderr over, but this then mixes stderr and stdout. How to keep it unmixed?

You will need to combine your knowledge of >(), 2>, and |. How to do it is a task I'll leave to you.

In this challenge, you have:

/challenge/hack: this produces data on stdout and stderr
/challenge/the: you must redirect hack's stderr to this program
/challenge/planet: you must redirect hack's stdout to this program
Go get the flag!
## Code
```
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{gl4OT69Jlev4eVeHawhLFOkIi_m.dFDNwYDLyUTN0czW}
```
## What I learnt
I struggled here as I would only use > once instead of twice and it took me some time to figure it out. One of them is used for redirection and the other one as we are duplicating it to two files at the same time.
