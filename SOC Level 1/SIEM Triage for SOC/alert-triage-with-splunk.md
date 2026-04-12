# [SIEM Triage for SOC]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Alert Triage With Splunk]  
**Date Completed**: [04//2026]

---

## 🧠 Summary

> In this lab, I learned the importance of 
---

## 🎯 Objectives
- [ ] 
      
---

## 🧰 Tools Used
- THM AttackBox
- 

---

## 📊 Analysis & Screenshots

*** Initial Access Alert ***

> In this section, i had to answer a few questions based on investigating
Alert Details:
Alert Name: Brute Force Activity Detection
Time: 17/09/2025 9:00:21 AM
Target Host: tryhackme-2404
Source IP: 10.10.242.248
by determining whether it should be considered suspicious. For the first question i had to figure out how many failed login attempts were made on the user john.smith. To figure this
out i first launched Splunk using the given link, then inputting the query:
index="linux-alert" sourcetype="linux_secure" 10.10.242.248
| search "Failed password for" user="john.smith"
| sort + _time
After doing so i was able to retrieve a total of 500 failed login attempts.
>
> <img width="1001" height="235" alt="1" src="https://github.com/user-attachments/assets/8f5f79d3-cdc8-436f-85ca-7b4ab4e7b0c7" />
> <img width="1033" height="248" alt="2" src="https://github.com/user-attachments/assets/ce665a25-b196-4f8d-9dd6-b848ea1f5fa1" />

> I then discovered the duration of the brute force attack to be around 5 minutes.
>
> <img width="1142" height="134" alt="3" src="https://github.com/user-attachments/assets/e7222c5d-668e-4d84-8b1d-d91bfdac6ef8" />
> <img width="1165" height="112" alt="4" src="https://github.com/user-attachments/assets/9e45b346-6ac5-4114-9ba1-7ed2c80e0a10" />

> I then figure out the username the attacker was able to privilege escalate to, which was the user root. I figured this out by entering the query:
index=linux-alert user=root
>
> <img width="556" height="325" alt="5" src="https://github.com/user-attachments/assets/bfa81eb0-53cc-448a-a080-9cf62b99f17d" />
> <img width="1179" height="187" alt="6" src="https://github.com/user-attachments/assets/2d42301d-ffd6-450f-9f93-7b09ab23d855" />

> For the final question of this section i discovered the name of the user account created by the attacker for persistence, which was "system-utm." I figured this out by inputting
the query:
index=linux-alert "new user"
>
> <img width="570" height="260" alt="7" src="https://github.com/user-attachments/assets/86b8ff80-d798-4296-9925-fe550bc96177" />
> <img width="1227" height="323" alt="8" src="https://github.com/user-attachments/assets/6fa5b896-99d0-4c09-8fd5-719adb4103df" />

*** Persistence Alert ***

> In this secton, i had to answer a few questions based on investigating
Alert Details:
Alert Name: Potential Task Scheduler Persistence Identified
Time: 30/08/2025 10:06:07 AM
Host: WIN-H015
User: oliver.thompson
Task Name: AssessmentTaskOne
by determining whether it should be considered suspicious. For the first question i had to figure out the ProcessId of the process that created this malicious task. To figure this
out i entered the query:
index="win-alert" EventCode=4698 AssessmentTaskOne
| table _time EventCode user_name host Task_Name Message
After doing so i was able to retrieve the ProcessId of "5816"
>
> <img width="560" height="293" alt="9" src="https://github.com/user-attachments/assets/93b94ddf-0470-4077-a17b-206b0b256759" />
> <img width="664" height="250" alt="10" src="https://github.com/user-attachments/assets/15f679b8-53ea-4e1e-8c08-370f8c7ab78a" />

> I then discovered the name of the parent process for the process that created this malicious task to be "cmd.exe."
>
> <img width="526" height="284" alt="11" src="https://github.com/user-attachments/assets/42c5cf21-3ff0-45c1-b48d-d7710d743f94" />
> <img width="610" height="277" alt="12" src="https://github.com/user-attachments/assets/26dee3b2-3994-4cc9-994b-510946989cf6" />

> I then found out the local group the attacker enumerated during discovery, which was found on page 2 after inputting the query:
index="win-alert" "DEV-QA-SERVER" localgroup
The local group discovered was "Administrators"
>
> <img width="539" height="248" alt="16" src="https://github.com/user-attachments/assets/b66db03a-bc85-4e80-b3fc-90f5447004a0" />
> <img width="775" height="768" alt="17" src="https://github.com/user-attachments/assets/bb4e4731-7373-4887-a713-7f9a3d73dad8" />

> For the last question of this section i discovered the name of the workstation from which the Threat actor logged into Host: WIN-H015. Which was "DEV-QA-SERVER." It was found by
inputting the query:
index="win-alert" "workstation name"
then navigating to page two.
>
> <img width="501" height="307" alt="13" src="https://github.com/user-attachments/assets/8639448c-994c-40b4-a218-d173823d2d18" />
> <img width="351" height="181" alt="14" src="https://github.com/user-attachments/assets/a1f85375-6ca3-4e1b-af51-24c01b897764" />
> <img width="672" height="699" alt="15" src="https://github.com/user-attachments/assets/05ab8c8d-d1e2-4317-8d52-636b40fcb786" />



















--- 

## Reflection

> This lab strengthened my ability to 
