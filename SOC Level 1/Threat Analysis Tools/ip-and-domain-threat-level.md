# [Threat Analysis Tools]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [IP and Domain Threat Intel]  
**Date Completed**: [04/05/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of enriching IP and domain data using open-source threat intelligence. This process helps quickly determine whether an indicator is
malicious or benign, reduces false positives, improves decision-making during investigations, and provides deeper insight into attacker behavior. It is a core skill for SOC
analysts, as it transforms raw alerts into actionable intelligence and enhances the accuracy and professionalism of analysis.

---

## 🎯 Objectives
- [ ] Understand IP and domain fundamentals (A records, NS records)
- [ ] Perform IP enrichment using RDAP and geolocation tools
- [ ] Analyze service exposure using Shodan and Censys
- [ ] Conduct reputation checks using VirusTotal
- [ ] Apply passive DNS and WHOIS analysis
      
---

## 🧰 Tools Used
- THM AttackBox
- RDAP (client.rdap.org)
- IPinfo
- Shodan
- Censys
- crt.sh
- VirusTotal
- NS Lookup

---

## 📊 Analysis & Screenshots

*** IP Building Blocks ***

> In this section, I answered several questions by investigating a downloadable report. For the first question, I identified the IP addresses for the A record associated with the
flagged domain advanced-ip-scanner[.]com. To do this, I downloaded and opened the report. Upon investigation, I discovered the IP addresses to be:

172.67.189.143, 104.21.9.202
>
> <img width="1063" height="711" alt="1" src="https://github.com/user-attachments/assets/c58b4d84-ce8f-4bcf-b245-ef7e50995b29" />

> For the next question, I identified the nameservers associated with the domain and defanged them. After navigating to the NS records, I retrieved the following:

jaziel[.]ns[.]cloudflare[.]com, summer[.]ns[.]cloudflare[.]com
>
> <img width="1006" height="305" alt="2" src="https://github.com/user-attachments/assets/e9061618-1da6-4c74-90f8-20f7c5464774" />
> <img width="1217" height="671" alt="3" src="https://github.com/user-attachments/assets/9883101e-9f25-4dab-8ddc-9c49e7907876" />
> <img width="1040" height="674" alt="4" src="https://github.com/user-attachments/assets/6a345374-403c-4e32-8af3-9ff62bc12924" />

*** IP Enrichment: Geolocation and ASN ***

> In this section, I investigated the IP address 64[.]31[.]63[.]194 using client.rdap.org. First, I identified the registration date by entering the IP into the RDAP tool. The IP
was registered on:

12/27/2010, 3:51:03 PM
>
> <img width="918" height="260" alt="5" src="https://github.com/user-attachments/assets/7cb30e72-2e48-4ff2-b2f6-348b58c91f83" />
> <img width="1009" height="877" alt="6" src="https://github.com/user-attachments/assets/12ba8f42-436d-4a02-ac7d-e83f1e721559" />

> Next, I identified the roles assigned to the entity NOC2791-ARIN. By reviewing the “entities” section, I found the roles to be:

Administrative and Technical
>
> <img width="837" height="287" alt="7" src="https://github.com/user-attachments/assets/ae3d2b77-a2b5-45c1-9461-99611d97c4db" />

> I then determined the country associated with the IP address using IPInfo. The result showed:

France
>
> <img width="935" height="863" alt="8" src="https://github.com/user-attachments/assets/b91499a1-d8d6-4173-923b-1d7937955fee" />

> Finally, I identified the Autonomous System:

AS136258
>
> <img width="953" height="261" alt="9" src="https://github.com/user-attachments/assets/2f927c58-d70d-4ccb-8438-4b180a2644fb" />

*** Service Exposure ***

> In this section, I investigated the IP address 85[.]188[.]1[.]133 using multiple services. First, I used Shodan to identify the exposed services. The first exposed service was:

FTP
>
> <img width="1496" height="536" alt="10" src="https://github.com/user-attachments/assets/da6e3fb0-81a7-4b7a-a2f7-4d079c8dac5c" />

> I then identified the number of open ports on the server:

6 open ports
>
> <img width="632" height="214" alt="11" src="https://github.com/user-attachments/assets/3486470a-387a-44c3-83f6-4432866d533a" />

> Next, I used Censys to retrieve the TLS certificate fingerprint:

5ea8e6046bdabaa8e23a1a012c01d1be5ccd42c66ef2577a59f3b3f0f056d12e
>
> <img width="1129" height="475" alt="12" src="https://github.com/user-attachments/assets/beade5ee-3a9c-427c-b560-d36f962021da" />
> <img width="653" height="276" alt="13" src="https://github.com/user-attachments/assets/8f25a258-1e97-4774-bce5-b1475ad5f58f" />

> Finally, I used crt.sh to identify the certificate’s Subject Common Name:

archive.scene.org
>
> <img width="854" height="406" alt="14" src="https://github.com/user-attachments/assets/034aa3c7-2c0c-4899-8a9c-ca09fbb95dfc" />
> <img width="866" height="298" alt="15" src="https://github.com/user-attachments/assets/cb6fa65d-a8fd-4c82-8925-606f0bcbfd6c" />

*** Reputation Checks and Passive DNS ***

> In this section, I investigated the IP address 166[.]1.160[.]118 using VirusTotal. First, I identified a file linked to the IP by navigating to the “Relations” tab. The
associated file was:

ff4c287c60ede1990442115bddd68201d25a735458f76786a938a0aa881d14ef.exe
>
> <img width="1065" height="756" alt="16" src="https://github.com/user-attachments/assets/aa0ee73a-89a0-49de-923e-f6b35811a408" />
> <img width="1341" height="681" alt="17" src="https://github.com/user-attachments/assets/fd67345e-290b-4b28-9dc3-ce421b5f1415" />

> I then reviewed the “Historical WHOIS” section and identified the associated organization:

Ace Data Centers, Inc.
>
> <img width="934" height="275" alt="18" src="https://github.com/user-attachments/assets/02861fcd-d367-48d6-b342-3127fda19f39" />

*** Challenge ***

> In this section, I enriched multiple indicators. First, I identified the RIR associated with 170[.]130[.]202[.]134 using RDAP. The result was:

ARIN
>
> <img width="1108" height="281" alt="19" src="https://github.com/user-attachments/assets/b69cd811-6ead-432e-b601-97869cb3ec19" />
> <img width="876" height="316" alt="20" src="https://github.com/user-attachments/assets/36e6bbc1-0292-4c96-bf0b-6ca5d04e6642" />

> Next, I identified the ASN using Shodan:

AS62904
>
> <img width="654" height="612" alt="21" src="https://github.com/user-attachments/assets/ea4cc6fe-d745-497a-9c63-6ab34747ee46" />

> Finally, I determined the number of NS records for the domain santagift[.]shop using NS Lookup:

4 NS records
>
> <img width="997" height="559" alt="22" src="https://github.com/user-attachments/assets/ab187b3f-f0b3-4b94-91da-b5d6bbb576b6" />
> <img width="1274" height="781" alt="23" src="https://github.com/user-attachments/assets/e186be9b-9594-4dc0-9a9b-8c2b9dd1b5c8" />
--- 

## Reflection

> This lab strengthened my ability to enrich IP and domain data using open-source threat intelligence and improved my confidence in analyzing real-world indicators.
