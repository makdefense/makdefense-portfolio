# [Network Traffic Analysis]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Wireshark: Traffic Analysis]  
**Date Completed**: [01//2026]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding

---

## 🎯 Objectives
- [ ] 

---

## 🧰 Tools Used
- THM AttackBox
- THM Wireshark
  
---

## 📊 Analysis & Screenshots

*** Nmap Scans ***

> For this room, I had to investigate packet-level details by synthesizing the analyst knowledge and Wireshark functionality for detecting anomalies and odd situations for a given
case. For the first section of the room i had to answer a few questions within the "Nmap Scans" section by investigating a "Exercise.pcapng" file.
>
> <img width="365" height="249" alt="1" src="https://github.com/user-attachments/assets/35987c37-e975-44ab-bc41-1ca0f5103e2f" />
> <img width="443" height="279" alt="2" src="https://github.com/user-attachments/assets/bcedc07b-c10d-4f8e-ad20-59ebc280f4e1" />

> For the first question i had to find the total number of the "TCP Connect" scans. To figure this out after launching the "Exercise.pcapng" file with Wireshark i navigated to the
top of the web application, inputted "tcp.flags.syn==1" into the input field, pressed the enter button, then navigated to the drop-down menu at the bottom titled
"Transmission Control Protocol," selected "Window size value: 62727" under the "Flags" sub drop-down menu and dragged it into the input field selected "and selected" to add it to
the existing "tcp.flag.syn==1" filter. After doing that i then navigated back to the input field, adding another filter alongside the other two filters by inputting
"and tcp.flags.ack==0," which led me to have the filter expression of "(tcp.flags.syn==1) && (tcp.window_size_value == 62727) and tcp.flags.ack==0." After correlating this filter
i pressed "Enter" which then gave me the total number of "TCP Connect" scans to be "1000."
>
> <img width="388" height="199" alt="3" src="https://github.com/user-attachments/assets/719ede97-7760-4a5e-a8da-2e1451978e79" />
> <img width="472" height="151" alt="4" src="https://github.com/user-attachments/assets/0cb45ce4-e596-449d-b17d-e316d6b0646e" />
> <img width="664" height="310" alt="5" src="https://github.com/user-attachments/assets/5544fa5e-d802-44ca-b86e-78196c70b365" />
> <img width="733" height="174" alt="6" src="https://github.com/user-attachments/assets/7f80f84c-d179-4762-9f35-f0ff71be82f8" />
> <img width="494" height="173" alt="7" src="https://github.com/user-attachments/assets/4cdc5222-efd5-4258-9f05-7a9166503694" />




---

## Reflection

> This lab provided me with knowledge about 
