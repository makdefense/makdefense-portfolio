# [Network Traffic Analysis]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Wireshark: Packet Operations]  
**Date Completed**: [01//2026]

---

## 🧠 Summary

> In this lab,

---

## 🎯 Objectives
- [ ] 

---

## 🧰 Tools Used
- THM AttackBox
- THM Wireshark
- THM 
  
---

## 📊 Analysis & Screenshots

*** Introduction ***

> For this room, I had to investigate an event at the packet-level using Wireshark. The file that i had to investigate was located on the THM AttackBox titled "Exercise.pcapng."
So after i launched the THM AttackBox i double-clicked the "Exercise.pcapng" file to open it with Wireshark to start the exercise.
>
> <img width="503" height="370" alt="1" src="https://github.com/user-attachments/assets/86c7e3b1-177e-4c3b-889c-89bb50393252" />

*** Statistics | Summary ***

> For the first exercise question under this section i had to figure out the IP address of the hostname that starts with "bbc." To figure this out i had to investigate the
resolved addresses by navigating to the top of the Wireshark application, then clicking the "Statistics" header, then "Resolved Addresses," then inputting within the input field
"bbc," which then retreived the IP address of "199.232.24.81" for the hostname that starts with "bbc."
>
> <img width="825" height="295" alt="2" src="https://github.com/user-attachments/assets/066d0ea5-f954-471b-979e-aa43f7ee2ed9" />
> <img width="817" height="679" alt="3" src="https://github.com/user-attachments/assets/8bf75b50-13d6-4d54-a1cf-4e637c654877" />

> For the next question i had to figure out the number of IPv4 conversations. To figure this out i had to navigate to the top of the Wireshark application, then click the
"Statistics" header, then "Conversations," then navigate to the "IPv4" section, which then retrieved 435 IPv4 connections.
>
> <img width="474" height="259" alt="4" src="https://github.com/user-attachments/assets/3700a854-8d15-4118-8cdd-5eef63d1be99" />
> <img width="697" height="300" alt="5" src="https://github.com/user-attachments/assets/be3aa552-80d0-431e-831c-f6146d765647" />

> For the next question i had to figure out how many bytes (k) were transferred from the "Micro-ST" MAC Address. To figure this out i navigated to the top of the Wireshark
application, then click the "Statistics" header, then "Endpoints," then check the "Name Resolution" box, which then retrieved the total number of bytes transferred from
"Micro-ST" to be "7474K."
>
> <img width="622" height="274" alt="6" src="https://github.com/user-attachments/assets/a113d503-2ccf-4f98-96ff-aaa107a03b92" />
> <img width="1110" height="705" alt="7" src="https://github.com/user-attachments/assets/44ea4861-3529-4b68-8dd9-0141fcf10ebc" />

> For the next question i had to figure out the number of "Kansas City" linked IP addresses. To figure this out i navigated to the top of the Wireshark application, clicked
"Statistics" header, then "Endpoints," then clicked "IPv4" section, which then retrieved a total of 4 IP addresses linked with "Kansas City."
>
> <img width="644" height="263" alt="8" src="https://github.com/user-attachments/assets/b09e7d4c-e873-45e9-89b8-7e543e572217" />
> <img width="1020" height="147" alt="9" src="https://github.com/user-attachments/assets/5af4eb1c-cfa2-4876-a8dd-49894417fbec" />

> For the last question of this section i had to figure out which IP address was linked with "Blicnet" AS Organisation. To figure this out i navigated to the top of the Wireshark
application, clicked "Endpoints," then navigated to the "AS Organisation" sub-header within the "IPv4" section, scrolled to find "Blicnet," after finding the organization, i
retrieved the IP address to be "188.246.82.7" with "Blicnet" AS Organisation.
>
> <img width="645" height="306" alt="10" src="https://github.com/user-attachments/assets/1c5da585-c142-4967-9de9-f8b87ae7eef3" />
> <img width="600" height="189" alt="11" src="https://github.com/user-attachments/assets/57715301-c619-4c02-a7ac-c80cb4e027e3" />
> <img width="421" height="115" alt="12" src="https://github.com/user-attachments/assets/17a91d77-7798-4dac-a382-9e83d1f17776" />

*** Statistics | Protocol Details ***

> Moving onto the next section of this lab for the first question of this exercise i had to figure out the most used IPv4 destination address. To figure this out i navigated to the
top of the Wireshark application, clicked "Statistics" header, then "Source and Destination Addresses," then clicked "Destination IPv4 Addresses" dropdown menu to expand it, then
hovered over to the "Count" dropdown menu, clicked it, which then retrieved the most used IPv4 address of "10.100.1.33."
>
> <img width="907" height="853" alt="13" src="https://github.com/user-attachments/assets/f87de3fc-ca34-47b2-bebb-6e7de686da81" />
> <img width="992" height="609" alt="14" src="https://github.com/user-attachments/assets/bb1d1d3f-d8f8-4480-8d26-dff84e2ebe17" />

> For the next question i had to figure out the max service request-response time of the DNS packets. To figure this out i navigated to the top of the Wireshark application,
selected "Statistics," then clicked on "DNS," then hovered over to the "Service Stats" dropdown header under the "Total Packets" header, after clicking it to expand it i
retrieved the max service request-response to be "0.467897."
>
> <img width="674" height="812" alt="15" src="https://github.com/user-attachments/assets/3f654fdc-a02d-4b61-8f76-b6f47bc8e977" />
> <img width="933" height="592" alt="16" src="https://github.com/user-attachments/assets/b23351f4-7995-471e-a97e-e7950b4be43b" />

> For the last question of this exercise i had to figure out the total number of HTTP requests accomplished by "rad[.]msn[.]com." To figure this out i navigated to the top of the
Wireshark applicaton, clicked "Statistics," then "HTTP," then "Requests," then under "HTTP Requests by HTTP HOST" i selected the domain "rad.msn.com," scrolled right to see
that the total number of HTTP Requests accomplished were "39."
>
> <img width="688" height="763" alt="17" src="https://github.com/user-attachments/assets/bcdcc2e0-1561-4e81-b543-11996462f2bb" />
> <img width="863" height="568" alt="19" src="https://github.com/user-attachments/assets/13493819-fe53-4cf4-80dc-6d9f3a47b15d" />
> <img width="919" height="595" alt="18" src="https://github.com/user-attachments/assets/6254caeb-b66e-45d1-b5fd-e5b4cdd43c08" />

*** Packet Filtering | Protocol Filters ***

> Moving onto the next section of this lab for the first question of this exercise i had to 

















---

## Reflection

> This lab provided me with knowledge about 
