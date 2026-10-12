# [Active Directory for SOC]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Detecting AD Credential Attacks]  
**Date Completed**: [10/11/2026]

**Lab Link**: [https://tryhackme.com/room/detectingadcredentialattacks]

---

## 🧠 Summary

> In this lab, I learned how to detect several common Active Directory credential attacks in Splunk, including Kerberoasting, AS-REP Roasting, LSASS credential dumping, DCSync, and
NTDS.dit extraction. I analyzed Windows and Active Directory security events to identify suspicious authentication behavior, credential access techniques, and indicators of attempts to
obtain or replicate password data. This lab helped me better understand how attackers target credentials within an Active Directory environment and how Splunk can be used to investigate
and detect these techniques.

---

## 🎯 Objectives

- [ ] Detect Kerberoasting through anomalous TGS requests with RC4 encryption
- [ ] Identify AS-REP Roasting by recognizing TGT requests for accounts with preauthentication disabled
- [ ] Detect LSASS credential dumping through suspicious process access patterns
- [ ] Identify DCSync attacks through unauthorized AD replication requests
- [ ] Detect NTDS.dit extraction through process creation and file write events on domain controllers
- [ ] Correlate credential access artifacts across host and domain controller logs to trace an attacker's escalation path

---


## 🧰 Tools Used
- THM AttackBox
- 

---

## 📊 Analysis & Screenshots

*** Detecting Kerberoasting ***

> For this section, I had to investigate the Kerberoasting activity using the queries above and then answer a few questions. For the first question, I had to determine how many service
accounts were targeted by Kerberoasting. Upon further investigation, I identified a total of 9 service accounts that were targeted by Kerberoasting.
>
> <img width="648" height="403" alt="1" src="https://github.com/user-attachments/assets/f57f673e-0762-4db5-8b78-0850e8b739bb" />
> <img width="2048" height="455" alt="2" src="https://github.com/user-attachments/assets/ad5af7d6-4934-4d20-8fd8-1c777c57e01d" />

> I then identified the account responsible for requesting the service tickets. After reviewing the relevant Kerberos activity in Splunk, I determined that the account was emma.wilson.

> Finally, I identified the source IP address that initiated the Kerberoasting activity. After reviewing the relevant Kerberos events in Splunk, I determined that the activity
originated from 10.5.90.1.

*** Detecting AS-REP Roasting ***

> I had to investigate AS-REP Roasting activity within the Splunk instance and then answer a question based on my findings. I was tasked with determining which account had Kerberos
preauthentication disabled. After reviewing the relevant events, I identified the account as alex.reed.
>
> <img width="2048" height="546" alt="3" src="https://github.com/user-attachments/assets/87774272-2d6b-483a-81f1-30456d06ac85" />

*** Detecting LSASS Credential Dumping ***

> Moving on to this section, I investigated LSASS access events within the Splunk instance and then answered a few questions based on my findings. For the first question, I had to
determine the full path of the process that accessed lsass.exe. After reviewing the relevant events, I identified the process path as C:\Windows\Temp\procdump64.exe.

I also identified the granted access value as 0x1FFFFF. In addition, the DLL shown in the CallTrace revealed the dump method as dbgcore.dll.
>
> <img width="2045" height="628" alt="4" src="https://github.com/user-attachments/assets/47e970ec-94ad-4fa2-9685-e5f093cd8d70" />

*** Detecting DCSync ***

> For this section, I had to investigate the DCSync activity and then answer a few questions based on my findings. For the first question, I had to determine which account performed the
DCSync attack. Upon further investigation, I identified the account as adm-luke.sullivan.

I also identified the Logon_ID associated with the DCSync session as 0x5A01668. Finally, I determined that the source IP address that initiated the DCSync activity was 10.5.90.1.
>
> <img width="2048" height="510" alt="5" src="https://github.com/user-attachments/assets/8849149d-35fa-452d-b43b-2df021234bd9" />

*** Detecting NTDS.dit Extraction ***

> Moving on to this section, I had to investigate NTDS.dit extraction activity and then answer a few questions based on my findings. For the first question, I had to determine the full
command line used to extract NTDS.dit. After conducting further investigation and using the appropriate search query within the Splunk instance, I identified the command line as:

ntdsutil "ac i ntds" "ifm" "create full C:\Perflogs\1" q q
>
> <img width="2047" height="531" alt="6" src="https://github.com/user-attachments/assets/f1ab1b79-f802-4cf3-94c5-8790655f4a5d" />

> I then identified the full shadow copy path from which the attacker copied ntds.dit. After reviewing the relevant activity in Splunk, I determined that the file was copied from:

\?\GLOBALROOT\Device\HarddiskVolumeShadowCopy7\Windows\NTDS\ntds.dit
>
> <img width="1813" height="584" alt="7" src="https://github.com/user-attachments/assets/7de873fb-57cc-4f8b-aeef-6a8707b32f41" />

> Finally, I identified the directory path where the attacker staged the files copied from the shadow copy. After reviewing the relevant events in Splunk, I determined that the files
were staged in:

C:\Windows\Temp
>
> <img width="1099" height="500" alt="8" src="https://github.com/user-attachments/assets/a12ab05b-d3ae-4f67-a162-a0e1928c5f2f" />

*** Investigation Challenge ***

> For this challenge, I had to determine whether a detection rule that triggered in the SIEM for a burst of TGS requests using RC4 encryption from a single source within a 60-second
window represented legitimate application activity or an active intrusion. I then had to determine how far the attacker progressed by answering a series of investigation questions.

For the first question, I had to identify which account was targeted by AS-REP Roasting. After conducting further investigation within Splunk, I determined that the targeted account was 
mia.turner.
>
> <img width="1144" height="704" alt="9" src="https://github.com/user-attachments/assets/8c1df4d9-3fb9-4f8e-8d20-3a390330c97b" />

> I then identified the account responsible for performing the Kerberoasting activity. After reviewing the relevant Kerberos events in Splunk, I determined that the account was
nathan.brooks.
>
> <img width="964" height="618" alt="10" src="https://github.com/user-attachments/assets/fb582c66-b330-4680-aa45-8cec9c19b865" />

> I then investigated the LSASS access activity on the workstation. After reviewing the relevant events in Splunk, I identified rundll32.exe as the process that accessed lsass.exe.

I also identified the granted access value associated with the LSASS dump as 0x1FFFFF.
>
> <img width="1617" height="585" alt="11" src="https://github.com/user-attachments/assets/86075515-e93e-420a-9c4c-696cb323bc77" />

> Finally, I identified the account responsible for performing the DCSync attack. After reviewing the relevant Active Directory events in Splunk, I determined that the account was
adm-luke.sullivan.
>
> <img width="1327" height="757" alt="12" src="https://github.com/user-attachments/assets/6a8d8b92-e0eb-4f59-82ee-d3f70067c4a7" />

---

## Reflection

> This lab strengthened my ability to detect and investigate credential-based attacks within an Active Directory environment using Splunk. It improved my understanding of how techniques
such as Kerberoasting, AS-REP Roasting, LSASS dumping, DCSync, and NTDS.dit extraction appear in security logs. The lab also helped me become more comfortable correlating suspicious
events, recognizing indicators of credential theft, and understanding how attackers attempt to gain deeper access within a Windows domain.
