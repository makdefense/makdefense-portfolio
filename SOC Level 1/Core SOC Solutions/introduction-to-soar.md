# [Core SOC Solutions]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Introduction to SOAR]  
**Date Completed**: [12/13/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding the traditional SOC and its challenges, which is that it gives you context on how security operations evolved, why
modern SOCs work the way they do, and what limitations you must overcome as an analyst. It helps you recognize gaps in visibility, staffing, processes, and technology so you can
work smarter, reduce alert fatigue, improve detection quality, and contribute to a more efficient security operation. Next, I learned about the importance of understanding how
SOAR overcomes SOC's challenges, which are that SOAR automates repetitive work, reduces alert fatigue, improves response speed, standardizes investigations, and allows analysts to
focus on high-value threat analysis. Knowing this helps you operate more efficiently, build better playbooks, and contribute to a modern, scalable security operation. Finally, I
learned about the importance of understanding SOAR Playbooks, which is that they define how incidents are automatically investigated, enriched, and responded to. Knowing playbooks
allows analysts to reduce manual work, increase consistency, improve response speed, eliminate human error, and ensure that SOC processes scale efficiently. Playbooks are the
backbone of modern automated security operations.


---

## 🎯 Objectives
- [ ] Understand the traditional SOC and its challenges
- [ ] Explore how SOAR overcomes these challenges
- [ ] Learn SOAR Playbooks

---

## 🧰 Tools Used
- THM Static Site
  
---

## 📊 Analysis & Screenshots

*** Threat Intel Workflow Practical ***

> For this room, I had to complete a practical in which I set up automated workflows (playbooks) to support security investigations. I had to figure out how to work a check-
list for a Threat Intelligence integration workflow.

> <img width="828" height="450" alt="soar1" src="https://github.com/user-attachments/assets/07577cee-bdb1-49b8-85db-b1352bff410f" />

> For the first instance, I had to figure out which settings to automate for "Case Management Settings." The settings that needed automation were "Create Case Ticket," "Communicate
Case Ticket," and "Assign Case Ticket." I left the "Delete Case Ticket" setting to manual.

> <img width="947" height="615" alt="soar2" src="https://github.com/user-attachments/assets/0bdbe5ed-4c31-48ff-b240-c943dd51ed38" />

> For the second instance, I had to figure out which settings to automate for "Threat Intelligence Feeds." The settings that needed automation were "Fetch New Incident Alerts,"
"Set Fetch Intervals," and "Failed Fetch Notifications." I left "Discard Old Alerts" to manual.

> <img width="910" height="619" alt="soar3" src="https://github.com/user-attachments/assets/afc0478a-e236-48af-b5db-45f80a891d5f" />

> In the third instance, I had to determine which settings to automate for "Incident Data Extraction." The settings that needed automation were "Extract Domains," "Extract URLs,"
and "Extract IPs." I left "Analyst Extraction" to manual.

> <img width="804" height="632" alt="soar4" src="https://github.com/user-attachments/assets/eea96ee1-ea38-449a-a434-d1dfab7fd1f8" />

> For the fourth instance, I had to figure out which settings to automate for "Reputation Checks." The settings that needed automation were "Reputation Results Output." I left
"Sandbox Testing" and "Analyst Validation" to the manual.

> <img width="802" height="727" alt="soar5" src="https://github.com/user-attachments/assets/17a455ac-fd6e-4f3e-8d17-99f252ac1359" />

> For the fifth instance, I had to figure out which settings to automate for "Course of Action." The settings that needed automation were "Block Domains," "Block IPs," "Block
URLs," and "Update Case Tickets." I left "Analyst Approve COA" to manual.

> <img width="816" height="662" alt="soar6" src="https://github.com/user-attachments/assets/7ba930e1-ffa6-429c-b597-fd857da16d37" />

> After completing all instances, I retrieved the flag "THM{AUT0M@T1N6_S3CUR1T¥}."

> <img width="884" height="493" alt="soar7" src="https://github.com/user-attachments/assets/d9fcf8ab-864c-45b5-bcb8-f80d162b808e" />
---

## Reflection

> This lab provided me with knowledge about the concepts and methodology surrounding security orchestration, automation, and repsonse.
