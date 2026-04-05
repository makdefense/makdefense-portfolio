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

*** Service Exposure ***

> Moving on to this section, i had to use several services to investigate the "85[.]188[.]1[.]133" IP address. For the first question, i had to use shodan.io to figure out the first
exposed service name of the 85[.]188[.]1[.]133 IP. After launching shodan.io, i inputted the IP within the input field, then pressed "enter." Upon further investigation i was able
to discover the first exposed service name to be "FTP."
>
> <img width="1496" height="536" alt="10" src="https://github.com/user-attachments/assets/da6e3fb0-81a7-4b7a-a2f7-4d079c8dac5c" />

> I then had to figure out how many open ports there were on the exposed server. Upon further investigation i was able to retrieve 6 open ports on the exposed server.
>
> <img width="632" height="214" alt="11" src="https://github.com/user-attachments/assets/3486470a-387a-44c3-83f6-4432866d533a" />

> Moving on to the next question, i had to use "search.censys.io" to figure out the TLS certificate fingerprint for the 85[.]188[.]1[.]133 IP. After launching the "search.censys.io"
web service, then inputting the IP addresses into the input field, then pressing "enter." I was able to retrieve the TLS certificate fingerprint
"5ea8e6046bdabaa8e23a1a012c01d1be5ccd42c66ef2577a59f3b3f0f056d12e."
>
> <img width="1129" height="475" alt="12" src="https://github.com/user-attachments/assets/beade5ee-3a9c-427c-b560-d36f962021da" />
> <img width="653" height="276" alt="13" src="https://github.com/user-attachments/assets/8f25a258-1e97-4774-bce5-b1475ad5f58f" />

> For the last question i had to figure out the Subject's commonName of the identified TLS certificate using the web service "crt.sh." Upon launching the service, then inputting the
TLS certificate into the input field, then pressing "enter" i was able to retrieve the Subject's commonName to be "archive.scene.org" under the "X509v3 Subject Alternative Name"
sub-header.
>
> <img width="854" height="406" alt="14" src="https://github.com/user-attachments/assets/034aa3c7-2c0c-4899-8a9c-ca09fbb95dfc" />
> <img width="866" height="298" alt="15" src="https://github.com/user-attachments/assets/cb6fa65d-a8fd-4c82-8925-606f0bcbfd6c" />

*** Reputation Checks and Passive DNS ***

> For this section, i had to answer a few questions based on investigating the "166[.]1.160[.]118" IP address using Virus Total. For the first question i had to figure out what file
has been linked to the 166[.]1.160[.]118 IP address. To figure this out i launched VirusTotal, then inputted the IP address into the input field, pressed "enter," then navigated to
the "Relations" section only to discover that the file "ff4c287c60ede1990442115bddd68201d25a735458f76786a938a0aa881d14ef.exe" was linked to 166[.]1.160[.]118 IP address.
>
> <img width="1065" height="756" alt="16" src="https://github.com/user-attachments/assets/aa0ee73a-89a0-49de-923e-f6b35811a408" />
> <img width="1341" height="681" alt="17" src="https://github.com/user-attachments/assets/fd67345e-290b-4b28-9dc3-ce421b5f1415" />

> For the last question i had to figure out which organisation was identified on historical WHOIS lookups. Upon further investigation, navigating to the sub-header
"Historical WHOIS lookups," i retrieved the organization "Ace Data Centers, Inc."
>
> <img width="934" height="275" alt="18" src="https://github.com/user-attachments/assets/02861fcd-d367-48d6-b342-3127fda19f39" />

*** Challenge ***

> For the final section of this room, i had to complete a challenge by answering a set of questions based on enriching three indicators. For the first question i had figure out the
RIR associated with 170[.]130[.]202[.]134 IP. To figure this out i launched the domain "client.rdap.org," then inputted the 170[.]130[.]202[.]134 IP into the input field, pressed
"enter," navigated down to the sub-header "Entites," and was able to retireve the RIR "ARIN."
>
> <img width="1108" height="281" alt="19" src="https://github.com/user-attachments/assets/b69cd811-6ead-432e-b601-97869cb3ec19" />
> <img width="876" height="316" alt="20" src="https://github.com/user-attachments/assets/36e6bbc1-0292-4c96-bf0b-6ca5d04e6642" />

> I then had to figure out what ASN the 170[.]130[.]202[.]134 IP was connected with. To figure this out i launched the we service "shodan.io," then inputted the
170[.]130[.]202[.]134 IP into the input field, pressed "enter," and upon further investigation i was able to retireve the ASN "AS62904."
>
> <img width="654" height="612" alt="21" src="https://github.com/user-attachments/assets/ea4cc6fe-d745-497a-9c63-6ab34747ee46" />

> Moving on to the next question, i had to figure out the number of NS records for the domain "santagift[.]shop." After launching the web service "NS lookup," then inputting the
domain into the input field, then pressing "enter," iwas able to retrieve the total number of  NS records of 4.
>
> <img width="997" height="559" alt="22" src="https://github.com/user-attachments/assets/ab187b3f-f0b3-4b94-91da-b5d6bbb576b6" />
> <img width="1274" height="781" alt="23" src="https://github.com/user-attachments/assets/e186be9b-9594-4dc0-9a9b-8c2b9dd1b5c8" />
--- 

## Reflection

> This lab strengthened my ability to 
