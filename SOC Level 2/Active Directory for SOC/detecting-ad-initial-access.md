# [Active Directory for SOC]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Detecting AD Initial Access]  
**Date Completed**: [10/05/2026]

**Lab Link**: [https://tryhackme.com/room/detectingadinitialaccess]

---

## 🧠 Summary

> In this lab, I learned how to detect Active Directory initial access attacks by analyzing IIS, NPS, and Windows Security logs. I reviewed authentication and access-related events to
identify suspicious activity that could indicate an attacker attempting to gain an initial foothold in the environment. The lab strengthened my ability to correlate information across
multiple log sources, recognize abnormal access patterns, and investigate potential threats within a Windows and Active Directory environment.

---

## 🎯 Objectives
- [ ] Analyze IIS logs to detect web application attacks and web shell activity
- [ ] Correlate Exchange/OWA authentication events with Windows Security logs
- [ ] Investigate VPN credential attacks using NPS event logs
- [ ] Investigate post-authentication activity to determine the impact of a breach
- [ ] Build investigation timelines by correlating application logs with Windows Security logs

---

## 🧰 Tools Used
- THM AttackBox
- 

---

## 📊 Analysis & Screenshots

*** Detecting Web Shell Deployment ***

> For this section, I had to answer a few questions based on an investigation of web shell activity within the IIS and Sysmon logs. For the first question, I had to determine the
filename of the web shell used by the attacker. After launching the Splunk instance and conducting further investigation, I was able to identify the filename as shell.aspx.
>
> <img width="828" height="479" alt="1" src="https://github.com/user-attachments/assets/1f0ab9e2-31b1-4d97-b6f8-3f824a267d64" />
> <img width="1611" height="636" alt="2" src="https://github.com/user-attachments/assets/0fa156a4-2314-4a8d-a47a-e18ee22296a6" />

> I then had to identify the IP address that was used to interact with the web shell. After reviewing the relevant logs in Splunk, I determined that the source IP address was
203.0.113.47.
>
> <img width="883" height="521" alt="3" src="https://github.com/user-attachments/assets/5a5abefc-bed0-48c7-87a0-41e9c69cac29" />

> I then identified the first reconnaissance command executed by the attacker after gaining access through the web shell. After reviewing the relevant activity in Splunk, I determined
that the attacker executed the whoami command to identify the user account under which the compromised process was running.
>
> <img width="1540" height="723" alt="4" src="https://github.com/user-attachments/assets/8618ce51-50b3-40bd-9dd1-3aad1abfb153" />

*** Detecting OWA Brute-Force Attacks ***

> For this section, I had to investigate the OWA brute-force attack using IIS and Windows Security logs and then answer a set of questions based on my findings. For the first question,
I identified a total of 15 failed login attempts that occurred during the OWA brute-force attack.
>
> <img width="2048" height="512" alt="5" src="https://github.com/user-attachments/assets/8eb31dbb-47a4-4d95-afd3-6aa3365fbc04" />

> I then identified the username that was successfully compromised during the OWA brute-force attack. After reviewing the relevant authentication events, I determined that the
compromised account was sarah.kim.
>
> <img width="390" height="280" alt="6" src="https://github.com/user-attachments/assets/78d1d74c-6ff6-4aab-ba74-7c32f2b516e2" />

> I then identified the source IP address responsible for conducting the OWA brute-force attack. After analyzing the relevant IIS and Windows Security logs, I determined that the attack
originated from 203.0.113.47.
>
> <img width="938" height="777" alt="7" src="https://github.com/user-attachments/assets/e490d075-0b50-4ddb-9be7-282a4969f332" />

> After identifying the successful login, I investigated the attacker’s subsequent activity to determine which path was accessed to reach the Exchange Admin Center. I found that the
attacker accessed the /ecp path.
>
> <img width="971" height="994" alt="8" src="https://github.com/user-attachments/assets/c729e30a-7fa7-4c25-b931-50601a8ba763" />

*** Detecting VPN Credential Attacks ***

> Moving on to this section, I was tasked with answering a few questions based on the VPN investigation covered in the readings. For the first question, I had to identify the username
that was successfully compromised via VPN following the credential attack. After entering the necessary query in Splunk and reviewing the results, I identified the compromised username
as david.chen.
>
> <img width="1386" height="560" alt="9" src="https://github.com/user-attachments/assets/cfa8d8f7-8ce3-4b98-b71c-57a598973dfa" />

> Based on the NPS Access-Accept event, I was able to identify the time of the successful VPN authentication as 10:47:06.
>
> <img width="875" height="825" alt="10" src="https://github.com/user-attachments/assets/917f2d9e-4653-4dd7-a4b1-3981a7928917" />

*** Investigation Challenge ***

> For this scenario, I had to answer a set of questions after reconstructing an attack on one of the organization’s IIS web servers that had been reported to the SOC team through an
alert. For the first question, I had to identify the filename of the web shell deployed by the attacker. After conducting further investigation, I identified the web shell filename as
error.aspx.
>
> <img width="808" height="654" alt="11" src="https://github.com/user-attachments/assets/cd020f33-1ef5-4f32-bc67-261fbe6150b0" />
> <img width="805" height="712" alt="12" src="https://github.com/user-attachments/assets/f1dda6c4-5ade-4285-80d2-d1ba3d616a52" />

> I then identified the first reconnaissance command executed by the attacker through the web shell. After reviewing the relevant activity, I determined that the attacker executed the
hostname command to identify the name of the compromised system.
>
> <img width="1653" height="793" alt="13" src="https://github.com/user-attachments/assets/3efe2c90-e778-4238-87d4-be31dfb827d4" />

> I then identified the URI path used by the attacker to upload the web shell to the server. After reviewing the relevant IIS activity, I determined that the web shell was uploaded
through /internalapp/upload.aspx.
>
> <img width="627" height="569" alt="14" src="https://github.com/user-attachments/assets/48085495-c2d7-439d-92df-97544211916b" />

> I then determined the time at which the web shell file was created on the server. After reviewing the relevant event data, I identified the file creation time as 10:40:33.
>
> <img width="1141" height="998" alt="15" src="https://github.com/user-attachments/assets/2a894059-52f1-42f8-b6c6-1d3950995492" />

---

## Reflection

> This lab strengthened my ability to investigate potential initial access attacks by analyzing and correlating IIS, NPS, and Windows Security logs. It improved my understanding of how
different log sources can work together to reveal suspicious authentication activity, unusual access attempts, and other indicators of compromise. Overall, the lab gave me more hands-on
experience with the type of log correlation and investigative analysis used by SOC analysts when identifying and validating potential threats in an Active Directory environment.
