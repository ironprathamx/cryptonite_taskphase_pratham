# A.1 Intro to Commands
## Question

In this challenge, you will invoke your first command! When you type a command and hit enter, the command will be invoked, as so:

hacker@dojo:~$ whoami
hacker
hacker@dojo:~$
Here, the user executed the whoami command, which simply prints the username (hacker) to the terminal. When the command terminates, the shell once again displays the prompt, ready for the next command.

In this level, invoke the hello command to get the flag! Keep in mind: commands in Linux are case sensitive: hello is different from HELLO.

## Code
```
Connected!
hacker@hello~intro-to-commands:~$ hello 
Success! Here is your flag:
pwn.college{QMfKJbL7Ybyo88Nsle1CrRe4_Bq.ddjNyUDLyUTN0czW}
hacker@hello~intro-to-commands:~$ 
```
## What I learnt

Here, hello is the command and on entering it, we get the flag. 

# A.2 Intro to Arguments
## Question 

Let's try something more complicated: a command with arguments, which is what we call additional data passed to the command. When you type a line of text and hit enter, the shell actually parses your input into a command and its arguments. The first word is the command, and the subsequent words are arguments. Observe:

hacker@dojo:~$ echo Hello
Hello
hacker@dojo:~$
In this case, the command was echo, and the argument was Hello. echo is a simple command that "echoes" all of its arguments back out onto the terminal, like you see in the session above.

Let's look at echo with multiple arguments:

hacker@dojo:~$ echo Hello Hackers!
Hello Hackers!
hacker@dojo:~$
In this case, the command was echo, and Hello and Hackers! were the two arguments to echo. Simple!

In this challenge, to get the flag, you must run the hello command (NOT the echo command) with a single argument of hackers. Try it now!

## Code
```
ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@hello~intro-to-arguments:~$ hello hackers
Success! Here is your flag:
pwn.college{4KzN5WD-HdtQPSPGHm_2q9-dobL.dhjNyUDLyUTN0czW}
hacker@hello~intro-to-arguments:~$
```
## What I learnt

hello is the command and hackers is the argument and on entering them together, we get the flag. 
