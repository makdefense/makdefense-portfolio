# [THM Splunk Investigations]

**TryHackMe Path**: [Challenge]  
**Lab Topic**: [Conti]  
**Date Completed**: [06/21/2026]

**Lab Link**: [https://tryhackme.com/room/contiransomwarehgh]

---

## 🧠 Summary

> In this challenge, I investigated a compromised Microsoft Exchange server that had been impacted by ransomware. Using Splunk, I analyzed server logs, security events, process
activity, and network-related data to determine how the attackers gained access and what actions they performed after compromising the system.

The investigation focused on identifying the initial attack vector, tracing suspicious activity on the Exchange server, and understanding how the ransomware infection unfolded. 
I reviewed indicators such as unusual web requests, command execution, suspicious files, attacker-controlled processes, and signs of privilege abuse or lateral movement.

This room reinforced how Splunk can be used during incident response to reconstruct an attack timeline, detect post-exploitation behavior, and identify the techniques used by 
attackers after compromising a vulnerable server. It also helped strengthen my ability to investigate ransomware activity, analyze Exchange server compromise evidence, and 
connect different log sources to understand the full scope of an intrusion.

---

## 🎯 Objectives
- [ ] An Exchange server was compromised with ransomware. Use Splunk to investigate how the attackers compromised the server.

---

## 🧰 Tools Used
- THM AttackBox
- Splunk
  
---

## 📊 Analysis & Screenshots

*** Exchange Server Compromised  ***

> In this section, I answered several questions related to performing an investigation of a compromised Exchange server using Splunk. Numerous employees reported that they
could not log in to Outlook due to Conti ransomware. For the first question, I was tasked with identifying the location of the ransomware. After launching Splunk and inputting
the query:

index=* cmd.exe

I was able to retrieve the following file path:

C:\Users\Administrator\Documents\cmd.exe
>
> <img width="1015" height="376" alt="1" src="https://github.com/user-attachments/assets/d0786a41-b65c-4edf-a20e-dddd291a5949" />
> <img width="752" height="490" alt="2" src="https://github.com/user-attachments/assets/726fd01d-f758-46b9-a984-5d93228cfe59" />
> <img width="1139" height="643" alt="3" src="https://github.com/user-attachments/assets/64642c10-78e0-49b3-b2f9-bd07d7084b4f" />

> I then identified the Sysmon event ID for the related file creation event:

11
>
> <img width="1037" height="851" alt="4" src="https://github.com/user-attachments/assets/7c0b20cf-24b7-4dc2-8471-1d71fe2d22be" />

> The MD5 hash of the ransomware was identified as:

290c7dfb01e50cea9e19da81a781af2c
>
> <img width="770" height="557" alt="5" src="https://github.com/user-attachments/assets/91435539-733e-4271-967b-f6f929e04ae5" />
> <img width="691" height="692" alt="6" src="https://github.com/user-attachments/assets/ff080b99-bdae-4d54-941e-3069c2246f58" />

> The file that was saved to multiple locations was:

readme.txt
>
> <img width="1117" height="594" alt="7" src="https://github.com/user-attachments/assets/c806f8db-e116-41bf-acd7-c43507ed5d2a" />

> The attacker used a specific command to add a new user to the compromised system. The command identified was:

net user /add securityninja hardToHack123$
>
> <img width="625" height="479" alt="8" src="https://github.com/user-attachments/assets/e31c9c95-696b-46f8-9404-72342c85528b" />
> <img width="863" height="285" alt="9" src="https://github.com/user-attachments/assets/20c6c266-70a3-4723-a39b-508feaa644f8" />

> The attacker then migrated the process for better persistence. The migrated process image and the original process image used when the attacker accessed the system were
identified as:

C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe

C:\Windows\System32\wbem\unsecapp.exe
>
> <img width="1164" height="1019" alt="10" src="https://github.com/user-attachments/assets/33a861cb-2855-4128-8091-9c5fbf2562be" />

> The attacker retrieved system hashes. The process image used to retrieve the system hashes was identified as:

C:\Windows\System32\lsass.exe
>
> <img width="1095" height="991" alt="11" src="https://github.com/user-attachments/assets/0776e456-b84f-4fee-9da3-dbaac30cd5b3" />

> The web shell exploit deployed to the system was identified as:

i3gfPctK1c2x.aspx
>
> <img width="1172" height="634" alt="12" src="https://github.com/user-attachments/assets/3a26a75f-0ceb-497a-9bcc-bd264a05b769" />

> The command line that executed this web shell was identified as:

attrib.exe -r \\win-aoqkg2as2q7.bellybear.local\C$\Program Files\Microsoft\Exchange Server\V15\FrontEnd\HttpProxy\owa\auth\i3gfPctK1c2x.aspx

This was found using the query:

index=* "i3gfPctK1c2x.aspx"
>
> <img width="1484" height="763" alt="13" src="https://github.com/user-attachments/assets/9203b58a-0f9c-4d43-94d8-8015a1302ded" />

> Finally, the three CVEs leveraged by this exploit were identified as:

CVE-2018-13374, CVE-2018-13379, CVE-2020-0796
>
> <img width="511" height="617" alt="14" src="https://github.com/user-attachments/assets/f5486bcb-3395-459b-8f30-dfc5904c3ce4" />

--- 

## Reflection

> This lab strengthened my ability to investigate ransomware incidents using Splunk by analyzing logs, identifying suspicious activity, and reconstructing how an attacker
compromised a server. It helped me better understand how Microsoft Exchange servers can be targeted, how attackers move from initial access to execution, and how
ransomware-related activity appears in security data.

I also improved my ability to connect different pieces of evidence, such as web activity, process execution, file changes, and security events, to build a clearer attack 
timeline. This challenge reinforced the importance of careful log analysis, asking the right investigative questions, and using SIEM tools to determine the root cause of a 
compromise.
