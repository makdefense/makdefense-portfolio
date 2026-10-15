# [Active Directory for SOC]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Detecting AD Lateral Movement]  
**Date Completed**: [10/14/2026]

**Lab Link**: [https://tryhackme.com/room/detectingadlateralmovement]

---

## 🧠 Summary

> In this lab, I learned how to detect lateral movement techniques involving SMB, PsExec, and Remote Desktop Protocol (RDP) by analyzing Windows Event Logs in Splunk. I reviewed
authentication, process execution, and remote access activity to identify suspicious behavior that could indicate an attacker moving between systems within a network. This lab improved
my understanding of how common lateral movement techniques appear in log data and how Splunk can be used to investigate and detect them.

---

## 🎯 Objectives

- [ ] Detect AD discovery commands through process creation and PowerShell Script Block logs
- [ ] Identify SMB-based lateral movement through admin share access patterns
- [ ] Identify PsExec usage through service installation artifacts, named pipe creation, and correlate source and destination events
- [ ] Detect RDP-based lateral movement using Logon Type 10 and trace multi-hop chains through Logon ID correlation and process artifacts
- [ ] Correlate artifacts across source and destination systems to trace an attacker's path

---


## 🧰 Tools Used
- THM AttackBox
- Splunk

---

## 📊 Analysis & Screenshots

*** Discovery and Reconnaissance ***

> For this section, I had to investigate the discovery activity and then answer a few questions. First, I had to determine which discovery command the attacker executed. After launching
the Splunk instance and reviewing the relevant events, I identified the first command executed by the attacker as:

nltest /domain_trusts
>
> <img width="954" height="693" alt="1" src="https://github.com/user-attachments/assets/dab79c04-2a1d-42fc-9534-7bb45eace866" />
> <img width="1756" height="619" alt="2" src="https://github.com/user-attachments/assets/1144a442-60a3-492c-884d-b2b34846e778" />

> I then identified the full PowerShell command used by the attacker to enumerate domain users. After reviewing the relevant PowerShell activity in Splunk, I determined that the command
was:

Import-Module ActiveDirectory; Get-ADUser -Filter * -Properties MemberOf | Select-Object Name, SamAccountName
>
> <img width="1541" height="636" alt="3" src="https://github.com/user-attachments/assets/0f083b92-fe1a-4477-b44f-9d22778ad8a8" />

*** Detecting SMB Lateral Movement ***

> For this section, I had to investigate SMB admin share access using Windows Security logs and then answer a few questions based on my findings. I first had to determine which account
was used to access the ADMIN$ share. After entering the appropriate query in Splunk and reviewing the results, I identified the account as luke.sullivan.
>
> <img width="2045" height="594" alt="4" src="https://github.com/user-attachments/assets/9eb01008-62dc-4e36-a62f-32baafdf6117" />

> I then identified the account responsible for executing the lateral movement commands. After reviewing the relevant activity in Splunk, I determined that the account was
michelle.smith.
>
> <img width="1003" height="631" alt="5" src="https://github.com/user-attachments/assets/9639c209-b1e4-4313-9339-c25a503ad841" />
> <img width="1505" height="586" alt="6" src="https://github.com/user-attachments/assets/33d5a31e-fea8-4fba-8830-d44a7ab7c194" />
> <img width="1109" height="651" alt="7" src="https://github.com/user-attachments/assets/00951ab0-c779-4c72-b923-f3b71616d6dd" />

*** Detecting PsExec Lateral Movement ***

> Moving on, I had to investigate PsExec lateral movement using Sysmon logs and then answer a few questions based on my findings. I first had to determine the destination host targeted
by the attacker via PsExec. After entering the appropriate query in Splunk and reviewing the results, I identified the destination host as THM-SQL-SRV.

> I then identified the first command executed by the attacker from the source machine using PsExec. After reviewing the relevant Sysmon activity in Splunk, I determined that the
command was:

C:\Tools\PsExec.exe -accepteula \THM-SQL-SRV cmd /c "hostname & whoami & ipconfig"
>
> <img width="1795" height="587" alt="8" src="https://github.com/user-attachments/assets/9f17ec15-f789-4431-8882-3860de7b0533" />

*** Detecting RDP Lateral Movement ***

> For this final walkthrough section, I had to investigate RDP lateral movement using Windows Security and Sysmon logs and then answer a few questions based on my findings. First, I had
to determine the source IP address of the RDP session that connected to the Domain Controller. After conducting further investigation in Splunk, I identified the source IP address as
10.5.30.120.
>
> <img width="2048" height="603" alt="9" src="https://github.com/user-attachments/assets/06fa15c1-4c30-4391-8ef3-ad54c3756e9e" />

> I then identified the original source IP address where the RDP lateral movement chain began. After reviewing the relevant authentication and Sysmon events in Splunk, I determined that
the activity originated from 10.5.50.12.
>
> <img width="2047" height="605" alt="10" src="https://github.com/user-attachments/assets/192a6934-16ee-4bfc-a721-6939f136567c" />

*** Investigation Challenge ***

> For this challenge, I was given a scenario in which the SOC team received an EDR alert for a suspicious service installation named svcupdate on THM-SHR-SRV. The service installation
had not been authorized by the team, so my task was to investigate the lateral movement activity, trace it back to its origin, and answer a series of related questions.

For the first question, I had to identify the full path of the service binary that was installed on the target system. After conducting further investigation, I determined that the full 
path was:

%SystemRoot%\svcupdate.exe
>
> <img width="824" height="370" alt="11" src="https://github.com/user-attachments/assets/968a8de4-952a-4502-b912-351b3e416805" />
> <img width="1168" height="734" alt="12" src="https://github.com/user-attachments/assets/516ffacb-6df5-4814-b0d6-b87dcc568be6" />
> <img width="1144" height="545" alt="13" src="https://github.com/user-attachments/assets/3de3008b-25ee-4e6d-aab9-212dfb260339" />

> Moving on, I identified the account that was used to access the ADMIN$ share on the target server. After reviewing the relevant SMB and authentication activity, I determined that the
account was ryan.chen.
>
> <img width="1900" height="579" alt="14" src="https://github.com/user-attachments/assets/479ef2e4-aa93-4f87-b600-5133d204bbbe" />

> I then identified the source IP address associated with the lateral movement to THM-SHR-SRV. After reviewing the relevant network and authentication activity, I determined that the
connection originated from 10.5.50.15.
>
> <img width="743" height="442" alt="15" src="https://github.com/user-attachments/assets/3c834a3e-33c8-402c-b471-bdb048bb6532" />

> I then identified the first remote command executed by the attacker on the lab machine. After reviewing the relevant activity, I determined that the command was:

"cmd" /c "hostname & whoami & ipconfig"
>
> <img width="1782" height="752" alt="16" src="https://github.com/user-attachments/assets/7f6d1255-a48c-421d-8be6-da062cf3243c" />

> Finally, I identified the host from which the attack originated. After tracing the lateral movement activity back to its source, I determined that the attack originated from THM-HR-WS.
>
> <img width="1942" height="711" alt="17" src="https://github.com/user-attachments/assets/e7535006-0ae1-4634-a33b-c291a4be8aba" />

---

## Reflection

> This lab strengthened my ability to detect and investigate lateral movement within a Windows environment by analyzing SMB, PsExec, and RDP activity in Splunk. It improved my
understanding of how attackers move between systems after gaining initial access and how these techniques appear within Windows Event Logs. The lab also helped me become more
comfortable correlating authentication, process execution, and remote access events to identify suspicious behavior and reconstruct attacker activity.
