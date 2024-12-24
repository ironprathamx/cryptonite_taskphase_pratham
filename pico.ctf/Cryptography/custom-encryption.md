# What I did
I used this python code:
```
from random import randint
import sys

a = 94
b = 29
cipher = [260307, 491691, 491691, 2487378, 2516301, 0, 1966764, 1879995, 1995687, 1214766, 0, 2400609, 607383, 144615, 1966764, 0, 636306, 2487378, 28923, 1793226, 694152, 780921, 173538, 173538, 491691, 173538, 751998, 1475073, 925536, 1417227, 751998, 202461, 347076, 491691]
def generator(g, x, p):
    return pow(g, x) % p


def encrypt(plaintext, key):
    cipher = []
    for char in plaintext:
        cipher.append(((ord(char) * key*311)))
    return cipher


def is_prime(p):
    v = 0
    for i in range(2, p + 1):
        if p % i == 0:
            v = v + 1
    if v > 1:
        return False
    else:
        return True


def dynamic_xor_encrypt(plaintext, text_key):
    cipher_text = ""
    key_length = len(text_key)
    for i, char in enumerate(plaintext[::-1]):
        key_char = text_key[i % key_length]
        encrypted_char = chr(ord(char) ^ ord(key_char))
        cipher_text += encrypted_char
    return cipher_text
def test(plain_text, text_key):
    p = 97
    g = 31
    if not is_prime(p) and not is_prime(g):
        print("Enter prime numbers")
        return
    a = randint(p-10, p)
    b = randint(g-10, g)
    print(f"a = {a}")
    print(f"b = {b}")
    u = generator(g, a, p)
    v = generator(g, b, p)
    key = generator(v, a, p)
    b_key = generator(u, b, p)
    shared_key = None
    if key == b_key:
        shared_key = key
    else:
        print("Invalid key")
        return
    semi_cipher = dynamic_xor_encrypt(plain_text, text_key)
    cipher = encrypt(semi_cipher, shared_key)
    print(f'cipher is: {cipher}')

def decrypt(cipher, key):
    plaintext = ""
    for num in cipher:
        decrypted_char = chr(num // (key * 311))  
        plaintext += decrypted_char
    return plaintext
def dynamic_xor_decrypt(cipher_text, text_key):
    decrypted_text = ""
    key_length = len(text_key)
    for i, char in enumerate(cipher_text):
        key_char = text_key[i % key_length]
        decrypted_char = chr(ord(char) ^ ord(key_char))
        decrypted_text = decrypted_char + decrypted_text 
    return decrypted_text

def decode_flag(cipher, text_key, g, p, a, b):

    u = generator(g, a, p)
    v = generator(g, b, p)
    key = generator(v, a, p)
    b_key = generator(u, b, p)
    cipher1 = decrypt(cipher, key)
    plaintext = dynamic_xor_decrypt(cipher1, text_key)

    return plaintext

text_key = "trudeau"
g = 31
p = 97
flag = decode_flag(cipher, text_key, g, p, a, b)
print(flag)
```
Since XOR is symmerical, using it with the same operation and key on the encrypted text will decrypt it. I didn't know about XOR much so I had to watch some videos to figure out that its symmetrical. The other decryption function was relatively easier to come up with. On running the code, I got the flag: picoCTF{custom_d2cr0pt6d_751a22dc}

