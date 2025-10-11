# [Cyber Defence Frameworks]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Summit]  
**Date Completed**: [10/11/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding 

---

## 🎯 Objectives
- [ ] Follow the Pyramid of Pain, increase the simulated adversaries' cost of operations and chase them away for good.

---

## 🧰 Tools Used
- THM Target Machine
- THM PicoSecure
  
---

## 📊 Analysis & Screenshots

*** Flag #1 ***

> For the first flag i had to capture i had to first scan "sample1.exe" file using Maleware Sandbox.
>
> <img width="479" height="472" alt="s1" src="https://github.com/user-attachments/assets/c5e9a78f-dfef-419b-8e6c-ab478c8391fa" />
> <img width="715" height="453" alt="s2" src="https://github.com/user-attachments/assets/0b4c63e9-daec-4861-93af-71495f95de3f" />

> After submitting the "sample1.exe" file for analysis i then had to copy and paste the SHA256 value into the input field of the "Detect Hashes" to add it to the blocklist.
>
> <img width="1258" height="762" alt="s3" src="https://github.com/user-attachments/assets/4dfd33af-49ac-4b1f-b442-cd3e0259f01a" />
> <img width="695" height="607" alt="s4" src="https://github.com/user-attachments/assets/171c7c69-2f0a-40f7-ba1e-d95225b5798f" />

> After successfully blocking "sample1.exe" SHA256 hash i retrieved the 1st flag.
>
> <img width="1349" height="593" alt="s5" src="https://github.com/user-attachments/assets/4d2cd921-5926-4f04-a633-58c20f3a34e7" />
> <img width="1358" height="687" alt="s6" src="https://github.com/user-attachments/assets/5d05ec20-3c08-48ad-b699-98828687f423" />

*** Flag #2 ***

> Moving onto capturing the second flag. I had to submit "sample2.exe" file for analysis.
>
> <img width="697" height="449" alt="s7" src="https://github.com/user-attachments/assets/05e83778-aa35-4e60-8534-615410ce44b6" />

> After submitting it for analysis i then discovered unusual network activity where the process "sample2.exe" made a GET request to an unsual IP address & port.
>
> <img width="1289" height="550" alt="s8" src="https://github.com/user-attachments/assets/2b57a14f-0a7e-48ae-82e7-edc4bdd6eca1" />

> So i then navigated to the left and selected the "Firewall Rule Manager," i then entered within the "Create Firewall Rule" area the type of Firewall which was "Egress,"
the source IP which was "Any," the destination IP which was "154.35.10.113," and the Action to "Deny."
>
> <img width="852" height="555" alt="s9" src="https://github.com/user-attachments/assets/dfa53ec9-2901-486a-b29f-e50e642be7b1" />

> After saving the new firewall rule i retrieved the second flag.
>
> <img width="1207" height="338" alt="s10" src="https://github.com/user-attachments/assets/c89c3d78-5bb4-4ea3-82e3-e0cdf7be862e" />
> <img width="1367" height="698" alt="s11" src="https://github.com/user-attachments/assets/98101854-dba9-4214-89e1-4cdae6793539" />

*** Flag #3 ***

> Moving onto capturing the third flag. I had to submit "sample3.exe" file for analysis.
>
> <img width="695" height="476" alt="s12" src="https://github.com/user-attachments/assets/1d29dbc0-ab95-44fa-9453-c12d4fab9310" />

> After scanning "sample3.exe" i then discovered two unusual DNS requests within the Network Activity and one specifically including the domain "emudyn.bresonicz.info"
and IP address "62.123.140.9."
>
> <img width="1256" height="812" alt="s14" src="https://github.com/user-attachments/assets/3db99e01-9172-4fbb-a20e-4fdc79dbdda2" />

> I then navigated to the left and selected the "DNS Rule Manager," i then entered within the "Create DNS Rule" area the Rule Name which was "No more pub IPS," the
Category which was "Malware," the Domain Name which was "emudyn.bresonicz.info," and the Action to "Deny."
>
> <img width="865" height="566" alt="s13" src="https://github.com/user-attachments/assets/777605e4-58c4-4223-b681-0a89b110d37a" />

> After saving the new DNS Rule i retrieved the third flag.
>
> <img width="1194" height="321" alt="s15" src="https://github.com/user-attachments/assets/f18effad-de36-4a67-ab57-1257efc2e597" />
> <img width="1136" height="583" alt="s16" src="https://github.com/user-attachments/assets/8263b149-33d7-408d-ab1e-e3962576cf86" />

*** Flag #4 ***

> To capture the 4th flag i had to submit "sample4.exe" process for analysis.
>
> <img width="706" height="447" alt="s18" src="https://github.com/user-attachments/assets/8be9ff75-2741-4293-989f-cca42bcab901" />

> After scaning "sample4.exe" i then discovered that the process had new suspicious activity which was that it made changes to the registry.
>
> <img width="1359" height="587" alt="s19" src="https://github.com/user-attachments/assets/241d988e-31cd-40bb-a417-85130d7443cb" />

> So to stop this activity i navigated to the left of the application and selected "Sigma Rule Builder," then selected "Sysmon Event Logs," then "Registry Modifications,"
i then entered the following information within the rule conditions and options area for Registry Key i inputted
"HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Defender\Real-Time Protection," for Registry Name i inputted "DisableRealtimeMonitoring," for the Value i put "1," and for
the ATT&CK ID i selected "Defensive Evasion TA0005."
>
> <img width="952" height="1042" alt="s21" src="https://github.com/user-attachments/assets/65922165-2ab6-4372-a42a-9b4fe9eec3f7" />

> After validatiing the rule i retrieved the validation information and the fourth flag.
>
> <img width="1183" height="740" alt="s22" src="https://github.com/user-attachments/assets/92a39084-6907-4920-95bc-4c59d1916f45" />
> <img width="1373" height="765" alt="s23" src="https://github.com/user-attachments/assets/626a94df-efe2-44b2-b012-8aaf18465d60" />

*** Flag #5 ***

> For the 5th flag i had to submit "sample5.exe" process for analysis.
>
> <img width="694" height="469" alt="s24" src="https://github.com/user-attachments/assets/dc4cd396-95ab-4679-a279-7734201b4391" />

> After scaning "sample5.exe" i then discovered that within the Network Activity there was a high number of consequitive connections, a total of 402.
> 
> <img width="1306" height="1060" alt="s25" src="https://github.com/user-attachments/assets/8f97c4d8-2c91-4fd1-964c-f6b19113b12f" />

> I then had to look at the attachment "outgoing_connections.log" to gather the Size & Frequency of the connections which was 97 bytes & 1800 seconds.
>
> <img width="1068" height="895" alt="s26" src="https://github.com/user-attachments/assets/3fd8083e-b7e2-4b51-81fe-abb6c4720dbd" />

> So to stop this activity i navigated to the left of the application and selected "Sigma Rule Builder," then selected "Sysmon Event Logs," then selected "Network
Connections," then entered the following information within the rule conditions and options area for Remote IP i inputted "Any," for Remote Port i inputted "Any,"
for the Size i inputted the value "97," then for the Frequency i inputted the value "1800," and for the ATT&CK ID i selected "Command and Control TA0011."
>
> <img width="894" height="1002" alt="s28" src="https://github.com/user-attachments/assets/af765984-b4a9-435d-8c09-754487323a09" />

> After validating the rule i retrieved the validation information and the fifth flag.
>
> <img width="1201" height="823" alt="s29" src="https://github.com/user-attachments/assets/09bba56f-e0dc-4d87-a1bf-7610cd8907ad" />
> <img width="1360" height="749" alt="s30" src="https://github.com/user-attachments/assets/145269bc-e46e-4f47-8a02-a15139ce7224" />

*** Final Flag ***

> For the last flag i had to submit "sample6.exe" process for analysis.
>
> <img width="708" height="367" alt="s31" src="https://github.com/user-attachments/assets/62d3c4a9-6d1d-4b9b-a3a9-110c81406c17" />

> After scanning "sample6.exe" i then discovered that within the File Activity there was one suspicious file dropped within the Windows system.
>
> <img width="1365" height="355" alt="s32" src="https://github.com/user-attachments/assets/201d9e2d-c0ed-4e52-8265-5aa3b024314a" />

> I then had to look at the attachment "commands.log" to gather the value of the String for process "cmd.exe" which was "%temp%\exfiltr8.log."
> 
> <img width="707" height="453" alt="s34" src="https://github.com/user-attachments/assets/a42bd674-50a3-4b8c-9e8c-ea8ad8d6a2ba" />

> To stop this activity i navigated to the left of the application and selected "Sigma Rule Builder," then selected "Sysmon Event Logs," then selected "Process Creation,"
then entered the following information within the rule conditions and options area for Process Name i inputted "cmd.exe," for CommandLine i selected the option
"Contains," for the String i inputted the value "%temp%\exfiltr8.log," and for the ATT&CK ID i selected "Discovery TA0007."
>
> <img width="914" height="1076" alt="s33" src="https://github.com/user-attachments/assets/55e567bd-0a69-4fad-b379-4fc756a8fb86" />

> After validating the rule i retrieved the last flag.
>
> <img width="1361" height="495" alt="s35" src="https://github.com/user-attachments/assets/f4a1c871-c4e3-43aa-800c-e9eb6174721b" />
---

## Reflection

> This lab provided me with knowledge about the 

