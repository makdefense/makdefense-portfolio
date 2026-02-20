# [Windows Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Windows Threat 1]  
**Date Completed**: [02/20/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding common Initial Access methods on Windows. This knowledge helps defenders recognize how attackers
first enter systems and stop them early. Detecting signs like suspicious logins, malicious files, or unusual activity prevents attackers from escalating
privileges or causing damage. These skills build essential SOC analyst abilities, strengthen incident response, and improve an organization’s overall security posture.

---

## 🎯 Objectives
- [ ] Explore how threat actors access and breach Windows machines
- [ ] Learn common Initial Access techniques via real-world examples
- [ ] Practice detecting every technique using Windows event logs

---

## 🧰 Tools Used
- THM Attackbox
  
---

## 📊 Analysis & Screenshots

*** Initial Access via RDP ***

> For this room, I began by answering questions under this section. I had to analyze the logs of the RDP breach scenario located at the pathway:
C:\Users\Administrator\Desktop\Practice\RDP Case\RDP-Security.evtx.

For the first question, I had to determine which user appeared to be the most actively brute-forced by botnets. To figure this out, I launched the RDP-
Security.evtx file and navigated to the event with the timestamp 5/20/2025 9:57:30 AM and Event ID 4625. Upon further investigation, I determined that the 
user most actively brute-forced by botnets was 
"Administrator."
>
> <img width="536" height="238" alt="1" src="https://github.com/user-attachments/assets/2cc22554-fc1b-4051-8f43-fe92259c7cc6" />
> <img width="819" height="373" alt="2" src="https://github.com/user-attachments/assets/439ca36e-58c4-4977-8e0f-9f53c0426e8d" />
> <img width="798" height="230" alt="3" src="https://github.com/user-attachments/assets/b8591e02-47ca-413b-b2af-8f29b5d46775" />
> <img width="569" height="836" alt="4" src="https://github.com/user-attachments/assets/7de0def2-c8b9-4628-b3fa-d52c3d21bd7b" />

> Moving on to the next question, I had to identify the real workstation name (hostname) of the threat actor. To determine this, I navigated to the
Network Information section for Event ID 4624 and saw that the real workstation name of the threat actor was "DESKTOP-QNBC4UU."
>
> <img width="631" height="827" alt="5" src="https://github.com/user-attachments/assets/6be83f0e-7d99-4774-8e70-674c667ef620" />

*** Initial Access via Phishing *** 

> In this section, I answered several questions by investigating three phishing attachment examples stored in:
C:\Users\Administrator\Desktop\Practice\Phishing Case 1-3.

For the first question, I had to find a hidden flag by running the "www,skype.com" file from the Phishing Case 1 folder. After launching the file, I 
retrieved the hidden flag:
THM{misleading_extension}.
>
> <img width="589" height="322" alt="6" src="https://github.com/user-attachments/assets/3edff7b0-951b-4f90-b9b7-47a8e1c95c55" />
> <img width="881" height="270" alt="7" src="https://github.com/user-attachments/assets/38446486-c33e-43e7-bced-956ac5d03d0d" />
> <img width="656" height="314" alt="8" src="https://github.com/user-attachments/assets/f59c4793-960a-406a-950c-9ebe1aeaf6e9" />

> For the next question, I had to determine which URL the malicious LNK file used to download the next-stage malware by investigating the second
attachment from the Phishing Case 2 folder. After navigating to and selecting the "Official Website" shortcut, I right-clicked it and selected Properties.
From there, I retrieved the URL:
http://wp16.hqywlqpa.thm:8000/cgi-bin/f
>
> <img width="658" height="317" alt="9" src="https://github.com/user-attachments/assets/0c60cec9-17f0-4ff7-87be-eaad20a31617" />
> <img width="1034" height="342" alt="10" src="https://github.com/user-attachments/assets/a6cf5b65-68ba-4b0d-a867-28b71412f503" />
> <img width="1025" height="356" alt="11" src="https://github.com/user-attachments/assets/a371781f-528c-4f5d-a83a-a355f254953a" />
> <img width="689" height="576" alt="12" src="https://github.com/user-attachments/assets/bbf91b7e-6c9b-49f4-a879-4b945ce91ea4" />
> <img width="586" height="618" alt="13" src="https://github.com/user-attachments/assets/0cfb6645-9599-4650-9a54-c020b78b0920" />

> For the last question of this section, I had to find the name of the double-extension file within the Phishing Case 3 folder. After opening the folder,
I identified the file:
best-cat.jpg.exe
>
> <img width="763" height="381" alt="14" src="https://github.com/user-attachments/assets/8b1320f1-6813-47fe-8aea-af4ee9ff1aef" />
> <img width="858" height="307" alt="15" src="https://github.com/user-attachments/assets/acacea6d-ffdd-4eca-8a31-dee652557442" />

*** Continuing Phishing Topic ***

> In this section, I answered several questions by investigating the third phishing case using the attached Sysmon logs:
C:\Users\Administrator\Desktop\Practice\Phishing Case 3\Phishing-Sysmon.evtx.

For the first question, I had to determine which file the user downloaded via the web browser. I launched the log file and selected Event ID 11 with the 
timestamp 5/20/2025 6:58:28 PM. Upon further investigation, I discovered that the downloaded file was:
C:\Users\Administrator\Downloads\top-cats.zip
>
> <img width="874" height="449" alt="16" src="https://github.com/user-attachments/assets/d23ebf2d-df13-4d0d-a339-b187c4ef93aa" />
> <img width="1143" height="488" alt="17" src="https://github.com/user-attachments/assets/e9697a2f-641c-4db5-a681-d7b65bdc89ff" />

> For the next question, I had to determine the folder the user used to extract the suspicious file. I reviewed Event ID 11 with the timestamp 5/20/2025
6:58:43 PM and identified the extraction folder as:
C:\Users\Administrator\Pictures
>
> <img width="1300" height="378" alt="18" src="https://github.com/user-attachments/assets/95398ae8-bf74-4992-8f94-57986f86d271" />

> For the second-to-last question, I had to determine the process ID of the launched phishing malware. I selected Event ID 22 with the timestamp 5/20/2025
6:59:18 PM and discovered that the process ID was 5484. I also identified that the malicious domain the malware attempted to connect to was:
rjj.store
>
> <img width="1266" height="563" alt="19" src="https://github.com/user-attachments/assets/65933c74-6bba-4974-9789-efb52c6cb542" />

*** Initial Access via USB ***

> For the last section of this room, I investigated a typical USB attack chain using the attached Sysmon logs:
C:\Users\Administrator\Desktop\Practice\USB Case\USB-Sysmon.evtx.

For the first question, I had to determine which USB file was launched by the user. I opened the log file and selected Event ID 1 with the timestamp 
5/20/2025 7:34:06 PM, which showed that the file launched by the user was:
E:\Open Sandisk 4GB USB.exe
>
> <img width="986" height="330" alt="20" src="https://github.com/user-attachments/assets/f6bc6dd0-3b65-4cee-8a61-59b9e85412b1" />
> <img width="1310" height="597" alt="21" src="https://github.com/user-attachments/assets/edf88a72-ae08-4c5b-a0d5-e61bd1a5ef5f" />

> For the next question, I had to determine which malicious file the malware dropped to disk. I selected Event ID 13 with the timestamp 5/20/2025 7:34:06
PM and discovered that the file dropped was:
C:\Users\Public\Documents\winupdate.exe
>
> <img width="1319" height="430" alt="22" src="https://github.com/user-attachments/assets/710e4853-bb86-4bb9-9741-878bc6ae9303" />

> For the final question, I had to determine which other USB drive the malware propagated to. I selected Event ID 11 with the timestamp 5/20/2025 7:34:06
PM and discovered that the malware propagated to:
*F:*
>
> <img width="1277" height="583" alt="23" src="https://github.com/user-attachments/assets/f7389395-2e97-408f-bcbc-aa9f206a43e3" />

--- 

## Reflection

> This lab strengthened my ability to explore common Initial Access methods on Windows and detect them effectively.
