# [Web Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Detecting Web DDoS  
**Date Completed**: [02/16/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding 

---

## 🎯 Objectives
- [ ] 
---

## 🧰 Tools Used
- THM Attackbox
- THM 
---

## 📊 Analysis & Screenshots

*** Log Analysis ***

> For this room, I began by answering questions under this section. For the first question, I had to investigate a "access.log" file on the Desktop that shows a denial-of-service.
I had to figure out the attacker's IP address. To figure this out, i launched the "access.log" file that was on the Desktop, then navigated through the results to find repeated
"GET" requests that seemed suspicious. After investigating i determined the attacker's IP address to be "203.12.23.195."
>
> <img width="466" height="262" alt="1" src="https://github.com/user-attachments/assets/ae780e72-7f32-4048-a2c3-11e5e0e4589f" />
> <img width="541" height="294" alt="2" src="https://github.com/user-attachments/assets/2fc7288f-1f49-4b6a-ba89-3838353a1bc9" />

> Moving on to the next question i had to figure out which page was repeatedly targeted by the attacker's requests. To figure this out i navigated to the "Get" requests under the
same IP address, and saw that the page that was repeatedly targeted by the attacker's requests to be "/login."
>
> <img width="874" height="261" alt="3" src="https://github.com/user-attachments/assets/0dd942d9-5be6-45c2-8410-ba9ff53ce126" />

> For the last question of this section i had to figure out the error code that legitimate users received after the DOS attack. To figure this out i scrolled to the bottom of the
results of the "access.log" file, investigated a legitimate IP address which was "192.168.1.10," and saw next to the "GET" request that the error code retrieved by legitimate users
to be "503."
>
> <img width="1086" height="132" alt="4" src="https://github.com/user-attachments/assets/5678a91d-3eac-45f1-a3b8-824297387ffc" />

*** Leveraging SIEMs ***

> Under this section, i had to answer a few questions using Splunk, and analyze web access logs that experienced a suspected DDoS attack. For the first question i had to figure out
the most frequently requested uri. To figure this out, i first launched Mozilla FireFox, copied and pasted the Splunk link: "http://MACHINE_IP:8000" into the input field, clicked
search, opened the "Search & Reporting" App in Splunk, then ran a search in the main index. After running the search i navigated to the left of the Splunk App, selected the "uri"
filter, and determined the most frequently requested uri to be "/search."
>
> <img width="753" height="250" alt="5" src="https://github.com/user-attachments/assets/b449cd71-6cf8-4c15-b600-1f2095dedc79" />
> <img width="474" height="206" alt="6" src="https://github.com/user-attachments/assets/b84d59b8-a621-4045-aa83-d21469b7977e" />
> <img width="922" height="339" alt="7" src="https://github.com/user-attachments/assets/7dad0590-dfe1-4cd4-b824-0b3966c4b015" />

> Moving on to the next question i had to figure out which clientip made the most reuqests to the target uri. To figure this out i navigated to the search field in the Splunk App,
entered index="main" uri="/search", pressed "enter," navigated to the left of the App, selected the filter "clientip," and determined the clientip that made the most requests to
the targeted uri to be "203.0.113.7."
>
> <img width="499" height="235" alt="8" src="https://github.com/user-attachments/assets/b7a8f86c-843c-4f71-8b88-b0fb3ffb8bb3" />
> <img width="947" height="431" alt="9" src="https://github.com/user-attachments/assets/94f64028-8671-404a-a767-8fef9db16c84" />

> For the next question i had to figure out how many IP addresses were part of the botnet that attacked my website. To figure this out i navigated to the left of the App, selected
"clientip" filter, and saw that there were a total of 60 IP addresses apart of the botnet that attacked my website.
>
> <img width="733" height="260" alt="10" src="https://github.com/user-attachments/assets/c9ca2f34-0545-495a-94d9-268bbaad0fe5" />

> Moving on to the next question i had to figure out which useragent was most commonly used by the attacking traffic. To figure this out i navigated back to the left of the Splunk
App, selected "useragent" filter and determined the most commonly useragent used by the attacking traffic to be "Java/1.8.0_181."
>
> <img width="626" height="337" alt="11" src="https://github.com/user-attachments/assets/de241f28-afcd-46f1-91ab-6a99af0d40fe" />

> For the second to last question i had to figure out the peak number of requests made per second during the attack by using the timechart command. To go about this i navigated
to the search field above, then entered index="main" | timechart span=1s count, pressed "enter," then selected the visualize tab. After doing this i detemrined the peak number of
requests made per second was "207."
>
> <img width="579" height="160" alt="12" src="https://github.com/user-attachments/assets/f713c6bf-62d2-43b5-a435-b107fe808350" />
> <img width="508" height="358" alt="13" src="https://github.com/user-attachments/assets/9b0a979a-92b2-4e2a-a256-59fa1112e780" />
















--- 

## Reflection

> This lab strengthened my ability to detect post-exploitation activity by analyzing logs, filesystem artifacts, and attacker command execution patterns.
