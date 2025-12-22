# [Phishing Analysis]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [The Greenholt Phish-CTF]  
**Date Completed**: [12//2025]

---

## 🧠 Summary

> In this lab, 
---

## 🎯 Objectives
- [ ] 
      
---

## 🧰 Tools Used
- THM 
  
---

## 📊 Analysis & Screenshots

***  ***

> For this room, i had to investigate an email sample to determine if it was legitimate for a sales executive at Greenholt PLC. For the first four questions i had to figure out
the Transfer Reference Number listed on the email's Subject, who the email was from, what was the person's email address, and what email address will recieve a reply to the same
email i am tasked to investigate. To figure this out i had to first launch the attached virtual machine, then navigate to the machine's desktop, and double-click on the
email file "challenge.eml" to open it. After opening it, i discovered that the Transfer Reference Number listed on the email's subject was "09674321." I then discovered that the
email was from "Mr. James Jackson," and his email address was "info@mutawamarine.com." For the email address that will receive a reply to the email was discovered to be
"info.mutawamarine@mail.com."
>
> <img width="360" height="648" alt="gp1" src="https://github.com/user-attachments/assets/40301c7a-b270-4706-962b-9d5292a64ed7" />
> <img width="967" height="270" alt="gp2" src="https://github.com/user-attachments/assets/0615b49e-bbb6-44e7-89ad-921d876d1d21" />

> Moving onto the next question i had to figure out the Originating IP. To figure this out i navigated to the top right, clicked "more" drop-down menu, selected "view source,"
then navigated through the email header information and saw that the originating IP was "192.119.71.157."
>
> <img width="447" height="472" alt="gp3" src="https://github.com/user-attachments/assets/246a64be-e73a-424e-836a-e6f3fdcd893f" />
> <img width="734" height="514" alt="gp4" src="https://github.com/user-attachments/assets/56e755e0-08d8-4a78-bf60-11f1e0fff962" />

> For the next question i had to figure out the owner of the Originating IP. To figure this out i simply went back to the IP address i found in the email header, copied & pasted it
into the web application "WhoIs," and saw that it belonged to "Hostwinds LLC."
>
> <img width="375" height="314" alt="gp5" src="https://github.com/user-attachments/assets/79a428a8-c4de-462a-adee-7447e62422ee" />
> <img width="1115" height="703" alt="gp6" src="https://github.com/user-attachments/assets/324023b3-d979-4aeb-9433-1bb0c88fa7fc" />

> Moving onto the next two questions i had to figure out the SPF record for the Return-Path domain, and the DMARC record for the Return-Path domain. To figure this out i navigated
back to the email header, copied everything within the email header & pasted it into the web application "mxlookup" under the "Email Header Analyzer" section. After doing this i
retrieved "v=spf1 include:spf.protection.outlook.com -all" for the SPF record, and "v=DMARC1; p=quarantine; fo=1" for the DMARC record.
>
> <img width="698" height="567" alt="gp7" src="https://github.com/user-attachments/assets/9908ab50-a408-4314-b505-106f6ce51d2d" />
> <img width="1191" height="565" alt="gp8" src="https://github.com/user-attachments/assets/e3b54c81-07dd-44df-975a-fa77494e37b4" />

> 









---

## Reflection

> This lab provided me with knowledge about 
