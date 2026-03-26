# [Threat Analysis Tools]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [File and Hash Threat Intel]  
**Date Completed**: [03//2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding 

---

## 🎯 Objectives
- [ ] 
      
---

## 🧰 Tools Used
- THM AttackBox
- 
---

## 📊 Analysis & Screenshots

*** Filenames and Paths ***

> In this section, i had to answer a question related to filename heuristic indicators. I had to figure out the file and the indicator because a file displayed one of
the indicators mentioned. I first launched CTI files, then upon further investigation i saw that the file name was payroll.pdf and according to the information under
"filename heuristic indicators" the indicator type for payroll.pdf was Double extensions.
>
> <img width="818" height="319" alt="1" src="https://github.com/user-attachments/assets/1564da33-ad4b-4a8a-9d0a-7333e6765c18" />
> <img width="1110" height="488" alt="2" src="https://github.com/user-attachments/assets/43fafcd1-fd9b-4898-9787-438d043ec49a" />

*** File Hash Lookup ***

> Moving on to this section, i had to answer a few questions by investigating the application name "bl0gger" within the CTI files folder. The first question was to
figure out the SHA256 hash of the file bl0gger. To figure this out i first located the file within the CTI folder to confirm that i was there, then launched
PowerShell, then inputted the command Get-FileHash .\bl0gger.exe, then "enter." After doing so i was able to retrieve the SHA256 hash of
"2672b6688d7b32a90f9153d2ff607d6801e6cbde61f509ed36d0450745998d58" for the application "bl0gger."
>
> <img width="685" height="336" alt="3" src="https://github.com/user-attachments/assets/1504783e-c54a-4de6-aaf4-acb5cb2264cc" />
> <img width="647" height="350" alt="4" src="https://github.com/user-attachments/assets/019a7494-fc78-4675-90bb-d2fb95cb8122" />
> <img width="809" height="678" alt="5" src="https://github.com/user-attachments/assets/63974582-1823-4690-a131-4f03837011d0" />

> Moving on to the next question for this section, i had to figure out the latest threat label used to identify the malicious file on VirusTotal. To figure this out
i launched VirusTotal, then copied and pasted the SHA256 i discovered into the input field, then clicked "enter." After doing so i discovered the threat label to be
"trojan.graftor/blackmoon."
>
> <img width="1024" height="716" alt="6" src="https://github.com/user-attachments/assets/3cf921fa-c3b5-47a2-86e7-10936a15257a" />
> <img width="997" height="503" alt="7" src="https://github.com/user-attachments/assets/740703e9-2f55-4c6c-9fe0-aa81382c3745" />

> Moving on to the next question i had to figure out when the file was first submitted for analysis. To figure this out i clicked the details tab, which led me to
discover the first submission time and date to be "2025-05-15 12:03:49"
>
> <img width="947" height="924" alt="8" src="https://github.com/user-attachments/assets/bca2bdc4-ccb0-4aa5-84dc-807fa886e1bc" />

> Moving on to the next question, which was related to the application titled "Morse-Code-Analyzer." I had to figure out which vendor classified the file as
non-malicious according to MalwareBazaar. To figure this out i first launched the CTI Files folder to confirm that the Morse-Code-Analyzer was there, i then launched
PowerShell to retrieve the SHA256 hash for the Morse-Code-Analyzer file, launched MalwareBazaar, then copied and pasted the SHA256 hash i retrieved into the input
field of the application, clicked the "enter" button, then upon further investigation i discovered the vendor to be "CyberFortress."
>
> <img width="565" height="313" alt="9" src="https://github.com/user-attachments/assets/d65a6319-8466-4679-b348-5a2be269cfc8" />
> <img width="899" height="144" alt="10" src="https://github.com/user-attachments/assets/97bd2784-d302-4acd-b9df-d4cd7057d85a" />
> <img width="1117" height="793" alt="11" src="https://github.com/user-attachments/assets/f2eb2213-2b89-408e-aa19-9695e380ee25" />
> <img width="1616" height="440" alt="12" src="https://github.com/user-attachments/assets/4f0fc628-1805-44d5-bc3e-4e646baa5ac9" />
> <img width="1216" height="299" alt="13" src="https://github.com/user-attachments/assets/9df02724-8a5f-40d9-9274-3c99f8cd787c" />

> Moving on to the last question of this section, i had to figure out which MITRE technique was flagged for persistence and privilege escalation for the
Morse-Code-Analyzer file. To figure this out i copied and pasted the SHA256 hash for the Morse-Code-Analyzer file into VirusTotal, clicked "enter," then navigated
to the Behavior tab, then further down to MITRE ATT&Ck Tactics & Techniques, then under Privilege Escalation i discovered that the technique that was flagged to be
"DLL Side-Loading" which was under the sub-technique "Hijack Execution Flow."
>
> <img width="1043" height="739" alt="14" src="https://github.com/user-attachments/assets/c3f1324d-9574-46ed-a32d-e06ebffe7a6f" />
> <img width="1081" height="424" alt="15" src="https://github.com/user-attachments/assets/4f2337cb-96b0-4884-a358-b0026b1f02c1" />
> <img width="980" height="544" alt="16" src="https://github.com/user-attachments/assets/7ddd3125-83b9-45bf-8ab9-5ff9387a9a59" />

*** Sandbox Analysis ***

> 
















--- 

## Reflection

> This lab strengthened my ability to 
