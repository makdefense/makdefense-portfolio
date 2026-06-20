# [THM Splunk Investigations]

**TryHackMe Path**: [Challenge]  
**Lab Topic**: [PS Eclipse]  
**Date Completed**: [06//2026]

---

## 🧠 Summary

> In this challenge,

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

> In this section, I played the role of a SOC analyst for an MSSP called TryNotHackME. I had to investigate the events on Keegan's Machine, according to an email recieved by a
customer. For the first question i had to identify the name of the suspicious binary that was downloaded to the endpoint. After launching Splunk, then investigating events with
EventCode=11 i discovered the name of the binary to be:
OUTSTANDING_GUTTER.exe
>
> <img width="1136" height="304" alt="1" src="https://github.com/user-attachments/assets/15565fbd-c095-41e7-bfde-eb11a4098b1e" />
> <img width="658" height="612" alt="2" src="https://github.com/user-attachments/assets/6792ee30-0efe-41d7-ac35-f7ec47319223" />
> <img width="731" height="456" alt="3" src="https://github.com/user-attachments/assets/6771f012-f864-4006-8ffe-16b160292375" />
> <img width="869" height="364" alt="4" src="https://github.com/user-attachments/assets/860ee7c6-aa57-422a-a1a0-28a7a0bca230" />

> I then identified the address that the binary was downloaded from to be:
hxxp[://]886e-181-215-214-32[.]ngrok[.]io
> 
> <img width="1495" height="800" alt="9" src="https://github.com/user-attachments/assets/46c57248-1c61-4fc6-b4c9-b2ee75352c6c" />
> <img width="2048" height="888" alt="5" src="https://github.com/user-attachments/assets/0ad2c859-6a3b-4c76-922c-dac9d202d198" />

> The Windows executable that was used to download the suspicious binary was identified as:
C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
>
> <img width="1137" height="556" alt="6" src="https://github.com/user-attachments/assets/62106ccb-0fe1-4232-97f2-2c40d3e6d676" />

> The command that was executed to configure the suspicious binary to run with elevated privileges, i identified as:
"C:\Windows\system32\schtasks.exe" /Create /TN OUTSTANDING_GUTTER.exe /TR C:\Windows\Temp\COUTSTANDING_GUTTER.exe /SC ONEVENT /EC Application /MO *[System/EventID=777] /RU SYSTEM /f
> <img width="710" height="441" alt="7" src="https://github.com/user-attachments/assets/e7ef16b6-5e1d-4112-b77a-e368ebc29f75" />
> <img width="1185" height="315" alt="8" src="https://github.com/user-attachments/assets/6d0119cf-e7c6-489a-90e6-7c9c94666933" />

> Moving on i then identified the permissions and the command to runthe suspicious binary as:
NT AUTHORITY\SYSTEM;"C:\Windows\system32\schtasks.exe" /Run /TN OUTSTANDING_GUTTER.exe
>
> <img width="1114" height="952" alt="10" src="https://github.com/user-attachments/assets/5648d082-e66e-4e05-a121-90bb89930274" />

> The suspicious binary then connected to a remote server. The address it connected to was:
hxxp[://]9030-181-215-214-32[.]ngrok[.]io
>
> <img width="1253" height="799" alt="11" src="https://github.com/user-attachments/assets/0381660e-07df-42c8-8431-286aea8fcdd7" />


 








--- 

## Reflection

> This lab strengthened my ability to 
