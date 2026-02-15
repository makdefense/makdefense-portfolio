# [Web Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Detecting Web Attacks]  
**Date Completed**: [02/14/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of 
---

## 🎯 Objectives
- [ ] Understand the common methods used for data exfiltration.
- [ ] Learn how to detect exfiltration attempts using network traffic analysis.
- [ ] Identify signs of exfiltration on endpoint devices.
- [ ] Correlate logs in a SIEM to uncover hidden exfiltration channels.

---

## 🧰 Tools Used
- THM 

---

## 📊 Analysis & Screenshots

*** Log Based Detection ***

> For this room, I had to answer a few questions under the section of "Log Based Detection." I had to analyze a "access.log" file on the Desktop. For the first question i had to
figure out the Attacker's User-Agent while performing the directory fuzz. To figure this out i first launched the "access.log" file located on the Desktop, browsed through all the
requests to find repeated GET requests to different endpoints. Upon finding the repeated GET requests to different endpoints i retrieved the User-Agent "FFUF v2.1.0."
>
> <img width="473" height="263" alt="1" src="https://github.com/user-attachments/assets/7db5d9fc-52d1-43b0-9e57-dc24d38b5f4d" />
> <img width="636" height="291" alt="2" src="https://github.com/user-attachments/assets/bc80c16f-4fc9-40ad-b771-87624404c341" />

> Moving onto the next qeustion i had to figure out the name of the page on which the attacker performs a brute-force attack. To figure this out i navigated through the requests,
specifically looking for "POST" requests. After finding several "POST" request, i then retrieved the name of the page to be "/login.php" where the attacker performs a brute-force
attack.
>
> <img width="967" height="385" alt="3" src="https://github.com/user-attachments/assets/f50a6ab4-2598-48be-9f50-60e67903ef61" />

> For the last question of this section, i had to figure out the complete decoded SQLi payload the attacker uses on the "/changeusername.php" form. To figure this out i scrolled
down to the last "GET" request, copied + pasted "/account/changeusername.php?q=%25%27+OR+%271%27%3D%271 HTTP/1.1" 200 289 "sqlmap/stable" into CyberChef, and this retrieved the
decoded SQLi payload of "%' OR '1'='1."
>
> <img width="1119" height="215" alt="4" src="https://github.com/user-attachments/assets/0d0412ab-9cc1-475e-92d6-78a1a4fdddab" />
> <img width="1395" height="796" alt="Screenshot 2026-02-14 at 10 25 33 PM" src="https://github.com/user-attachments/assets/f2fe3682-312a-433b-ae9c-fda341e94fb7" />


> 


***  ***



--- 

## Reflection

> This lab provided me with knowledge on how to detect data exfiltration attempts across various network channels.
