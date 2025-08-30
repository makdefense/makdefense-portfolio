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
- THM JohnTheRipper
  
---


## 📊 Analysis & Screenshots

> After launching the Virtual Machine: Crypto-JTR v04, I first read through the "Cracking Basic Hashes" section and then proceeded to start the first practical. For the first practical, I had to determine the type of
hash of the file "hash1.txt." To do this, I navigated to the directory "Task04" by inputting "ls," then pressing "enter" to see all the directories, then I inputted "cd John-the-Ripper-The-Basics," then pressed
"enter," then inputted "cd Task04," and pressed "enter" to fully get into the directory "Task04." From there, I entered "ls" to list all the files in that directory and saw the "hash1.txt" file. I then
input "cat hash1.txt" to display the contents of the file, which was the hash value of "2e728dd31fb5949bc39cac5a9f066498." After discovering the hash value for the file, I then launched the Python tool to identify
the specific type of hash. I inputted "python3 hash-id.py," then pressed "enter," then copied and pasted the hash: "2e728dd31fb5949bc39cac5a9f066498," then pressed "enter" and got the hash type of "MD5."
> <img width="1026" height="426" alt="jtr1" src="https://github.com/user-attachments/assets/ec7a2243-5c54-42d5-903b-015bf281c458" />

> Next, I had to figure out the cracked value of the "hash1.txt" file. I did this by inputting "john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash1.txt," then pressing "enter." This then
displayed "biscuit" as the cracked value of "hash1.txt."
> <img width="1358" height="226" alt="jtr2" src="https://github.com/user-attachments/assets/4ca14af5-16d3-40f6-8845-8ed93aa9d3fb" />

> I then had to figure out the hash type of "hash2.txt." I did this by inputting "cat hash2.txt" and then pressing "Enter" to retrieve the full hash value, which was "1A732667F3917C0F4AA98BB13011B9090C6F8065." I then
input "python3 hash-id.py," then pressed "enter," then copied and pasted the hash: "1A732667F3917C0F4AA98BB13011B9090C6F8065," then pressed "enter" and got the hash type of "SHA-1."
> <img width="1000" height="410" alt="jtr3" src="https://github.com/user-attachments/assets/d6f7b0ec-9003-43f4-8ce8-da3f6c234000" />

> Next, I had to determine the cracked value of the "hash2.txt" file. I did this by inputting "john --format=Raw-SHA1 --wordlist=/usr/share/wordlists/rockyou.txt hash2.txt," then pressing "enter." This then
displayed "kangaroo" as the cracked value of "hash2.txt."
> <img width="1333" height="224" alt="jtr4" src="https://github.com/user-attachments/assets/18367d67-284f-4268-804b-495d61d8c549" />

> Next, I had to figure out the hash type of "hash3.txt." I did this by inputting "cat hash3.txt," then pressing "enter" to get the full hash value, which was
"D7F4D3CCEE7ACD3DD7FAD3AC2BE2AAE9C44F4E9B7FB802D73136D4C53920140A," I then inputted "python3 hash-id.py," then pressed "enter," then copied and pasted the hash:
"D7F4D3CCEE7ACD3DD7FAD3AC2BE2AAE9C44F4E9B7FB802D73136D4C53920140A," then pressed "enter" and got the hash type of "SHA-256."
> <img width="1002" height="411" alt="jtr5" src="https://github.com/user-attachments/assets/68f43a46-115b-46d6-8813-c8e4bdc2955b" />

> I then had to figure out the crack value of the "hash3.txt" file. I did this by inputting "john --format=Raw-SHA256 --wordlist=/usr/share/wordlists/rockyou.txt hash3.txt," then pressing "enter." This then displayed
"microphone" as the cracked value of "hash3.txt."
> <img width="1389" height="242" alt="jtr6" src="https://github.com/user-attachments/assets/d91b6398-9369-4cea-b4ab-1831afd9eaf7" />

> Finally, for the Cracking Basic Hashes practical, I followed the same steps I took for hash1.txt, hash2.txt, and hash3.txt for hash4.txt, and obtained the hash type: "whirlpool" and the cracked value: "colossal."
> <img width="1328" height="418" alt="jtr7" src="https://github.com/user-attachments/assets/d0537452-7a8f-4db0-b375-d0c085324fc8" />
> <img width="1427" height="224" alt="jtr8" src="https://github.com/user-attachments/assets/4c6272df-6d92-4c11-a696-e1d65e8a64fd" />

> Following this, I was given a "Cracking Windows Authentication Hashes" practical, where I had to first determine the format to crack the hash value of the file "ntlm.txt." So first I had to navigate to the directory
in which the file was, so I input "cd Task05," then pressed "enter," and typed "ls" to see if the file was actually in the directory in which it was. I then input "john --list=formats | grep -iF "NT" to see
if the format was "NT" to crack the file's hash of "5460C85BD858A11475115D2DD3A82333," and it was.
> <img width="945" height="230" alt="jtr9" src="https://github.com/user-attachments/assets/5046ef3b-60d1-49d6-af26-a00f521bf4dc" />

> Next, I had to find the cracked value of the password file "ntml.txt." To do this, I input "john --format=NT --wordlist=/usr/share/wordlists/rockyou.txt ntlm.txt," then pressed "enter," and was given the
cracked value of "mushroom."
> <img width="1268" height="231" alt="jtr10" src="https://github.com/user-attachments/assets/d6770f1d-81cf-4a99-8baf-ece666c4d254" />

> I was then given a practical to crack a /etc/shadow Hash. I had to try to crack the password hash of the root user provided in the "etchashes.txt" file, which was located in the directory "Task06." To do this,
I first input "cd Task06" to navigate to the directory, then input the command "unshadow local_passwd local_shadow > etchashes.txt," which combines /etc/shadow passwords with the /etc/passwd file so
JTR can understand the data that needs to be cracked. Next, I input the command used for breaking the output that I fed to JTR using unshadowing, which was
"john --wordlist=/usr/share/wordlists/rockyou.txt --format=sha512crypt etchashes.txt," then pressed the "enter" button to load the password hash, which was "1234."
> <img width="1365" height="319" alt="jtr11" src="https://github.com/user-attachments/assets/61cb74c4-5d88-40da-9e3e-0e2d4a60c760" />

> Next, I was given a practical to use John's Single Crack Mode to access a hash and crack it in the directory "/John-the-Ripper-The-Basics/Task07/," I had to assume the password belonged to the user "Joker." To do this,
I first navigated to the directory where the "hash07.txt" file was located by inputting "cd John-the-Ripper-The-Basics," then pressing "Enter," followed by "cd Task07" and pressing "Enter" again. I then input "ls" to
list all files and saw the "hash07.txt" file. Next, I input "cat hash07.txt," then "enter" to display the file's hash, which was "7bf6d9bb82bed1302f331fc6b816aada," then input "nano hash07.txt," then "enter" to edit the
file's hash by adding "joker:" because I had to assume the hash belonged to the user "Joker." After exiting nano mode, I then entered "cat hash07.txt" to verify that the file displayed
"joker:7bf6d9bb82bed1302f331fc6b816aada." And it did. I then proceeded with John's single crack mode by inputting "john --single --format=raw-md5 hash07.txt," followed by "enter," which displayed the cracked hash
"Jok3r."
> <img width="528" height="83" alt="jtr12" src="https://github.com/user-attachments/assets/011d65fc-1a45-4cbd-ab8f-4494c12d760a" />
> <img width="961" height="350" alt="jtr13" src="https://github.com/user-attachments/assets/9b052280-0067-497a-819e-ca9dceed37bd" />

> Next, I was given a practical to crack a secured zip file and figure out its password within the directory: "~/John-the-Ripper-The-Basics/Task09/." To do this i first navigated to "Task09" by inputting "cd Task09,"
then "enter," then "ls" to view all the files in the directory and saw the "secure.zip" file, i then had to convert it into hash format so i did this by inputting "zip2john secure.zip > zip_hash.txt," then "enter," then
cracked the hash by inputting "john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt" and got the password: "pass123."
> <img width="1170" height="243" alt="jtr14" src="https://github.com/user-attachments/assets/37fdf0b7-c513-4d7f-a77c-7a0db0649f13" />
> I then had to figure out the contents of the flag that was in the zip file. I did this by inputting "unzip secure.zip," then "enter," then "ls" to confirm the extracted sub-directory was within the directory, and it
was. The directory was called "zippy." I then input "cd zippy," then "enter," to navigate to the directory, then "ls" to see the contents of the directory, and saw a "flag.txt" file, then finally "cat flag.txt" to
display the flag, which was "THM{w3ll_d0n3_h4sh_r0y4l}."
> <img width="754" height="173" alt="jtr15" src="https://github.com/user-attachments/assets/200ac6a1-c780-4380-bcc6-550999fc25ff" />

> Next, I had to do a practical that involved cracking password-protected RAR archives, which was to crack the password for the "secure.rar" file located in the directory "Task10." To do this, I input "cd Task10" to
navigate to the directory where the RAR file was located, then "enter," then "ls" to make sure the secure.rar file was located in the directory, then input the command "rar2john secure.rar > rar_hash.txt" to convert
the RAR file into a hash format that JTR could understand. After converting the RAR file, I then input "john --wordlist=/usr/share/wordlists/rockyou.txt rar_hash.txt" to crack the password, which was "password."
> <img width="1176" height="451" alt="jtr16" src="https://github.com/user-attachments/assets/d526ab8c-925e-46a4-a9f0-89749e1e53e3" />
> I then had to determine the contents of the flag that was in the RAR file. I did this by inputting "unrar x secure.rar," then "enter," then "ls" to confirm that the RAR file was extracted, and discovered the "flag.txt"
file. Finally, I input "cat flag.txt" to display the contents of the flag, which was "THM{r4r_4rch1ve5_th15_t1m3}."
> <img width="759" height="368" alt="jtr17" src="https://github.com/user-attachments/assets/fe485190-b566-4fc0-bb0a-45f0066de7de" />

> Next, I had to do a practical that involved cracking SSH Keys with John. I had to crack the hash of the "id_rsa" file, which was located in the directory "Task11." To do this, I input "cd Task11" to navigate to the
directory where the SSH file was located, then "enter," then "ls" to make sure the SSH file was located in the directory, then input the command "/opt/john/ssh2john.py id_rsa > id_rsa_hash.txt" to convert the
"id_rsa" private key into hash formatso JTR can crack it. After converting the private key, I then cracked it by inputting "john --wordlist=/usr/share/wordlists/rockyou.txt id_rsa_hash.txt," which gave the password
"mango."
> <img width="1223" height="484" alt="jtr18" src="https://github.com/user-attachments/assets/d02a824c-41af-4c07-954b-ab067c253fd7" />

---

## Reflection

> This lab provided me with knowledge about 
