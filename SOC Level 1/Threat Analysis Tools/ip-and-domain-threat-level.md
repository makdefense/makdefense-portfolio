# [Threat Analysis Tools]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [IP and Domain Threat Intel]  
**Date Completed**: [03//2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding 

---

## 🎯 Objectives
- [ ] 
      
---

## 🧰 Tools Used
- THM AttackBox
- 

---

## 📊 Analysis & Screenshots

*** IP Building Blocks ***

> In this section, i had to answer a few questions based on investigating a downloadable report. For the first question i had to figure out the IP addresses for the A Record
associated with the flagged domain "advanced-ip-sccanner[.]com." To figure this out i simply downloaded the report, then launched it. Upon further investigation i was able to
discover the IP addresses to be "172.67.189.143,104.21.9.202."
>
> <img width="1063" height="711" alt="1" src="https://github.com/user-attachments/assets/c58b4d84-ce8f-4bcf-b245-ef7e50995b29" />

> Moving on to the next question i had to figure out the nameservers that was associated with the IP addresses, then defang the addresses. After navigating down to the NS records,
and upon further investigation i was able to retrieve the defanged addresses "jaziel[.]ns[.]cloudflare[.]com, and summer[.]ns[.]cloudflare[.]com."
>
> <img width="1006" height="305" alt="2" src="https://github.com/user-attachments/assets/e9061618-1da6-4c74-90f8-20f7c5464774" />
> <img width="1217" height="671" alt="3" src="https://github.com/user-attachments/assets/9883101e-9f25-4dab-8ddc-9c49e7907876" />
> <img width="1040" height="674" alt="4" src="https://github.com/user-attachments/assets/6a345374-403c-4e32-8af3-9ff62bc12924" />

*** IP Enrichment: Geolocation and ASN ***

> Moving on to this section, i had to answer a few questions based on using "client.rdap.org" to investigate the IP address "64[.]31[.]63[.]194." For the first question i had to
figure out when "64[.]31[.]63[.]194" IP was logged for registration. To figure this out i first launched the domain "client.rdap.org," then entered the IP address within the input
field, then pressed "enter." After pressing "enter" i was able to discover that the IP was logged for registration on 12/27/2010, 3:51:03 PM.
>
> <img width="918" height="260" alt="5" src="https://github.com/user-attachments/assets/7cb30e72-2e48-4ff2-b2f6-348b58c91f83" />
> <img width="1009" height="877" alt="6" src="https://github.com/user-attachments/assets/12ba8f42-436d-4a02-ac7d-e83f1e721559" />

> Moving on to the next question, i had to figure out what roles were assigned to the entity Entity NOC2791-ARIN associated with the 64[.]31[.]63[.]194 IP address. To figure this
out i simply scrolled further down, then discovered the roles that were assigned to be "administrative, and technical" right under the "entities" sub-header.
>
> <img width="837" height="287" alt="7" src="https://github.com/user-attachments/assets/ae3d2b77-a2b5-45c1-9461-99611d97c4db" />

> For the next question i had to figure out the country's name for the 64[.]31[.]63[.]194 IP address. Upon further investigation, using IP info, after inputting the IP address into
the input field i was able to retrieve the country "France" under the summary sub-header.
>
> <img width="935" height="863" alt="8" src="https://github.com/user-attachments/assets/b91499a1-d8d6-4173-923b-1d7937955fee" />

> For the last question i had to identify the Autonomous System linked with the same IP address. To figure this out i simply stayed within the summary section, navigated to the top,
and retrieved the Autonomous System "AS136258."
>
> <img width="953" height="261" alt="9" src="https://github.com/user-attachments/assets/2f927c58-d70d-4ccb-8438-4b180a2644fb" />










--- 

## Reflection

> This lab strengthened my ability to 
