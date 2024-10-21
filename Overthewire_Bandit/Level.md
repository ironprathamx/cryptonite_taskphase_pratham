# Level 0->1
## Question
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.
## Code
```
bandit0@bandit:~$ cat readme
Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

bandit0@bandit:~$ ssh bandit1
ssh: Could not resolve hostname bandit1: Temporary failure in name resolution
bandit0@bandit:~$ ssh bandit1@bandit.labs.overthewire.org -p 2220
The authenticity of host '[bandit.labs.overthewire.org]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit0/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit0/.ssh/known_hosts).
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

!!! You are trying to log into this SSH server with a password on port 2220 from localhost.
!!! Connecting from localhost is blocked to conserve resources.
!!! Please log out and log in again.

bandit1@bandit.labs.overthewire.org: Permission denied (publickey).
bandit0@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
xo@xo ~ % ssh bandit1@bandit.labs.overthewire.org -p 2220

                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

bandit1@bandit.labs.overthewire.org's password: 

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

bandit1@bandit:~$ 
```
## What I learnt
I learnt more about using SSH and joining other servers which wasn't there in the previous course. I tried to login to the new user bandit1 from my old user bandit0 but i had to exit first and then login again. I had to google to learn how to log out of a server.
# Level 1->2
## Question
The password for the next level is stored in a file called - located in the home directory
## Code
```
bandit1@bandit:~$ ls
-
bandit1@bandit:~$ cat -
cat _
cat _
^C
bandit1@bandit:~$ cat _
cat: _: No such file or directory
bandit1@bandit:~$ cat ./-
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```
## What I learnt
First I tried catting it like a normal file but then I realised that this must be a type of exception. In the last course from TP-1, we were taught about relative paths so I catted the file using its path and thus got the password.

# Level 2->3
## Question
The password for the next level is stored in a file called spaces in this filename located in the home directory
## Code
```
bandit2@bandit:~$ ls
spaces in this filename
bandit2@bandit:~$ ls -l
total 4
-rw-r----- 1 bandit3 bandit2 33 Sep 19 07:08 spaces in this filename
bandit2@bandit:~$ cat spaces in this filename
cat: spaces: No such file or directory
cat: in: No such file or directory
cat: this: No such file or directory
cat: filename: No such file or directory
bandit2@bandit:~$ cat "spaces in this filename"
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
bandit2@bandit:~$ 
```
## What I learnt
We can use double quotation to call programs or file names that have spaces in them.

# Level 3->4
## Question
The password for the next level is stored in a hidden file in the inhere directory.
## Code
```
bandit3@bandit:~$ ls -a
.  ..  .bash_logout  .bashrc  inhere  .profile
bandit3@bandit:~$ cat inhere
cat: inhere: Is a directory
bandit3@bandit:~$ cd inhere
bandit3@bandit:~/inhere$ ls -a
.  ..  ...Hiding-From-You
bandit3@bandit:~/inhere$ cat ...Hiding-From-You
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
bandit3@bandit:~/inhere$ 
```
## What I learnt
Nothing. I already knew how to find all the hidden files or directories which are hidden by starting them with a dot.

# Level 4->5
## Question
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.
## Code
```
bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ cd inhere
bandit4@bandit:~/inhere$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
bandit4@bandit:~/inhere$ cat ./-file00
?p??&?y?,?(jo?.at?:uf?^???@bandit4@bandit:~/inhere$ cat ./-file01
i?R?,?Λ?:Y?????%?A????B??ͩ?bandit4@bandit:~/inhere$ cat ./-file02
3?	?)Ʈ?#Y??-6c??IR-?$????:??bandit4@bandit:~/inhere$ cat ./-file03
???/?
     ??????qGi??,?2?Yb?
dbandit4@bandit:~/inhere$ cat ./-file04
ۙ?rOx????h0~ey
??c?~?h?n??G1bandit4@bandit:~/inhere$ cat ./-file05
}???ߓ??ߤ??W>??#lk?d?ܮ??yE??bandit4@bandit:~/inhere$ cat ./-file06
6?0]?\?$?1?%???????o@??b/??bandit4@bandit:~/inhere$ cat ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```
## What I learnt
Nothing.
# Level 5->6
## Question
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable
1033 bytes in size
not executable
## Code
```
bandit5@bandit:~$ cd inhere
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere04  maybehere08  maybehere12  maybehere16
maybehere01  maybehere05  maybehere09  maybehere13  maybehere17
maybehere02  maybehere06  maybehere10  maybehere14  maybehere18
maybehere03  maybehere07  maybehere11  maybehere15  maybehere19
bandit5@bandit:~/inhere$ ls -l
total 80
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere00
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere01
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere02
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere03
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere04
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere05
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere06
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere07
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere08
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere09
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere10
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere11
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere12
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere13
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere14
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere15
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere16
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere17
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere18
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere19
bandit5@bandit:~/inhere$ ls -h
maybehere00  maybehere04  maybehere08  maybehere12  maybehere16
maybehere01  maybehere05  maybehere09  maybehere13  maybehere17
maybehere02  maybehere06  maybehere10  maybehere14  maybehere18
maybehere03  maybehere07  maybehere11  maybehere15  maybehere19
bandit5@bandit:~/inhere$ ls -lh
total 80K
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere00
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere01
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere02
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere03
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere04
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere05
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere06
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere07
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere08
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere09
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere10
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere11
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere12
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere13
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere14
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere15
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere16
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere17
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere18
drwxr-x--- 2 root bandit5 4.0K Sep 19 07:08 maybehere19
bandit5@bandit:~/inhere$ ls -alh
total 88K
drwxr-x--- 22 root bandit5 4.0K Sep 19 07:08 .
drwxr-xr-x  3 root root    4.0K Sep 19 07:08 ..
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere00
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere01
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere02
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere03
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere04
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere05
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere06
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere07
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere08
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere09
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere10
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere11
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere12
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere13
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere14
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere15
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere16
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere17
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere18
drwxr-x---  2 root bandit5 4.0K Sep 19 07:08 maybehere19
bandit5@bandit:~/inhere$ cat maybehere00
cat: maybehere00: Is a directory
bandit5@bandit:~/inhere$ man find
bandit5@bandit:~/inhere$ find -size 1033c -type f
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        bandit5@bandit:~/inhere$ 
```
## What I learnt
At first, I thought that maybehere were files and it took me a few moments to realise that I had to look in files that were inside them. I learnt about the argumens for find. I already knew them from the previous course but I forgot about them since it had been long since I used them but I knew about the man command so I looked it up in its man page.
