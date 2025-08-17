# [Cryptography]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Hashing Basics]  
**Date Completed**: [08/16/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding 

---

## 🎯 Objectives
- [ ] Learn about Hash functions and collisions
- [ ] Learn about the role of hashing in authentication systems
- [ ] Learn how to recognize stored hash values
- [ ] Learn how to crack hash values
- [ ] Learn about the use of hashing for integrity protection
     
---

## 🧰 Tools Used
- THM AttackBox
- THM Linux
- Website: hashcat.net
  
---


## 📊 Analysis & Screenshots

> After launching AttackBox, I read the introduction to Hashing Basics, then was given the first practical to find the SHA256 hash of the "passport.jpg" file in the directory "~/Hashing-Basics/Task-2." To do
this i inputted "ls," to list all the working directories, then pressed "enter" button, Next i changed directories by inputting "cd home/user/Hashing-Basics," after changing to the directory i then inputted
"ls" to list the directories that were in the "Hashing-Basics" directory and what i saw was some other directories which included "Task-2." I then input "cd Task-2," then the "enter" button to switch to that
directory. Next, I input "ls" to list the contents of the "Task-2" directory and saw the "passport.jpg" file that we had to find the hash value for. So to find "passport.jpg" SHA256 hash, I inputted "SHA256
sum passport.jpg," then pressed "enter," and was given the hash value: "77148c6f605a8df855f2b764bcc3be749d7db814f5f79134d2aa539a64b61f02."
> <img width="803" height="320" alt="hash_basic1" src="https://github.com/user-attachments/assets/6ff2462f-119b-4157-8ad7-e5d1eb031f47" />

> I was then given a practical to find the 20th password within a file called "rockyou.txt." To do this, I input the command "head -n 20 rockyou.txt," then pressed the "enter" button. This then displayed
The 20th password is "qwerty."
> <img width="507" height="430" alt="hash_basic2" src="https://github.com/user-attachments/assets/473772ee-6d19-4929-a49f-3106dc3a4583" />

> Next, I was given a practical to crack the hash of "5b31f93c09ad1d065c0491b764d04933" using an online tool. To do this, I used "hashes.com" and entered the "5b31f93c09ad1d065c0491b764d04933" hash into
the input field, and the hash that was given was "tryhackme."
> <img width="507" height="378" alt="hash_basic3" src="https://github.com/user-attachments/assets/e4f54ba9-efd0-40df-a001-0fa2a6732470" />

> I then had to use hashcat to crack the hash "$2a$06$7yoU3Ng8dHTXphAg913cyO6Bjs3K5lBnwq5FJyA6d01pMSrddr1ZG" within Linux, which was saved in the directory "~/Hashing-Basics/Task-6/hash1.txt." To do this, I
first googled the hash's type and saw that the type was "3200," so I then inputted the command "hashcat -m 3200 -a 0 Hashing-Basics/Task-6/hash1.txt rockyou.txt," then pressed "enter," and was given
"85208520" as the cracked hash value.
> <img width="872" height="92" alt="hash_basics4" src="https://github.com/user-attachments/assets/c89bcb55-e783-47f9-94b3-bc2a07679487" />
> <img width="792" height="482" alt="hash_basics5" src="https://github.com/user-attachments/assets/24976c2e-24f1-44c4-9f15-0856c361604c" />

> I then had to use hashcat to crack the SHA2-256 hash "9eb7ee7f551d2f0ac684981bd1f1e2fa4a37590199636753efe614d4db30e8e1" within Linux, which was saved in the directory "~/Hashing-Basics/Task-6/hash3.txt."
To do this, I inputted the command "hashcat -m 1400 -a 0 /Hashing-Basics/Task-6/hash3.txt rockyou.txt," then pressed "enter," and was given "halloween" as the cracked hash value.
>  <img width="927" height="81" alt="hash_basics6" src="https://github.com/user-attachments/assets/c9cbf82f-f084-439a-b31d-ebc96ebdfbf2" />
> <img width="773" height="470" alt="hash-basics67" src="https://github.com/user-attachments/assets/86ec8a80-9206-4b22-b920-2b4ffeb8ac13" />

> Following, I had to use hashcat to crack the hash, "$6$GQXVvW4EuM$ehD6jWiMsfNorxy5SINsgdlxmAEl3.yif0/c3NqzGLa0P.S7KRDYjycw5bnYkF5ZtB8wQy8KnskuWQS3Yr1wQ0" within Linux, which was saved in the directory
"~/Hashing-Basics/Task-6/hash3.txt." I first had to Google the hash's type and saw that the type was "1800," so I then inputted the command "hashcat -m 1800 -a 0 /Hashing-Basics/Task-6/hash3.txt rockyou.txt,"
Then, I pressed "enter" and was given "spaceman" as the cracked hash value.
> <img width="873" height="52" alt="hash_basics8" src="https://github.com/user-attachments/assets/4932d28a-a204-4cd1-ac82-96f76ca70715" />
> <img width="1062" height="477" alt="hash_basics9" src="https://github.com/user-attachments/assets/2a7006a8-56d8-437f-aee9-2267c3c90e14" />

> For the last Password Cracking practical, I had to crack the hash "b6b0d451bbf6fed658659a9e7e5598fe." To do this, I used the website "hashes.com," copied and pasted the hash within the input field, and got
"funforyou" as the cracked hash value.
> <img width="469" height="285" alt="hash_basics10" src="https://github.com/user-attachments/assets/e676948e-7b04-4a0b-aa6b-9d425c5b2a41" />

> Moving on, I was given another exercise to find the SHA256 hash of the "libgcrypt-1.11.0.tar.bz2" file, which was in the "~/Hashing-Basics/Task-7" directory. To do this, I first used the command "cd" to
navigate to the " ~/Hashing-Basics/Task-7" directory, then inputted "ls" to make sure the "libgcrypt-1.11.0.tar.bz2" file was in the directory, then I inputted the command "sha256sum libgcrypt-1.11.0.tar.bz2,"
then pressed "enter," and was given the cracked hash of "09120c9867ce7f2081d6aaa1775386b98c2f2f246135761aae47d81f58685b9c."
> <img width="919" height="131" alt="hash_basics11" src="https://github.com/user-attachments/assets/5299dd31-f770-4203-be8d-245aa3072eff" />

> Next, I had to figure out the hashcat mode number for "HMAC-SHA512 (key = $pass)." To do this, I went to the website: "https://hashcat.net/wiki/doku.php?id=example_hashes#specific_hash_types," and scrolled
through the generic hash types and saw that "HMAC-SHA512 (key = $pass)" fell under the hashcat code number of "1750."
> <img width="428" height="195" alt="hash_basics12" src="https://github.com/user-attachments/assets/38208ead-044f-47f0-a208-48822053aace" />

> For the final practical, I had to use base64 to decode "RU5jb2RlREVjb2RlCg==" which was saved as "decode-this.txt" file in the directory "~/Hashing-Basics/Task-8." To do this i first had to navigate
to the directory "~/Hashing-Basics/Task-8," so i inputted "cd Hashing-Basics," then pressed "enter," then inputted "cd Task-8," then "enter" again, then inputted the "ls" commnad to list the files within
the directory to make sure "decode-this.txt" file was in the directory. To decode "decode-this.txt" file, I inputted the command "base64 -d decode-this.txt," and was given the original word "ENcodeDEcode."
>  <img width="790" height="234" alt="hash_basics13" src="https://github.com/user-attachments/assets/1e2502ca-8f39-449e-b553-013199f53e76" />

---

## Reflection

> This lab provided me with knowledge about 
