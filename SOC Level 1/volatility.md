# [SIEM Triage for SOC]

**TryHackMe Path**: [Walkthrough]  
**Lab Topic**: [Volatility]  
**Date Completed**: [05/07/2026]

---

## 🧠 Summary

> In this lab, I performed memory forensics analysis using the Volatility framework to investigate two separate cases involving suspicious activity and malware infection.

---

## 🎯 Objectives
- [ ] Learn how to perform memory forensics with Volatility!
      
---

## 🧰 Tools Used
- THM AttackBox
- Terminal
- ChatGPT


## 📊 Analysis & Screenshots

*** Practical Investigations ***

> In this section, I answered several questions related to two cases using Volatility. The first case involved investigating a suspicious IP within a memory file located at
/Scenarios/Investigations/Investigation-1.vmem, and the second case involved conducting post-analysis of a memory file located at /Scenarios/Investigations/Investigation-2.raw.

For the first question, I had to determine the build version of the host machine in Case 001. To accomplish this, I used the following command:

python3 vol.py -f /Scenarios/Investigations/Investigation-1.vmem windows.info

This returned the build version: "2600.xpsp.080413-2111."
>
> <img width="1448" height="272" alt="1" src="https://github.com/user-attachments/assets/d2b6b41f-677c-4253-b4ef-2ecc98633182" />
> <img width="1304" height="250" alt="2" src="https://github.com/user-attachments/assets/7d2abe77-e370-4e7c-9be3-2cb4fd7cd33e" />
> <img width="1455" height="547" alt="3" src="https://github.com/user-attachments/assets/18a95f84-1dab-4d14-869d-17ec164632ec" />
> <img width="1498" height="316" alt="4" src="https://github.com/user-attachments/assets/e44e4e5b-2cb7-4539-a58c-a5db0d5d0aec" />

> Next, I identified the time the memory file was acquired as "2012-07-22 02:45:08."
>
> <img width="1495" height="205" alt="5" src="https://github.com/user-attachments/assets/3e99da1e-f9c7-466b-beea-b19c47126c77" />

> I then discovered a suspicious process in Case 001 by using the following command:

python3 vol.py -f /Scenarios/Investigations/Investigation-1.vmem windows.psscan

This returned the process "reader_sl.exe."
>
> <img width="1319" height="434" alt="6" src="https://github.com/user-attachments/assets/b6e26a53-afcc-4fb9-9c13-fae15b8f6bb6" />

> The parent process of the suspicious process was identified as "explorer.exe."

> The parent process of the suspicious process was identified as "explorer.exe."
The PID of the suspicious process was 1640, and the parent process PID was 1484.

> To determine the user agent used by the adversary in Case 001, I used the following commands:

python3 vol.py -f /Scenarios/Investigations/Investigation-1.vmem -o /tmp windows.memmap.memmap --pid 1640 --dump
strings /tmp/pid.1640.dmp | grep -i "user-agent"

This returned the user agent:
"Mozilla/5.0 (Windows; U; MSIE 7.0; Windows NT 6.0; en-US)."
>
> <img width="1494" height="226" alt="7" src="https://github.com/user-attachments/assets/05b4202a-55c5-408d-90f5-374ea1ad34f8" />
> <img width="1092" height="173" alt="8" src="https://github.com/user-attachments/assets/533d879e-7574-4654-97cd-033639fefe6d" />

> Further investigation revealed Chase Bank as one of the suspicious domains.
>
> <img width="1503" height="427" alt="9" src="https://github.com/user-attachments/assets/5f514242-80b5-4bc6-ae08-ba14e8dd8c9f" />

> In Case 002, I identified a suspicious process running at PID 740 as "@WanaDecryptor@" using the following command:

python3 vol.py -f /Scenarios/Investigations/Investigation-2.raw windows.pstree
>
> <img width="1288" height="471" alt="10" src="https://github.com/user-attachments/assets/e3e218e3-a31a-420f-855d-b70c847ba1b3" />

> The full path of the suspicious binary associated with PID 740 was identified as:

C:\Intel\ivecuqmanpnirkt615\@WanaDecryptor@.exe

This was obtained using the following command:

vol -f /Scenarios/Investigations/Investigation-2.raw windows.dlllist | grep 740
>
> <img width="1501" height="603" alt="11" src="https://github.com/user-attachments/assets/9ee604a5-a675-429a-81b3-1d392fcbee82" />

> The parent process of PID 740 was identified as "tasksche.exe."
The parent process PID was identified as 1940.
>
> <img width="1226" height="223" alt="12" src="https://github.com/user-attachments/assets/039ad0e3-7a87-48f8-9857-83450f3f651e" />

> The type of malware present on the system in Case 002 was identified as WannaCry ransomware.
>
> <img width="509" height="444" alt="13" src="https://github.com/user-attachments/assets/5d781b0b-aaa7-48c4-92a9-0f2cbd78bf7e" />

> The DLL loaded by the decryptor for socket creation was identified as "Ws2_32.dll."
>
> <img width="1401" height="375" alt="14" src="https://github.com/user-attachments/assets/f835f7fe-2eb9-4b62-868c-6ea5e4959fe1" />

> A known mutex indicator associated with WannaCry was identified as:
"MsWinZonesCacheCounterMutexA", using the following command:

vol -f /Scenarios/Investigations/Investigation-2.raw windows.handles | grep 1940
>
> <img width="1390" height="701" alt="15" src="https://github.com/user-attachments/assets/174ce1a0-7f87-405d-b7a7-8597090512a6" />

> Finally, the plugin used to identify all files loaded from the WannaCry malware working directory was identified as "windows.filescan", using the command:

python3 vol.py -h

--- 

## Reflection

> Overall, this lab strengthened my ability to perform memory-based investigations, detect malicious processes, and correlate forensic artifacts to identify attacker behavior
and malware presence.
