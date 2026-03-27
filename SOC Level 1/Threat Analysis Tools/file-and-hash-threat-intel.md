# [Threat Analysis Tools]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [File and Hash Threat Intel]  
**Date Completed**: [03/26/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding how to enrich file and hash artifacts using threat intelligence. This skill allows security analysts to
quickly determine whether a file is malicious and understand its context within a broader threat landscape. By taking a file hash (such as SHA-256) and querying
threat intelligence sources, analysts can identify known malware, associated campaigns, related domains or IPs, and previous sightings. This enrichment process
transforms raw data into actionable intelligence, enabling faster and more accurate decision-making during investigations. It also helps prioritize alerts, reduce
false positives, and improve overall incident response by providing deeper insight into attacker behavior and tactics. Ultimately, this skill allows analysts to move
beyond basic detection and perform more effective threat hunting and analysis.

---

## 🎯 Objectives
- [ ] Interpret suspicious filepaths and filenames using heuristics.
- [ ] Generate and validate file hashes.
- [ ] Leverage VirusTotal and MalwareBazaar to enrich newly observed binaries.
- [ ] Extract behaviour from sandbox telemetry and map it to MITRE ATT&CK.
      
---

## 🧰 Tools Used
- THM AttackBox
- Hybrid Analysis
- VirusTotal
- MalwareBazaar

---

## 📊 Analysis & Screenshots

*** Filenames and Paths ***

> In this section, I answered a question related to filename heuristic indicators. I had to identify the file and the associated indicator because a file displayed
one of the listed indicators. I first launched the CTI Files folder, and upon further investigation, I observed that the file name was payroll.pdf. According to the
information under “Filename Heuristic Indicators,” the indicator type for payroll.pdf was double extensions.
>
> <img width="818" height="319" alt="1" src="https://github.com/user-attachments/assets/1564da33-ad4b-4a8a-9d0a-7333e6765c18" />
> <img width="1110" height="488" alt="2" src="https://github.com/user-attachments/assets/43fafcd1-fd9b-4898-9787-438d043ec49a" />

*** File Hash Lookup ***

> In this section, I answered several questions by investigating the application named bl0gger within the CTI Files folder. The first task was to determine the SHA-
256 hash of the file. I located the file to confirm its presence, launched PowerShell, and executed the command:

Get-FileHash .\bl0gger.exe

After running the command, I retrieved the SHA-256 hash:

2672b6688d7b32a90f9153d2ff607d6801e6cbde61f509ed36d0450745998d58
>
> <img width="685" height="336" alt="3" src="https://github.com/user-attachments/assets/1504783e-c54a-4de6-aaf4-acb5cb2264cc" />
> <img width="647" height="350" alt="4" src="https://github.com/user-attachments/assets/019a7494-fc78-4675-90bb-d2fb95cb8122" />
> <img width="809" height="678" alt="5" src="https://github.com/user-attachments/assets/63974582-1823-4690-a131-4f03837011d0" />

> Next, I had to identify the latest threat label associated with the file on VirusTotal. I pasted the SHA-256 hash into VirusTotal and discovered the threat label:

trojan.graftor/blackmoon
>
> <img width="1024" height="716" alt="6" src="https://github.com/user-attachments/assets/3cf921fa-c3b5-47a2-86e7-10936a15257a" />
> <img width="997" height="503" alt="7" src="https://github.com/user-attachments/assets/740703e9-2f55-4c6c-9fe0-aa81382c3745" />

> I then identified when the file was first submitted for analysis by navigating to the “Details” tab. The first submission date and time was:

2025-05-15 12:03:49
>
> <img width="947" height="924" alt="8" src="https://github.com/user-attachments/assets/bca2bdc4-ccb0-4aa5-84dc-807fa886e1bc" />

> Next, I analyzed the application Morse-Code-Analyzer. I retrieved its SHA-256 hash using PowerShell, searched it on MalwareBazaar, and identified the vendor that
classified the file as non-malicious:

CyberFortress
> <img width="565" height="313" alt="9" src="https://github.com/user-attachments/assets/d65a6319-8466-4679-b348-5a2be269cfc8" />
> <img width="899" height="144" alt="10" src="https://github.com/user-attachments/assets/97bd2784-d302-4acd-b9df-d4cd7057d85a" />
> <img width="1117" height="793" alt="11" src="https://github.com/user-attachments/assets/f2eb2213-2b89-408e-aa19-9695e380ee25" />
> <img width="1616" height="440" alt="12" src="https://github.com/user-attachments/assets/4f0fc628-1805-44d5-bc3e-4e646baa5ac9" />
> <img width="1216" height="299" alt="13" src="https://github.com/user-attachments/assets/9df02724-8a5f-40d9-9274-3c99f8cd787c" />

> Finally, I identified the MITRE ATT&CK technique flagged for persistence and privilege escalation. By analyzing the file in VirusTotal and navigating to the
“Behavior” tab, I found that the technique was:

DLL Side-Loading (Hijack Execution Flow)
>
> <img width="1043" height="739" alt="14" src="https://github.com/user-attachments/assets/c3f1324d-9574-46ed-a32d-e06ebffe7a6f" />
> <img width="1081" height="424" alt="15" src="https://github.com/user-attachments/assets/4f2337cb-96b0-4884-a358-b0026b1f02c1" />
> <img width="980" height="544" alt="16" src="https://github.com/user-attachments/assets/7ddd3125-83b9-45bf-8ab9-5ff9387a9a59" />

*** Sandbox Analysis ***

> In this section, I analyzed bl0gger.exe using Hybrid Analysis. I first identified the tags associated with the file, which were:

BlackMoon, Discovery, windows-server-utility
>
> <img width="1961" height="596" alt="17" src="https://github.com/user-attachments/assets/4ef9f52c-4296-4985-888f-b823b72ab070" />

> Next, I identified the stealth command executed by the file by navigating to the “Indicators” section. The command was:

regsvr32 %WINDIR%\Media\ActiveX.ocx /s
>
> <img width="1088" height="497" alt="18" src="https://github.com/user-attachments/assets/d0332122-74f9-4acf-a967-08b776447ea3" />

> I then identified the additional process spawned from the file by reviewing the process tree. The process was:

werfault.exe
>
> <img width="863" height="477" alt="19" src="https://github.com/user-attachments/assets/9d28217c-70fb-4e73-bab7-e1661b7f0dad" />

> Next, I analyzed payroll.pdf and determined that it was masquerading as the Windows file:

svchost.exe
>
> <img width="992" height="207" alt="20" src="https://github.com/user-attachments/assets/1052d20f-9e6d-429a-bc14-7f52b2f3fdd5" />
> <img width="1381" height="431" alt="21" src="https://github.com/user-attachments/assets/8f40f644-3606-4396-934b-189770b8cba4" />

> I also identified the associated URL linked to the file using Hybrid Analysis:

hxxp://121.182.174.27:3000/server.exe
>
> <img width="1464" height="459" alt="23" src="https://github.com/user-attachments/assets/6bc6d1cf-b6a8-41db-bda3-9b08952d84c2" />

> Lastly, I identified that a total of 454 extracted strings were found during sandbox analysis.
>
> <img width="1142" height="803" alt="22" src="https://github.com/user-attachments/assets/f826f02a-9f4f-42bf-8e08-0a5b72cb1de3" />

*** Threat Intelligence Challenge ***

> In this section, I completed a challenge using the file Challenge.bin.sample. I first retrieved the SHA-256 hash using PowerShell:

43b0ac119ff957bb209d86ec206ea1ec3c51dd87bebf7b4a649c7e6c7f3756e7
>
> <img width="1338" height="492" alt="24" src="https://github.com/user-attachments/assets/93bdb1e2-150e-42be-9704-c115a6a24fde" />
> <img width="920" height="305" alt="25" src="https://github.com/user-attachments/assets/f08c4b5c-d742-4bd6-b567-c9c16534b73d" />

> I then identified the malware family tags on VirusTotal:

akira, filecryptor
>
> <img width="1069" height="864" alt="26" src="https://github.com/user-attachments/assets/a193f5c3-3074-475c-ad76-d3d77cfc915b" />
> <img width="1087" height="380" alt="27" src="https://github.com/user-attachments/assets/d43a9eaa-009b-4ed1-85cd-4f08e16fe9d2" />

> I also identified when the file was first observed in the wild:

2024-10-30 17:17:24 UTC
>
> <img width="798" height="904" alt="28" src="https://github.com/user-attachments/assets/37343f37-1092-4607-8f00-73b46d184725" />

> Next, I identified the dropped file during execution:

akira_readme.txt
>
> <img width="1237" height="367" alt="29" src="https://github.com/user-attachments/assets/f7adecbd-37a7-4720-bd17-9ad327b6f5d0" />
> <img width="948" height="579" alt="30" src="https://github.com/user-attachments/assets/66fb8ac8-a9cc-4f1c-a110-2543e469396f" />

> I then identified the PowerShell command executed:

Get-WmiObject Win32_Shadowcopy | Remove-WmiObject
>
> <img width="996" height="415" alt="31" src="https://github.com/user-attachments/assets/f4ad6f9a-47ae-4845-83f9-807993e46b54" />

> Finally, I determined that the MITRE ATT&CK technique associated with this command was:

T1490 – Inhibit System Recovery

--- 

## Reflection

> This lab strengthened my ability to enrich file and hash artifacts using threat intelligence.
