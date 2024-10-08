# B.1 The Root
## Question
Alright, so the filesystem starts at /. Under that, there are a whole mess of other directories, configuration files, programs, and, most importantly, flags. In this level, we've added a program right in /, called pwn, that will give you the flag. All you need to do for this level is to invoke this program!

You can invoke a program by providing its path on the command line. In this case, you'll be giving the exact path, starting from /, so the path would be /pwn. This style of path, one that starts with the root directory, is referred to as an "absolute path".

Start the challenge, launch a terminal, invoke the pwn program using its absolute path, and Capture that Flag! Good luck!
## Code
```
hacker@paths~the-root:~$ ls
Desktop
hacker@paths~the-root:~$ cd ..
hacker@paths~the-root:/home$ ls
hacker
hacker@paths~the-root:/home$ cd ..
hacker@paths~the-root:/$ ls
bin        dev   home   lib64   mnt  proc  run   sys  var
boot       etc   lib    libx32  nix  pwn   sbin  tmp
challenge  flag  lib32  media   opt  root  srv   usr
hacker@paths~the-root:/$ /pwn
BOOM!!!
Here is your flag:
pwn.college{sXdpXIP2gfYuPmv9pvaPsdz438v.dhzN5QDLyUTN0czW}
hacker@paths~the-root:/$ 
```
## What I learnt
Here, I first navigated to the root directory and pwn file was present there so I just entered its root address and got the flag.

# B.2 Program and Absolute Paths
## Question 
Let's explore a slightly more complicated path! Except for in the previous level, challenges in pwn.college are in the challenge directory and the challenge directory is, in turn, right in the root directory (/). The path to the challenge the directory is, thus, /challenge. The name of the challenge program in this level is run, and it lives in the /challenge directory. Thus, the path to the run challenge program is /challenge/run.

This challenge again requires you to execute it by invoking its absolute path. You'll want to execute the run file that is in the challenge directory that is, in turn, in the / directory. If you invoke the challenge correctly, it will give you the flag. Good luck!
##Code
```
hacker@paths~program-and-absolute-paths:~$ ls
Desktop
hacker@paths~program-and-absolute-paths:~$ cd /challenge
hacker@paths~program-and-absolute-paths:/challenge$ ls
DESCRIPTION.md  run
hacker@paths~program-and-absolute-paths:/challenge$ /run
ssh-entrypoint: /run: Is a directory
hacker@paths~program-and-absolute-paths:/challenge$ cat run
#!/opt/pwn.college/bash

if [ "${0:0:1}" != "/" ]
then
	echo -e "${COLOR_RED}Incorrect...${COLORLESS}"
	echo "You did not call this challenge using an absolute path!"
	echo "An absolute path is anchored at the root of the filesystem, so it starts with /"
	exit 1
fi

echo -e "${COLOR_GREEN}Correct!!!${COLORLESS}"
echo "$0 is an absolute path! Here is your flag:"
/bin/cat /flag
hacker@paths~program-and-absolute-paths:/challenge$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{EhI91wAyo-87tU-dXT1VbDLjhoH.dVDN1QDLyUTN0czW}
hacker@paths~program-and-absolute-paths:/challenge$
```
## What I learnt
Here, I first went to the challenge directory and I have some prior experience with the Linux CLI so I didn't know what I had to do and got confused as I tried to cat the file, a mistake which I repeated many times in further programs, exactly and this is when I realised that on just entering the absolute path of a file, we can execute it. 

# B.3 Position thy self
## Question
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$ cd /some/new/directory
This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.

As an aside, now you can see what the ~ was in the prompt! It shows the current that your shell is located at.

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program. Good luck!
## Code
```
hacker@paths~position-thy-self:~$ cd /challenge
hacker@paths~position-thy-self:/challenge$ ls
DESCRIPTION.md  run
hacker@paths~position-thy-self:/challenge$ cat run
#!/opt/pwn.college/bash

RANDOM=$(cksum /flag  | awk '{print $1}')
CANDIDATES=(
	"/"
	"/tmp"
	"/var"
	"/etc"
	"/sys"
	"/proc/$PPID"
	"/proc/$PPID/fd"
	"/home"
	"/usr/bin"
	"/var/log"
	"/sys/kernel"
	"/etc/apt/sources.list.d"
	"/usr/include"
	"/usr/share/zoneinfo/posix/Asia"
	"/usr/aarch64-linux-gnu/include/gnu"
	"/usr/share/doc"
	"/usr/share/doc/fontconfig"
	"/usr/share/build-essential"
	"/var/lib/apt/lists"
)
NEEDED=${CANDIDATES[ $RANDOM % ${#CANDIDATES[@]} ]}

while [[ ! -d "$NEEDED" ]]
do
	NEEDED=${CANDIDATES[ $RANDOM % ${#CANDIDATES[@]} ]}
done

if [ "$PWD" != "$NEEDED" ]
then
	echo -e "${COLOR_RED}Incorrect...${COLORLESS}"
	echo "You are not currently in the $NEEDED directory."
	echo 'Please use the `cd` utility to change directory appropriately.'
	exit 1
fi

if [ "${0:0:1}" != "/" ]
then
	echo -e "${COLOR_RED}Incorrect...${COLORLESS}"
	echo "You did not call this challenge using an absolute path!"
	echo "An absolute path is anchored at the root of the filesystem, so it starts with /"
	exit 1
fi

echo -e "${COLOR_GREEN}Correct!!!${COLORLESS}"
echo "$0 is an absolute path, invoked from the right directory!"
echo "Here is your flag:"
/bin/cat /flag
hacker@paths~position-thy-self:/challenge$ /challenge/run
Incorrect...
You are not currently in the /sys/kernel directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:/challenge$ cat /sys/kernel 
cat: /sys/kernel: Is a directory
hacker@paths~position-thy-self:/challenge$ cd /sys/kernel
hacker@paths~position-thy-self:/sys/kernel$ ls
address_bits  cgroup         crash_elfcorehdr_size  iommu_groups        kexec_crash_size  mm          profiling      reboot    software_nodes  uevent_helper  warn_count
boot_params   config         debug                  irq                 kexec_loaded      notes       rcu_expedited  security  sunrpc          uevent_seqnum
btf           cpu_byteorder  fscaps                 kexec_crash_loaded  livepatch         oops_count  rcu_normal     slab      tracing         vmcoreinfo
hacker@paths~position-thy-self:/sys/kernel$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{Q-QCxIbhbo77MuL1caqrCe2DFkE.dZDN1QDLyUTN0czW}
hacker@paths~position-thy-self:/sys/kernel$ 
```
## What I learnt
I repeated the cat mistake here and there is a lot of pointless code here like I had no reason to use ls once I was in /sys/kernel but I just did it. I was going to remove it but I decided to keep such errors anyway to document my growth and journey more properly and accurately.

# B.4 Position elsewhere
## Question
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$ cd /some/new/directory
This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.

As an aside, now you can see what the ~ was in the prompt! It shows the current that your shell is located at.

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program. Good luck!
## Code
```
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/build-essential directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /usr/share/build-essential
hacker@paths~position-elsewhere:/usr/share/build-essential$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{46_jDJC8rIDTXdrp8YaFXl3qCq7.ddDN1QDLyUTN0czW}
hacker@paths~position-elsewhere:/usr/share/build-essential$ 
```
## What I learnt
Here, the code is way neater as I didn't repeat the mistakes. I first executed /challenge/run to know which directory I had to go to, went to that directory and excecuted run again to get the flag.

# B.5 Position yet elsewhere
## Question
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$ cd /some/new/directory
This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.

As an aside, now you can see what the ~ was in the prompt! It shows the current that your shell is located at.

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program. Good luck!
## Code
```
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /etc/apt/sources.list.d directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /etc/apt/sources.list.d
hacker@paths~position-yet-elsewhere:/etc/apt/sources.list.d$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{AslApNR9snoYyJ3I1s0UzPcmpC5.dhDN1QDLyUTN0czW}
hacker@paths~position-yet-elsewhere:/etc/apt/sources.list.d$ 
```
## What I learnt 
It is the same as last question

# B.6 implicit relative paths, from /
## Question
Now you're familiar with the concept of referring to absolute paths and changing directories. If you put in absolute paths everywhere, then it really doesn't matter what directory you are in, as you likely found out in the previous three challenges.

However, the current working directory does matter for relative paths.

A relative path is any path that does not start at root (i.e., it does not start with /).
A relative path is interpreted relative to your current working directory (cwd).
Your cwd is the directory that your prompt is currently located at.
This means how you specify a particular file, depends on where the terminal prompt is located.

Imagine we want to access some file located at /tmp/a/b/my_file.

If my cwd is /, then a relative path to the file is tmp/a/b/my_file.
If my cwd is /tmp, then a relative path to the file is a/b/my_file.
If my cwd is /tmp/a/b/c, then a relative path to the file is ../my_file. The .. refers to the parent directory.
Let's try it here! You'll need to run /challenge/run using a relative path while having a current working directory of /. For this level, I'll give you a hint. Your relative path starts with the letter c 😊
## Code
```
hacker@paths~implicit-relative-paths-from-:~$ challenge/run
ssh-entrypoint: challenge/run: No such file or directory
hacker@paths~implicit-relative-paths-from-:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~implicit-relative-paths-from-:~$ pwd
/home/hacker
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ pwd
/
hacker@paths~implicit-relative-paths-from-:/$ ls
bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hacker@paths~implicit-relative-paths-from-:/$ cd challenge
hacker@paths~implicit-relative-paths-from-:/challenge$ ls
DESCRIPTION.md  run
hacker@paths~implicit-relative-paths-from-:/challenge$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~implicit-relative-paths-from-:/challenge$ cd ..
hacker@paths~implicit-relative-paths-from-:/$ 
hacker@paths~implicit-relative-paths-from-:/$ /challenge/run
Incorrect...
You invoked this challenge with an absolute path. This challenge needs a relative path!
hacker@paths~implicit-relative-paths-from-:/$ /run
ssh-entrypoint: /run: Is a directory
hacker@paths~implicit-relative-paths-from-:/$ ../challenge/run
Incorrect...
This challenge must be invoked with a relative path that starts with a letter!
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{8En0FRCGsqYNB4Fh807MqxNE4zR.dlDN1QDLyUTN0czW}
hacker@paths~implicit-relative-paths-from-:/$
```
## What I learnt 
It took me a while to get this as I wasn't used to this. 

# B.7 explicit relative paths, from /
## Questions
Previously, your relative path was "naked": it directly specified the directory to descend into from the current directory. In this level, we're going to explore more explicit relative paths.

In most operating systems, including Linux, every directory has two implicit entries that you can reference in paths: . and ... The first, ., refers right to the same directory, so the following absolute paths are all identical to each other:

/challenge
/challenge/.
/challenge/./././././././././
/./././challenge/././
The following relative paths are also all identical to each other:

challenge
./challenge
./././challenge
challenge/.
Of course, if your current working directory is /, the above relative paths are equivalent to the above absolute paths.

This challenge will get you using . in your relative paths. Get ready!
## Code
```
hacker@paths~explicit-relative-paths-from-:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ /challenge/run
Incorrect...
You invoked this challenge with an absolute path. This challenge needs a relative path!
hacker@paths~explicit-relative-paths-from-:/$ challenge/run
Incorrect...
This challenge must be called with a relative path that explicitly starts with a `.`!
hacker@paths~explicit-relative-paths-from-:/$ challenge/./run
Incorrect...
This challenge must be called with a relative path that explicitly starts with a `.`!
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{0FRKtwUCHiW8gOjrbS-KEHNku5B.dBTN1QDLyUTN0czW}
hacker@paths~explicit-relative-paths-from-:/$
```
## What I learnt
This made me more comfortable with using paths

# B.8 implicit relative path
## Questions
In this level, we'll practice refering to paths using . a bit more. This challenge will need you to run it from the /challenge directory. Here, things get slightly tricky.

Linux explicitly avoids automatically looking in the current directory when you provide a "naked" path. Consider the following:

hacker@dojo:~$ cd /challenge
hacker@dojo:/challenge$ run
This will not invoke /challenge/run. This is actually a safety measure: if Linux searched the current directory for programs every time you entered a naked path, you could accidentally execute programs in your current directory that happened to have the same names as core system utilities! As a result, the above commands will yield the following error:

bash: run: command not found
We'll explore the mechanisms behind this concept later, but in this challenge, will learn how to explicitly use relative paths to launch run in this scenario. The way to do this is to tell Linux that you explicitly want to execute a program in the current directory, using . like in the previous levels. Give it a try now!
## Code
```
hacker@paths~implicit-relative-path:~$ cd /
hacker@paths~implicit-relative-path:/$ cd challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{wS9vontOkvcf6fye8SDw703-6Sr.dFTN1QDLyUTN0czW}
hacker@paths~implicit-relative-path:/challenge$
```

## What I learnt
Nothing 

# B.9 home sweet home
## Questions
Every user has a home directory, typically under /home in the filesystem. In the dojo, you are the hacker user, and your home directory is /home/hacker. The home directory is typically where users store most of their personal files. As you make your way through pwn.college, this is where you'll store most of your solutions.

Typically, your shell session will start with your home directory as your current working directory. Consider the initial prompt:

hacker@dojo:~$
The ~ in this prompt is the current working directory, with ~ being shorthand for /home/hacker. Bash provides and uses this shorthand because, again, most of your time will be spent in your home directory. Thus, whenever bash sees ~ provided as the start of an argument in a way consistent with a path, it will expand it to your home directory. Consider:

hacker@dojo:~$ echo LOOK: ~
LOOK: /home/hacker
hacker@dojo:~$ cd /
hacker@dojo:/$ cd ~
hacker@dojo:~$ cd ~/asdf
hacker@dojo:~/asdf$ cd ~/asdf
hacker@dojo:~/asdf$ cd ~
hacker@dojo:~$ cd /home/hacker/asdf
hacker@dojo:~/asdf$
Note that the expansion of ~ is an absolute path, and only the leading ~ is expanded. This means, for example, that ~/~ will be expanded to /home/hacker/~ rather than /home/hacker/home/hacker.

Fun fact: cd will use your home directory as the default destination:

hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ cd
hacker@dojo:~$
Now it's your turn to play! In this challenge, /challenge/run will write a copy of the flag to any file you specify as an argument on the commandline, with these constraints:

Your argument must be an absolute path.
The path must be inside your home directory.
Before expansion, your argument must be three characters or less.
## Code
```
hacker@paths~home-sweet-home:~$ ls
Desktop
hacker@paths~home-sweet-home:~$ touch hi
hacker@paths~home-sweet-home:~$ /challenge/run
You must provide an argument to /challenge/run when you invoke it!
hacker@paths~home-sweet-home:~$ /challenge/run /~/hi
The argument you provided must not have been longer than 3 characters (it's 
currently 5 characters long)!
hacker@paths~home-sweet-home:~$ /challenge/run /~/
The argument you provided is not under your home directory!
hacker@paths~home-sweet-home:~$ /challenge/run ~/hi
The argument you provided must not have been longer than 3 characters (it's 
currently 4 characters long)!
hacker@paths~home-sweet-home:~$ touch h
hacker@paths~home-sweet-home:~$ /challenge/run ~/h
Writing the file to /home/hacker/h!
... and reading it back to you:
pwn.college{UFaDzC_ACu8q6THl2qXZ2xdUU0u.dNzM4QDLyUTN0czW}
hacker@paths~home-sweet-home:~$ 
```
## What I learnt
I first created a file called 'hi' but then I realised if I used that, it would be longer than two characters so I created a file called 'h' instead and used it as the argument.


