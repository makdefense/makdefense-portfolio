# [Phishing Analysis]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [The Greenholt Phish-CTF]  
**Date Completed**: [12/23/2025]

---

## 🧠 Summary

> In this lab, I used the knowledge I attained from the rooms within the phishing analysis module to analyze a malicious email.

---

## 🎯 Objectives
- [ ] Commplete "The Greenholt Phish" Room
     
---

## 🧰 Tools Used
- THM Attackbox
- THM ThunderBird
- THM Terminal
- VirusTotal
- Google Chrome

---

## 📊 Analysis & Screenshots

*** Just another day as a SOC Analyst ***

> For this room, I had to investigate an email sample to determine if it was legitimate for a sales executive at Greenholt PLC. For the first four questions, I had to figure out
the Transfer Reference Number listed in the email's Subject, who the email was from, what the person's email address was, and what email address would receive a reply to the same
email I am tasked to investigate. To figure this out, I first had to launch the attached virtual machine, then navigate to the machine's desktop, and double-click on the
email file "challenge.eml" to open it. After opening it, I discovered that the Transfer Reference Number listed in the email's Subject was "09674321." I then found that the
email was from "Mr. James Jackson," and his email address was "info@mutawamarine.com." The email address that will receive a reply to the email was discovered to be
"info.mutawamarine@mail.com."
>
> <img width="360" height="648" alt="gp1" src="https://github.com/user-attachments/assets/40301c7a-b270-4706-962b-9d5292a64ed7" />
> <img width="967" height="270" alt="gp2" src="https://github.com/user-attachments/assets/0615b49e-bbb6-44e7-89ad-921d876d1d21" />

> Moving on to the next question, I had to figure out the Originating IP. To figure this out, I navigated to the top right, clicked the "more" drop-down menu, selected "view
source," then, I navigated through the email header information and saw that the originating IP was "192.119.71.157."
>
> <img width="447" height="472" alt="gp3" src="https://github.com/user-attachments/assets/246a64be-e73a-424e-836a-e6f3fdcd893f" />
> <img width="734" height="514" alt="gp4" src="https://github.com/user-attachments/assets/56e755e0-08d8-4a78-bf60-11f1e0fff962" />

> For the next question, I had to figure out the owner of the Originating IP. To figure this out, I went back to the IP address I found in the email header, copied & pasted it
into the web application "WhoIs," and saw that it belonged to "Hostwinds LLC."
>
> <img width="375" height="314" alt="gp5" src="https://github.com/user-attachments/assets/79a428a8-c4de-462a-adee-7447e62422ee" />
> <img width="1115" height="703" alt="gp6" src="https://github.com/user-attachments/assets/324023b3-d979-4aeb-9433-1bb0c88fa7fc" />

> Moving on to the following two questions, I had to determine the SPF record and DMARC record for the Return-Path domain. To figure this out, I navigated
back to the email header, copied everything within the email header & pasted it into the web application "mxlookup" under the "Email Header Analyzer" section. After doing this, I
retrieved "v=spf1 include:spf.protection.outlook.com -all" for the SPF record, and "v=DMARC1; p=quarantine; fo=1" for the DMARC record.
>
> <img width="698" height="567" alt="gp7" src="https://github.com/user-attachments/assets/9908ab50-a408-4314-b505-106f6ce51d2d" />
> <img width="1191" height="565" alt="gp8" src="https://github.com/user-attachments/assets/e3b54c81-07dd-44df-975a-fa77494e37b4" />

> Moving on to the next question, I had to figure out the name of the attachment in the email I was investigating. To figure this out, I navigated back to the email header,
and saw that the attachment's name was "SWT_#09674321____PDF__.CAB."
>
> <img width="675" height="537" alt="gp9" src="https://github.com/user-attachments/assets/e8633c72-9e80-4766-97e9-fe458500fd5b" />

> For the next question, I had to compute the SHA-256 hash of the file attachment. To figure this out, I downloaded the attachment onto the Desktop by navigating to the bottom
email, then launched the Terminal application, input the command "ls," then "enter," then "cd Desktop," then "enter," then "ls," then "enter." After doing all this, I was able to
see the attachment from the email I downloaded onto the Desktop. Now to list the SHA256 of the attachment i entered the command "sha256sum SWT_#09674321____PDF__.CAB," then
"enter." After doing this, I was able to retrieve the SHA256 of "2e91c533615a9bb8929ac4bb76707b2444597ce063d84a4b33525e25074fff3f."
>
> <img width="1104" height="246" alt="gp10" src="https://github.com/user-attachments/assets/08e8c402-0c67-4b19-a3b4-b6d1a69c9b07" />
> <img width="752" height="498" alt="gp11" src="https://github.com/user-attachments/assets/b3504cbb-8233-43fe-9e88-82937ac28fe7" />
> <img width="777" height="516" alt="gp12" src="https://github.com/user-attachments/assets/29c96da1-bfe0-4bc6-be9a-fec160198721" />

> For the last two questions in this challenge, I had to determine the attachment's file size and the actual file extension. To figure this out, I launched
Google Chrome on my machine, launched the website "VirusTotal," copied & pasted the SHA256 into the input field, then pressed "enter." After the search
ran its course, I then navigated to the "details" tab to see the attachment's file size to be "400.26 KB" and the actual file extension of the attachment to be "RAR."
>
> <img width="1000" height="656" alt="gp13" src="https://github.com/user-attachments/assets/543f3f99-9649-44d8-938c-e1fdfbdf485d" />
> <img width="800" height="640" alt="gp14" src="https://github.com/user-attachments/assets/c7ccff4e-8941-4a59-8bb0-279e42cef88e" />
> <img width="691" height="590" alt="gp15" src="https://github.com/user-attachments/assets/961dce6e-3d7e-4d78-a794-87bfa6ffcada" />
---

## Reflection

> This lab provided me with knowledge about analyzing malicious emails.
