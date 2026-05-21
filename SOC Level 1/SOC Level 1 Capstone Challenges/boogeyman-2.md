# [SOC Level 1 Capstone Challenges]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Boogeyman 2]  
**Date Completed**: [05/12/2026]

---

## 🧠 Summary

> In this lab, I further developed my end-to-end incident response skills by analyzing a compromised machine that resulted from a Human Resources Specialist opening a malicious
document.

---

## 🎯 Objectives
- [ ] Complete Challenge Room
      
---

## 🧰 Tools Used
- THM AttackBox
- Terminal
- VirusTotal

---

## 📊 Analysis & Screenshots

*** Spear Phishing Human Resources ***

> In this section, I answered several questions related to analyzing and assessing the impact of a compromise that affected Maxine, a Human Resources Specialist.

I first identified the email used to send the phishing message as "westaylor23@outlook.com
", the victim’s email as "maxine.beck@quicklogisticsorg.onmicrosoft.com
", and the malicious document as "Resume_WesleyTaylor.doc."
>
> <img width="623" height="321" alt="1" src="https://github.com/user-attachments/assets/eaad8cf8-dfd9-407c-82d5-b2582c96195e" />
> <img width="727" height="379" alt="2" src="https://github.com/user-attachments/assets/1ac0f58d-28de-4b18-9d03-f313538b0780" />
> <img width="1195" height="513" alt="3" src="https://github.com/user-attachments/assets/a8b205cc-f40e-401c-830c-8211da129e46" />

> Next, I retrieved the MD5 hash of the malicious document using the terminal. After entering the appropriate command, I obtained the following MD5 hash:
52c4384a0b9e248b95804352ebec6c5b
>
> <img width="749" height="186" alt="4" src="https://github.com/user-attachments/assets/945dfd77-8ad4-47b7-8b8f-0f4a9c2e8de7" />

> The URL used to download the stage 2 payload from the document’s macro was identified as:
https://files.boogeymanisback.lol/aa2a9c53cbb80416d3b47d85538d9971/update.png

I discovered this by submitting the MD5 hash to VirusTotal.
>
> <img width="1174" height="920" alt="5" src="https://github.com/user-attachments/assets/aae4c2db-62a7-4fe4-9334-bd5555632d9a" />

> The process responsible for executing the downloaded stage 2 payload was identified as "wscript.exe."
>
> <img width="781" height="270" alt="6" src="https://github.com/user-attachments/assets/046f5e7b-e6d1-4ef2-acca-ba41f81e96a7" />

> The full path of the malicious stage 2 payload was identified as:
C:\ProgramData\update.js, based on the results from VirusTotal.
>
> <img width="587" height="198" alt="7" src="https://github.com/user-attachments/assets/3b19a82a-ed3c-487c-9cdb-745d661cb3f4" />

> I then identified the PID of the process that executed the stage 2 payload as 4260, and its parent PID as 1124.
>
> <img width="1018" height="276" alt="8" src="https://github.com/user-attachments/assets/defada20-4e0d-4d21-ade9-8e16cd40fc7f" />
> <img width="648" height="156" alt="9" src="https://github.com/user-attachments/assets/3dbd7746-9dec-4c98-b3b8-e9c90d8b0980" />

> The URL used to download the malicious binary executed by the stage 2 payload was identified as:
https://files.boogeymanisback.lol/aa2a9c53cbb80416d3b47d85538d9971/update.exe
>
> <img width="1029" height="226" alt="10" src="https://github.com/user-attachments/assets/bbe857a4-5f2d-42f9-836c-5e5ce72f98b7" />

> The PID of the malicious process used to establish the C2 connection was identified as 6216.
> 
> <img width="956" height="250" alt="11" src="https://github.com/user-attachments/assets/fc1b237d-4ea7-43c7-9035-fd024f8b3b22" />
> <img width="765" height="230" alt="12" src="https://github.com/user-attachments/assets/415a68c4-61a8-4641-a7f1-d80cfc2c1cea" />

> The full path of the malicious process responsible for establishing the C2 connection was identified as:
C:\Windows\Tasks\updater.exe

I determined this using the following command:

vol -f WKSTN-2961.raw windows.dlllist | grep 6216
>
> <img width="1301" height="219" alt="13" src="https://github.com/user-attachments/assets/183aa586-13a9-4e7f-b183-ebe9bdf1e82d" />

> The IP address and port of the C2 connection initiated by the malicious binary were identified as:
128.199.95.189:8080, using the windows.netscan command.
>
> <img width="1251" height="309" alt="14" src="https://github.com/user-attachments/assets/f69cf920-0633-4a8e-a2ee-7cbbd477c35e" />

> The full file path of the malicious email attachment, based on the memory dump, was identified as:
C:\Users\maxine.beck\AppData\Local\Microsoft\Windows\INetCache\Content.Outlook\WQHGZCFI\Resume_WesleyTaylor (002).doc

I discovered this using the command:

vol -f WKSTN-2961.raw windows.filescan | grep .doc
>
> <img width="1284" height="126" alt="15" src="https://github.com/user-attachments/assets/69771c21-11dc-4774-ae52-2eb5b36cc77b" />

> For the final question, I identified the full command used by the attacker to maintain persistent access.

I first created a memory dump using:

vol -f WKSTN-2961.raw windows.memmap --dump --pid 6216

Then, I extracted relevant strings using:

strings WKSTN-2961.raw | grep "schtasks"

This revealed the persistence command used by the attacker:

schtasks /Create /F /SC DAILY /ST 09:00 /TN Updater /TR 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe -NonI -W hidden -c \"IEX ([Text.Encoding]::UNICODE.GetString([Convert]::FromBase64String((gp HKCU:\Software\Microsoft\Windows\CurrentVersion debug).debug)))\"'
>
> <img width="1056" height="117" alt="16" src="https://github.com/user-attachments/assets/e4676aa5-a531-4ec3-bc8a-0fe6df60ce2f" />
> <img width="1510" height="600" alt="17" src="https://github.com/user-attachments/assets/91c1d477-b8a7-4e33-8e62-d876d78a7185" />

--- 

## Reflection

> This lab strengthened my ability to perform end-to-end incident response by analyzing phishing-based attacks, identifying multi-stage payload execution, tracing process
activity, and uncovering persistence mechanisms used by attackers.
