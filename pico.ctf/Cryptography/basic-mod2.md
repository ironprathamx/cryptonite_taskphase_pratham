# What I did
I used the following python code:
```
L=[268,413,438,313,426,337,272,188,392,338,77,332,139,113,92,239,247,120,419,72,295,190,131]
charset = "xABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789_"
flag="".join(charset[pow(num,-1,41)] for num in L)
print(flag)
```
Here. a twist is that we have to start from index 1 and not 0 so I put a random char at index 0, which won't get used. Also the concept of inverse modulo is used here which is pow(x,-1,y) which is the inverse of x%y.
