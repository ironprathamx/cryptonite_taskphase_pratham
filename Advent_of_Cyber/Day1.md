# What I did
I just followed along and did all the steps. It was really cool as I was learning forensic type tools and learnt about exiftool. There are two files song.mp3 and somg.mp3. We check their properties using file file_name command. After that we further inspect somg.mp3 using exiftool after we find out that it is a link. exiftool allows us to realise that it runs a code from a github page. The github page has a comment "Created by the one and only MM". 
The link is https://raw.githubusercontent.com/MM-WarevilleTHM/IS/refs/heads/main/IS.ps1
From here, we get the user MM-WarevilleTHM and we continue the investigation. 
<img width="1278" alt="Screenshot 2024-12-04 at 8 43 46 PM" src="https://github.com/user-attachments/assets/edb5b75d-9b60-41ce-84d1-5537e8c77631">
All of these answers can be found either in the Github pages by investigating further or in the powershell script or the response to exiftool. 
