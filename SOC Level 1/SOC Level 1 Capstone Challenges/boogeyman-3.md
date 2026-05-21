# [SOC Level 1 Capstone Challenges]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Boogeyman 3]  
**Date Completed**: [05/15/2026]

---

## 🧠 Summary

> In this lab, I continued to develop my end-to-end incident response skills by analyzing a compromised machine resulting from an attacker maintaining persistence and targeting a
CEO through a phishing attack.

---

## 🎯 Objectives
- [ ] Complete Challenge Room
      
---

## 🧰 Tools Used
- THM AttackBox
- Kibana Elastic

---

## 📊 Analysis & Screenshots

*** The Chaos Inside ***

> In this section, I answered questions related to analyzing the new tactics, techniques, and procedures (TTPs) used by the threat group known as the Boogeyman. During the
investigation, I used Elastic (Kibana) for analysis.

The Boogeyman maintained persistence and targeted the CEO, Evan Hutchinson. For the first question, I needed to identify the PID of the process that executed the initial Stage 1 
payload. I launched Kibana, set the date range provided by the security team (August 29–30, 2023), and searched for execution-related events. After investigation, I identified the 
PID as 6392.
>
> <img width="721" height="247" alt="1" src="https://github.com/user-attachments/assets/d212e6fe-f9e7-41fe-a115-af99083b3744" />
> <img width="629" height="613" alt="2" src="https://github.com/user-attachments/assets/f328bfb5-5fff-464b-81ad-25117c20fb60" />
> <img width="433" height="436" alt="3" src="https://github.com/user-attachments/assets/068e9b27-fdf4-46af-8390-292f04690540" />
> <img width="709" height="548" alt="4" src="https://github.com/user-attachments/assets/af41d630-3068-4a1a-8a54-2ba465d3fc3e" />
> <img width="333" height="508" alt="5" src="https://github.com/user-attachments/assets/8e670671-98e1-41e3-8fe8-02f4a1dba1b4" />
> <img width="1106" height="272" alt="6" src="https://github.com/user-attachments/assets/19898892-b8a9-4dfa-8b8a-59ea09ee4606" />

> I then identified the full command-line value showing that the Stage 1 payload attempted to copy a file to another location. The command was:
"C:\Windows\System32\xcopy.exe" /s /i /e /h D:\review.dat C:\Users\EVAN~1.HUT\AppData\Local\Temp\review.dat
>
> <img width="386" height="506" alt="7" src="https://github.com/user-attachments/assets/a4d05438-f83b-4af8-8f90-b60edd915670" />
> <img width="546" height="319" alt="8" src="https://github.com/user-attachments/assets/cb300131-61ca-4553-aafd-702aaf12d717" />

> I also discovered the command used to execute the implanted file:
"C:\Windows\System32\rundll32.exe" D:\review.dat,DllRegisterServer
>
> <img width="372" height="663" alt="9" src="https://github.com/user-attachments/assets/31dbf3c9-485f-4b5f-9298-0463b6824ae8" />
> <img width="976" height="227" alt="10" src="https://github.com/user-attachments/assets/53aa1342-5f80-40b8-b4b1-417e56891f01" />

> Next, I identified the scheduled task created by the malicious script to maintain persistence. The task name was "Review."
>
> <img width="1105" height="572" alt="11" src="https://github.com/user-attachments/assets/28e80732-3743-401c-ad23-a1f0daa4e1fa" />

> When the implanted file executed, it initiated a potential C2 connection. Using the following query:
event provider: "Microsoft-Windows-Sysmon" AND event.code: 3
I identified the C2 IP and port as:
165.232.170.151:80
>
> <img width="1456" height="611" alt="12" src="https://github.com/user-attachments/assets/04a25646-9a25-4b70-a1b7-aa0e04035036" />
> <img width="408" height="175" alt="13" src="https://github.com/user-attachments/assets/897e600c-b4ad-4a8a-981f-9229e3fc69af" />

> I then discovered that the attacker used fodhelper.exe to perform a UAC bypass.
>
> <img width="528" height="493" alt="14" src="https://github.com/user-attachments/assets/3c12ea59-219b-4b14-8c49-62a967a6d955" />
> <img width="1498" height="639" alt="15" src="https://github.com/user-attachments/assets/caae9e38-5155-4b0b-9458-bf08155cc9d6" />

> After gaining elevated privileges, the attacker attempted credential dumping. I identified the GitHub link used to download the tool:
https://github.com/gentilkiwi/mimikatz/releases/download/2.2.0-20220919/mimikatz_trunk.zip
This tool is associated with Mimikatz.
>
> <img width="1271" height="865" alt="16" src="https://github.com/user-attachments/assets/8994f439-1cdd-465c-a73e-fdd6ff6d9e12" />

> After successfully dumping credentials, the attacker used them to access another machine. The compromised credential pair was:
itadmin:F84769D250EB95EB2D7D8B4A1C5613F2

I identified this using the query:
"WKSTN-1327" AND event.provider: "Microsoft-Windows-Sysmon" AND event.code: 1
>
> <img width="1177" height="838" alt="17" src="https://github.com/user-attachments/assets/b9e71b56-5529-4995-9fbc-2d3ab2502d10" />
> <img width="932" height="690" alt="18" src="https://github.com/user-attachments/assets/8cde36c8-76e6-4296-b94f-a4a20a0c56b9" />


> The attacker then attempted to enumerate accessible file shares. The file accessed from a remote share was:
IT_Automation.ps1

I identified this using the query:
"WKSTN 0051" AND powersehll.exe AND *file*
>
> <img width="984" height="750" alt="19" src="https://github.com/user-attachments/assets/14c4d522-904c-412b-8ddb-e3b9cdc3a4f4" />

> The attacker used credentials found within the remote file to continue lateral movement. The credentials retrieved were:
QUICKLOGISTICS\allan.smith:Tr!ckyP@ssw0rd987
>
> <img width="1474" height="815" alt="20" src="https://github.com/user-attachments/assets/95094d6d-c4fb-48f3-b3ab-6f257ef7902d" />

> The hostname of the attacker’s next target machine was identified as:
WKSTN-1327
>
> <img width="392" height="313" alt="21" src="https://github.com/user-attachments/assets/c6006802-fba9-42e4-9272-a712bb523197" />

> After lateral movement, I identified the parent process of the malicious command executed on the second compromised machine as:
wsmprovhost.exe
>
> <img width="900" height="612" alt="22" src="https://github.com/user-attachments/assets/1902f433-8768-49fe-8874-6d0f3380333b" />

> The attacker then dumped additional credentials on the second machine. The newly obtained credentials were:
administrator:00f80f2538dcb54e7adc715c0e7091ec

> After gaining access to the domain controller, the attacker performed a DCSync attack. The additional account identified during this activity was:
backupda
>
> <img width="1223" height="716" alt="23" src="https://github.com/user-attachments/assets/9662e59c-fb46-44f9-8724-9e60810c2880" />

> Finally, the attacker attempted to download a ransomware payload. The download link was:
http://ff.sillytechninja.io/ransomboogey.exe
>
> <img width="1495" height="858" alt="24" src="https://github.com/user-attachments/assets/5721ba1a-29bc-48c8-9e71-6711edb9e3d7" />

--- 

## Reflection

> This lab strengthened my ability to perform end-to-end incident response by analyzing phishing-based attacks, identifying multi-stage payload execution, tracking persistence
mechanisms, detecting privilege escalation, and investigating lateral movement and credential dumping across multiple systems.
