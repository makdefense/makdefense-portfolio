# [Windows Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Windows Logging for SOC]  
**Date Completed**: [02//2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding 

---

## 🎯 Objectives
- [ ] 

---

## 🧰 Tools Used
- THM Attackbox
- THM 

---

## 📊 Analysis & Screenshots

*** Security Log: Authentication ***

> For this room, I began by answering questions under this section. For the first question, I had to investigate the "Practice-Security.evtx" file on the VM's Desktop, then figure
out which IP performed a brute-force of the THM-PC. To figure this out i first launched the "Practice-Security.evtx" file, then navigated to the top of the "Event Viewer," selected
"View," then "Sort By," then "Event ID." After doing all of this i discovered that the log with the Event ID of 4625 means that it was a failed log in. So upon further investigation
of that specific log i retrieved the IP of "10.10.53.248" that performed the brute-force of the THM-PC.
>
> <img width="716" height="372" alt="1" src="https://github.com/user-attachments/assets/c64454a0-41fb-4481-910f-ae8ddf62bb04" />
> <img width="661" height="311" alt="2" src="https://github.com/user-attachments/assets/16001e43-a7ac-43a9-952b-386549250bbf" />
> <img width="650" height="299" alt="3" src="https://github.com/user-attachments/assets/1f385a44-62a4-4823-883c-9b0ddf6a267e" />

> Moving on to the next question i had to figure out which user has been breached as a result of the attack. Upon further investigation i determined that the user "Administrator" had
been breached.

> For the last question for this section i had to figure out the Logon ID of the malicious RDP login. To figure this out i navigated to the Event with the timestamp of
"5/17/2025 10:53:41 PM" and the Event ID of 4624. I then selected it to investigate further and discovered that the Logon ID was "0x183C36D."
>
> <img width="623" height="240" alt="4" src="https://github.com/user-attachments/assets/e0fdca12-6ad1-46e6-929c-39cfb18c01da" />
> <img width="723" height="414" alt="5" src="https://github.com/user-attachments/assets/2a3a0571-430a-4eec-bb00-2c52e526ab76" />

*** Security Log: User Management ***

> Moving on to this section i had to then answer a few questions related to the same "Practice-Security.evtx" file. For the first question i had to figure out which user was created
by the attacker soon after the RDP login. To figure this out i navigated, then selected the Event with the timestamp of "5/17/2025 10:54:59" and Event ID 4722. Upon further
investigation of this Event, i determined that the created user was "svc_sysrestore."
>
> <img width="636" height="172" alt="6" src="https://github.com/user-attachments/assets/89ad034b-5d18-45b3-8d25-a9d45a90f378" />
> <img width="646" height="297" alt="7" src="https://github.com/user-attachments/assets/c71c6122-1ccd-4aac-8c3c-54b0b359000a" />

> For the next question i had to figure out which two privileged groups were the backdoor user added to. To figure this out i navigated, then selected both Events with timestamp
"5/17/2025 10:55:24 PM," and "5/17/2025 10:55:12 PM" with Event ID 4732 respectively. Upon further investigation i discovered that the two privileged groups were 
"Backup Operators, Remote Desktop Users."
>
> <img width="679" height="511" alt="8" src="https://github.com/user-attachments/assets/0a9bbd32-89a2-4f04-889b-c7e19229f580" />
> <img width="708" height="555" alt="9" src="https://github.com/user-attachments/assets/3130ac9e-d2e7-411a-ad62-9433bf537231" />

*** Sysmon: Process Monitoring ***

> Moving on to this section i had to answer a few questions related to "Practice-Sysmon.evtx" file on the VM's Desktop. For the first question i had to investigate the file, then
figure out which web browser did Sarah use to browse the web. To figure this out i lauched the "Practice-Sysmon.evtx" file, then navigated, and selected the Event with the timestamp
of "5/18/2025 4:02:29 PM." Upon further investigation i determined that the web browser Sarach used was "Google Chrome."
>
> <img width="678" height="318" alt="10" src="https://github.com/user-attachments/assets/fe3c0628-a771-4145-aed4-bff554ff6c9d" />
> <img width="1253" height="222" alt="11" src="https://github.com/user-attachments/assets/66c85c40-e41e-4030-bc2f-e762004266d6" />
> <img width="850" height="552" alt="12" src="https://github.com/user-attachments/assets/4bd47b6f-d58b-4bf4-a050-f68fa458322e" />

> For the next question i had to which file Sarah downloaded from the browser. To figure this out i navigated, then selected the Event with timestamp "5/18/2025 4:08:58 PM" with
Event ID 3. Upon further investigation i discovered that the file that Sarah downloaded was linked as "C:\Users\sarah.miller\Downloads\ckjg.exe."
>
> <img width="1164" height="273" alt="13" src="https://github.com/user-attachments/assets/25513064-2e1c-4c19-9419-860fdd998fcc" />
> <img width="914" height="435" alt="14" src="https://github.com/user-attachments/assets/d628c6e3-044d-4ecf-a27f-bc3d8623f79b" />

> For the last question of this section i had to figure out which URL the file was downloaded from. To figure this out i navigated, then selected the Event with the timestamp of
"5/18/2025 4:07:38 PM" and Event ID 15. Upon further investigation i determined the URL to be "http://gettsveriff.com/bgj3/ckjg.exe."
>
> <img width="1113" height="185" alt="15" src="https://github.com/user-attachments/assets/59ccb3a7-8796-4794-968d-67848008b607" />
> <img width="907" height="471" alt="16" src="https://github.com/user-attachments/assets/3e2a8e43-8582-415d-a5b3-499c41182b51" />

*** Sysmon: Files and Network ***

> Moving on to this section i had to answer a few questions related to the same "Practice-Sysmon.evtx" file. For the first question i had to figure out which file was created by
the downloaded malware to persist on the host. To figure this out i selected the Event with the timestamp of "5/18/2025 4:08:46 PM" and Event ID 11. Upon further investigation
I discovered that the file created was linked as "C:\Users\sarah.miller\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\DeleteApp.url."
>
> <img width="1211" height="206" alt="17" src="https://github.com/user-attachments/assets/5a9114b9-4ae6-441c-8419-4ee889f6de1c" />
> <img width="1035" height="298" alt="18" src="https://github.com/user-attachments/assets/f7f6010b-3e87-4a8e-990d-b55306604fea" />

> For the next question i had to figure out what the Command & Control server malware was connected to. To figure this out i navigated, then selected the Event with the timestamp
of "5/18/2025 4:08:58 PM" and Event ID 3. I then discovered that the server the C2 was connected to was "193.46.217.4:7777."
>
> <img width="1374" height="229" alt="19" src="https://github.com/user-attachments/assets/202f8108-9f36-41a0-955f-146e19e2f145" />
> <img width="706" height="235" alt="20" src="https://github.com/user-attachments/assets/e9c5223d-6287-4ae3-9162-56c783a3d232" />

> For the last question, i had to figure out which domain does the malicious IP correspond to. To figure this out i navigated, then selected the Event with the timestamp of
"5/18/2025 4:08:58 PM" and Event ID 22. Upon further investigation i retrieved the domain of "hkfasfsafg.click."
>
> <img width="1352" height="237" alt="21" src="https://github.com/user-attachments/assets/30744a0e-15c6-49b1-8911-e08a599d0f7e" />
> <img width="711" height="441" alt="22" src="https://github.com/user-attachments/assets/66e355ed-b1eb-49bd-a156-9ede72ccffa0" />

*** PowerShell: Logging Commands ***

> For this last section of the room, i had to answer a few questions based on the Administrator's PS history on the VM. For the first question i had to figure out which PowerShell
command was executed first. To figure this out i had to first navigate through the VM to find the Text Document "ConsoleHost_history," which was located in directory "PSReadLine."
After launching the Text Document, i discovered that the first executed PowerShell command was "Get-ComputerInfo."
>
> <img width="1259" height="605" alt="23" src="https://github.com/user-attachments/assets/415d7d2e-7b48-48ce-bbfb-4435393a8b05" />
> <img width="674" height="329" alt="24" src="https://github.com/user-attachments/assets/54da8e02-ea03-483f-aa11-20319b80a9e6" />

> Moving on to the next question i had to figure out when the Administrator ran the first PS command. To determine this i had to right-click on the "ConsoleHost_history" Text
Document, then select Properties. I then retrieved the date of "May 18, 2025."
>
> <img width="943" height="675" alt="25" src="https://github.com/user-attachments/assets/f65a7a11-096a-4451-9d4b-17f80320257b" />
> <img width="619" height="670" alt="26" src="https://github.com/user-attachments/assets/4b1a303c-05ab-45ca-9eb2-765e64ffa75d" />

>


























--- 

## Reflection

> This lab strengthened my ability to detect post-exploitation activity by analyzing logs, filesystem artifacts, and attacker command execution patterns.
