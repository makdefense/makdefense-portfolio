# [Cyber Threat Intelligence]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Friday Overtime - CTF]  
**Date Completed**: [10/29/2025]

---

## 🧠 Summary

> In this lab, I learned how to investigate a potential threat within a financial institution using multiple programs.

---

## 🎯 Objectives
- [ ] Complete "Friday Overtime"

---

## 🧰 Tools Used
- THM AttackBox
- THM Chromium
- THM CTI Platform
- CyberChef
- VirusTotal
  
---

## 📊 Analysis & Screenshots

*** Challenge Scenario ***

> For this room, I had to complete a practical in which I took charge of a ticket at PandaProbe Intelligence as a CTI analyst. The ticket was considered to be a potential breach because it contained
multiple file attachments, presumed to be malware samples. For the first question, I had to figure out who shared the malware samples. To go about figuring this out, I had to first launch the VM within
THM, then launch Chromium.

> <img width="613" height="190" alt="fot1" src="https://github.com/user-attachments/assets/b31d7e64-c78c-4f55-9950-53801365973a" />

> After launching Chromium, I was directed to a landing page with the header "Panda Probe Intelligence." I had to use the credentials "Username: ericatracy" and "Password: Intel321!" to log in to
the DocIntel platform.

> <img width="892" height="834" alt="fot2" src="https://github.com/user-attachments/assets/eb020391-c742-47db-925b-2861d7a462ff" />

> After logging in to the platform, I was directed to a file attachment that showed it was shared by "Oliver Bennett."

> <img width="1184" height="484" alt="fot3" src="https://github.com/user-attachments/assets/fa112c35-c804-458f-b7c1-959ae58980cf" />

> Moving on to the second question, I had to determine the SHA-1 hash of the file "pRsm.dll" in samples.zip. To figure this out, I navigated to the right of the platform and selected the document
under "Latest documents."

> <img width="633" height="307" alt="fot4" src="https://github.com/user-attachments/assets/bd8519cd-5950-4ef4-baf3-4e35dcb163d9" />

> After selecting that, I was then directed to a "samples.zip" file under "File Attachments." When I clicked the "samples.zip" file, it downloaded the file to the system's "Downloads" folder.

> <img width="500" height="207" alt="fot5" src="https://github.com/user-attachments/assets/5abc50ba-3605-4d68-892a-17de3b41a2ca" />
> <img width="543" height="202" alt="fot6" src="https://github.com/user-attachments/assets/9461f59f-aecb-4045-84de-1bcce53bb42c" />

> After downloading the "samples.zip" file, I double-clicked it to open it and located the "pRsm.dll" file, which needed to be unzipped to obtain its SHA1 hash value.

> <img width="738" height="547" alt="fot7" src="https://github.com/user-attachments/assets/468c8873-9285-434f-8923-00d335b2e0ba" />

> So to unzip this file, I navigated back to the DocIntel platform to retrieve the password to the attached archive and saw that it was "Panda321!"

> <img width="499" height="162" alt="fot8" src="https://github.com/user-attachments/assets/df331828-53bd-4e06-80d3-99b719aaed19" />

> After getting the password, I launched the "Terminal" application and entered the command "pwd" to confirm the current directory. After typing the command, I saw that I was in "/ericatracy"
directory.

> <img width="379" height="86" alt="fot9" src="https://github.com/user-attachments/assets/8dfe2638-b5a6-4e08-b954-fe1268db10c2" />

> I then navigated to the "Downloads" directory, which held the "samples.zip" file by inputting the command "cd Downloads." Then, to unzip the "samples.zip" file, I input the command "unzip samples.zip."
Then "enter," then was prompted to enter the password "Panda321!" After entering the password, all files in the attached archive were unzipped.

> <img width="596" height="291" alt="fot10" src="https://github.com/user-attachments/assets/ce6344e8-e7eb-46e1-a6ba-1fe9cdb17f0f" />

> To retrieve the SHA1 hash value for the "pRsm.dll" file, I input the command "sha1sum pRsm.dll," then "enter," and retrieved the SHA1 hash value of "9d1ecbbe8637fed0d89fca1af35ea821277ad2e8."

> <img width="797" height="123" alt="fot11" src="https://github.com/user-attachments/assets/aded9b6b-2d66-4a73-a0ee-a25446f6952d" />

> Moving on to the third question, I want to figure out which malware framework uses these DLLs as add-on modules. To figure this out, I launched "Google Chrome" on my system and googled "pRsm dll malware
framework," then clicked on the first link that popped up, which was by "WeLiveSecurity."

> <img width="499" height="106" alt="fot12" src="https://github.com/user-attachments/assets/6a8d65d4-5197-49e6-8552-43e1a1ec5fe8" />
> <img width="798" height="206" alt="fot13" src="https://github.com/user-attachments/assets/9e6d908f-971a-4883-b128-e777b62f2ff9" />

> I then navigated the website and saw the malware framework was "MgBot," under the header "Toolset."

> <img width="871" height="402" alt="fot14" src="https://github.com/user-attachments/assets/d99afc71-2781-4da8-9d8b-3bf7cb524936" />

> Moving on to the fourth question, I had to determine which MITRE ATT&CK Technique was associated with the use of pRsm.dll within the "MgBot" framework. To figure this out, I just scrolled down and saw
that the Technique was "T1123."

> <img width="847" height="314" alt="fot15" src="https://github.com/user-attachments/assets/e647c50f-58c1-4de1-a0cf-f928c265e307" />

> For the fifth question, I had to figure out the CyberChef-defanged URL of the malicious download location, first seen on 2020/11/02 on the "WeLiveSecurity" website. To figure this out, I scrolled down
to the header "Technical Analysis," selected the first URL, and copied it.

> <img width="888" height="843" alt="fot16" src="https://github.com/user-attachments/assets/a24a01af-c04e-428c-ad31-87158832cdd1" />

> I then launched the website "CyberChef," hovered over to the left, typed in "defang," selected "defang URL," copied and pasted the URL into the right input field, and retrieved the defanged URL
of "hxxp[://]update[.]browser[.]qq[.]com/qmbs/QQ/QQUrlMgr_QQ88_4296[.]exe" within the output field.

> <img width="1184" height="276" alt="fot17" src="https://github.com/user-attachments/assets/7c074fae-7e28-497c-8aa6-0de72debc15c" />
> <img width="411" height="159" alt="fot18" src="https://github.com/user-attachments/assets/fbd9fb87-1158-47e3-963d-87105ef80a35" />
> <img width="1264" height="609" alt="fot19" src="https://github.com/user-attachments/assets/13f74c8a-e308-42a1-b512-d6842af0a312" />

> Moving on to the sixth question, I had to figure out the CyberChef-defanged IP address of the C&C server first detected on 2020/09/14 using these modules. To figure this out, I went back to the
"WeLiveSecurity" website and navigated to the header "Network," selected the second IP address, and copied it.

> <img width="871" height="352" alt="fot20" src="https://github.com/user-attachments/assets/d0e98ed2-9e56-4d7d-8ad0-4bafd3fd6a1a" />

> Next, I went back to CyberChef, hovered over to the left, and typed in "defang" within the input field, selected defanged IP, took the IP address I copied from the "WeLiveSecurity" website, and pasted it
into the input field on the right within "CyberChef," and retrieved the defanged IP address of "122[.]10[.]90[.]12."

> <img width="414" height="219" alt="fot21" src="https://github.com/user-attachments/assets/87aea484-8240-4d74-9be6-755ee6a4f09e" />
> <img width="907" height="621" alt="fot22" src="https://github.com/user-attachments/assets/17891696-b619-4eeb-b440-8269e73faeb4" />

> For the last question, I had to determine the MD5 hash of the SpyAgent family of spyware, hosted on the same IP address and targeting Android devices in Jun 2025. To figure this out, I copied the IP
address "122.10.90.12," launched "VirusTotal," then pasted the IP address within the input field.

> <img width="852" height="717" alt="fot23" src="https://github.com/user-attachments/assets/23a1a75c-2fcb-4266-9d19-d2fe947006fa" />

> I then navigated to the "Relations" tab and saw the MD5 hash value "951F41930489A8BFE963FCED5D8DFD79" in the "Communication Files" section on the right under "Android."

> <img width="1110" height="716" alt="fot24" src="https://github.com/user-attachments/assets/4a51ecdf-cc53-47a9-a917-e6a152be1948" />

---

## Reflection

> This lab provided me with knowledge of stepping into the shoes of a Cyber Threat Intelligence Analyst and testing my investigative skills on a potential threat using various programs.

