# What I did
I haven't understood the concepts yet but I had an idea of what to do. I have shared my terminal down below. I removed the filenames to reduce the clutter and make it more readable. I have also saved two videos that I am going to watch on this topic to understand SHA and checksum better. 
```
ctf-player@pico-chall$ ls
checksum.txt  decrypt.sh  files
ctf-player@pico-chall$ cat decrypt.sh

        #!/bin/bash

        # Check if the user provided a file name as an argument
        if [ $# -eq 0 ]; then
            echo "Expected usage: decrypt.sh <filename>"
            exit 1
        fi

        # Store the provided filename in a variable
        file_name="$1"

        # Check if the provided argument is a file and not a folder
        if [ ! -f "/home/ctf-player/drop-in/$file_name" ]; then
            echo "Error: '$file_name' is not a valid file. Look inside the 'files' folder with 'ls -R'!"
            exit 1
        fi

        # If there's an error reading the file, print an error message
        if ! openssl enc -d -aes-256-cbc -pbkdf2 -iter 100000 -salt -in "/home/ctf-player/drop-in/$file_name" -k picoCTF; then
            echo "Error: Failed to decrypt '$file_name'. This flag is fake! Keep looking!"
        fi
        ctf-player@pico-chall$ cat checksum.txt
fba9f49bf22aa7188a155768ab0dfdc1f9b86c47976cd0f7c9003af2e20598f7
ctf-player@pico-chall$ cd files
ctf-player@pico-chall$ ls
02kLdPvr  3azP1Vr5  7iM83rpT  Ds4StPpk	JPzzPv2R  PVAhaXhI  W2hZvcID  aAv6C6d8	fFbQAlD7  lY9YUKSk  sHWDCVFR  whsqK6Xi
3XFTF7vi  7enMn1rk  DUx15XmG  JKlfmBiL	PK3nRKAh  U6Za1XXb  a5BwxEPT  fANUtdte	lCWOa2m6  s1T1hXGi  wR9DoLPS
ctf-player@pico-chall$ cd ..
ctf-player@pico-chall$ sha256sum files/*
87c3b0d3c1ed24251e37b0751349b306686f2a0251a3faafeb0e901bab96b26a  files/02kLdPvr
c3366a02b371e9e36ef62ecffffafb99d5e6f380a8ff2c2ada684e3e528c5ec2  files/ziobqxT9
ctf-player@pico-chall$ sha256sum files/* | grep fba9f49bf22aa7188a155768ab0dfdc1f9b86c47976cd0f7c9003af2e20598f7
fba9f49bf22aa7188a155768ab0dfdc1f9b86c47976cd0f7c9003af2e20598f7  files/87590c24
ctf-player@pico-chall$ cat files/87590c24
Salted__?b?B
<i?4?hQ[)???uj??$??0]?E?X???W?h?rU?G?????d>ctf-player@pico-chall$ ./decrypt.sh ./files/87590c24
picoCTF{trust_but_verify_87590c24}
ctf-player@pico-chall$ Connection to rhea.picoctf.net closed by remote host.
Connection to rhea.picoctf.net closed.
prathamjoshi@Prathams-MacBook-Air ~ % 
```
I am going to watch the following videos on this:
1- https://www.youtube.com/watch?v=orIgy2MjqrA
2- https://www.youtube.com/watch?v=gzLgT1SVW0Q
