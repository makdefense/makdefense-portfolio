# [Cyber Threat Intelligence]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [MISP]  
**Date Completed**: [10//2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding 

---

## 🎯 Objectives
- [ ] Learn about MISP and why it was developed.
- [ ] Learn about its core features and terminologies
- [ ] Learn how to navigate the dashboard
- [ ] Learn about event creation and management
- [ ] Learn about feeds and taxonomies

---

## 🧰 Tools Used
- THM AttackBox
- THM MISP
- THM Mozilla FireFox
 
---

## 📊 Analysis & Screenshots

*** Scenario Event ***

> After reading the sections within MISP i was given a scenario event to complete, i had to investigate an event and correlate the details with my SIEM that was published by CIRCL with "PupyRAT" infection.
For the first question i had to figure out the event ID that has been assigned to the "PupyRAT" event. To figure this out i first launched the MISP by going to Mozilla FireFox and inputting the website
"https://10-201-89-204.reverse-proxy-us-east-1.tryhackme.com/" into the input field, then pressing "enter."
>
> <img width="918" height="183" alt="misp1" src="https://github.com/user-attachments/assets/196dae8e-d5da-4d97-908f-6f7e7f76fbf4" 

> After logging into the MISP with the credentials "Username: Analyst@THM.thm" and "Password: Analyst12345&" i then navigated to the right of the home page and inputted "PupyRAT" within the input field
of the events filter, then pressed "filter."
>
> <img width="524" height="233" alt="misp2" src="https://github.com/user-attachments/assets/2eb80c3d-0079-4779-af5c-92c989acf4c1" />

> When i pressed "filter" it popped up the event "PupyRAT."
>
> <img width="1876" height="697" alt="misp3" src="https://github.com/user-attachments/assets/fe9aff7d-f053-40fc-8183-0cf7b3b7bd63" />

> I then navigated to the left of the filter result and saw the event ID of "1145."
>
> <img width="545" height="251" alt="misp4" src="https://github.com/user-attachments/assets/eaf03911-ef55-4d59-8085-721cfee472fc" />

> For the next question i had to figure out what specifically the adversary was gaining into organizations. To figure this out i simply navigated around the search result and saw the "malware type" to be
"Remote Access."
>
> <img width="670" height="103" alt="misp5" src="https://github.com/user-attachments/assets/694e1682-6ba0-4bdd-930e-1c83e8968407" />

> Moving onto the next question i had to figure out the IP address that has been mapped as the "PupyRAT C2 Server." To figure this out i hovered over to the right of the page and selected the "view"
icon.
>
> <img width="261" height="198" alt="misp6" src="https://github.com/user-attachments/assets/c94895d3-a404-48d6-809e-f2cd3163ae09" />

> After clicking the view icon i scrolled down to "network activity" and saw the IP address of "89.107.62.39" mapped as the command and control server.
>
> <img width="1513" height="112" alt="misp7" src="https://github.com/user-attachments/assets/1a8ec711-41de-4f55-8477-16a6bde532bf" />

> For the second to last question i had to figure out which attack group is known to use this form of attack from the "Intrusion Set Galaxy." To figure this out i just navigated to the top and saw
within the "Tags" that the attack group was "Magic Hound."
>
> <img width="562" height="87" alt="misp8" src="https://github.com/user-attachments/assets/5686647f-f694-4070-b9f8-b52b34064f92" />

> For the final question i had to figure out what was the taxonomy tag set with a Certainty level of 50. To figure this out i just navigated to the "Tags" area and saw under the certainty level of 50
the tag set was "OSINT."
>
> <img width="804" height="272" alt="misp9" src="https://github.com/user-attachments/assets/cb4dd15e-ac6e-4153-aad9-953d7ec1432e" />

---

## Reflection

> This lab provided me with knowledge about MISP as a threat sharing platform.
