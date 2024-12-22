# What I did
I read the source code and made my own code to decrypt it and get the flag.
I did it in python as its the language I am most comfortable in. 
```
x="jU5t_a_sna_3lpm18gb41_u_4_mfr340"
i=0
while i<8:
    print(x[i], end="")
    i+=1
while i<16:
    print(x[23-i],end="")
    i+=1
while i<32:
    print(x[46-i],end="")
    i+=2
i=31
while i>=17:
    print(x[i],end="")
    i-=2
```
