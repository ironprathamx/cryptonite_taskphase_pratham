# C.1 cat: not the pet, but the command!
## Questions
One of the most critical Linux commands is cat. cat is most often used for reading out files, like so:

hacker@dojo:~$ cat /challenge/DESCRIPTION.md
One of the most critical Linux commands is `cat`.
`cat` is most often used for reading out files, like so:
cat will concatenate (hence the name) multiple files if provided multiple arguments. For example:

hacker@dojo:~$ cat myfile
This is my file!
hacker@dojo:~$ cat yourfile
This is your file!
hacker@dojo:~$ cat myfile yourfile
This is my file!
This is your file!
hacker@dojo:~$ cat myfile yourfile myfile
This is my file!
This is your file!
This is my file!
Finally, if you give no arguments at all, cat will read from the terminal input and output it. We'll explore that in later challenges...

In this challenge, I will copy the flag to the flag file in your home directory (where your shell starts). Go read it with cat!
## Code
```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{Yr8DTMOyzau6QjWiDAe9wbaKmJr.dFzN1QDLyUTN0czW}
hacker@commands~cat-not-the-pet-but-the-command:~$
```
## What I learnt
Nothing
# C.2 catting absolute paths
## Questions
In the last level, you did cat flag to read the flag out of your home directory! You can, of course, specify cat's arguments as absolute paths:

hacker@dojo:~$ cat /challenge/DESCRIPTION.md
In the last level, you did `cat flag` to read the flag out of your home directory!
You can, of course, specify `cat`'s arguments as absolute paths:
...
In this directory, I will not copy it to your home directory, but I will make it readable. You can read it with cat at its absolute path: /flag.

FUN FACT: /flag is where the flag always lives in pwn.college, but unlike in this challenge, you typically can't access that file directly.
## Code
```
Connected!                                                                        
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{clASMTEoe5ilLWMyVBV454_zZN9.dlTM5QDLyUTN0czW}
hacker@commands~catting-absolute-paths:~$ 
```
## What I learnt
Nothing

# C.3 more catting practice 
## Questions 
You can specify all sorts of paths as arguments to commands, and we'll practice some more with cat. In this level, I'll put the flag in some crazy directory, and I will not allow you to change directories with cd, so no cat flag for you. You must retrieve the flag by absolute path, wherever it is.
## Code
```
You used 'cd'! In this level, I don't allow you to change the working directory 
--- you MUST chase pass 'cat' the absolute path of where I put it on the 
filesystem (which is /usr/share/cmake/flag).
hacker@commands~more-catting-practice:~$ pwd 
/home/hacker
hacker@commands~more-catting-practice:~$ ls ..
hacker
hacker@commands~more-catting-practice:~$ ls /
bin  boot  challenge  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hacker@commands~more-catting-practice:~$ ls usr 
ls: cannot access 'usr': No such file or directory
hacker@commands~more-catting-practice:~$ cat /usr/share/cmake/flag
pwn.college{siiYRV2mjEBQ2ajqfpWoFVyDPnB.dBjM5QDLyUTN0czW}
```
## What I learnt
I accidentally used cd and got the actual location :(
# C.4 grepping for a needle in a haystack
## Questions
Sometimes, the files that you might cat out are too big. Luckily, we have the grep command to search for the contents we need! We'll learn it in this challenge.

There are many ways to grep, and we'll learn on way here:

hacker@dojo:~$ grep SEARCH_STRING /path/to/file
Invoked like this, grep will search the file for lines of text containing SEARCH_STRING and print them to the console.

In this challenge, I've put a hundred thousand lines of text into the /challenge/data.txt file. Grep it for the flag!

HINT: The flag always starts with the text pwn.college.
## Code
```
Connected!                                                                        
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{YGWmJJnrn7pXHjtxxWRcaba6Z1t.ddTM4QDLyUTN0czW}
hacker@commands~grepping-for-a-needle-in-a-haystack:~$
```
## What I learnt
Every flag has pwn.college so I grepped it in the file and got the exact flag as the output.

# C.5 listing files
## Questions
So far, we've told you which files to interact with. But directories can have lots of files (and other directories) inside them, and we won't always be here to tell you their names. You'll need to learn to list their contents using the ls command!

ls will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided. Observe:

hacker@dojo:~$ ls /challenge
run
hacker@dojo:~$ ls
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$ ls /home/hacker
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$
In this challenge, we've named /challenge/run with some random name! List the files in /challenge to find it.
## Code
```
Connected!                                                                        
hacker@commands~listing-files:~$ ls /challenge
7089-renamed-run-2373  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/7089-renamed-run-2373
Yahaha, you found me! Here is your flag:
pwn.college{EIMtRHb29_PzgfvtQ9KCFjUD7zK.dhjM4QDLyUTN0czW}
hacker@commands~listing-files:~$ 
```
## What I learnt
Nothing. 

# C.6 touching files
## Questions
Of course, you can also create files! There are several ways to do this, but we'll look at a simple command here. You can create a new, blank file by touching it with the touch command:

hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ touch pwnfile
hacker@dojo:/tmp$ ls
pwnfile
hacker@dojo:/tmp$
It's that simple! In this level, please create two files: /tmp/pwn and /tmp/college, and run /challenge/run to get your flag!
## Code
```
Connected!                                                                        
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{cqB45VlRjyP6WMqYm2-VlpsRBL8.dBzM4QDLyUTN0czW}
hacker@commands~touching-files:~$
```
## What I learnt
Nothing 

# C.7 removing files
## Questions
Files are all around you. Like candy wrappers, there'll eventually be too many of them. In this level, we'll learn to clean up!

In Linux, you remove files with the rm command, as so:

hacker@dojo:~$ touch PWN
hacker@dojo:~$ touch COLLEGE
hacker@dojo:~$ ls
COLLEGE     PWN
hacker@dojo:~$ rm PWN
hacker@dojo:~$ ls
COLLEGE
hacker@dojo:~$
Let's practice. This challenge will create a delete_me file in your home directory! Delete it, then run /challenge/check, which will make sure you've deleted it and then give you the flag!
## Code
```
Connected!                                                                        
hacker@commands~removing-files:~$ ls
Desktop  delete_me  h  hi
hacker@commands~removing-files:~$ rm delete_me h
hacker@commands~removing-files:~$ ls
Desktop  hi
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{s16oFJzpPudhGVzrwI-t0lIsCyI.dZTOwUDLyUTN0czW}
hacker@commands~removing-files:~$
```
## What I learnt
Nothing.

# C.8 hidden files
## Question 
Interestingly, ls doesn't list all the files by default. Linux has a convention where files that start with a . don't show up by default in ls and in a few other contexts. To view them with ls, you need to invoke ls with the -a flag, as so:

hacker@dojo:~$ touch pwn
hacker@dojo:~$ touch .college
hacker@dojo:~$ ls
pwn
hacker@dojo:~$ ls -a
.college	pwn
hacker@dojo:~$
Now, it's your turn! Go find the flag, hidden as a dot-prepended file in /.
## Code
```
Connected!                                                                        
hacker@commands~hidden-files:~$ ls / -a
.  ..  .dockerenv  .flag-3759109575628  bin  boot  challenge  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hacker@commands~hidden-files:~$ cat /.flag-3759109575628
pwn.college{MIcy0jkUXMj575BKXCuMonPI_80.dBTN4QDLyUTN0czW}
hacker@commands~hidden-files:~$ 
```
## What I learnt
I learnt something here, which even helped me in the Oasis CTF. 

# C.9 An Epic Filesystem Quest
## Question
With your knowledge of cd, ls, and cat, we're ready to play a little game!

We'll start it out in /. Normally:

hacker@dojo:~$ cd /
hacker@dojo:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  proc  run   srv  tmp  var
boot  dev        flag  lib   lib64  media   opt  root  sbin  sys  usr
That's a lot of contents! One day, you will be quite familiar with them, but already, you might recognize the flag file and the challenge directory.

In this challenge, I have hidden the flag! Here, you will use ls and cat to follow my breadcrumbs and find it! Here's how it'll work:

Your first clue is in /. Head on over there.
Look around with ls. There'll be a file named HINT or CLUE or something along those lines!
cat that file to read the clue!
Depending on what the clue says, head on over to the next directory (or don't!).
Follow the clues to the flag!
Good luck!
## Code
```
Connected!                                                                        
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
INFO  bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hacker@commands~an-epic-filesystem-quest:/$ cat INFO
Tubular find!
The next clue is in: /usr/share/doc/libxkbcommon0
hacker@commands~an-epic-filesystem-quest:/$ cat flag
cat: flag: Permission denied
hacker@commands~an-epic-filesystem-quest:/$ ls /usr/share/doc/libxkbcommon0
BLUEPRINT  changelog.Debian.gz  copyright
hacker@commands~an-epic-filesystem-quest:/$ /usr/share/doc/libxkbcommon0/BLUEPRINT
ssh-entrypoint: /usr/share/doc/libxkbcommon0/BLUEPRINT: Permission denied
hacker@commands~an-epic-filesystem-quest:/$ cat /usr/share/doc/libxkbcommon0/BLUEPRINT
Great sleuthing!
The next clue is in: /var/cache/man/fr

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/$ ls /var/cache/man/fr -a 
.  ..  .CLUE  CACHEDIR.TAG  cat1  cat5  cat7  cat8  index.db
hacker@commands~an-epic-filesystem-quest:/$ cat /var/cache/man/fr cat1
cat: /var/cache/man/fr: Is a directory
cat: cat1: No such file or directory
hacker@commands~an-epic-filesystem-quest:/$ cat /var/cache/man/fr .cat1
cat: /var/cache/man/fr: Is a directory
cat: .cat1: No such file or directory
hacker@commands~an-epic-filesystem-quest:/$ cat /var/cache/man/fr/.cat1
cat: /var/cache/man/fr/.cat1: No such file or directory
hacker@commands~an-epic-filesystem-quest:/$ cat /var/cache/man/fr/cat1
cat: /var/cache/man/fr/cat1: Is a directory
hacker@commands~an-epic-filesystem-quest:/$ cat /var/cache/man/fr/.CLUE
Lucky listing!
The next clue is in: /opt/linux/linux-5.4/tools/testing/selftests/tc-testing/bpf

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/$ ls /opt/linux/linux-5.4/tools/testing/selftests/tc-testing/bpf -a 
.  ..  .EVIDENCE  Makefile  action.c
hacker@commands~an-epic-filesystem-quest:/$ cat /opt/linux/linux-5.4/tools/testing/selftests/tc-testing/bpf/.EVIDENCE
Tubular find!
The next clue is in: /opt/ghidra/Ghidra/Features/GhidraServer/data/yajsw-stable-13.09/lib/extended/sigar

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/$ cat /opt/ghidra/Ghidra/Features/GhidraServer/data/yajsw-stable-13.09/lib/extended/sigar
cat: /opt/ghidra/Ghidra/Features/GhidraServer/data/yajsw-stable-13.09/lib/extended/sigar: Is a directory
hacker@commands~an-epic-filesystem-quest:/$ ls /opt/ghidra/Ghidra/Features/GhidraServer/data/yajsw-stable-13.09/lib/extended/sigar -a
.  ..  BRIEF-TRAPPED  sigar-1.6.4.jar  sigar-lib-1.6.4.jar
hacker@commands~an-epic-filesystem-quest:/$ cat BRIEF-TRAPPED
cat: BRIEF-TRAPPED: No such file or directory
hacker@commands~an-epic-filesystem-quest:/$ cat /opt/ghidra/Ghidra/Features/GhidraServer/data/yajsw-stable-13.09/lib/extended/sigar/BRIEF-TRAPPED
Tubular find!
The next clue is in: /opt/angr-management/_internal/PySide6

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/$ ls  /opt/angr-management/_internal/PySide6 -a 
.                Qt              QtDataVisualization.abi3.so  QtOpenGL.abi3.so         QtPrintSupport.abi3.so  QtQuickWidgets.abi3.so  QtWebEngineCore.abi3.so     libpyside6.abi3.so.6.7
..               QtCore.abi3.so  QtGui.abi3.so                QtOpenGLWidgets.abi3.so  QtQml.abi3.so           QtSvg.abi3.so           QtWebEngineWidgets.abi3.so  libpyside6qml.abi3.so.6.7
DOSSIER-TRAPPED  QtDBus.abi3.so  QtNetwork.abi3.so            QtPositioning.abi3.so    QtQuick.abi3.so         QtWebChannel.abi3.so    QtWidgets.abi3.so
hacker@commands~an-epic-filesystem-quest:/$ cat  /opt/angr-management/_internal/PySide6/DOSSIER-TRAPPED
Tubular find!
The next clue is in: /opt/rappel/t

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/$ ls /opt/rappel/t -a
.  ..  MEMO-TRAPPED  Makefile  mov-amd64.sh  mov-armv8.sh  mov-x86.sh
hacker@commands~an-epic-filesystem-quest:/$ cat /opt/rappel/t/MEMO-TRAPPED
Congratulations, you found the clue!
The next clue is in: /opt/ghidra/Ghidra/Processors/Dalvik/data
hacker@commands~an-epic-filesystem-quest:/$ ls /opt/ghidra/Ghidra/Processors/Dalvik/data -a
.  ..  NOTE  build.xml  languages  sleighArgs.txt
hacker@commands~an-epic-filesystem-quest:/$ cat /opt/ghidra/Ghidra/Processors/Dalvik/data/NOTE
Lucky listing!
The next clue is in: /opt/linux/linux-5.4/arch/sh/mm

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ cd /opt/linux/linux-5.4/arch/sh/mm
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/sh/mm$ ls
Kconfig   alignment.c      cache-j2.c    cache-sh3.c  cache-sh7705.c  consistent.c  fault.c        init.c           kmap.c   numa.c     sram.c         tlb-sh3.c  tlb-urb.c   tlbflush_32.c
Makefile  asids-debugfs.c  cache-sh2.c   cache-sh4.c  cache-shx3.c    extable_32.c  flush-sh4.c    ioremap.c        mmap.c   pgtable.c  tlb-debugfs.c  tlb-sh4.c  tlbex_32.c  tlbflush_64.c
README    cache-debugfs.c  cache-sh2a.c  cache-sh5.c  cache.c         extable_64.c  hugetlbpage.c  ioremap_fixed.c  nommu.c  pmb.c      tlb-pteaex.c   tlb-sh5.c  tlbex_64.c  uncached.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/sh/mm$ cat README
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{gsz5Lm-LPdbopyB90OHbOqy-mNn.dljM4QDLyUTN0czW}
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/sh/mm$
```
## What I learnt
Nothing. It was slightly fun though.

# C.10 making directories 
## Question
We can create files. How about directories? You make directories using the mkdir command. Then you can stick files in there!

Watch:

hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ mkdir my_directory
hacker@dojo:/tmp$ ls
my_directory
hacker@dojo:/tmp$ cd my_directory
hacker@dojo:/tmp/my_directory$ touch my_file
hacker@dojo:/tmp/my_directory$ ls
my_file
hacker@dojo:/tmp/my_directory$ ls /tmp/my_directory/my_file
/tmp/my_directory/my_file
hacker@dojo:/tmp/my_directory$
Now, go forth and create a /tmp/pwn directory and make a college file in it! Then run /challenge/run, which will check your solution and give you the flag!
## Code
```
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ ls /tmp
bin  hsperfdata_root  pwn  tmp.XvrUsDZh8M
hacker@commands~making-directories:~$ cd /tmp/pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{wzePuM-Z8eW7uXfc-r2sEGGn-UH.dFzM4QDLyUTN0czW}
hacker@commands~making-directories:/tmp/pwn$
```
## What I learnt
Nothing. 

# C.11 finding files
## Questions
So now we know how to list, read, and create files. But how do we find them? We use the find command!

The find command takes optional arguments describing the search criteria and the search location. If you don't specify a search criteria, find matches every file. If you don't specify a search location, find uses the current working directory (.). For example:

hacker@dojo:~$ mkdir my_directory
hacker@dojo:~$ mkdir my_directory/my_subdirectory
hacker@dojo:~$ touch my_directory/my_file
hacker@dojo:~$ touch my_directory/my_subdirectory/my_subfile
hacker@dojo:~$ find
.
./my_directory
./my_directory/my_subdirectory
./my_directory/my_subdirectory/my_subfile
./my_directory/my_file
hacker@dojo:~$
And when specifying the search location:

hacker@dojo:~$ find my_directory/my_subdirectory
my_directory/my_subdirectory
my_directory/my_subdirectory/my_subfile
hacker@dojo:~$
And, of course, we can specify the criteria! For example, here, we filter by name:

hacker@dojo:~$ find -name my_subfile
./my_directory/my_subdirectory/my_subfile
hacker@dojo:~$ find -name my_subdirectory
./my_directory/my_subdirectory
hacker@dojo:~$
You can search the whole filesystem if you want!

hacker@dojo:~$ find / -name hacker
/home/hacker
hacker@dojo:~$
Now it's your turn. I've hidden the flag in a random directory on the filesystem. It's still called flag. Go find it!

Several notes. First, there are other files named flag on the filesystem. Don't panic if the first one you try doesn't have the actual flag in it. Second, there're plenty of places in the filesystem that are not accessible to a normal user. These will cause find to generate errors, but you can ignore those; we won't hide the flag there! Finally, find can take a while; be patient!
## Code
```
hacker@commands~finding-files:~$ cd /
hacker@commands~finding-files:/$ find -name flag 
find: ‘./root’: Permission denied
find: ‘./proc/1/task/1/fd’: Permission denied
find: ‘./proc/1/task/1/fdinfo’: Permission denied
find: ‘./proc/1/task/1/ns’: Permission denied
find: ‘./proc/1/fd’: Permission denied
find: ‘./proc/1/map_files’: Permission denied
find: ‘./proc/1/fdinfo’: Permission denied
find: ‘./proc/1/ns’: Permission denied
find: ‘./proc/7/task/7/fd’: Permission denied
find: ‘./proc/7/task/7/fdinfo’: Permission denied
find: ‘./proc/7/task/7/ns’: Permission denied
find: ‘./proc/7/fd’: Permission denied
find: ‘./proc/7/map_files’: Permission denied
find: ‘./proc/7/fdinfo’: Permission denied
find: ‘./proc/7/ns’: Permission denied
find: ‘./var/log/private’: Permission denied
find: ‘./var/log/apache2’: Permission denied
find: ‘./var/log/mysql’: Permission denied
find: ‘./var/cache/ldconfig’: Permission denied
find: ‘./var/cache/apt/archives/partial’: Permission denied
find: ‘./var/cache/private’: Permission denied
find: ‘./var/lib/apt/lists/partial’: Permission denied
find: ‘./var/lib/php/sessions’: Permission denied
find: ‘./var/lib/mysql-files’: Permission denied
find: ‘./var/lib/private’: Permission denied
find: ‘./var/lib/mysql-keyring’: Permission denied
find: ‘./var/lib/mysql’: Permission denied
find: ‘./tmp/tmp.XvrUsDZh8M’: Permission denied
find: ‘./run/mysqld’: Permission denied
find: ‘./run/sudo’: Permission denied
find: ‘./etc/ssl/private’: Permission denied
./usr/local/lib/python3.8/dist-packages/pwnlib/flag
./usr/local/share/radare2/5.9.5/flag
./usr/lib/python3/dist-packages/binwalk/config/flag
./opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
./opt/radare2/libr/flag
./nix/store/pmvk2bk4p550w182rjfm529kfqddnvh3-python3.11-pwntools-4.12.0/lib/python3.11/site-packages/pwnlib/flag
./nix/store/1yagn5s8sf7kcs2hkccgf8d0wxlrv5sz-radare2-5.9.0/share/radare2/5.9.0/flag
hacker@commands~finding-files:/$ cat ./usr/local/lib/python3.8/dist-packages/pwnlib/flag
cat: ./usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:/$ cd ./usr/local/lib/python3.8/dist-packages/pwnlib/flag
hacker@commands~finding-files:/usr/local/lib/python3.8/dist-packages/pwnlib/flag$ ls
__init__.py  __pycache__  flag.py
hacker@commands~finding-files:/usr/local/lib/python3.8/dist-packages/pwnlib/flag$ cat flag.py 
"""Describes a way to submit a key to a key server.
"""
from __future__ import absolute_import
from __future__ import division

import os

from pwnlib.args import args
from pwnlib.log import getLogger
from pwnlib.tubes.remote import remote

env_server  = args.get('FLAG_HOST', 'flag-submission-server').strip()
env_port    = args.get('FLAG_PORT', '31337').strip()
env_file    = args.get('FLAG_FILE', '/does/not/exist').strip()
env_exploit_name = args.get('EXPLOIT_NAME', 'unnamed-exploit').strip()
env_target_host  = args.get('TARGET_HOST', 'unknown-target').strip()
env_team_name    = args.get('TEAM_NAME', 'unknown-team').strip()

log = getLogger(__name__)

def submit_flag(flag,
                exploit=env_exploit_name,
                target=env_target_host,
                server=env_server,
                port=env_port,
                team=env_team_name):
    """
    Submits a flag to the game server

    Arguments:
        flag(str): The flag to submit.
        exploit(str): Exploit identifier, optional
        target(str): Target identifier, optional
        server(str): Flag server host name, optional
        port(int): Flag server port, optional
        team(str): Team identifier, optional

    Optional arguments are inferred from the environment,
    or omitted if none is set.

    Returns:
        A string indicating the status of the key submission,
        or an error code.

    Doctest:

        >>> l = listen()
        >>> _ = submit_flag('flag', server='localhost', port=l.lport)
        >>> c = l.wait_for_connection()
        >>> c.recvall().split()
        [b'flag', b'unnamed-exploit', b'unknown-target', b'unknown-team']
    """
    flag = flag.strip()

    log.success("Flag: %r" % flag)

    data = "\n".join([flag,
                      exploit,
                      target,
                      team,
                      '']).encode('ascii')

    if os.path.exists(env_file):
        write(env_file, data)
        return

    try:
        with remote(server, int(port)) as r:
            r.send(data)
            return r.recvall(timeout=1)
    except Exception:
        log.warn("Could not submit flag %r to %s:%s", flag, server, port)
hacker@commands~finding-files:/usr/local/lib/python3.8/dist-packages/pwnlib/flag$ cd ./usr/local/share/radare2/5.9.5/flag
ssh-entrypoint: cd: ./usr/local/share/radare2/5.9.5/flag: No such file or directory
hacker@commands~finding-files:/usr/local/lib/python3.8/dist-packages/pwnlib/flag$ cd /usr/local/share/radare2/5.9.5/flag
hacker@commands~finding-files:/usr/local/share/radare2/5.9.5/flag$ ls
tags.r2
hacker@commands~finding-files:/usr/local/share/radare2/5.9.5/flag$ cat tags.r2
ft alloc *.malloc *.free$ *.calloc *.kalloc *.realloc
ft crypto *.encrypt *.decrypt *.aes *.AES *.blowfish *._des *._rc2 *.serpent *._cbc
ft dylib *.dlopen *.dlsym *.dlclose *.mmap *.LoadLibrary *.GetProcAddress
ft env *.getenv *.putenv *.unsetenv *.setenv *.GetEnvironmentVariable *.SetEnvironmentVariable *.ExpandEnvironmentStrings
ft fs *.open$ *.close *.read$ *.write *.CloseHandle *.FindFirstFileW *._wfopen *._wstat *.ftruncate *.lseek *._chsize *.GetFullPathName *.realpath *.RemoveDirectory *.DeleteFile *.CreateFile *.WriteFile *.UnmapViewOfFile *.CreateFileMapping *.MapViewOfFile *.readlink *.chmod *.fchmod *.chown *.stat *.fstat *.lstat *.fstatat *.lstat64 *.stat64 *.chflags *.fchflags *.lchflags
ft network *.socket *.connect *.bind$ *.listen *.accept *.sendto *.recvfrom *.gethostbyname *.htons *.ntohs
ft process *.getpid *.getppid *.kill *.exit *.abort *.assert *.gethostid *.sethostid *.sysctl
ft stdout ^printf *.puts *.write
ft string *.strcat *.strcpy *.strncpy *.strlen *.strtok *.strstr *.strlcpy *.asprintf *.sprintf *.snprintf
ft tags.py import os from sys import argv for fname in argv[1:]: with open(fname) as f: text = ' '.join(f.read().splitlines()) print('ft %s %s' % (os.path.basename(fname), text))
ft threads *.pthread_create *.pthread_mutex_init *.pthread_cond_init *.CreateThread *.TerminateThread *.WaitForSingleObject *.GetCurrentThreadId
ft time *.settimeofday *.gettimeofday *.time *.adjtime *.ctime *.timed *.date$ *.sleep *.Sleep *.usleep *.clock_nanosleep *.localtime *.asctime *.difftime *.gmtime *.mktime *.timelocal *.timegm *.tzfile *.tzset
hacker@commands~finding-files:/usr/local/share/radare2/5.9.5/flag$ cd /usr/lib/python3/dist-packages/binwalk/config/flag
ssh-entrypoint: cd: /usr/lib/python3/dist-packages/binwalk/config/flag: Not a directory
hacker@commands~finding-files:/usr/local/share/radare2/5.9.5/flag$ cat /usr/lib/python3/dist-packages/binwalk/config/flag
pwn.college{EytA1d9BIR0IOh2Bdjpxj_8T-Br.dJzM4QDLyUTN0czW}
```
## What I learnt
A lot of patience and mental capacity is needed to solve some challenges. This took a lot more time than it may seem. 

# C.12 linking files
## Question
If you use Linux (or computers) for any reasonable length of time to do any real work, you will eventually run into some variant of the following situation: you want two programs to access the same data, but the programs expect that data to be in two different locations. Luckily, Linux provides a solution to this quandry: links.

Links come in two flavors: hard and soft (also known as symbolic) links. We'll differentiate the two with an analogy:

A hard link is when you address your appartment using multiple addresses that all lead directly to the same place (e.g., Apt 2 vs Unit 2).
A soft link is when you move appartments and have the postal service automatically forward your mail from your old place to your new place.
In a filesystem, a file is, conceptually, an address at which the contents of that file live. A hard link is an alternate address that indexes that data --- accesses to the hard link and accesses to the original file are completely identical, in that they immediate yield the necessary data. A soft/symbolic link, instead, contains the original file name. When you access the symbolic link, Linux will realize that it is a symbolic link, read the original file name, and then (typically) automatically access that file. In most cases, both situations result in accessing the original data, but the mechanisms are different.

Hard links sound simpler to most people (case in point, I explained it in one sentence above, versus two for soft links), but they have various downsides and implementation gotchas that make soft/symbolic links, by far, the more popular alternative.

In this challenge, we will learn about symbolic links (also also known as symlinks). Symbolic links are created with the ln command with the -s argument, like so:

hacker@dojo:~$ cat /tmp/myfile
This is my file!
hacker@dojo:~$ ln -s /tmp/myfile /home/hacker/ourfile
hacker@dojo:~$ cat ~/ourfile
This is my file!
hacker@dojo:~$
You can see that accessing the symlink results in getting the original file contents! Also, you can see the usage of ln -s. Note that the original file path comes before the link path in the command!

A symlink can be identified as such with a few methods. For example, the file command, which takes a filename and tells you what type of file it is, will recognize symlinks:

hacker@dojo:~$ file /tmp/myfile
/tmp/myfile: ASCII text
hacker@dojo:~$ file ~/ourfile
/home/hacker/ourfile: symbolic link to /tmp/myfile
hacker@dojo:~$
Okay, now you try it! In this level the flag is, as always, in /flag, but /challenge/catflag will instead read out /home/hacker/not-the-flag. Use the symlink, and fool it into giving you the flag!
## Code
```
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /home/hacker/not-the-flag
ssh-entrypoint: /home/hacker/not-the-flag: Permission denied
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{4g1oUMKxIX7dKYiiZRMCeB_gSzx.dlTM1UDLyUTN0czW}
hacker@commands~linking-files:~$ 
```
## What I learnt
This one was very challenging and I did learn quite some stuff here. It firstly took me a lot of time to crack this. In this, /challenge/catflag is made in a way that it will read the contents of ~/not-the-flag. So we have to create that file as a symlink for the file that we want to read which is /flag. We don't have permissions to read /flag or its symlink but we can execute /challenge/catflag and it will read out the contents of the file ~/not-the-flag. Since it is a symlink for /flag, we are indirectly able to get the flag. 

