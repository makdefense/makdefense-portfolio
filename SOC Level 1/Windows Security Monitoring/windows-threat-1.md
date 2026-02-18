# [Windows Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Windows Threat 1]  
**Date Completed**: [02//2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding

---

## 🎯 Objectives
- [ ] 

---

## 🧰 Tools Used
- THM Attackbox
- THM 

---

## 📊 Analysis & Screenshots

*** Initial Access via RDP ***

> For this room, I began by answering questions under this section. I had to analyze the logs of the RDP breach scenario located with the pathway
"C:\Users\Administrator\Desktop\Practice\RDP Case\RDP-Security.evtx." For the first question i had to figure out which user seemed to be the most actively brute-forced by botnets.
To figure this out i launched the "RDP-Security.evtx" file, then navigated to the Event with the timestamp of "5/20/2025 9:57:30 AM," and Event ID 4625. Upon further
investigation i determined that the user that was most actively brte-forced by botnets was "Administrator."
>
> <img width="536" height="238" alt="1" src="https://github.com/user-attachments/assets/2cc22554-fc1b-4051-8f43-fe92259c7cc6" />
> <img width="819" height="373" alt="2" src="https://github.com/user-attachments/assets/439ca36e-58c4-4977-8e0f-9f53c0426e8d" />
> <img width="798" height="230" alt="3" src="https://github.com/user-attachments/assets/b8591e02-47ca-413b-b2af-8f29b5d46775" />
> <img width="569" height="836" alt="4" src="https://github.com/user-attachments/assets/7de0def2-c8b9-4628-b3fa-d52c3d21bd7b" />

> Moving on to the next question, i had to get the real Workstation Name (hostname) of the threat actor





--- 

## Reflection

> This lab strengthened my ability to 
