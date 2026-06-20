# [THM Splunk Investigations]

**TryHackMe Path**: [Challenge]  
**Lab Topic**: [PS Eclipse]  
**Date Completed**: [06/20/2026]

---

## 🧠 Summary

> In this challenge, I worked as a SOC analyst investigating a suspected ransomware incident on a customer endpoint belonging to a user named Keegan. The client reported that the
machine was still operational, but several files had unusual extensions, raising concerns that ransomware activity may have occurred.

Using Splunk, I analyzed endpoint and security event logs from Monday, May 16th, 2022, to determine what happened on Keegan’s device. I investigated process execution, suspicious 
file activity, command-line behavior, and indicators commonly associated with ransomware, such as file modification, encryption attempts, and abnormal executable activity.

Throughout the investigation, I applied log analysis and incident response techniques to reconstruct the timeline of events and identify whether malicious activity took place. 
This challenge reinforced the importance of using SIEM data to investigate ransomware behavior, validate client concerns, and support accurate incident reporting in an MSSP 
environment.

---

## 🎯 Objectives
- [ ] Use Splunk to investigate the ransomware activity.
      
---

## 🧰 Tools Used
- THM AttackBox
- Splunk
  
---

## 📊 Analysis & Screenshots

*** Ransomware or not ***

> In this section, I played the role of a SOC analyst for an MSSP called TryNotHackMe. I had to investigate the events on Keegan’s machine based on an email received from a
customer. For the first question, I had to identify the name of the suspicious binary that was downloaded to the endpoint. After launching Splunk and investigating events with
EventCode=11, I discovered the name of the binary to be:

OUTSTANDING_GUTTER.exe
>
> <img width="1136" height="304" alt="1" src="https://github.com/user-attachments/assets/15565fbd-c095-41e7-bfde-eb11a4098b1e" />
> <img width="658" height="612" alt="2" src="https://github.com/user-attachments/assets/6792ee30-0efe-41d7-ac35-f7ec47319223" />
> <img width="731" height="456" alt="3" src="https://github.com/user-attachments/assets/6771f012-f864-4006-8ffe-16b160292375" />
> <img width="869" height="364" alt="4" src="https://github.com/user-attachments/assets/860ee7c6-aa57-422a-a1a0-28a7a0bca230" />

> I then identified the address from which the binary was downloaded:

hxxp[://]886e-181-215-214-32[.]ngrok[.]io
> 
> <img width="1495" height="800" alt="9" src="https://github.com/user-attachments/assets/46c57248-1c61-4fc6-b4c9-b2ee75352c6c" />
> <img width="2048" height="888" alt="5" src="https://github.com/user-attachments/assets/0ad2c859-6a3b-4c76-922c-dac9d202d198" />
> <img width="1253" height="799" alt="11" src="https://github.com/user-attachments/assets/54de45eb-90c7-4ee3-a725-e93c91e595c4" />

> The Windows executable used to download the suspicious binary was identified as:

C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
>
> <img width="1137" height="556" alt="6" src="https://github.com/user-attachments/assets/62106ccb-0fe1-4232-97f2-2c40d3e6d676" />

> I identified the command executed to configure the suspicious binary to run with elevated privileges as:

"C:\Windows\system32\schtasks.exe" /Create /TN OUTSTANDING_GUTTER.exe /TR C:\Windows\Temp\COUTSTANDING_GUTTER.exe /SC ONEVENT /EC Application /MO *[System/EventID=777] /RU SYSTEM /f
> <img width="710" height="441" alt="7" src="https://github.com/user-attachments/assets/e7ef16b6-5e1d-4112-b77a-e368ebc29f75" />
> <img width="1185" height="315" alt="8" src="https://github.com/user-attachments/assets/6d0119cf-e7c6-489a-90e6-7c9c94666933" />

> Moving on, I identified the permissions and command used to run the suspicious binary as:

NT AUTHORITY\SYSTEM;"C:\Windows\system32\schtasks.exe" /Run /TN OUTSTANDING_GUTTER.exe
>
> <img width="1114" height="952" alt="10" src="https://github.com/user-attachments/assets/5648d082-e66e-4e05-a121-90bb89930274" />

> The suspicious binary then connected to a remote server. The address it connected to was:

hxxp[://]9030-181-215-214-32[.]ngrok[.]io
>
> <img width="1106" height="725" alt="12" src="https://github.com/user-attachments/assets/904af320-1e52-450c-ac83-6dd7b4d3e550" />
> <img width="1493" height="773" alt="13" src="https://github.com/user-attachments/assets/4c7fbf4c-5f8f-4db9-84cb-93726ca7302a" />

> I then discovered that a PowerShell script named script.ps1 was downloaded to the same location.
>
> <img width="939" height="730" alt="14" src="https://github.com/user-attachments/assets/c149cba0-6e32-4210-8ec6-a59459b6e9d2" />

> The malicious script was flagged as malicious. Using its SHA256 hash in VirusTotal, I identified the actual name of the malicious script as:

BlackSun.ps1
>
> <img width="1483" height="699" alt="15" src="https://github.com/user-attachments/assets/c1669712-a903-4076-bdf2-0c8d5c23a05e" />
> <img width="910" height="406" alt="16" src="https://github.com/user-attachments/assets/8e98f121-77d9-4464-a3c2-b02e57babf50" />

> The full path of the ransom note saved to disk was identified as:

C:\Users\keegan\Downloads\vasg6b0wmw029hd\BlackSun_README.txt
>
> <img width="1038" height="603" alt="17" src="https://github.com/user-attachments/assets/d9a5b168-244a-4eeb-9f54-73a378073ff2" />

> The script also saved an image file to disk, which replaced Keegan’s desktop wallpaper. The full path of the image was identified as:

C:\Users\Public\Pictures\blacksun.jpg
>
> <img width="1055" height="905" alt="18" src="https://github.com/user-attachments/assets/21c55a2c-4622-4825-9bed-ae97a96be198" />

--- 

## Reflection

> This lab strengthened my ability to investigate suspected ransomware activity using Splunk in a SOC environment. I developed a better understanding of how to analyze endpoint
logs, process execution data, and suspicious file activity to determine whether malicious behavior occurred on a user’s machine.

I also improved my ability to build an investigation timeline by reviewing events from a specific time frame and connecting related activity across multiple log sources. This 
helped me better understand how ransomware behavior may appear in logs, including abnormal file extensions, suspicious commands, and unusual executable activity.

Additionally, this challenge reinforced the importance of validating client concerns with evidence instead of making assumptions. By using Splunk to investigate Keegan’s device, 
I practiced identifying indicators of compromise and interpreting security events in a structured way.

Overall, this lab improved my confidence in handling ransomware investigations and better prepared me for real-world SOC and MSSP environments where analysts must quickly 
determine what happened, assess impact, and support incident response efforts.
