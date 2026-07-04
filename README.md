# Cryptonite Cybersecurity Task Phase

This repository contains my notes and writeups from the Cryptonite Cybersecurity Task Phase. I wrote these while working through hands-on challenges in Linux, cryptography, reverse engineering, binary exploitation, digital forensics, web exploitation, and CTFs.

Each file records my reasoning, failed attempts, commands and scripts I used, and what I learned—not just final answers. The repo exists to keep that process in one place instead of scattered across challenge platforms.

**Topics:** Linux · Cryptography · Reverse Engineering · Binary Exploitation · Digital Forensics · Web Exploitation · CTFs

## About the Task Phase

Cryptonite is a student cybersecurity program built around practical work. The path I followed:

- **Weeks 1–2:** Linux command-line basics via [pwn.college Linux Luminarium](https://pwn.college/linux-luminarium/)
- **Between phases:** [OverTheWire Bandit](https://overthewire.org/wargames/bandit/) for SSH, file navigation, and encoding
- **Later phase:** [picoCTF](https://play.picoctf.org/) challenges across multiple domains, selected [TryHackMe Advent of Cyber](https://tryhackme.com/) days, and [NiteCTF](https://nitectf.com/)

Not every challenge here has a complete writeup. This is a record of the work I documented, not a full solution set.

## Repository Overview



### `Linux_Luminarium/`

Notes from pwn.college's Linux Luminarium modules—shell usage, documentation and man pages, piping, permissions, and basic user administration.

### `Overthewire_Bandit/`

Bandit levels 0–13. Mostly SSH, finding files, and working with encodings and compressed data.

### `pico.ctf/`

picoCTF writeups grouped by category:


| Folder                 | Topics                                                                                    |
| ---------------------- | ----------------------------------------------------------------------------------------- |
| `Web_Exploitation/`    | Cookie tampering, SQL injection, XXE/SOAP, HTML and robots.txt inspection, path traversal |
| `Cryptography/`        | Caesar and Vigenère ciphers, RSA, modular arithmetic, substitution ciphers, Morse code    |
| `Forensics/`           | Wireshark, file type identification, ExifTool, hex editing, steganography                 |
| `Reverse_Engineering/` | GDB, Java vault-door source reading, introductory ARM assembly                            |
| `Binary_Exploitation/` | Buffer overflows, format string leaks, introductory heap problems                         |
| `General_Skills/`      | SSH, binary search, endianness                                                            |


Some entries stop mid-challenge—for example, SQLi writeups where I got the first injection working but not the full exploit chain.

### `Advent_of_Cyber/`

Notes from five Advent of Cyber days: metadata forensics, YARA and Windows malware analysis, XXE with Burp Suite, and Frida on a browser game.

### `nitectf.md`

NiteCTF competition notes. Partial progress on three challenges, including a multi-stage Freakanada chain (ExifTool, Vigenère, Git history, Discord bot, spectrogram) where I reached the last steps but missed the Morse code piece.

## Tools

- **Languages & Scripting** :
Bash, Python

- **Linux Utilities** :
SSH, `grep`, `find`, `strings`, `base64`, piping and redirection

- **Security Tools** :
GDB, pwntools, Burp Suite, browser dev tools, ExifTool, Wireshark, Gobuster, John the Ripper, YARA, Frida, FLOSS, netcat

- **Platforms** :
pwn.college, OverTheWire, picoCTF, TryHackMe, NiteCTF

I also used dcode.fr for quick cipher checks when I was still learning the underlying math.

## Skills Developed

- **Working from the shell**: navigation, permissions, reading docs to figure out unfamiliar commands.

- **Web**: spotting and trying basic SQLi, XXE, and cookie manipulation.

- **Crypto**: classical ciphers and modular arithmetic, with some gaps I noted explicitly in the writeups.

- **Forensics**: inspecting file metadata, packet captures, and binary file structure.

- **Reverse engineering**: reading source and using GDB to follow assembly.

- **Binary exploitation**: introductory buffer overflows, format string leaks, and heap basics.

- **CTF work**: chaining OSINT, encoding, and file analysis steps under time pressure.

## Learning Philosophy

These writeups are rough on purpose. I kept notes when something failed, when I had to google a basic command, or when I got a flag without fully understanding why it worked—like using an online RSA decoder before revisiting the math later.

The goal was to learn how to work through unfamiliar problems, not to produce a clean list of solved flags. If an entry ends abruptly or admits confusion, that usually reflects where I actually was at the time.
