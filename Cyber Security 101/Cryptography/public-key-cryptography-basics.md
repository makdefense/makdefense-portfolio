# [Cryptography]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Public Key Cryptography Basics]  
**Date Completed**: [08/15/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding the basics of public key cryptography (PKC), which is the foundation for the most secure communication, authentication, and digital trust in
today's world. I also learned the importance of understanding the common uses of asymmetric encryption in PKC, which is that it gives you context - so it's not just "math with keys," but a practical tool you
know when and how to apply. Then I learn the importance of understanding RSA in PKC, which is like the "alphabet" of asymmetric encryption. Even if you later move on to more advanced or modern algorithms,
knowing RSA gives you a solid base to understand the rest. The importance of understanding DH in PKC is that it is a foundational method for securely agreeing on a shared secret over an insecure channel,
which is something you can't do with symmetric encryption alone. Following this, I then learned about the importance of understanding SSH in the context of PKC, which is that SSH is the day-to-day workhorse of secure
system access, and PKC is the engine that makes it secure. Without understanding SSH in a PKC context, you can't confidently manage or secure remote systems. Next, I learned about the importance of understanding
digital signatures and certificates in PKC, which is that digital signatures prove "who" sent something and that it wasn't altered; certificates prove that the "who" is legitimate. Without them, secure communi-
cation and online trust would collapse. Finally, the importance of understanding PGP and GPG in PKC is that they are the "hands-on workshop" for PKC. They take the theory of PKC and put it into practice for
secure communication, signatures, and file encryption in a way you'll use in the field.

---

## 🎯 Objectives
- [ ] Learn about PKC: Basics
- [ ] Learn about Common Use of Asymmetric Encryption
- [ ] Learn about RSA
- [ ] Learn about Diffie-Hellman Key Exchange
- [ ] Learn about SSH
- [ ] Learn about Digital Signatures and Certificates
- [ ] PGP and GPG
     
---

## 🧰 Tools Used
- THM AttackBox
- THM Linux Command Line
  
---


## 📊 Analysis & Screenshots

> After launching AttackBox, i logged in using SSH with user "user" and password "Tryhackme123" to IP Address "10.201.81.144."
> <img width="734" height="169" alt="crypto1" src="https://github.com/user-attachments/assets/d6986ead-f04c-4dcd-816b-07b52dfbb32d" />

> I was then given a practical to do at the end of the room. I had to use GPG to decrypt the message that was in "~/Public-Crypto-Basics/Task-7" and retrieve the secret word To do this, I first had to change
directories to up to "Task-7," so first i inputted "cd /home/user/Public-Crypto-Basics," pressed "enter," then inputted "cd Task-7," then pressed "enter." After being in the directory, I input "ls" to list the
contents of the selected directory. What was displayed were two files: "message.gpg" and "tryhackme.key." "message.gpg" was the message we had to decrypt, so I then had to import the "tryhackme.key" first before
decrypting "message.gpg." I did this by inputting "gpg --import tryhackme.key," then pressing "enter." I was then able to decrypt the "message.gpg" file by inputting "gpg --decrypt message.gpg," and figured out the
secret word was "Pineapple."
> <img width="733" height="371" alt="crypto2" src="https://github.com/user-attachments/assets/9ab57a5c-08f1-433a-9b74-289ebbfdf67a" />

---

## Reflection

> This lab provided me with knowledge about the basics of PKC, RSA, Common Use of Asymmetric Encryption, DH Key Exchange, SSH, Digital Signatures & Certificates, and PGP & GPG.
