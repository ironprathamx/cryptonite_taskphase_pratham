# What I did
I am already familiar with the concept of modulo as its used in cryptography a lot. I made this python code to get the flag.
```
L=[350,63,353,198,114,369,346,184,202,322,94,235,114,110,185,188,225,212,366,374,261,213]
charset = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789_"
for i in L:
    z=i%37
flag="".join(charset[num % 37] for num in L)
print(flag)
```
The output to this was "R0UND_N_R0UND_ADD17EC2" and we get the flag on putting it inside picoCTF{}

