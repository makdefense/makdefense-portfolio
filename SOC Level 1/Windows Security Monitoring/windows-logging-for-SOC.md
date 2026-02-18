# [Windows Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Windows Logging for SOC]  
**Date Completed**: [02/17/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding how to use system logs to detect threats. Logs record system activity and reveal signs of attacks. They help analysts detect
threats early, investigate incidents, understand what attackers did, and protect systems in real time. Mastering log analysis is a key skill for cybersecurity professionals,
especially SOC analysts, because it turns theoretical knowledge into real-world defensive ability.

---

## 🎯 Objectives
- [ ] Understand how to find and interpret important Windows event logs
- [ ] Learn invaluable for monitoring log sources like Sysmon and PowerShell
- [ ] Prepare for using the mentioned logs in SOC-SIM and the following rooms
- [ ] Practice your log analysis skills on multiple event log datasets

---

## 🧰 Tools Used
- THM Attackbox
- THM PowerShell
- THM Sysmon

---

## 📊 Analysis & Screenshots

*** Security Log: Authentication ***

> For this room, I began by answering questions under this section. For the first question, I had to investigate the "Practice-Security.evtx" file on the VM’s desktop and determine
which IP performed a brute-force attack on THM-PC. To do this, I launched the file, navigated to the top of Event Viewer, selected View → Sort By → Event ID. After doing this, I
discovered that Event ID 4625 indicates a failed login. Upon further investigation of that specific log, I retrieved the IP 10.10.53.248, which performed the brute-force attack
against THM-PC.
>
> <img width="716" height="372" alt="1" src="https://github.com/user-attachments/assets/c64454a0-41fb-4481-910f-ae8ddf62bb04" />
> <img width="661" height="311" alt="2" src="https://github.com/user-attachments/assets/16001e43-a7ac-43a9-952b-386549250bbf" />
> <img width="650" height="299" alt="3" src="https://github.com/user-attachments/assets/1f385a44-62a4-4823-883c-9b0ddf6a267e" />

> Moving on to the next question, I had to determine which user account was compromised as a result of the attack. After further investigation, I identified that the breached user
was Administrator.

> For the last question in this section, I needed to determine the Logon ID of the malicious RDP login. To do this, I navigated to the event with the timestamp 5/17/2025 10:53:41 PM
and Event ID 4624. After inspecting the event details, I discovered that the Logon ID was 0x183C36D.
>
> <img width="623" height="240" alt="4" src="https://github.com/user-attachments/assets/e0fdca12-6ad1-46e6-929c-39cfb18c01da" />
> <img width="723" height="414" alt="5" src="https://github.com/user-attachments/assets/2a3a0571-430a-4eec-bb00-2c52e526ab76" />

*** Security Log: User Management ***

> In this section, I answered questions related to the same "Practice-Security.evtx" file. First, I had to determine which user account was created by the attacker shortly after the
RDP login. I navigated to the event with timestamp 5/17/2025 10:54:59 PM and Event ID 4722. After analyzing the event details, I determined that the created user account was
svc_sysrestore.
>
> <img width="636" height="172" alt="6" src="https://github.com/user-attachments/assets/89ad034b-5d18-45b3-8d25-a9d45a90f378" />
> <img width="646" height="297" alt="7" src="https://github.com/user-attachments/assets/c71c6122-1ccd-4aac-8c3c-54b0b359000a" />

> Next, I needed to identify which two privileged groups the backdoor user was added to. I navigated to events with timestamps 5/17/2025 10:55:24 PM and 5/17/2025 10:55:12 PM, both
with Event ID 4732. After reviewing the logs, I found the user was added to:

"Backup Operators"

"Remote Desktop Users"
>
> <img width="679" height="511" alt="8" src="https://github.com/user-attachments/assets/0a9bbd32-89a2-4f04-889b-c7e19229f580" />
> <img width="708" height="555" alt="9" src="https://github.com/user-attachments/assets/3130ac9e-d2e7-411a-ad62-9433bf537231" />

*** Sysmon: Process Monitoring ***

> In this section, I investigated the "Practice-Sysmon.evtx" file. The first question required me to determine which web browser Sarah used. I opened the file, located the event
with timestamp 5/18/2025 4:02:29 PM, and determined that the browser used was Google Chrome.
>
> <img width="678" height="318" alt="10" src="https://github.com/user-attachments/assets/fe3c0628-a771-4145-aed4-bff554ff6c9d" />
> <img width="1253" height="222" alt="11" src="https://github.com/user-attachments/assets/66c85c40-e41e-4030-bc2f-e762004266d6" />
> <img width="850" height="552" alt="12" src="https://github.com/user-attachments/assets/4bd47b6f-d58b-4bf4-a050-f68fa458322e" />

> Next, I had to determine which file Sarah downloaded. I located the event with timestamp 5/18/2025 4:08:58 PM and Event ID 3. After analyzing the event, I discovered the
downloaded file path was:
C:\Users\sarah.miller\Downloads\ckjg.exe
>
> <img width="1164" height="273" alt="13" src="https://github.com/user-attachments/assets/25513064-2e1c-4c19-9419-860fdd998fcc" />
> <img width="914" height="435" alt="14" src="https://github.com/user-attachments/assets/d628c6e3-044d-4ecf-a27f-bc3d8623f79b" />

> For the final question in this section, I had to determine the URL from which the file was downloaded. I navigated to the event with timestamp 5/18/2025 4:07:38 PM and Event ID
15, which showed the source URL:
http://gettsveriff.com/bgj3/ckjg.exe
> <img width="1113" height="185" alt="15" src="https://github.com/user-attachments/assets/59ccb3a7-8796-4794-968d-67848008b607" />
> <img width="907" height="471" alt="16" src="https://github.com/user-attachments/assets/3e2a8e43-8582-415d-a5b3-499c41182b51" />

*** Sysmon: Files and Network ***

> In this section, I analyzed the same "Practice-Sysmon.evtx" file. First, I needed to determine which file was created by the downloaded malware to maintain persistence on the
host. I located the event with timestamp 5/18/2025 4:08:46 PM and Event ID 11. The log revealed that the malware created the file:
C:\Users\sarah.miller\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\DeleteApp.url
>
> <img width="1211" height="206" alt="17" src="https://github.com/user-attachments/assets/5a9114b9-4ae6-441c-8419-4ee889f6de1c" />
> <img width="1035" height="298" alt="18" src="https://github.com/user-attachments/assets/f7f6010b-3e87-4a8e-990d-b55306604fea" />

> Next, I had to identify the Command-and-Control (C2) server the malware connected to. I located the event with timestamp 5/18/2025 4:08:58 PM and Event ID 3, which showed the C2
address:
193.46.217.4:7777
>
> <img width="1374" height="229" alt="19" src="https://github.com/user-attachments/assets/202f8108-9f36-41a0-955f-146e19e2f145" />
> <img width="706" height="235" alt="20" src="https://github.com/user-attachments/assets/e9c5223d-6287-4ae3-9162-56c783a3d232" />

> For the final question, I needed to determine which domain corresponded to the malicious IP. I navigated to the event with timestamp 5/18/2025 4:08:58 PM and Event ID 22, which
revealed the domain:
hkfasfsafg.click
>
> <img width="1352" height="237" alt="21" src="https://github.com/user-attachments/assets/30744a0e-15c6-49b1-8911-e08a599d0f7e" />
> <img width="711" height="441" alt="22" src="https://github.com/user-attachments/assets/66e355ed-b1eb-49bd-a156-9ede72ccffa0" />

*** PowerShell: Logging Commands ***

> In this final section, I analyzed the Administrator’s PowerShell history. First, I needed to determine which PowerShell command was executed first. I navigated through the VM to
locate the "ConsoleHost_history" text document in the PSReadLine directory. After opening it, I discovered that the first executed command was:
Get-ComputerInfo
>
> <img width="1259" height="605" alt="23" src="https://github.com/user-attachments/assets/415d7d2e-7b48-48ce-bbfb-4435393a8b05" />
> <img width="674" height="329" alt="24" src="https://github.com/user-attachments/assets/54da8e02-ea03-483f-aa11-20319b80a9e6" />

> Next, I had to determine when the Administrator executed the first PowerShell command. I right-clicked the ConsoleHost_history file, selected Properties, and retrieved the date:
May 18, 2025
>
> <img width="943" height="675" alt="25" src="https://github.com/user-attachments/assets/f65a7a11-096a-4451-9d4b-17f80320257b" />
> <img width="619" height="670" alt="26" src="https://github.com/user-attachments/assets/4b1a303c-05ab-45ca-9eb2-765e64ffa75d" />

> For the final question, I needed to find a hidden flag stored in a PowerShell history file. I navigated to the ConsoleHost_history file for user thm.bob. After opening it, I
retrieved the hidden flag:
THM{it_was_me!}
>
> <img width="954" height="440" alt="27" src="https://github.com/user-attachments/assets/fff8c31f-2962-4cfa-a693-a924a4a62346" />
> <img width="848" height="544" alt="28" src="https://github.com/user-attachments/assets/c8abc1e5-6d80-4dee-833b-4064e6ba16bd" />

--- 

## Reflection

> This lab strengthened my ability to analyze system logs and detect threats by identifying malicious activity, tracing attacker actions, and correlating system events across
multiple log sources.
