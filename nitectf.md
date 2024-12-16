I attempted several challs but the following ones are the only ones where I made progress. Other than these, I started learning about the pwn module because of the CTF. I will also try to use qemu emulation instead of a proper virtualbox as I feel like it will serve me better.


# Cybernotes
Using the gobuster tool, I found the uploads directory in the website, which gave me the login credentials. I logged in but I couldn't figure out what to do afterward


# Beyond a display
Here, I read towers from the top left of the image and the right side had text in hindi which confirmed that it was in India. After this, I followed several metro lines, which I suspected could have this image but before I could progress more, a teammate found the flag.
Another hint here was the multidimensional billboard.

# Freakanada
This is the one where I made major progress and helped the team a lot. I first exiftooled the image we got, which gave me this text:
ZIT HQZI OL GWLEXKTR, WXZ ZIT ZKXZI SOTL OF ZIT LIQRGVL. LTTA ZIT HQZZTKFL. QDGFU ZIT EIQGL, Q WTQEGF QVQOZL: izzhl://woz.sn/yktqatlztof0. GFSN ZIT VGKZIN VOSS LTT ZIT XFLTTF. ZIT PGXKFTN IQL PXLZ WTUXF
On decoding it, I got bit.ly/freakenstein0 which got me to a proton drive from where I downloaded ducky.jpg. ON doing strings to it, we get a github link and in the repository, there are two md files with freaky aah alien characters. On decoding them, we get :
We were here
Somehow forgotten
After that, i look at commits, one of the files is a list of coordinates and another file is a lot of text and on mapping, we get a discord link to a server. the server has a bot. i entered 3301 after a few guesses because cicada. Then it wanted two more primes from the first image. The dimensions of the image were both prime so i entered the product of 3301 and those two numbers and I got coordinates as a result. On entering them in google maps, I reached freaky backshots cliff. Scan qr code and get wav file and on spectrograph we get part of the flag and morse code. on using vigenere cipher and another part of the flag which was in readme of github, we get the flag. I didn't solve it as I missed the morse code but I came very close so im pretty happy. from the screen to the ring to the pen to the king.
