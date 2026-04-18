# [SIEM Triage for SOC]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [ItsyBitsy]  
**Date Completed**: [04/18/2026]

---

## 🧠 Summary

> In this lab, I put my ELK knowledge together to investigate an incident.

---

## 🎯 Objectives
- [ ] Complete Challenge Room
      
---

## 🧰 Tools Used
- THM AttackBox
- Elastic

---

## 📊 Analysis & Screenshots

*** Scenario - Investigate a potential C2 communication alert ***

> In this room, I had to answer several questions based on examining the network connection logs of the user "Browne" using the "connection_logs" index in Kibana. For the first
question, I had to determine how many events were returned for the month of March 2022. I first launched Elastic, then entered the query:
"index=connection_logs", which returned a total of 1,482 events for March 2022.
>
> <img width="493" height="420" alt="1" src="https://github.com/user-attachments/assets/167343b1-5037-4616-95b9-3d6651f22860" />
> <img width="1497" height="428" alt="2" src="https://github.com/user-attachments/assets/c2054139-ebea-4976-bcce-e84b6b5b6a29" />

> I then discovered 192.166.65.54 as the IP address associated with the suspected user in the logs by navigating to the left side of the application and hovering over "source_ip."
>
> <img width="627" height="690" alt="3" src="https://github.com/user-attachments/assets/2c3ecd4b-dc8f-43f8-a823-46353206b7ea" />

> I then identified "bitsadmin" as the legitimate Windows binary used to download a file from the C2 server.
>
> <img width="849" height="609" alt="4" src="https://github.com/user-attachments/assets/3aae142b-2fee-4359-a4f6-0bf9b0dcde9c" />

> Moving on to the next question, I retrieved the file-sharing site, pastebin.com, which the infected machine connected to during this period. It also acted as a C2 server used by
the malware authors to communicate.
>
> <img width="1144" height="223" alt="5" src="https://github.com/user-attachments/assets/45a3e8c5-b8c3-4990-bd88-ef98c3341dc6" />

> The full URL of the C2 server to which the infected host connected was "pastebin.com/yTg0Ah6a."
>
> <img width="781" height="422" alt="6" src="https://github.com/user-attachments/assets/93bede44-2e72-4e9f-ad8f-955ccedf55c9" />

> I then navigated to the full URL of the C2 server to find the file that was accessed on the file-sharing site, which was "secret.txt."
>
> <img width="263" height="51" alt="7" src="https://github.com/user-attachments/assets/c7e92618-da77-4430-83f3-e9c1e36c3599" />
> <img width="482" height="201" alt="8" src="https://github.com/user-attachments/assets/d03a12f9-ac7c-4dfc-8208-78b34ababf83" />

> Finally, the secret code contained in the file was "THM{SECRET__CODE}."
>
> <img width="533" height="180" alt="9" src="https://github.com/user-attachments/assets/0d8c65e6-c398-47cd-9826-67aef4fce9bc" />

--- 

## Reflection

> This lab strengthened my ability to investigate a C2 communication alert using Elastic.
