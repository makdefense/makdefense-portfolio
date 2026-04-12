# [SIEM Triage for SOC]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Alert Triage With Splunk]  
**Date Completed**: [04/11/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of using Splunk to quickly triage alerts, investigate activity across multiple data sources, and respond to threats efficiently.

It is a key skill for SOC analysts.
---

## 🎯 Objectives
- [ ] Learn how to properly investigate alerts in a SOC environment.
- [ ] Understand how to investigate brute-force attacks on Linux systems.
- [ ] Discover the persistence mechanism on Windows systems.
- [ ] Analyse a web shell on a vulnerable web server.
- [ ] Learn how to investigate alerts for three given scenarios using Splunk.
      
---

## 🧰 Tools Used
- THM AttackBox
- Splunk

---

## 📊 Analysis & Screenshots

*** Initial Access Alert ***

> In this section, I answered several questions by investigating the following alert:

Alert Details:

Alert Name: Brute Force Activity Detection

Time: 17/09/2025 9:00:21 AM

Target Host: tryhackme-2404

Source IP: 10.10.242.248

My task was to determine whether the activity should be considered suspicious.

For the first question, I identified how many failed login attempts were made against the user john.smith. I launched Splunk and used the query:

index="linux-alert" sourcetype="linux_secure" 10.10.242.248
| search "Failed password for" user="john.smith"
| sort + _time

This returned a total of 500 failed login attempts.
>
> <img width="1001" height="235" alt="1" src="https://github.com/user-attachments/assets/8f5f79d3-cdc8-436f-85ca-7b4ab4e7b0c7" />
> <img width="1033" height="248" alt="2" src="https://github.com/user-attachments/assets/ce665a25-b196-4f8d-9dd6-b848ea1f5fa1" />

> I then determined that the duration of the brute force attack was approximately 5 minutes.
>
> <img width="1142" height="134" alt="3" src="https://github.com/user-attachments/assets/e7222c5d-668e-4d84-8b1d-d91bfdac6ef8" />
> <img width="1165" height="112" alt="4" src="https://github.com/user-attachments/assets/9e45b346-6ac5-4114-9ba1-7ed2c80e0a10" />

> Next, I identified the account the attacker successfully escalated privileges to, which was root, using the query:
index=linux-alert user=root
>
> <img width="556" height="325" alt="5" src="https://github.com/user-attachments/assets/bfa81eb0-53cc-448a-a080-9cf62b99f17d" />
> <img width="1179" height="187" alt="6" src="https://github.com/user-attachments/assets/2d42301d-ffd6-450f-9f93-7b09ab23d855" />

> Finally, I identified the user account created by the attacker for persistence as "system-utm" using the query:
index=linux-alert "new user"
>
> <img width="570" height="260" alt="7" src="https://github.com/user-attachments/assets/86b8ff80-d798-4296-9925-fe550bc96177" />
> <img width="1227" height="323" alt="8" src="https://github.com/user-attachments/assets/6fa5b896-99d0-4c09-8fd5-719adb4103df" />

*** Persistence Alert ***

> In this section, I investigated the following alert:

Alert Details:

Alert Name: Potential Task Scheduler Persistence Identified

Time: 30/08/2025 10:06:07 AM

Host: WIN-H015

User: oliver.thompson

Task Name: AssessmentTaskOne

My objective was to determine whether this activity was suspicious.

For the first question, I identified the ProcessId of the process that created the malicious task using the query:

index="win-alert" EventCode=4698 AssessmentTaskOne
| table _time EventCode user_name host Task_Name Message

This returned the ProcessId 5816.
>
> <img width="560" height="293" alt="9" src="https://github.com/user-attachments/assets/93b94ddf-0470-4077-a17b-206b0b256759" />
> <img width="664" height="250" alt="10" src="https://github.com/user-attachments/assets/15f679b8-53ea-4e1e-8c08-370f8c7ab78a" />

> I then identified the parent process responsible for creating the task, which was cmd.exe.
>
> <img width="526" height="284" alt="11" src="https://github.com/user-attachments/assets/42c5cf21-3ff0-45c1-b48d-d7710d743f94" />
> <img width="610" height="277" alt="12" src="https://github.com/user-attachments/assets/26dee3b2-3994-4cc9-994b-510946989cf6" />

> Next, I determined the local group that the attacker enumerated during discovery. Using the query:
index="win-alert" "DEV-QA-SERVER" localgroup
I found the group to be "Administrators."
>
> <img width="539" height="248" alt="16" src="https://github.com/user-attachments/assets/b66db03a-bc85-4e80-b3fc-90f5447004a0" />
> <img width="775" height="768" alt="17" src="https://github.com/user-attachments/assets/bb4e4731-7373-4887-a713-7f9a3d73dad8" />

> Finally, I identified the workstation from which the threat actor logged into host WIN-H015 as "DEV-QA-SERVER." This was found using the query:
index="win-alert" "workstation name"
>
> <img width="501" height="307" alt="13" src="https://github.com/user-attachments/assets/8639448c-994c-40b4-a218-d173823d2d18" />
> <img width="351" height="181" alt="14" src="https://github.com/user-attachments/assets/a1f85375-6ca3-4e1b-af51-24c01b897764" />
> <img width="672" height="699" alt="15" src="https://github.com/user-attachments/assets/05ab8c8d-d1e2-4317-8d52-636b40fcb786" />

*** Web Shell Alert ***

> In the final section, I investigated the following alert:

Alert Details:

Alert Name: Potential Web Shell Upload Detected

Time: 14/09/2025 09:31:51 AM

Resource: http://web.trywinme.thm

Suspicious IP: 171.251.232.40

My task was to determine whether the activity should be considered suspicious.

For the first question, I identified when the brute-force activity using Hydra began. I used the query:

index=web-alert 171.251.232.40
| table _time clientip useragent uri_path method status
| sort + _time

This returned the timestamp 2025-09-14 21:20:27.
>
> <img width="472" height="271" alt="18" src="https://github.com/user-attachments/assets/e4fa0e10-d599-406a-98ea-24be42bba584" />
> <img width="778" height="413" alt="19" src="https://github.com/user-attachments/assets/bd45eb0a-c89d-43db-b881-6187581c1169" />

> I then identified the user agent used by the attacker when interacting with the web shell as:
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/138.0.0.0 Safari/537.36
>
> <img width="526" height="166" alt="20" src="https://github.com/user-attachments/assets/884706fb-0ac1-47f2-9282-c8fc396209df" />
> <img width="1485" height="123" alt="21" src="https://github.com/user-attachments/assets/6723202b-85db-4ef0-92ec-08780f70808c" />

> Finally, I determined that the attacker made a total of 4 requests to the server via the web shell, based on the query shown in the screenshot.
>
> <img width="1492" height="567" alt="22" src="https://github.com/user-attachments/assets/85d8f4cb-428f-429a-b732-1e5c70d9eccb" />

--- 

## Reflection

> This lab strengthened my ability to use Splunk to triage alerts and investigate malicious activity efficiently.
