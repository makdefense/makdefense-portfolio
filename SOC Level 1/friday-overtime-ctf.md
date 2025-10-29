# [Cyber Threat Intelligence]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Friday Overtime - CTF]  
**Date Completed**: [10//2025]

---

## 🧠 Summary

> In this lab, I learned how to

---

## 🎯 Objectives
- [ ]  

---

## 🧰 Tools Used
- THM 
- 
  
---

## 📊 Analysis & Screenshots

*** Challenge Scenario ***

> For this room i had to complete a practical where i had to take charge of a ticket at PandaProbe Intelligence as a CTI analyst. The ticket was considered to be a potential breach, because it contained
multiple file attachments, presumed to be malware samples. For the first question i had to figure out who shared the malware samples. To go about figuring this out i had to first launch the VM within
THM, then launch Chromium.
>
> <img width="613" height="190" alt="fot1" src="https://github.com/user-attachments/assets/b31d7e64-c78c-4f55-9950-53801365973a" />

> After launching chromium, i was directed to a landing page with the header "Panda Probe Intelligence," i had to then use the credentials "Username: ericatracy" and "Password: Intel321!" to login into
the DocIntel platform.
>
> <img width="892" height="834" alt="fot2" src="https://github.com/user-attachments/assets/eb020391-c742-47db-925b-2861d7a462ff" />

> After logging into the platform, i was then directed to the file attachment that showed it was shared by "Oliver Bennett."
>
> <img width="1184" height="484" alt="fot3" src="https://github.com/user-attachments/assets/fa112c35-c804-458f-b7c1-959ae58980cf" />

> Moving onto the second question i had to then figure out the SHA1 hash of the file "pRsm.dll" inside samples.zip. To figure this out i navigated to the right of the platform and selected the document
under "Latest documents."
>
> <img width="633" height="307" alt="fot4" src="https://github.com/user-attachments/assets/bd8519cd-5950-4ef4-baf3-4e35dcb163d9" />

> After selecting that, i was then directed to a "samples.zip" file under "File Attachments" when i clicked the "samples.zip" file it downloaded the file onto the system within the "Downloads" folder.
>
> <img width="500" height="207" alt="fot5" src="https://github.com/user-attachments/assets/5abc50ba-3605-4d68-892a-17de3b41a2ca" />
> <img width="543" height="202" alt="fot6" src="https://github.com/user-attachments/assets/9461f59f-aecb-4045-84de-1bcce53bb42c" />

> After downloading the "samples.zip" file, i then double-clicked the file to open it and located the "pRsm.dll" file that needed to be unzipped to acquire its SHA1 hash value.
>
> <img width="738" height="547" alt="fot7" src="https://github.com/user-attachments/assets/468c8873-9285-434f-8923-00d335b2e0ba" />

> So to unzip this file, i navigated back to the DocIntel platform to retrieve the password to the attached archive and saw that it was "Panda321!"
>
> <img width="499" height="162" alt="fot8" src="https://github.com/user-attachments/assets/df331828-53bd-4e06-80d3-99b719aaed19" />

> Afte getting the password, i then launch the "Terminal" application, then inputted the command "pwd" to confirm the current directory i was in. After typing the command i saw that i was in "/ericatracy"
directory.
>
> <img width="379" height="86" alt="fot9" src="https://github.com/user-attachments/assets/8dfe2638-b5a6-4e08-b954-fe1268db10c2" />

> I then navigated to the "Downloads" directory which held the "samples.zip" file by inputting the command "cd Downloads." Then to unzip the "samples.zip" file i inputted the command "unzip samples.zip,"
then "enter," then was prompted to enter the password, which was "Panda321!" After entering the password every file within the attached archive was unzipped.
>
> <img width="596" height="291" alt="fot10" src="https://github.com/user-attachments/assets/ce6344e8-e7eb-46e1-a6ba-1fe9cdb17f0f" />

> To retrieve the SHA1 hash value for "pRsm.dll" file inputted the command "sha1sum pRsm.dll," then "enter," and retrieved the SHA1 hash value of "9d1ecbbe8637fed0d89fca1af35ea821277ad2e8."
>
> <img width="797" height="123" alt="fot11" src="https://github.com/user-attachments/assets/aded9b6b-2d66-4a73-a0ee-a25446f6952d" />

> Moving onto the third question, i to figure out which malware framework utilizes these DLLs as add-on modules. To figure this out i launch "Google Chrome" on my system and googled "pRsm dll malware
framework," then clicked on the first link that popped up which was by "WeLiveSecurity."
>
> <img width="499" height="106" alt="fot12" src="https://github.com/user-attachments/assets/6a8d65d4-5197-49e6-8552-43e1a1ec5fe8" />
> <img width="798" height="206" alt="fot13" src="https://github.com/user-attachments/assets/9e6d908f-971a-4883-b128-e777b62f2ff9" />

> I then navigated down within the website and saw the malware framework to be "MgBot" which was under the header "Toolset."
>
> <img width="871" height="402" alt="fot14" src="https://github.com/user-attachments/assets/d99afc71-2781-4da8-9d8b-3bf7cb524936" />

> Moving onto the fourth question i had to figure out which MITRE ATT&CK Technique was linked to using pRsm.dll in within the "MgBot" framework. To figure this out i just scrolled down and saw that the
Technique was "T1123."
>
> <img width="847" height="314" alt="fot15" src="https://github.com/user-attachments/assets/e647c50f-58c1-4de1-a0cf-f928c265e307" />

> For the fifth question, 



---

## Reflection

> This lab provided me with knowledge about 

