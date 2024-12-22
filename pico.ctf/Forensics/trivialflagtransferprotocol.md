# WHat I did
 First I tried to figure out what pcapng is. After learning about it, i then downloaded wireshark and opened the file using it. I got overwhelmed by the number of files and asked chatGPT what to do. Export objects then TFTP and then we get a bunch of files. I downloaded all. There are three images and some text files with rot13 encoded text in it. 
 On decoding it, I got:
 
TFTP DOESNT ENCRYPT OUR TRAFFIC SO WE MUST DISGUISE OUR FLAG TRANSFER. FIGURE OUT A WAY TO HIDE THE FLAG AND I WILL CHECK BACK FOR THE PLAN

I USED THE PROGRAM AND HID IT WITH -DUEDILIGENCE .CHECKOUTTHEPHOTOS

There was also a file called program.deb and I googled what .deb is and its for debian. Then I unzipped it using a tool called 'ar' and i got a folder and one of the files was steghide. Then I realised that I should do steg. It asked for password which is DUEDILIGENCE and then I got a flag.txt and then the flag. 
