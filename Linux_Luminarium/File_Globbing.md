# E.1 Matching with *
## Question
The first glob we'll learn is *. When it encounters a * character in any argument, the shell will treat it as "wildcard" and try to replace that argument with any files that match the pattern. It's easier to show you than explain:

hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_*
Look: file_a file_b file_c
Of course, though in this case, the glob resulted in multiple arguments, it can just as simply match only one. For example:

hacker@dojo:~$ touch file_a
hacker@dojo:~$ ls
file_a
hacker@dojo:~$ echo Look: file_*
Look: file_a
When zero files are matched, by default, the shell leaves the glob unchanged:

hacker@dojo:~$ touch file_a
hacker@dojo:~$ ls
file_a
hacker@dojo:~$ echo Look: nope_*
Look: nope_*
The * matches any part of the filename except for / or a leading . character. For example:

hacker@dojo:~$ echo ONE: /ho*/*ck*
ONE: /home/hacker
hacker@dojo:~$ echo TWO: /*/hacker
TWO: /home/hacker
hacker@dojo:~$ echo THREE: ../*
THREE: ../hacker
Now, practice this yourself! Starting from your home directory, change your directory to /challenge, but use globbing to keep the argument you pass to cd to at most four characters! Once you're there, run /challenge/run for the flag!
## Code
```
Connected!                                                                        
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /challende 
You specified the path to 'cd' to in more than 4 characters. Disallowed!
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /challenge
You specified the path to 'cd' to in more than 4 characters. Disallowed!
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{YNZdPDryQvJUWj1Zl2WpK27bFf2.dFjM4QDLyUTN0czW}
hacker@globbing~matching-with-:/challenge$ 
```
## What I learnt
Here, I learnt that * is used to take the space of an undefined amount of characters. For example ch* doesn't mean that it only contains 3 characters. In the home directory, only challenge directory started with ch so I used ch* to enter it.

# E.2 Matching with ?
## Question
Next, let's learn about ?. When it encounters a ? character in any argument, the shell will treat it as single-character wildcard. This works like *, but only matches one character. For example:

hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_cc
hacker@dojo:~$ ls
file_a	file_b	file_cc
hacker@dojo:~$ echo Look: file_?
Look: file_a file_b
hacker@dojo:~$ echo Look: file_??
Look: file_cc
Now, practice this yourself! Starting from your home directory, change your directory to /challenge, but use the ? character instead of c and l in the argument to cd! Once you're there, run /challenge/run for the flag!
## Code
```
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{UplT1HRJd8nCm37ZC5BnIp7rihn.dJjM4QDLyUTN0czW}
hacker@globbing~matching-with-:/challenge$ 
```
## What I learnt
Its similar to * but ? is only used to take the place of one character instead of an undefined number of characters.

# E.3 Matching with []
## Question
Next, we will cover []. The square brackes are, essentially, a limited form of ?, in that instead of matching any character, [] is a wildcard for some subset of potential characters, specified within the brackets. For example, [pwn] will match the character p, w, or n. For example:

hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_[ab]
Look: file_a file_b
Try it here! We've placed a bunch of files in /challenge/files. Change your working directory to /challenge/files and run /challenge/run with a single argument that bracket-globs into file_b, file_a, file_s, and file_h!
## Code
```
Connected!                                                                        
hacker@globbing~matching-with-:~$ ls
Desktop  hi  not-the-flag
hacker@globbing~matching-with-:~$ pwd
/home/hacker
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ ls
file_a  file_b  file_c  file_d  file_e  file_f  file_g  file_h  file_i  file_j  file_k  file_l  file_m  file_n  file_o  file_p  file_q  file_r  file_s  file_t  file_u  file_v  file_w  file_x  file_y  file_z
hacker@globbing~matching-with-:/challenge/files$ /challenge/run --file_[absh]
Your expansion did not expand to the requested files (file_a, file_b, file_h, 
and file_s). Instead, it expanded to:
--file_[absh]
hacker@globbing~matching-with-:/challenge/files$ /challenge/run --/challenge/files/file_[absh]
Your expansion did not expand to the requested files (file_a, file_b, file_h, 
and file_s). Instead, it expanded to:
--/challenge/files/file_[absh]
hacker@globbing~matching-with-:/challenge/files$ /challenge/run /challenge/files/file_[absh]
Your expansion did not expand to the requested files (file_a, file_b, file_h, 
and file_s). Instead, it expanded to:
/challenge/files/file_a /challenge/files/file_b /challenge/files/file_h /challenge/files/file_s
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[absh]
You got it! Here is your flag!
pwn.college{oBp68j7oY10N_W1F7Psqj_osN_C.dNjM4QDLyUTN0czW}
```
## What I learnt  
Inside [], we enter the characters which can be present in the unknown or unspecified character.

# E.4 Matching paths with []
## Question
Globbing happens on a path basis, so you can expand entire paths with your globbed arguments. For example:

hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: /home/hacker/file_[ab]
Look: /home/hacker/file_a /home/hacker/file_b
Now it's your turn. Once more, we've placed a bunch of files in /challenge/files. Starting from your home directory, run /challenge/run with a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h files!
## Code
```
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{Qoje4HFnx3LMH7fOs_nJLHRmk6U.dRjM4QDLyUTN0czW}
```
## What I learnt
Nothing. 

# E.5 Mixing globs
## Question
Now, let's put the previous levels together! We put a few happy, but diversely-named files in /challenge/files. Go cd there and, using the globbing you've learned, write a single, short (6 characters or less) glob that will match the files "challenging", "educational", and "pwning"!
## Code
```
hacker@globbing~mixing-globs:~$ cd /challenge
hacker@globbing~mixing-globs:/challenge$ ls
DESCRIPTION.md  files  run
hacker@globbing~mixing-globs:/challenge$ /challenge/run [cep]*
Error: please run with a working directory of /challenge/files!
hacker@globbing~mixing-globs:/challenge$ /challenge/run /challenge/files/[cep]*
Error: please run with a working directory of /challenge/files!
hacker@globbing~mixing-globs:/challenge$ cd files
hacker@globbing~mixing-globs:/challenge/files$ ls
amazing    challenging  educational  great  incredible  kind      magical  optimistic  queenly  splendid   uplifting   wonderful  youthful
beautiful  delightful   fantastic    happy  jovial      laughing  nice     pwning      radiant  thrilling  victorious  xenial     zesty
hacker@globbing~mixing-globs:/challenge/files$ cd ..
hacker@globbing~mixing-globs:/challenge$ cd files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run ./[cep]*
Error: your argument is too long! It must be 6 characters or less.
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{8MlYZwGAyEkUFdelU3PLJvjSKoM.dVjM4QDLyUTN0czW}
hacker@globbing~mixing-globs:/challenge/files$
```
## What I learnt
The first letters of the file names that we have to match with are non repeating so we can just enter the starting letters in [] and then * ahead it.

# E.6 Exclusionary globbing
## Question
Sometimes, you want to filter out files in a glob! Luckily, [] helps you do just this. If the first character in the brackets is a ! or (in newer versions of bash) a ^, the glob inverts, and that bracket instance matches characters that aren't listed. For example:

hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_[!ab]
Look: file_c
hacker@dojo:~$ echo Look: file_[^ab]
Look: file_c
hacker@dojo:~$ echo Look: file_[ab]
Look: file_a file_b
Armed with this knowledge, go forth to /challenge/files and run /challenge/run with all files that don't start with p, w, or n!

NOTE: The ! character has a different special meaning in bash when it's not the first character of a [] glob, so keep that in mind if things stop making sense! ^ does not have this problem, but is also not compatible with older shells.
## Code
```
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{ctvWVYSiSCNHrRTkmvKXzzMIH_8.dZjM4QDLyUTN0czW}
hacker@globbing~exclusionary-globbing:/challenge/files$
```
## What I learnt
When we use !, we are excluding what we write after that from the cases that match. Therefore, on writing [!pwn]*, we are excluding all files that begin with the letters p, w or n.


