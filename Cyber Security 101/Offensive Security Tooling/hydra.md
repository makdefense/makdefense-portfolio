# [Offensive Security Tooling]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Hydra]  
**Date Completed**: [09/21/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding Hydra, which is a widely used tool that teaches you how attackers perform credential-based attacks, and knowing it helps you
identify, test, and defend against those attacks responsibly.

## 🎯 Objectives
- [ ] Learn about and how to use Hydra
      
---

## 🧰 Tools Used
- THM Machine
- THM Hydra

---

## 📊 Analysis & Screenshots

*** Using Hydra ***

> After launching the THM Machine and reading through the Hydra Intro and Using Hydra sections, I was given a practical to use Hydra to brute-force Molly's web password to capture a flag. To go about this,
I first launched the website given for the Hydra Challenge, which was "http://10.201.114.151"

> <img width="1076" height="832" alt="hydra1" src="https://github.com/user-attachments/assets/6676d3cb-a83f-4e0f-8746-5c0f8b9964b3" />

> Next, I went back to the Linux terminal and input the following command to brute-force Molly's web password
"hydra -l molly -P /usr/share/wordlists/rockyou.txt 10.201.114.151 http-post-form "/login:username=^USER^&password=^PASS^:Your username or password is incorrect."
then pressed "enter," which retrieved the web password "sunshine" for Molly.

> <img width="1703" height="204" alt="hydra3" src="https://github.com/user-attachments/assets/a93cafb8-d9ec-4bd0-a44f-07235b766852" />

> I then went back to the Hydra Challenge website on Mozilla Firefox and used the login credentials to log in to the user "molly," and retrieved the flag "THM{2673a7dd116de68e85c48ec0b1f2612e}."

> <img width="1155" height="362" alt="hydra4" src="https://github.com/user-attachments/assets/9b0e3011-f6a3-49d7-b643-5181b3d282ed" />

> I was then given another exercise to brute-force Molly's SSH password to retrieve another flag. To do this, I opened the Linux terminal and ran the following command
"hydra -l molly -P /usr/share/wordlists/rockyou.txt 10.201.114.151 -t 4 ssh"
then, I pressed "enter," which retrieved the SSH password "butterfly" for Molly.

> <img width="1188" height="204" alt="hydra5" src="https://github.com/user-attachments/assets/5bf01af4-a1c5-4cf6-941f-d226711ad8ac" />

> After retrieving the SSH login credentials for Molly, I stayed in the Linux terminal and inputted the command "ssh molly@10.201.114.151," pressed "enter," inputted "yes," and was logged in as Molly
via SSH.

> <img width="783" height="96" alt="hydra6" src="https://github.com/user-attachments/assets/f463a510-ec96-4d21-a5e7-cc832b326963" />

> I then entered the command "ls" followed by "enter" to list all files and directories within the user "molly," and saw the "flag2.txt" file. So I then input "cat flag2.txt," pressed "enter," and
retrieved the flag "THM{c8eeb0468febbadea859baeb33b2541b}."

> <img width="558" height="121" alt="hydra7" src="https://github.com/user-attachments/assets/bac601c5-7655-4607-8321-35cdf1fe50ee" />

---

## Reflection

> This lab provided me with knowledge about Hydra and how to use it by bruteforcing a user's SSH and Web password.
