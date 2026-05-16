# [SIEM Triage for SOC]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Boogeyman 3]  
**Date Completed**: [05//2026]

---

## 🧠 Summary

> In this lab, 

---

## 🎯 Objectives
- [ ] Complete Challenge Room
      
---

## 🧰 Tools Used
- THM AttackBox
- 

---

## 📊 Analysis & Screenshots

*** The Chaos Inside ***

> In this section, i had to answer questions related to analyzing the new tactics, techniques, and procedures (TTPs) of the threat group named the Boogeyman. During the
investigation, i am tasked with using Kibana for my analyzation. The Boogeyman continued persistence and now targeted the CEO Evan Hutchinson. For the first question i had to
figure out the PID of the process that executed the initial stage 1 payload. To figure this out i launched Kibana, then set the date range given by the security team for the
incident, which was August 29 and August 30, 2023. I then searched "Execute," then upon investigation i discoverd the PID to be "6392" of the process the executed the stage 1
payload.
>
> <img width="721" height="247" alt="1" src="https://github.com/user-attachments/assets/d212e6fe-f9e7-41fe-a115-af99083b3744" />
> <img width="629" height="613" alt="2" src="https://github.com/user-attachments/assets/f328bfb5-5fff-464b-81ad-25117c20fb60" />
> <img width="433" height="436" alt="3" src="https://github.com/user-attachments/assets/068e9b27-fdf4-46af-8390-292f04690540" />
> <img width="709" height="548" alt="4" src="https://github.com/user-attachments/assets/af41d630-3068-4a1a-8a54-2ba465d3fc3e" />
> <img width="333" height="508" alt="5" src="https://github.com/user-attachments/assets/8e670671-98e1-41e3-8fe8-02f4a1dba1b4" />
> <img width="1106" height="272" alt="6" src="https://github.com/user-attachments/assets/19898892-b8a9-4dfa-8b8a-59ea09ee4606" />

> I then discovered the full command-line value of the execution where that the stage 1 payload attempted to implant a file to another location. The full command-line value
was:
"C:\Windows\System32\xcopy.exe" /s /i /e /h D:\review.dat C:\Users\EVAN~1.HUT\AppData\Local\Temp\review.dat
>
> <img width="386" height="506" alt="7" src="https://github.com/user-attachments/assets/a4d05438-f83b-4af8-8f90-b60edd915670" />
> <img width="546" height="319" alt="8" src="https://github.com/user-attachments/assets/cb300131-61ca-4553-aafd-702aaf12d717" />

> I then discovered the full command-line value of the execution where the implanted file was eventually used and executed by the stage 1 payload. The full command-line value
was:
"C:\Windows\System32\rundll32.exe" D:\review.dat,DllRegisterServer
>
> <img width="372" height="663" alt="9" src="https://github.com/user-attachments/assets/31dbf3c9-485f-4b5f-9298-0463b6824ae8" />
> <img width="976" height="227" alt="10" src="https://github.com/user-attachments/assets/53aa1342-5f80-40b8-b4b1-417e56891f01" />

> Moving onto the next question, i retrieved the scheduled task created by a malicious script when the attacker used the stage 1 payload to establish a persistence mechanism.
The scheduled task identified was "Review."
>
> <img width="1105" height="572" alt="11" src="https://github.com/user-attachments/assets/28e80732-3743-401c-ad23-a1f0daa4e1fa" />

> When the execution of the implanted file inside the machine initiated a potential C2 connection, i had to figure out the IP and port used by this connection. Upon further
analysis, by selecting the appropriate filter fields and using the query:
event provider: "Microsoft-Windows-Sysmon" AND event.code: 3
i identified the IP and port used to be:
165.232.170.151:80
>
> <img width="1456" height="611" alt="12" src="https://github.com/user-attachments/assets/04a25646-9a25-4b70-a1b7-aa0e04035036" />
> <img width="408" height="175" alt="13" src="https://github.com/user-attachments/assets/897e600c-b4ad-4a8a-981f-9229e3fc69af" />

> Moving on i discovered the name of the process used by the attacker to execute a UAC bypass to be:
fodhelper.exe
with the help of ChatGPT.
>
> <img width="528" height="493" alt="14" src="https://github.com/user-attachments/assets/3c12ea59-219b-4b14-8c49-62a967a6d955" />
> <img width="1498" height="639" alt="15" src="https://github.com/user-attachments/assets/caae9e38-5155-4b0b-9458-bf08155cc9d6" />

> Upon gaining high privilege machine access, the attacker attempted to dump the credential inside the machine. I identified the github link used by the attacker to download a tool
for the credential dumping to be:
https://github.com/gentilkiwi/mimikatz/releases/download/2.2.0-20220919/mimikatz_trunk.zip
i found this by searching the query "mimikatz" as this is a well-konown post-exploitation tool used to extract credentials from Windows systems.
>
> <img width="1271" height="865" alt="16" src="https://github.com/user-attachments/assets/8994f439-1cdd-465c-a73e-fdd6ff6d9e12" />

> After successfully dumping the credentials inside the machine, the attacker then used the credentials to gain access to another machine. The username and hash of the new
credential pair was discovered to be:
itadmin:F84769D250EB95EB2D7D8B4A1C5613F2 
i figured this out by using the query:
"WKSTN-1327" AND event.provider: "Microsoft-Windows-Sysmon" AND event.code: 1
>
> <img width="1177" height="838" alt="17" src="https://github.com/user-attachments/assets/b9e71b56-5529-4995-9fbc-2d3ab2502d10" />



















--- 

## Reflection

> This lab strengthened my ability to 
