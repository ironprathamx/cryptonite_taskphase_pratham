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

