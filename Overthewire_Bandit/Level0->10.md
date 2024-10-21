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
```
## What I learnt
At first, I thought that maybehere were files and it took me a few moments to realise that I had to look in files that were inside them. I learnt about the argumens for find. I already knew them from the previous course but I forgot about them since it had been long since I used them but I knew about the man command so I looked it up in its man page.

# Level 6->7
## Question
The password for the next level is stored somewhere on the server and has all of the following properties:

owned by user bandit7
owned by group bandit6
33 bytes in size
## Code
```
bandit6@bandit:~$ ls
bandit6@bandit:~$ ls -a
.  ..  .bash_logout  .bashrc  .profile
bandit6@bandit:~$ cd ..
bandit6@bandit:/home$ cd ..
bandit6@bandit:/$ ls
bin                drifter     krypton  lib.usr-is-merged  mnt   run                 srv  var
bin.usr-is-merged  etc         lib      libx32             opt   sbin                sys
boot               formulaone  lib32    lost+found         proc  sbin.usr-is-merged  tmp
dev                home        lib64    media              root  snap                usr
bandit6@bandit:/$ cd ..
bandit6@bandit:/$ find -type f -size 33c 
find: ‘./drifter/drifter14_src/axTLS’: Permission denied
find: ‘./root’: Permission denied
./usr/src/linux-headers-6.8.0-1014-aws/arch/x86/include/generated/uapi/asm/sockios.h
./usr/src/linux-headers-6.8.0-1014-aws/arch/x86/include/generated/uapi/asm/termios.h
./usr/src/linux-headers-6.8.0-1014-aws/arch/x86/include/generated/asm/local64.h
./usr/src/linux-aws-headers-6.8.0-1014/arch/arm/include/asm/xen/swiotlb-xen.h
./usr/src/linux-aws-headers-6.8.0-1014/arch/arm64/include/asm/xen/swiotlb-xen.h
./usr/lib/tmpfiles.d/man-db.conf
./usr/lib/grub/i386-pc/video.lst
./usr/lib/python3/dist-packages/jeepney/io/__init__.py
./usr/include/x86_64-linux-gnu/asm/sockios.h
./usr/include/x86_64-linux-gnu/asm/termios.h
find: ‘./snap’: Permission denied
find: ‘./tmp’: Permission denied
find: ‘./proc/tty/driver’: Permission denied
find: ‘./proc/2425544/task/2425544/fdinfo/6’: No such file or directory
find: ‘./proc/2425544/fdinfo/5’: No such file or directory
find: ‘./home/bandit31-git’: Permission denied
./home/bandit15/.bandit14.password
./home/bandit18/readme
./home/bandit17/.bandit16.password
find: ‘./home/ubuntu’: Permission denied
./home/bandit1/-
./home/bandit2/spaces in this filename
./home/bandit16/.bandit15.password
./home/bandit4/inhere/-file08
./home/bandit4/inhere/-file02
./home/bandit4/inhere/-file09
./home/bandit4/inhere/-file01
./home/bandit4/inhere/-file00
./home/bandit4/inhere/-file05
./home/bandit4/inhere/-file07
./home/bandit4/inhere/-file03
./home/bandit4/inhere/-file06
./home/bandit4/inhere/-file04
./home/bandit3/inhere/...Hiding-From-You
./home/bandit21/.prevpass
find: ‘./home/bandit5/inhere’: Permission denied
find: ‘./home/bandit30-git’: Permission denied
find: ‘./home/drifter8/chroot’: Permission denied
./home/bandit25/.bandit24.password
find: ‘./home/drifter6/data’: Permission denied
./home/drifter0/chroot/drifter0.password
find: ‘./home/bandit29-git’: Permission denied
find: ‘./home/bandit28-git’: Permission denied
find: ‘./home/bandit27-git’: Permission denied
find: ‘./lost+found’: Permission denied
find: ‘./etc/polkit-1/rules.d’: Permission denied
./etc/formulaone_pass/formulaone2
./etc/formulaone_pass/formulaone1
./etc/formulaone_pass/formulaone0
./etc/formulaone_pass/formulaone6
./etc/formulaone_pass/formulaone5
./etc/formulaone_pass/formulaone3
find: ‘./etc/multipath’: Permission denied
./etc/drifter_pass/drifter14
./etc/drifter_pass/drifter3
./etc/drifter_pass/drifter15
./etc/drifter_pass/drifter13
./etc/drifter_pass/drifter7
./etc/drifter_pass/drifter4
./etc/drifter_pass/drifter5
./etc/drifter_pass/drifter12
./etc/drifter_pass/drifter8
./etc/drifter_pass/drifter2
./etc/drifter_pass/drifter6
./etc/drifter_pass/drifter10
./etc/drifter_pass/drifter0
./etc/drifter_pass/drifter9
./etc/drifter_pass/drifter1
find: ‘./etc/stunnel’: Permission denied
./etc/machine-id
./etc/profile.d/colon.sh
find: ‘./etc/xinetd.d’: Permission denied
find: ‘./etc/credstore.encrypted’: Permission denied
find: ‘./etc/ssl/private’: Permission denied
./etc/bandit_pass/bandit30
./etc/bandit_pass/bandit9
./etc/bandit_pass/bandit12
./etc/bandit_pass/bandit27
./etc/bandit_pass/bandit15
./etc/bandit_pass/bandit22
./etc/bandit_pass/bandit10
./etc/bandit_pass/bandit6
./etc/bandit_pass/bandit29
./etc/bandit_pass/bandit18
./etc/bandit_pass/bandit17
./etc/bandit_pass/bandit26
./etc/bandit_pass/bandit1
./etc/bandit_pass/bandit2
./etc/bandit_pass/bandit16
./etc/bandit_pass/bandit23
./etc/bandit_pass/bandit4
./etc/bandit_pass/bandit19
./etc/bandit_pass/bandit20
./etc/bandit_pass/bandit3
./etc/bandit_pass/bandit32
./etc/bandit_pass/bandit21
./etc/bandit_pass/bandit33
./etc/bandit_pass/bandit7
./etc/bandit_pass/bandit5
./etc/bandit_pass/bandit25
./etc/bandit_pass/bandit11
./etc/bandit_pass/bandit31
./etc/bandit_pass/bandit24
./etc/bandit_pass/bandit13
./etc/bandit_pass/bandit8
./etc/bandit_pass/bandit14
./etc/bandit_pass/bandit28
find: ‘./etc/sudoers.d’: Permission denied
find: ‘./etc/credstore’: Permission denied
find: ‘./dev/shm’: Permission denied
find: ‘./dev/mqueue’: Permission denied
./opt/radare2/libr/arch/p/arm/v35/arch-arm64/.git/refs/remotes/origin/HEAD
./opt/radare2/libr/arch/p/arm/v35/arch-armv7/.git/refs/remotes/origin/HEAD
./opt/radare2/shlr/www/m/css/networkerr.css
./opt/pwndbg/.venv/lib/python3.12/site-packages/jedi/third_party/typeshed/third_party/3/six/moves/tkinter_filedialog.pyi
./opt/pwndbg/.venv/lib/python3.12/site-packages/jedi/third_party/typeshed/third_party/3/six/moves/tkinter_tkfiledialog.pyi
./opt/pwndbg/.venv/lib/python3.12/site-packages/jedi/third_party/typeshed/third_party/3/six/moves/urllib_robotparser.pyi
find: ‘./var/log/amazon’: Permission denied
find: ‘./var/log/unattended-upgrades’: Permission denied
find: ‘./var/log/chrony’: Permission denied
find: ‘./var/log/private’: Permission denied
find: ‘./var/tmp’: Permission denied
find: ‘./var/spool/cron/crontabs’: Permission denied
find: ‘./var/spool/bandit24’: Permission denied
find: ‘./var/spool/rsyslog’: Permission denied
find: ‘./var/cache/ldconfig’: Permission denied
find: ‘./var/cache/apt/archives/partial’: Permission denied
find: ‘./var/cache/pollinate’: Permission denied
find: ‘./var/cache/private’: Permission denied
find: ‘./var/cache/apparmor/2425d902.0’: Permission denied
find: ‘./var/cache/apparmor/baad73a1.0’: Permission denied
find: ‘./var/lib/polkit-1’: Permission denied
find: ‘./var/lib/amazon’: Permission denied
./var/lib/dpkg/info/libip4tc2:amd64.shlibs
./var/lib/dpkg/info/libtasn1-6:amd64.shlibs
./var/lib/dpkg/info/install-info.triggers
./var/lib/dpkg/info/libip6tc2:amd64.shlibs
./var/lib/dpkg/info/login.conffiles
./var/lib/dpkg/info/libatm1t64:amd64.shlibs
./var/lib/dpkg/info/liblerc4:amd64.shlibs
./var/lib/dpkg/info/bandit7.password
./var/lib/dpkg/info/libpython3.12-minimal:amd64.conffiles
./var/lib/dpkg/info/libcurl4t64:amd64.shlibs
./var/lib/dpkg/info/networkd-dispatcher.conffiles
./var/lib/dpkg/info/libfwupd2:amd64.shlibs
find: ‘./var/lib/apt/lists/partial’: Permission denied
find: ‘./var/lib/chrony’: Permission denied
find: ‘./var/lib/snapd/void’: Permission denied
find: ‘./var/lib/snapd/cookie’: Permission denied
find: ‘./var/lib/private’: Permission denied
find: ‘./var/lib/ubuntu-advantage/apt-esm/var/lib/apt/lists/partial’: Permission denied
find: ‘./var/lib/update-notifier/package-data-downloads/partial’: Permission denied
find: ‘./var/lib/udisks2’: Permission denied
find: ‘./var/crash’: Permission denied
find: ‘./boot/efi’: Permission denied
find: ‘./boot/lost+found’: Permission denied
./boot/grub/i386-pc/video.lst
find: ‘./sys/kernel/tracing’: Permission denied
find: ‘./sys/kernel/debug’: Permission denied
find: ‘./sys/fs/pstore’: Permission denied
find: ‘./sys/fs/bpf’: Permission denied
find: ‘./run/lock/lvm’: Permission denied
./run/lock/test/pwn/pass
./run/lock/test/temp/endpasswd.txt
find: ‘./run/systemd/inaccessible/dir’: Permission denied
find: ‘./run/systemd/propagate/systemd-udevd.service’: Permission denied
find: ‘./run/systemd/propagate/systemd-resolved.service’: Permission denied
find: ‘./run/systemd/propagate/systemd-networkd.service’: Permission denied
find: ‘./run/systemd/propagate/irqbalance.service’: Permission denied
find: ‘./run/systemd/propagate/systemd-logind.service’: Permission denied
find: ‘./run/systemd/propagate/chrony.service’: Permission denied
find: ‘./run/systemd/propagate/polkit.service’: Permission denied
find: ‘./run/systemd/propagate/ModemManager.service’: Permission denied
find: ‘./run/systemd/propagate/fwupd.service’: Permission denied
find: ‘./run/systemd/propagate/bolt.service’: Permission denied
find: ‘./run/lvm’: Permission denied
find: ‘./run/log/journal/ec2dd69f90c4a6285216f71caca9bbca’: Permission denied
find: ‘./run/cryptsetup’: Permission denied
find: ‘./run/multipath’: Permission denied
find: ‘./run/screen/S-bandit20’: Permission denied
find: ‘./run/screen/S-bandit27’: Permission denied
find: ‘./run/screen/S-bandit28’: Permission denied
find: ‘./run/screen/S-bandit24’: Permission denied
find: ‘./run/screen/S-bandit17’: Permission denied
find: ‘./run/screen/S-bandit12’: Permission denied
find: ‘./run/screen/S-bandit29’: Permission denied
find: ‘./run/screen/S-bandit23’: Permission denied
find: ‘./run/screen/S-bandit1’: Permission denied
find: ‘./run/screen/S-bandit31’: Permission denied
find: ‘./run/screen/S-bandit21’: Permission denied
find: ‘./run/screen/S-bandit22’: Permission denied
find: ‘./run/screen/S-bandit19’: Permission denied
find: ‘./run/screen/S-bandit30’: Permission denied
find: ‘./run/screen/S-bandit33’: Permission denied
find: ‘./run/screen/S-bandit25’: Permission denied
find: ‘./run/screen/S-bandit16’: Permission denied
find: ‘./run/screen/S-bandit0’: Permission denied
find: ‘./run/screen/S-bandit2’: Permission denied
find: ‘./run/sudo’: Permission denied
find: ‘./run/user/11001’: Permission denied
find: ‘./run/user/11013’: Permission denied
find: ‘./run/user/11023’: Permission denied
find: ‘./run/user/11016’: Permission denied
find: ‘./run/user/11028’: Permission denied
find: ‘./run/user/11024’: Permission denied
find: ‘./run/user/11027’: Permission denied
find: ‘./run/user/11015’: Permission denied
find: ‘./run/user/11003’: Permission denied
find: ‘./run/user/11020’: Permission denied
find: ‘./run/user/11032’: Permission denied
find: ‘./run/user/11025’: Permission denied
find: ‘./run/user/11026’: Permission denied
find: ‘./run/user/11014’: Permission denied
find: ‘./run/user/11021’: Permission denied
find: ‘./run/user/11022’: Permission denied
find: ‘./run/user/11004’: Permission denied
find: ‘./run/user/11000’: Permission denied
find: ‘./run/user/11006/systemd/inaccessible/dir’: Permission denied
find: ‘./run/user/11012’: Permission denied
find: ‘./run/user/11005’: Permission denied
find: ‘./run/user/11011’: Permission denied
find: ‘./run/user/11002’: Permission denied
find: ‘./run/user/11008’: Permission denied
find: ‘./run/user/11009’: Permission denied
find: ‘./run/user/11017’: Permission denied
find: ‘./run/user/11007’: Permission denied
find: ‘./run/user/11031’: Permission denied
find: ‘./run/user/11019’: Permission denied
find: ‘./run/user/11030’: Permission denied
find: ‘./run/user/8001’: Permission denied
find: ‘./run/user/8003’: Permission denied
find: ‘./run/user/11010’: Permission denied
find: ‘./run/user/11033’: Permission denied
find: ‘./run/user/8002’: Permission denied
find: ‘./run/user/8006’: Permission denied
find: ‘./run/chrony’: Permission denied
find: ‘./run/udisks2’: Permission denied
bandit6@bandit:/$ find  -user bandit7 -group bandit6 -size 33c 
find: ‘./drifter/drifter14_src/axTLS’: Permission denied
find: ‘./root’: Permission denied
find: ‘./snap’: Permission denied
find: ‘./tmp’: Permission denied
find: ‘./proc/tty/driver’: Permission denied
find: ‘./proc/2431057/task/2431057/fd/6’: No such file or directory
find: ‘./proc/2431057/task/2431057/fdinfo/6’: No such file or directory
find: ‘./proc/2431057/fd/5’: No such file or directory
find: ‘./proc/2431057/fdinfo/5’: No such file or directory
find: ‘./home/bandit31-git’: Permission denied
find: ‘./home/ubuntu’: Permission denied
find: ‘./home/bandit5/inhere’: Permission denied
find: ‘./home/bandit30-git’: Permission denied
find: ‘./home/drifter8/chroot’: Permission denied
find: ‘./home/drifter6/data’: Permission denied
find: ‘./home/bandit29-git’: Permission denied
find: ‘./home/bandit28-git’: Permission denied
find: ‘./home/bandit27-git’: Permission denied
find: ‘./lost+found’: Permission denied
find: ‘./etc/polkit-1/rules.d’: Permission denied
find: ‘./etc/multipath’: Permission denied
find: ‘./etc/stunnel’: Permission denied
find: ‘./etc/xinetd.d’: Permission denied
find: ‘./etc/credstore.encrypted’: Permission denied
find: ‘./etc/ssl/private’: Permission denied
find: ‘./etc/sudoers.d’: Permission denied
find: ‘./etc/credstore’: Permission denied
find: ‘./dev/shm’: Permission denied
find: ‘./dev/mqueue’: Permission denied
find: ‘./var/log/amazon’: Permission denied
find: ‘./var/log/unattended-upgrades’: Permission denied
find: ‘./var/log/chrony’: Permission denied
find: ‘./var/log/private’: Permission denied
find: ‘./var/tmp’: Permission denied
find: ‘./var/spool/cron/crontabs’: Permission denied
find: ‘./var/spool/bandit24’: Permission denied
find: ‘./var/spool/rsyslog’: Permission denied
find: ‘./var/cache/ldconfig’: Permission denied
find: ‘./var/cache/apt/archives/partial’: Permission denied
find: ‘./var/cache/pollinate’: Permission denied
find: ‘./var/cache/private’: Permission denied
find: ‘./var/cache/apparmor/2425d902.0’: Permission denied
find: ‘./var/cache/apparmor/baad73a1.0’: Permission denied
find: ‘./var/lib/polkit-1’: Permission denied
find: ‘./var/lib/amazon’: Permission denied
./var/lib/dpkg/info/bandit7.password
find: ‘./var/lib/apt/lists/partial’: Permission denied
find: ‘./var/lib/chrony’: Permission denied
find: ‘./var/lib/snapd/void’: Permission denied
find: ‘./var/lib/snapd/cookie’: Permission denied
find: ‘./var/lib/private’: Permission denied
find: ‘./var/lib/ubuntu-advantage/apt-esm/var/lib/apt/lists/partial’: Permission denied
find: ‘./var/lib/update-notifier/package-data-downloads/partial’: Permission denied
find: ‘./var/lib/udisks2’: Permission denied
find: ‘./var/crash’: Permission denied
find: ‘./boot/efi’: Permission denied
find: ‘./boot/lost+found’: Permission denied
find: ‘./sys/kernel/tracing’: Permission denied
find: ‘./sys/kernel/debug’: Permission denied
find: ‘./sys/fs/pstore’: Permission denied
find: ‘./sys/fs/bpf’: Permission denied
find: ‘./run/lock/lvm’: Permission denied
find: ‘./run/systemd/inaccessible/dir’: Permission denied
find: ‘./run/systemd/propagate/systemd-udevd.service’: Permission denied
find: ‘./run/systemd/propagate/systemd-resolved.service’: Permission denied
find: ‘./run/systemd/propagate/systemd-networkd.service’: Permission denied
find: ‘./run/systemd/propagate/irqbalance.service’: Permission denied
find: ‘./run/systemd/propagate/systemd-logind.service’: Permission denied
find: ‘./run/systemd/propagate/chrony.service’: Permission denied
find: ‘./run/systemd/propagate/polkit.service’: Permission denied
find: ‘./run/systemd/propagate/ModemManager.service’: Permission denied
find: ‘./run/systemd/propagate/fwupd.service’: Permission denied
find: ‘./run/systemd/propagate/bolt.service’: Permission denied
find: ‘./run/lvm’: Permission denied
find: ‘./run/log/journal/ec2dd69f90c4a6285216f71caca9bbca’: Permission denied
find: ‘./run/cryptsetup’: Permission denied
find: ‘./run/multipath’: Permission denied
find: ‘./run/screen/S-bandit20’: Permission denied
find: ‘./run/screen/S-bandit27’: Permission denied
find: ‘./run/screen/S-bandit28’: Permission denied
find: ‘./run/screen/S-bandit24’: Permission denied
find: ‘./run/screen/S-bandit17’: Permission denied
find: ‘./run/screen/S-bandit12’: Permission denied
find: ‘./run/screen/S-bandit29’: Permission denied
find: ‘./run/screen/S-bandit23’: Permission denied
find: ‘./run/screen/S-bandit1’: Permission denied
find: ‘./run/screen/S-bandit31’: Permission denied
find: ‘./run/screen/S-bandit21’: Permission denied
find: ‘./run/screen/S-bandit22’: Permission denied
find: ‘./run/screen/S-bandit19’: Permission denied
find: ‘./run/screen/S-bandit30’: Permission denied
find: ‘./run/screen/S-bandit33’: Permission denied
find: ‘./run/screen/S-bandit25’: Permission denied
find: ‘./run/screen/S-bandit16’: Permission denied
find: ‘./run/screen/S-bandit0’: Permission denied
find: ‘./run/screen/S-bandit2’: Permission denied
find: ‘./run/sudo’: Permission denied
find: ‘./run/user/11001’: Permission denied
find: ‘./run/user/11013’: Permission denied
find: ‘./run/user/11023’: Permission denied
find: ‘./run/user/11016’: Permission denied
find: ‘./run/user/11028’: Permission denied
find: ‘./run/user/11024’: Permission denied
find: ‘./run/user/11027’: Permission denied
find: ‘./run/user/11015’: Permission denied
find: ‘./run/user/11003’: Permission denied
find: ‘./run/user/11020’: Permission denied
find: ‘./run/user/11032’: Permission denied
find: ‘./run/user/11025’: Permission denied
find: ‘./run/user/11026’: Permission denied
find: ‘./run/user/11014’: Permission denied
find: ‘./run/user/11021’: Permission denied
find: ‘./run/user/11022’: Permission denied
find: ‘./run/user/11004’: Permission denied
find: ‘./run/user/11000’: Permission denied
find: ‘./run/user/11006/systemd/inaccessible/dir’: Permission denied
find: ‘./run/user/11012’: Permission denied
find: ‘./run/user/11005’: Permission denied
find: ‘./run/user/11011’: Permission denied
find: ‘./run/user/11002’: Permission denied
find: ‘./run/user/11008’: Permission denied
find: ‘./run/user/11009’: Permission denied
find: ‘./run/user/11017’: Permission denied
find: ‘./run/user/11007’: Permission denied
find: ‘./run/user/11031’: Permission denied
find: ‘./run/user/11019’: Permission denied
find: ‘./run/user/11030’: Permission denied
find: ‘./run/user/8001’: Permission denied
find: ‘./run/user/8003’: Permission denied
find: ‘./run/user/11010’: Permission denied
find: ‘./run/user/11033’: Permission denied
find: ‘./run/user/8002’: Permission denied
find: ‘./run/user/8006’: Permission denied
find: ‘./run/chrony’: Permission denied
find: ‘./run/udisks2’: Permission denied
bandit6@bandit:/$ cat ./var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```
## What I learnt
THe permission denied thing is really annoying as most of the options were that so after solving it, I googled and found out that doing '2>/dev/null' removed many of them. Other than that, I learnt about two new arguments for find command.

# Level 7->8
## Question 
The password for the next level is stored in the file data.txt next to the word millionth
## Code
```
bandit7@bandit:~$ ls
data.txt
bandit7@bandit:~$ grep millionth data.txt
millionth	dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```
## What I learnt
Nothing.

# Level 8->9
## Question
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

## Code
```
bandit8@bandit:~$ ls
data.txt
bandit8@bandit:~$ man sort
bandit8@bandit:~$ sort data.txt
(i removed the data here) 
bandit8@bandit:~$ 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM: command not found
bandit8@bandit:~$ sort data.txt | uniq -u
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```
## What I learnt
I learnt about sort and uniq commands. I kind of found the password by manually going through the file tho I mean I didn't do it on purpose I just stumpled across it but then I googled about uniq as it was a command mentioned in the website and uniq is close to unique so then I used it. I already know how to pipe so this was pretty easy.

# Level 9->10
## Question
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

## Code
```
bandit9@bandit:~$ grep -o '==' data.txt
grep: data.txt: binary file matches
bandit9@bandit:~$ ls
data.txt
bandit9@bandit:~$ man strings
bandit9@bandit:~$ 
bandit9@bandit:~$ cat data.txt
??%?P??????A???#=??C??LMS6v??pL?d?M
(a lot more of this nonsense)
k?7iL?????62h?O?O????錶5?Cbandit9@bandit:~$ strings data.txt
h!]v
r>)1
v0i)b 
B:PyZ
#0/u
dyaE
F#X[
7$'0'T
^^^K
Y5}|
9g_$
^h#%EG
	Fq/
/OZ[4'
D#?P
POl%
}========== the
db*Nz
cc5M
`oaT
E:zr0
!S:%_
yG@q-
-c5N
xHp\
wS>n
^B~9
Q!vw
'5jl
. \,
66exg
h^Ad
,`Cd80
UB;N
U@j?
p\l=
te24
UNvlE
U%^6
JB]H:|v
|M '
{QMrWv
8:%	XD
H"hU
/uP_
(mhY
+6,hH
4vjm4
q09B
^8NSs
2>X)
Y>v4
lKUO
U>QkM:,V
imZ?L
>^?X
;c<Q=.dEXU!
j!ZL
jX09
5bBK
4Rl_7gH
F 4Cq
#61QW
hqI.X
3JprD========== passwordi
7`4(WG
& `T
_eOdY
G>Wu}
o|)s
z_b^
HCg\@0
z8N_-Z`
v7\y
s>|5
!$L&
Qm1U
JH|)
qi{|p
Yy6]
BWu7
qC(=	
"t<2-u
i)W5
Czmnf&v
TO"'
~fDV3========== is
R<+{
)DtZ
)>tgdu
FvkY
Z)w,
|:H5
I;j@
0V[1
d_hnA;
oH`w
7=oc
_N]d
3>\kGG
drfx
}UQB
uP6{
hu%lLj
F>x!&
[^?_
M<ls%
"kz8I
zP=	
6o+u
piUv
a*xX$
%!~D
xfvO
Oq.g
(p^A
-45c
^w#K
FP&!
ba+D
n.i3m
GMKB
#s}t
K>]`c
sn)>
v8jB
"x|L
}ZIg
r~rB
+_38
Z@bj:
~de=
.sjd
	qT\
>T`q
Ylyg<
t1QAk
@99F
oxGz$W~"
9+`1
_$>S
J]epm
pfT8
I`8l
fL'~_
a	Z	
DT[N
z9wo
5Gfy
"}@>bn
O(k$N
zw[@
!a5^
9Z8]
sqEAj
D)A'r
an	g
'3pp(
s(-Qv
3k=fQ
usTR
Nyz3wI
+)&_i
WDp8
u"o~
p(67
WZ+(
?o&g
k	 `
~o=0
6+$N
:'3z
uJw&
&kIIJ
b4glu
]NJR
 %uW
|r_s
zVw-
Q$QBW
Q{h%w
69}=
?uPsH
@WG|
%"=Y
Pew%J
&3[2
*u;(%P
dA`d
|>,p
oY%\
3W`j
D+io?
=tZ~07
^6Og
Tx+X
rs2J
 -M8<
Dq^B
Qv"Y
fk)B
g+;Y
 Uum
D9========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
u1Ebi
&x(>G
.`EQ
w>}x
D%(f
1#4!9
:79(
m!}B
| Zd
qQ>Gu
!6D(
J?,2
IEO*
uu>@	;
KrQ!
$V8a
{vl0pup
AWwyxY
j(ue
X<'j
<HR]/
7!`tcT7
Gp(2
FoOvx
hF|W
3edvE%
_#@k
N=~[!N
-VSe
a0XJ
3;8_
zA=?0j
b}M>s
%Xi-
Qobt
6Cjk
H`U	^
+v J
4(clh~U
#R^g
Xgz|
)oRj
bandit9@bandit:~$ FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```
## What I learnt
strings command prints out the human readable parts of a file and although I could have piped it and used grep, I kind of again just found it manually and it was pretty much sticking out from the rest of the data. 



