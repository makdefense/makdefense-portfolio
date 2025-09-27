# [Defensive Security]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Incident Response Fundamentals]  
**Date Completed**: [09/27/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding what incidents are and their severity levels, which is that they turn noise into prioritised action - they tell your team what to do first,
who to notify, and how fast to act, which reduces damage, saves time, and makes responses repeatable and auditable. Next, I learned about the importance of understanding the common types of incidents,
which is that they turn vague alarms into fast, correct action - you detect faster, respond smarter, reduce business impact, and build repeatable defenses. Following, I learned about the phases of
incident response from SANS and NIST Frameworks, which is that they give you proven, repeatable roadmaps for handling security incidents - learning their phases teaches you what to do, when to do it, who
should act, and why each step matters. That turns chaotic firefighting into defensible, fast, and measurable incident response. Finally, I learned about the importance of understanding the tools for
incident detection and response, along with the role of playbooks, which is that tools surface and let you act on evidence; playbooks tell people precisely what to do with that evidence so you contain
damage fast, preserve evidence, and prevent repeat mistakes.

---

## 🎯 Objectives
- [ ] Learn what are incidents and their severity levels
- [ ] Learn about the Common types of incidents
- [ ] Learn about Phases of Incident Response from SANS and NIST Frameworks
- [ ] Learn the Tools for Incident Detection and Response along with the role of PlayBooks
      
---

## 🧰 Tools Used
- THM Site
  
---

## 📊 Analysis & Screenshots

*** Lab Work Incident Response ***

> After reading through all the sections within Incident Response Fundamentals, I was given a practical exercise at the end to initiate an incident by downloading an attachment from a phishing email.
First, I had to open the site within the THM room. I then had to figure out the name of the malicious email sender. To do this, I just clicked the message "We have sent you the payment for the month of
April," after clicking the message, I saw that the name of the malicious email sender was 'Jeff Johnson."

> <img width="464" height="372" alt="ir1" src="https://github.com/user-attachments/assets/b0494d40-9531-4b34-9ae7-f1fd50c1e683" />

> I then had to determine the threat vector. I figured this out by basically seeing that the malicious email sender sent an email with an attachment, so the threat vector was classified as "email
attachment."

> I then had to figure out how many devices downloaded the file. To figure this out, I downloaded the "Payslip.pdf" file and saw a pop-up called "Malware detected on host!" I then clicked the "Take Actions"
button and saw that the total number of devices that downloaded the file was 3. The device names were "HOST-ATYU," "HOST-IOPE," and "HOST-HKNV."

> <img width="840" height="504" alt="ir3" src="https://github.com/user-attachments/assets/ab75a4b7-fbe1-4046-9e0a-6332b4a75ff9" />

> I then had to figure out how many devices executed the file. I saw this by checking that "HOST-HKNV" had an "executed" status under the "state" category within the environment.

> <img width="729" height="93" alt="ir7" src="https://github.com/user-attachments/assets/2aadcf48-4666-4e55-a587-20e597117f3d" />

> I then had to quarantine the hosts "HOST-ATYU" and "HOST-IOPE" and then investigate the host "HOST-HKNV." I was then prompted with a message titled "Isolate The Host." After clicking the "Isolate The
Host" button, I contained the malicious email sent from "Jeff Johnson" and retrieved the flag "THM{My_First_Incident_Response}"

> <img width="484" height="346" alt="ir6" src="https://github.com/user-attachments/assets/4e3756c3-a77b-4b5a-a275-7a0d2d54a5c2" />

---

## Reflection

> This lab provided me with knowledge about how to perform Incident Response in cybersecurity.
