# [Web Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Detecting Web DDoS] 
**Date Completed**: [02/16/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding denial-of-service (DoS) attacks, detection methods, and protection strategies. These attacks can shut down systems and
disrupt business operations. Learning how to recognize traffic anomalies, identify attack patterns, and apply defensive measures helps analysts respond quickly and prevent
outages. These skills build real incident-response capability and are essential for cybersecurity professionals, especially SOC analysts.
---

## 🎯 Objectives
- [ ] Learn how denial-of-service attacks function
- [ ] Understand attacker motives behind the disruptive attacks
- [ ] See how web logs can help you reveal signs of web DoS and DDoS
- [ ] Get practice analyzing denial-of-service attacks through log analysis
- [ ] Discover detection and mitigation techniques defenders can use

---

## 🧰 Tools Used
- THM Attackbox
- THM Splunk
- THM Mozilla FireFox

---

## 📊 Analysis & Screenshots

*** Log Analysis ***

> For this room, I began by answering questions under this section. For the first question, I had to investigate an "access.log" file on the Desktop that showed a denial-of-
service attack. I had to determine the attacker’s IP address. To do this, I opened the "access.log" file located on the Desktop and navigated through the results to find repeated
GET requests that appeared suspicious. After investigating, I determined that the attacker’s IP address was "203.12.23.195."
>
> <img width="466" height="262" alt="1" src="https://github.com/user-attachments/assets/ae780e72-7f32-4048-a2c3-11e5e0e4589f" />
> <img width="541" height="294" alt="2" src="https://github.com/user-attachments/assets/2fc7288f-1f49-4b6a-ba89-3838353a1bc9" />

> Moving on to the next question, I had to determine which page was repeatedly targeted by the attacker’s requests. To do this, I navigated through the GET requests from the same
IP address and observed that the repeatedly targeted page was "/login."
>
> <img width="874" height="261" alt="3" src="https://github.com/user-attachments/assets/0dd942d9-5be6-45c2-8410-ba9ff53ce126" />

> For the last question of this section, I had to determine the error code that legitimate users received after the DoS attack. To do this, I scrolled to the bottom of the
"access.log" results and investigated a legitimate IP address, "192.168.1.10." I observed next to the GET request that the error code returned to legitimate users was "503."
>
> <img width="1086" height="132" alt="4" src="https://github.com/user-attachments/assets/5678a91d-3eac-45f1-a3b8-824297387ffc" />

*** Leveraging SIEMs ***

> Under this section, I had to answer several questions using Splunk and analyze web access logs that experienced a suspected DDoS attack. For the first question, I had to
determine the most frequently requested URI. To do this, I first launched Mozilla Firefox, copied and pasted the Splunk link "http://MACHINE_IP:8000" into the address bar, opened
the Search & Reporting app in Splunk, and ran a search in the main index. After running the search, I navigated to the left panel of the Splunk interface, selected the "uri"
filter, and determined that the most frequently requested URI was "/search."
>
> <img width="753" height="250" alt="5" src="https://github.com/user-attachments/assets/b449cd71-6cf8-4c15-b600-1f2095dedc79" />
> <img width="474" height="206" alt="6" src="https://github.com/user-attachments/assets/b84d59b8-a621-4045-aa83-d21469b7977e" />
> <img width="922" height="339" alt="7" src="https://github.com/user-attachments/assets/7dad0590-dfe1-4cd4-b824-0b3966c4b015" />

> Moving on to the next question, I had to determine which clientip made the most requests to the target URI. To do this, I navigated to the Splunk search field and entered:
index="main" uri="/search"
After running the search, I selected the "clientip" filter and determined that the client IP that made the most requests to the targeted URI was "203.0.113.7."
>
> <img width="499" height="235" alt="8" src="https://github.com/user-attachments/assets/b7a8f86c-843c-4f71-8b88-b0fb3ffb8bb3" />
> <img width="947" height="431" alt="9" src="https://github.com/user-attachments/assets/94f64028-8671-404a-a767-8fef9db16c84" />

> For the next question, I had to determine how many IP addresses were part of the botnet that attacked the website. To do this, I navigated to the left panel of the Splunk
interface, selected the "clientip" filter, and observed that there were a total of 60 IP addresses that were part of the botnet.
>
> <img width="733" height="260" alt="10" src="https://github.com/user-attachments/assets/c9ca2f34-0545-495a-94d9-268bbaad0fe5" />

> Moving on to the next question, I had to determine which user agent was most commonly used by the attacking traffic. To do this, I selected the "useragent" filter and
determined that the most commonly used user agent was "Java/1.8.0_181."
>
> <img width="626" height="337" alt="11" src="https://github.com/user-attachments/assets/de241f28-afcd-46f1-91ab-6a99af0d40fe" />

> For the second-to-last question, I had to determine the peak number of requests made per second during the attack using the timechart command. To do this, I entered the
following query:
index="main" | timechart span=1s count
After running the query and selecting the Visualize tab, I determined that the peak number of requests per second was 207.
>
> <img width="579" height="160" alt="12" src="https://github.com/user-attachments/assets/f713c6bf-62d2-43b5-a435-b107fe808350" />
> <img width="508" height="358" alt="13" src="https://github.com/user-attachments/assets/9b0a979a-92b2-4e2a-a256-59fa1112e780" />

> For the last question, I had to determine which legitimate (non-attacking) client IP received the first 503 response status after the attack. To do this, I entered the
following query:
index="main" status=503
After running the search, I navigated to page 8 and scrolled to the earliest timestamp showing a 503 response. I determined that the first legitimate client IP to receive a 503
response was "10.10.0.27."
>
> <img width="526" height="166" alt="14" src="https://github.com/user-attachments/assets/de39344f-47b7-4d73-aec0-14dcb546e299" />
> <img width="454" height="170" alt="15" src="https://github.com/user-attachments/assets/7f441c4f-ec98-4a21-981e-0e10cfe31e1f" />
> <img width="1247" height="139" alt="16" src="https://github.com/user-attachments/assets/9e0d809a-0510-48ac-b957-bf218f4edfd0" />

--- 

## Reflection

> This lab strengthened my ability to detect volumetric attack patterns, analyze traffic anomalies, and identify indicators of distributed denial-of-service activity using both
logs and SIEM tools.
