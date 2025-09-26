# [Offensive Security Tooling]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [SQLMap: The Basics]  
**Date Completed**: [09/26/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding SQL injection vulnerability, which is that it teaches you how attackers steal and manipulate data, how to test for the problem safety, and
(most importantly) how to stop it with secure coding and controls. I then learned the importance of understanding how to hunt SQL injection through the SQLMap tool, which teaches you how SQLi
works in practice, how to validate fixes, how to tune detections, and how to prioritize remediation.

---

## 🎯 Objectives
- [ ] Learn about SQL injection vulnerability
- [ ] Learn how to hunt SQL injection through the SQLMap tool.
      
---

## 🧰 Tools Used
- THM AttackBox
- THM Linux
- THM SQLMap tool

---

## 📊 Analysis & Screenshots

*** Practical Exercise ***

> After launching the THM Machine and reading through the SQL Injection Vulnerability and Automated SQL Injection Tool, I had a practical to complete. The first question I had was to figure out how many
databases were in a given web application. The given web application's website was "http://10.201.60.176/ai/login." So I navigated to the website by inputting "http://10.201.60.176/ai/login" in the
search bar of Mozilla Firefox.

> <img width="840" height="877" alt="sql1" src="https://github.com/user-attachments/assets/cc7d2aa9-cf7b-4aad-bc44-699e2a2aa05d" />

> I then had to extract a URL with its GET parameters using a process that involved inputting test login credentials into the input fields. After inputting login credentials "test" and "1234," I then
right-clicked on the page, pressed "inspect," then navigated to the "network" tab, and then copied the URL from the "GET" request section.

> <img width="1016" height="596" alt="sql2" src="https://github.com/user-attachments/assets/205d366b-2812-44db-b9bb-49330f04a891" />

> I then launched the Linux Terminal, I inputted the command syntax "sqlmap -u 'http://10.201.60.176/ai/includes/user_login?email=test&password=test' --dbs," then pressed "enter" to figure out how many
databases were in the web application. After running the command, I retrieved six databases.

> <img width="899" height="280" alt="sql3-1" src="https://github.com/user-attachments/assets/7d291f3e-31f4-483e-8abd-0ec51dc1eb2a" />

> For the following question in the practical, I had to figure out the name of the table available in the "ai" database. To do this, I input the command syntax
"sqlmap -u 'http://10.201.60.176/ai/includes/user_login?email=test&password=test' -D ai --tables," then pressed "enter," and retrieved the name of the table "user."

> <img width="1439" height="821" alt="sql4" src="https://github.com/user-attachments/assets/1c88bf9d-92fd-47d7-a51d-38ee1dbfe23e" />

> Finally, for the last question, I had to figure out the password of the email test@chatai.com. To do so, I had to input the command syntax
"sqlmap -u 'http://10.201.60.176/ai/includes/user_login?email=test&password=test' -D ai -T user --dump," then pressed "enter" to retrieve the password "12345678" for the email test@chatai.com.

> <img width="718" height="248" alt="sql5" src="https://github.com/user-attachments/assets/20c81e55-a8c4-49b3-81ca-470347957751" />

---

## Reflection

> This lab provided me with knowledge about SQL injection and how to exploit a vulnerability through the SQLMap Tool.
