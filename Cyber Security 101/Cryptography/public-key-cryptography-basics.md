# [Cryptography]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Public Key Cryptography Basics]  
**Date Completed**: [08//2025]

---

## 🧠 Summary

> In this lab, 

---

## 🎯 Objectives
- [ ] Learn about
     
---

## 🧰 Tools Used
- THM AttackBox
- THM Linux Command Line
  
---

---

## 📊 Analysis & Screenshots

> After launching AttackBox, i logged in using SSH with user "user" and password "Tryhackme123" to IP Address "10.201.81.144."
> <img width="734" height="169" alt="crypto1" src="https://github.com/user-attachments/assets/d6986ead-f04c-4dcd-816b-07b52dfbb32d" />

> I then was give a practical to do at the end of the room. I had to use GPG to decrypt the message that was in "~/Public-Crypto-Basics/Task-7" and retrieve the secret word To do this, I first had to change
directories to up to "Task-7," so first i inputted "cd /home/user/Public-Crypto-Basics," pressed "enter," then inputted "cd Task-7," then pressed "enter." After being in the directory i inputted "ls" to listed the
content of the selected directory. What was displayed was two files "message.gpg" and "tryhackme.key," "message.gpg" was the message we had to decrypt, so i then had to import the "tryhackme.key" first before
decrypting "message.gpg." I did this by inputting "gpg --import tryhackme.key," then pressed "enter." I was then able to decrypt the "message.gpg" file by inputting "gpg --decrypt message.gpg," and figured out the
secret word was "Pineapple."
> <img width="733" height="371" alt="crypto2" src="https://github.com/user-attachments/assets/9ab57a5c-08f1-433a-9b74-289ebbfdf67a" />

---

## Reflection

> This lab provided me with knowledge about 
