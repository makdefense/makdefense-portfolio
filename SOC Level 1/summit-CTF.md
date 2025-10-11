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

> After scanning "sample3.exe" i then discovered two unusual DNS requests within the Network Activity and one specifically including the domain "emudyn.bresonicz.info" and
IP address "62.123.140.9."
>
> <img width="1256" height="812" alt="s14" src="https://github.com/user-attachments/assets/3db99e01-9172-4fbb-a20e-4fdc79dbdda2" />

> I then navigated to the left and selected the "DNS Rule Manager," i then entered within the "Create DNS Rule" area the Rule Name which was "No more pub IPS," the
Category which was "Malware," the Domain Name which was "emudyn.bresonicz.info," and the Action to "Deny."
>
> <img width="865" height="566" alt="s13" src="https://github.com/user-attachments/assets/777605e4-58c4-4223-b681-0a89b110d37a" />

> After saving the new DNS Rule i retrieved the third flag.
>
> <img width="1194" height="321" alt="s15" src="https://github.com/user-attachments/assets/f18effad-de36-4a67-ab57-1257efc2e597" />
> <img width="4096" height="2560" alt="s16" src="https://github.com/user-attachments/assets/63b7782b-d734-4da5-90ee-379432520b33" />

*** Flag #4 ***















---

## Reflection

> This lab provided me with knowledge about the 

