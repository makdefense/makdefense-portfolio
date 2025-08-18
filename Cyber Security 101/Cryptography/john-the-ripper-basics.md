# [Cryptography]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [John the Ripper: The Basics]  
**Date Completed**: [08//2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding

---

## 🎯 Objectives
- [ ] Learn about 
     
---

## 🧰 Tools Used
- THM AttackBox
- 
  
---


## 📊 Analysis & Screenshots

> After launching the Virtual Machine: Crypto - JTR v04, I first read through "Cracking Basic Hashes" section, then went along to start the first practical, for the first practical i had to determine the type of
hash of the file "hash1.txt." To do this i navigated to the directory "Task04" by inputting "ls," then pressing "enter" to see all the directories, then I inputted "cd John-the-Ripper-The-Basics," then pressed
"enter," then inputted "cd Task04," and pressed "enter" to fully get into the directory "Task04." From there i inputted "ls" to list all the files that were in that directory and saw the "hash1.txt" file, i then
inputted "cat hash1.txt" to display the contents of the file which was the hash value of "2e728dd31fb5949bc39cac5a9f066498." After discovering the hash value for the file i then launched the python tool to identify
the specific type of hash, i inputted "python3 hash-id.py," then pressed "enter," then copied and pasted the hash: "2e728dd31fb5949bc39cac5a9f066498," then pressed "enter" and got the hash type of "MD5."
> <img width="1026" height="426" alt="jtr1" src="https://github.com/user-attachments/assets/ec7a2243-5c54-42d5-903b-015bf281c458" />

> Next i had to figure out the cracked value of the "hash1.txt" file, i did this by inputting "john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash1.txt," then pressing "enter." This then
displayed "biscuit" as the cracked value of "hash1.txt."
> <img width="1358" height="226" alt="jtr2" src="https://github.com/user-attachments/assets/4ca14af5-16d3-40f6-8845-8ed93aa9d3fb" />

> I then had to figure out the hash type of "hash2.txt." I did this by inputting "cat hash2.txt," then pressing "enter" to get the full hash value which was "1A732667F3917C0F4AA98BB13011B9090C6F8065," i then
inputted "python3 hash-id.py," then pressed "enter," then copied and pasted the hash: "1A732667F3917C0F4AA98BB13011B9090C6F8065," then pressed "enter" and got the hash type of "SHA-1."
> <img width="1000" height="410" alt="jtr3" src="https://github.com/user-attachments/assets/d6f7b0ec-9003-43f4-8ce8-da3f6c234000" />

> Next i had to figure out the cracked value of "hash2.txt" file, i did this by inputting "john --format=Raw-SHA1  --wordlist=/usr/share/wordlists/rockyou.txt hash2.txt," then pressing "enter." This then
displayed "kangeroo" as the cracked value of "hash2.txt."
> <img width="1333" height="224" alt="jtr4" src="https://github.com/user-attachments/assets/18367d67-284f-4268-804b-495d61d8c549" />

> Next i had to figure out the hash type of "hash3.txt." I did this by inputting "cat hash3.txt," then pressing "enter" to get the full hash value which was
"D7F4D3CCEE7ACD3DD7FAD3AC2BE2AAE9C44F4E9B7FB802D73136D4C53920140A," i then inputted "python3 hash-id.py," then pressed "enter," then copied and pasted the hash:
"D7F4D3CCEE7ACD3DD7FAD3AC2BE2AAE9C44F4E9B7FB802D73136D4C53920140A," then pressed "enter" and got the hash type of "SHA-256."
> <img width="1002" height="411" alt="jtr5" src="https://github.com/user-attachments/assets/68f43a46-115b-46d6-8813-c8e4bdc2955b" />

> I then had to figure out the crack value of "hash3.txt" file, i did this by inputting "john --format=Raw-SHA256 --wordlist=/usr/share/wordlists/rockyou.txt hash3.txt," then pressing "enter." This then displayed
"microphone" as the cracked value of "hash3.txt."
> <img width="1389" height="242" alt="jtr6" src="https://github.com/user-attachments/assets/d91b6398-9369-4cea-b4ab-1831afd9eaf7" />

> Finally for the Cracking Basic Hashes practical, i did the same steps i did for hash1.txt, hash2.txt, and hash3.txt for hash4.txt and got the hash type: "whirlpool" and cracked value: "colossal."
> <img width="1328" height="418" alt="jtr7" src="https://github.com/user-attachments/assets/d0537452-7a8f-4db0-b375-d0c085324fc8" />
> <img width="1427" height="224" alt="jtr8" src="https://github.com/user-attachments/assets/4c6272df-6d92-4c11-a696-e1d65e8a64fd" />

>






---

## Reflection

> This lab provided me with knowledge about 
