# Level 10->11
## Question
The password for the next level is stored in the file data.txt, which contains base64 encoded data
## Code
```
bandit10@bandit:~$ man base64
bandit10@bandit:~$ ls
data.txt
bandit10@bandit:~$ base64 -d data.txt
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```
## What I learnt
base64 encoding and decoding is possible in C and pretty convenient.

# Level 11->12
## Question
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

## Code
```
bandit11@bandit:~$ cat data.xt
cat: data.xt: No such file or directory
bandit11@bandit:~$ cat data.txt
Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4
bandit11@bandit:~$ The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

## What I learnt
Well it was easy as I realised it was using ROT13 as I have had some experience in CTFs (just Oasis and the one in Tech Tatva). I used a website online dcode.fr i think to decode it and get the password.

# Level 12->13 
## Question 
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

## Code
```

```

## What I learnt

