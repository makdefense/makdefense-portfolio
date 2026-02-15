# [Web Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Detecting Web Attacks]  
**Date Completed**: [02/14/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of 
---

## 🎯 Objectives
- [ ] Understand the common methods used for data exfiltration.
- [ ] Learn how to detect exfiltration attempts using network traffic analysis.
- [ ] Identify signs of exfiltration on endpoint devices.
- [ ] Correlate logs in a SIEM to uncover hidden exfiltration channels.

---

## 🧰 Tools Used
- THM 

---

## 📊 Analysis & Screenshots

*** Log Based Detection ***

> For this room, I had to answer a few questions under the section of "Log Based Detection." I had to analyze a "access.log" file on the Desktop. For the first question i had to
figure out the Attacker's User-Agent while performing the directory fuzz. To figure this out i first launched the "access.log" file located on the Desktop, browsed through all the
requests to find repeated GET requests to different endpoints. Upon finding the repeated GET requests to different endpoints i retrieved the User-Agent "FFUF v2.1.0."
>
> <img width="473" height="263" alt="1" src="https://github.com/user-attachments/assets/7db5d9fc-52d1-43b0-9e57-dc24d38b5f4d" />
<img width="473" height="263" alt="1" src="https://github.com/user-attachments/assets/7db5d9fc-52d1-43b0-9e57-dc24d38b5f4d" />

>


--- 

## Reflection

> This lab provided me with knowledge on how to detect data exfiltration attempts across various network channels.
