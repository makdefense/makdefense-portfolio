# [THM Walkthrough]

**TryHackMe Path**: [Walkthrough]  
**Lab Topic**: [Sysmon]  
**Date Completed**: [06/15/2026]

**Lab Link**: [https://tryhackme.com/room/sysmon]

---

## 🧠 Summary

> In this lab, I learned how to utilize Sysmon (System Monitor) to enhance endpoint visibility and monitor system activity within a Windows environment. I gained hands-on
experience configuring and analyzing Sysmon logs to capture detailed information about process creation, network connections, file modifications, registry changes, and other
security-relevant events.

Throughout the lab, I explored how Sysmon complements traditional Windows Event Logs by providing deeper insight into system behavior and potential indicators of compromise. I 
learned how to identify important Sysmon Event IDs, interpret logged activity, and use the collected data to support threat detection and incident investigations.

This lab reinforced the importance of endpoint monitoring in modern security operations, improving my ability to detect suspicious activity, investigate attacker behavior, and 
leverage Sysmon as a valuable source of telemetry for threat hunting and SOC investigations.

---

## 🎯 Objectives
- [ ] Complete Sysmon Walkthrough
      
---

## 🧰 Tools Used
- THM AttackBox
- Sysmon

---

## 📊 Analysis & Screenshots

*** Cutting out the Noise ***

> In this section, I conducted an investigation using the Filtering.evtx file in Event Viewer. For the first question, I had to determine how many Event ID 3 events were present
in the file. After applying the necessary filter i was able to retrieve a total of:
73,591 events with Event ID 3.
>
> <img width="702" height="424" alt="1" src="https://github.com/user-attachments/assets/bda7187e-89f0-49ad-badc-717fec64f16f" />
> <img width="1299" height="531" alt="2" src="https://github.com/user-attachments/assets/3b7572f1-744f-467e-a50b-6dc5e63b211d" />
> <img width="1036" height="957" alt="3" src="https://github.com/user-attachments/assets/2e2eec1f-37d2-4931-a6ee-e73d8c31dca4" />
> <img width="1013" height="314" alt="4" src="https://github.com/user-attachments/assets/664534b1-4137-4376-be42-657d1f65e88e" />

> I then identified the UTC timestamp of the first network event in the same log file.
2021-01-06 01:35:50.464
>
> <img width="1046" height="778" alt="5" src="https://github.com/user-attachments/assets/26a02ab5-5b37-48df-aa66-a53d7505751d" />

*** Detecting Mimikatz ***

> In this section, I practiced detecting Mimikatz using the provided EVTX file. After launching PowerShell, I executed the following command:
Get-WinEvent -Path C:\Users\THM-Analyst\Desktop\Scenarios\Practice\Hunting_Mimikatz.evtx -FilterXPath '*/System/EventID=10 and */EventData/Data[@Name="TargetImage"] and */EventData/Data="C:\Windows\system32\lsass.exe"'
>
> <img width="1271" height="742" alt="6" src="https://github.com/user-attachments/assets/190afd20-a4c8-49ba-b7a9-51010f88435c" />
> <img width="1504" height="227" alt="7" src="https://github.com/user-attachments/assets/b210a98c-8d8c-461a-9c8e-3681221c4aa9" />
> <img width="1071" height="912" alt="8" src="https://github.com/user-attachments/assets/b4ae6c8e-5df6-4138-a935-a736ff695623" />


*** Hunting Malware ***

> I then practiced hunting RATs and command-and-control (C2) servers that utilized back-connect ports. To detect this activity, I executed the following query:
Get-WinEvent -Path C:\Users\THM-Analyst\Desktop\Scenarios\Practice\Hunting_Rats.evtx -FilterXPath '*/System/EventID=3 and */EventData/Data[@Name="DestinationPort"] and */EventData/Data=8080'
>
> <img width="880" height="308" alt="10" src="https://github.com/user-attachments/assets/edfdf285-4322-4e2c-bfcf-6d14407354b3" />
> <img width="1502" height="364" alt="9" src="https://github.com/user-attachments/assets/3459420a-2dce-4b1c-b7bd-bce993c0f65e" />
> <img width="1127" height="769" alt="11" src="https://github.com/user-attachments/assets/15c9f7c9-0d2a-4857-ad11-f6602e2725b0" />

*** Hunting Persistence ***

> In this section, I investigated startup persistence using the EVTX file T1023. After filtering for Event ID 11, I successfully identified the persistence mechanism. I then
identifed Registry Key Persistence by investigating the etvx file T1060. After filtering out the events with Event ID 11 it was discovered.
>
> <img width="1037" height="546" alt="12" src="https://github.com/user-attachments/assets/8ecb063f-b3cd-4c0f-b95a-93252acec8ec" />
> <img width="1157" height="586" alt="13" src="https://github.com/user-attachments/assets/c5e0c46d-be4f-4717-be6f-b08597852280" />
> <img width="955" height="455" alt="14" src="https://github.com/user-attachments/assets/3d29ee2e-3a6a-4529-9099-dfd976b0abf3" />
> <img width="1217" height="632" alt="15" src="https://github.com/user-attachments/assets/f1321771-982d-4a35-84ba-cd90b3b12ad9" />

*** Detecting Evasion Techniques ***

> I learned how to detect several common defense-evasion techniques. First, I figured out how to hunt alternate data streams by investigating the evtx file,
then looking for the event with the Task Category with the description "File Stream Created." I then detected remote thread activity by investigating the EVTX file Detecting Remote Threads. By entering the command syntax:
Get-WinEvent -Path C:\Users\THM-Analyst\Desktop\Scenarios\Practice\Detecting_RemoteThreads.evtx -FilterXPath '*/System/EventID=8'
>
> <img width="964" height="530" alt="16" src="https://github.com/user-attachments/assets/0f90d283-ca9b-4820-8d93-4f58f940bfc7" />
> <img width="1151" height="610" alt="17" src="https://github.com/user-attachments/assets/c12842fe-221a-4388-b17d-2a088ac240cb" />
> <img width="1193" height="727" alt="18" src="https://github.com/user-attachments/assets/6be08d44-a623-4dfe-a837-8a78155f2e44" />
> <img width="1140" height="307" alt="19" src="https://github.com/user-attachments/assets/e89b6004-ce7f-4794-955e-a5c68eddeb53" />

*** Practical Investigations ***

> In this practical investigation section, my task was to analyze several EVTX files and answer a series of investigative questions. For the first etvx file I had to first figure
out the full registry key of the USB device calling svchost.exe. Upon further analysis, I identified the full registry key as:
HKLM\System\CurrentControlSet\Enum\WpdBusEnumRoot\UMB\2&37c186b&0&STORAGE#VOLUME#_??_USBSTOR#DISK&VEN_SANDISK&PROD_U3_CRUZER_MICRO&REV_8.01#4054910EF19005B3&0#\FriendlyName
>
> <img width="1317" height="589" alt="20" src="https://github.com/user-attachments/assets/6d22bf22-6bf7-4de9-af49-b7e984568866" />
> <img width="1225" height="901" alt="21" src="https://github.com/user-attachments/assets/9d32c149-788f-44b1-ae2a-c2656543f5f3" />

> I discovered the device name when being called by RawAccessRead to be:
\Device\HarddiskVolume3
>
> <img width="1056" height="670" alt="22" src="https://github.com/user-attachments/assets/0663b88b-87fe-4d53-9f02-dc36833e0c2a" />

> The first process executed was:
rundll32.exe
>
> <img width="1100" height="912" alt="23" src="https://github.com/user-attachments/assets/d6210390-f970-475c-bc0b-c81624da6120" />

> I investigated a suspicious file that executed code while masquerading as an HTML file.
I first identified the full path of the payload to be:
C:\Users\IEUser\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\S97WTYG7\update.hta
>
> <img width="1121" height="480" alt="24" src="https://github.com/user-attachments/assets/00e5adad-735e-4485-b5ce-2414a3f3ed18" />
> <img width="1064" height="975" alt="25" src="https://github.com/user-attachments/assets/ce4dcb08-fee1-406e-82eb-66acc5515766" />

> The full path of the file used to disguise the payload was identified as:
C:\Users\IEUser\Downloads\update.html
>
> <img width="1033" height="331" alt="26" src="https://github.com/user-attachments/assets/14de59dc-16e3-4f78-a624-7effbbf05cdd" />

> The signed binary that executed the payload was:
C:\Windows\System32\mshta.exe
>
> <img width="1078" height="964" alt="27" src="https://github.com/user-attachments/assets/bc6833f8-f488-43be-ab41-dd5ba99f9382" />

> The identified IP of the adversary was:
10.0.2.18
>
> <img width="897" height="441" alt="28" src="https://github.com/user-attachments/assets/5187ecdb-dc97-48f7-ba5a-6b3ea7885811" />

> The back connect port identifed was:
4443
> <img width="580" height="473" alt="29" src="https://github.com/user-attachments/assets/22c599e2-1818-4e03-8da8-77c178898ce4" />

> Moving on to the next etvx file "Investigation 3.1." I had to perform an investigation of the persistence the adversary managed to setup on my endpoints, to determine how the
adversary established persistence on the endpoint.. First I identifed the IP of the suspected adversary to be:
172.30.1.253
>
> <img width="1227" height="390" alt="30" src="https://github.com/user-attachments/assets/75688afc-b6a4-49bf-aa87-f26b3f53ac32" />
> <img width="1099" height="815" alt="31" src="https://github.com/user-attachments/assets/9ba19142-49b9-492a-a827-f3e26a23d8c1" />

> The hostname of the affected endpoint was identified as:
DESKTOP-O153T4R
<img width="832" height="611" alt="32" src="https://github.com/user-attachments/assets/e5e91ace-2195-4ddb-9784-308f70e347c4" />

> The hostname of the C2 server communicating with the endpoint was identified as:
empirec2
>
> <img width="1075" height="686" alt="33" src="https://github.com/user-attachments/assets/57df7c8c-f20e-45da-b086-6b896bf03a5b" />

> The registry where the payload was stored was identified as:
HKLM\SOFTWARE\Microsoft\Network\debug
The Powershell launch code used to launch the payload was identified as:
"C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -c "$x=$((gp HKLM:Software\Microsoft\Network debug).debug);start -Win Hidden -A \"-enc $x\" powershell";exit;
>
> <img width="1130" height="811" alt="34" src="https://github.com/user-attachments/assets/fa78291d-7934-486c-9654-acb9d3ca278d" />

> For the next etvx file "Investigation 3.2." I performed a similar investigation to the previous scenario. The identified IP of the adversary was:
172.168.103.188
>
> <img width="1421" height="752" alt="35" src="https://github.com/user-attachments/assets/e998fc12-6c9d-427e-a773-114a0a41bf95" />
> <img width="959" height="819" alt="36" src="https://github.com/user-attachments/assets/db3973fe-6564-423f-9304-61c00e3e166f" />

> The full path of the payload location was identified as:
c:\users\q\AppData:blah.txt
>
> <img width="1139" height="656" alt="37" src="https://github.com/user-attachments/assets/762834e3-fc3d-4bed-bbc8-55cf08085e56" />

> The full command used to create the scheduled task was identified as:
"C:\WINDOWS\system32\schtasks.exe" /Create /F /SC DAILY /ST 09:00 /TN Updater /TR "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe -NonI -W hidden -c \"IEX ([Text.Encoding]::UNICODE.GetString([Convert]::FromBase64String($(cmd /c ''more < c:\users\q\AppData:blah.txt'''))))\""
>
> <img width="1179" height="753" alt="38" src="https://github.com/user-attachments/assets/e5cfd5ff-13a0-4bda-830a-65a2eb7d8add" />

> The process that was accessed by schtask.exe that would be considered suspicious behavior turned out to be:
lsass.exe
>
> <img width="1087" height="971" alt="39" src="https://github.com/user-attachments/assets/8af4fb6f-14dc-4e0c-a03a-5384fb5cea1f" />

> Finally, for the EVTX file Investigation 4, I conducted an additional investigation after discovering that the adversary had established command-and-control (C2) communications
with several endpoints. The identifed IP of the adversary was:
172.30.1.253
>
> <img width="1076" height="898" alt="41" src="https://github.com/user-attachments/assets/9e550bb2-8414-47eb-9ed6-01786829db96" />

> The port the adversary operated on was:
80
then the identifed C2 the adversary utilized was:
Empire
>
> <img width="1054" height="976" alt="42" src="https://github.com/user-attachments/assets/18e8eed9-2ebf-4c69-8d39-5879af749f1c" />

--- 

## Reflection

> This lab strengthened my ability to use Sysmon to monitor endpoint activity and identify security-relevant events within a Windows environment. I developed a stronger
understanding of how Sysmon generates detailed telemetry that can be used to detect suspicious behavior, investigate incidents, and improve overall visibility across systems.

I also enhanced my ability to analyze Sysmon event data by examining process creation, network connections, file modifications, and registry activity. This helped me better 
understand how attackers interact with systems and how those actions can be identified through endpoint logging.

Additionally, I gained valuable experience working with Sysmon Event IDs and interpreting the information they provide. This reinforced the importance of collecting high-quality 
endpoint telemetry to support threat hunting, incident response, and forensic investigations.

Overall, this lab improved my confidence in leveraging Sysmon as a security monitoring tool and better prepared me for real-world SOC environments where endpoint visibility and 
log analysis play a critical role in detecting and responding to threats.


