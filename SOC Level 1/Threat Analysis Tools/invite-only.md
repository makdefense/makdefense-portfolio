# [Threat Analysis Tools]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Invite Only]  
**Date Completed**: [04/07/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of extracting insight from a set of flagged artifacts and distilling the information into usable threat intelligence. This is important
because it turns raw alerts into clear, actionable insights—helping identify real threats, respond faster, and make better decisions.
This is a core skill for SOC analysts and what makes you valuable in cybersecurity.

---

## 🎯 Objectives
- [ ] Analyze flagged findings
      
---

## 🧰 Tools Used
- THM AttackBox
- Virus Total
- Google Chrome

---

## 📊 Analysis & Screenshots

*** Invite Only ***

> In this section, my task was to analyze two suspicious findings that were flagged and escalated by an L1 analyst. The two flagged findings were:
Flagged IP: 101[.]99[.]76[.]120
Flagged SHA256 hash: 5d0509f68a9b7c415a726be75a078180e3f02e59866f193b0a99eee8e39c874f
> For the first question, I had to determine the name of the file associated with the flagged SHA256 hash. To do this, I launched VirusTotal, copied and pasted the SHA256 hash into
the input field, and pressed "Enter." This revealed the file name as "syshelpers.exe."
>
> <img width="1056" height="635" alt="1" src="https://github.com/user-attachments/assets/c1407f8c-6067-4111-b68d-751b8732b140" />
> <img width="955" height="314" alt="2" src="https://github.com/user-attachments/assets/ce8cb7ca-0d33-4ff1-9f8c-87c8133bdbbc" />

> I then needed to identify the file type associated with the flagged SHA256 hash. I navigated to the "Basic Properties" section under "Details," which showed the file type as
"Win32 EXE."
>
> <img width="1169" height="405" alt="3" src="https://github.com/user-attachments/assets/f468c9bc-8eee-41fe-b9e8-d513d14e4c69" />

> Next, I had to determine the execution parents of the flagged hash. By scrolling to the "Execution Parents" section, I identified them as "361GJX7J" and "installer.exe."
>
> <img width="730" height="202" alt="4" src="https://github.com/user-attachments/assets/ea36197b-f3e8-45ce-848f-ea97427a8af6" />

> I then located the dropped file associated with the flagged hash, which was "Aclient.exe."
>
> <img width="1178" height="225" alt="5" src="https://github.com/user-attachments/assets/cca4e64a-aedf-4075-b28f-01423ca87fbe" />

> For the next step, I researched the second hash related to the file discovered earlier ("installer.exe") and identified four malicious files that were dropped. These files were:
"searchhost.exe," "syshelpers.exe," "nat.vbs," and "runsys.vbs."
>
> <img width="1024" height="346" alt="6" src="https://github.com/user-attachments/assets/7ad175e1-a3ee-48b9-a408-e2d4de6f3e89" />
> <img width="1665" height="414" alt="7" src="https://github.com/user-attachments/assets/04554e68-3b30-4893-9202-127f795e793d" />
> <img width="1109" height="736" alt="8" src="https://github.com/user-attachments/assets/83b0d753-7997-461e-9ef6-52fb40e79bbd" />

> I then analyzed the files related to the flagged IP. I copied and pasted the IP into VirusTotal, navigated to the "Community" section, and identified the malware family as
"AsyncRAT."
>
> <img width="936" height="642" alt="9" src="https://github.com/user-attachments/assets/e52bd7b3-0379-4e12-a810-70e200f9fe58" />
> <img width="900" height="386" alt="10" src="https://github.com/user-attachments/assets/1b54de3d-1a33-43b1-95bb-85313f01d122" />
> <img width="897" height="389" alt="11" src="https://github.com/user-attachments/assets/2d2dc6db-aff8-4c38-afe8-bfeeb826a9f8" />

> Next, I determined the title of the original report where the flagged indicators were mentioned. Under the IOC context for AsyncRAT, I found the report titled:
"From Trust to Threat: Hijacked Discord Invites Used for Multi-Stage Malware Delivery."
>
> <img width="932" height="361" alt="12" src="https://github.com/user-attachments/assets/48ca7764-ed3a-445e-a815-1022f07a82f6" />
> <img width="1217" height="453" alt="13" src="https://github.com/user-attachments/assets/55b9e147-47f5-4492-80eb-3f09a7c0165b" />

> After reviewing the report, I answered additional questions. I identified the tool used by attackers to steal cookies from the Google Chrome browser as "ChromeKatz."
>
> <img width="808" height="366" alt="14" src="https://github.com/user-attachments/assets/c130be02-82d8-424a-8c12-36ddfdaa62a4" />

> I also determined that the phishing technique used by the attackers was "ClickFix."
>
> <img width="1007" height="422" alt="15" src="https://github.com/user-attachments/assets/cf5dfa23-9814-4664-82af-e6725a841f80" />

> Finally, I identified the platform used to redirect the malicious user as "Discord."
>
> <img width="1418" height="235" alt="16" src="https://github.com/user-attachments/assets/f1f3860b-e9bc-42c7-9c18-62d66ac5b416" />

--- 

## Reflection

> This lab strengthened my ability to extract insight from flagged artifacts and distill that information into actionable threat intelligence.
