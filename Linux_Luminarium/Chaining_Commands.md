# K.1 Chaining with Semicolons 
## Question
The easiest way to chain commands is ;. In most contexts, ; separates commands in a similar way to how Enter separates lines. So, this:

hacker@dojo:~$ echo COLLEGE > pwn
hacker@dojo:~$ cat pwn
COLLEGE
hacker@dojo:~$
Is roughly the same as this:

hacker@dojo:~$ echo COLLEGE > pwn; cat pwn
COLLEGE
hacker@dojo:~$
Basically, when you hit Enter, your shell executes your typed command and, after that command terminates, give you the prompt to input another command. The semicolon is analogous, just without the prompt and with you entering both commands before anything is executed.

Give it a try now! In this level, you must run /challenge/pwn and then /challenge/college, chaining them with a semicolon.
## Code
```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{Y1SlPWzLJ8Bu3GfhQPY6C9BOb-X.dVTN4QDLyUTN0czW}
```
## What I learnt
This felt a bit like C programming language.
# K.2 Your First Shell Script
## Question 
As you combine more and more commands to achieve complex effects, the length of the combined prompt quickly gets really annoying to deal with. When this happens, you can put these commands in a file, called a shell script, and run them by executing the file! For example, consider our semicolon technique:

hacker@dojo:~$ echo COLLEGE > pwn; cat pwn
COLLEGE
hacker@dojo:~$
We can create a shell script called pwn.sh (by convention, shell scripts are frequently named with a sh suffix):

echo COLLEGE > pwn
cat pwn
And then we can execute by passing it as an argument to a new instance of our shell (bash)! When a shell is invoked like this, rather than taking commands from the user, it reads commands from the file.

hacker@dojo:~$ ls
hacker@dojo:~$ bash pwn.sh
COLLEGE
hacker@dojo:~$ ls
pwn
hacker@dojo:~$
You can see that the shell script executed both commands, creating and printing the pwn file.

Now, it's your turn! Same as last level, run /challenge/pwn and then /challenge/college, but this time in a shell script called x.sh, then run it with bash!

NOTE: We haven't yet talked about Linux's amazing array of competent command line file editors. For now, feel free to use the Text Editor application in Desktop mode (Applications->Accessories->Text Editor) or the default editor in the VSCode Workspace!
## Code
```
hacker@chaining~your-first-shell-script:~$ vim x.sh 
hacker@chaining~your-first-shell-script:~$ ls
Desktop
hacker@chaining~your-first-shell-script:~$ touch x.sh 
hacker@chaining~your-first-shell-script:~$ ls
Desktop  x.sh
hacker@chaining~your-first-shell-script:~$ echo /challenge/pwn > x.sh 
hacker@chaining~your-first-shell-script:~$ echo /challenge/college >> x.sh 
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{0DynjBY81Rphh2EzS7x0zUKGFwK.dFzN4QDLyUTN0czW}
```
## What I learnt
I tried using vim, which is a tool that I had some prior experience with but I think it didn't work since I was on Mac. I just echoed the commands in the code then and ran it. This was pretty interesting to me. I bet hackers use this a lot to run their codes in system computers.
# K.3 Redirecting Script Output 
## Question 
Let's try something a bit trickier! You've piped output between programs with |, but so far, this has just been between one command's output and a different command's input. But what if you wanted to send the output of several programs to one command? There are a few ways to do this, and we'll explore a simple one here: redirecting output from your script!

As far as the shell is concerned, your script is just another command. That means you can redirect its input and output just like you did for commands in the Piping module! For example, you can write it to a file:

hacker@dojo:~$ cat script.sh
echo PWN
echo COLLEGE
hacker@dojo:~$ bash script.sh > output
hacker@dojo:~$ cat output
PWN
COLLEGE
hacker@dojo:~$
All of the various redirection methods work: > for stdout, 2> for stderr, < for stdin, >> and 2>> for append-mode redirection, >& for redirecting to other file descriptors, and | for piping to another command.

In this level, we will practice piping (|) from your script to another program. Like before, you need to create a script that calls the /challenge/pwn command followed by the /challenge/college command, and pipe the output of the script into a single invocation of the /challenge/solve command!
## Code
```
hacker@chaining~redirecting-script-output:~$ x.sh | /challenge/solve
ssh-entrypoint: x.sh: command not found
The data piped from /challenge/pwn did not match what I expected. I 
re-randomize the data every time you input a new line to the shell, so you must 
get it right in one shot! Make sure to pipe the output from your script to 
/challenge/solve.
hacker@chaining~redirecting-script-output:~$ ls
Desktop  x.sh
hacker@chaining~redirecting-script-output:~$ cat x.sh 
/challenge/pwn
/challenge/college
hacker@chaining~redirecting-script-output:~$ bash cat x.sh | /challenge/solve 
No shenanigans with bash options yet, please! Just run your script with 'bash 
x.sh'.
Please name your script with an '.sh' extension. This isn't strictly necessary 
eventually, but we'll keep things explicit for the next few levels.
The data piped from /challenge/pwn did not match what I expected. I 
re-randomize the data every time you input a new line to the shell, so you must 
get it right in one shot! Make sure to pipe the output from your script to 
/challenge/solve.
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve 
Correct! Here is your flag:
pwn.college{kv7heTKZjqLCoXF3AcnT8Gkl62q.dhTM5QDLyUTN0czW}
```
## What I learnt 
Some silly mistakes here.
# K.4 Executable Shell Scripts 
## Question
You have written your first shell script, but calling it via bash script.sh is a pain. Why do you need that bash?

When you invoke bash script.sh, you are, of course launching the bash command with the script.sh argument. This tells bash to read its commands from script.sh instead of standard input, and thus your shell script is executed.

It turns out that you can avoid the need to manually invoke bash. If your shell script file is executable (recall File Permissions), you can simply invoke it via its relative or absolute path! For example, if you create script.sh in your home directory and make it executable, you can invoke it via /home/hacker/script.sh or ~/script.sh or (if your working directory is /home/hacker) ./script.sh.

Try that here! Make a shellscript that will invoke /challenge/solve, make it executable, and run it without explicitly invoking bash!
## Code
```
hacker@chaining~executable-shell-scripts:~$ echo /challenge/solve > x.sh
hacker@chaining~executable-shell-scripts:~$ ./x.sh
ssh-entrypoint: ./x.sh: Permission denied
hacker@chaining~executable-shell-scripts:~$ chmod o+x ./x.sh 
hacker@chaining~executable-shell-scripts:~$ ./x.sh
ssh-entrypoint: ./x.sh: Permission denied
hacker@chaining~executable-shell-scripts:~$ ls -l
total 8
drwxr-xr-x 2 hacker hacker 4096 Sep 30 16:20 Desktop
-rw-r--r-x 1 hacker hacker   17 Oct  3 13:43 x.sh
hacker@chaining~executable-shell-scripts:~$ chmod u+x ./x.sh
hacker@chaining~executable-shell-scripts:~$ ./x.sh
Congratulations on your shell script execution! Your flag:
pwn.college{cx0O7xh4-qQZW4YcYf4QMTCZby_.dRzNyUDLyUTN0czW}
```
## What I learnt
I learnt how to execute shell scripts without using bash command.
