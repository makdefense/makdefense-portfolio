# [Core SOC Solutions]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Elastic Stack: The Basics]  
**Date Completed**: [12/09/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding

---

## 🎯 Objectives
- [ ] 

---

## 🧰 Tools Used
- THM AttackBox
- THM ELK Instance
- THM Mozilla FireFox
  
---

## 📊 Analysis & Screenshots

*** Lab Connection ***

> For this room, i had to learn how to use the Elastic Stack for log investigations. I had to first set up the lab connection by launching the target machibe then launching the
THM AttackBox, launching Mozilla FireFox, then inputting the link "http://10.67.157.183" within the input field to access the ELK Instance. After pressing "Enter" i was brought
to the login screen for the ELK Instance. I then used the credentials "Analyst" and "analyst123" to login.
>
> <img width="723" height="678" alt="elas1" src="https://github.com/user-attachments/assets/c464f033-6bc7-458a-b5a8-f84bb58822ab" />

*** Discover Tab ***

> After reading through this section, i was given my first question which was to figure out how many hits were returned after selecting the "vpn_connections" and filter from
31st December 2021 to 2nd Feb 2022. To figure this out i first selected the index "vpn_connections," then navigated to the top right hand corner of the Instance, selected
the dates "31st December 2021 to 2nd Feb 2022" under "Absolute" mode, then pressed "Update" which returned "2861" hits.
>
> <img width="736" height="609" alt="elas2" src="https://github.com/user-attachments/assets/fdebde9e-4552-416a-a80d-29b5b73f1fca" />
> <img width="593" height="427" alt="elas3" src="https://github.com/user-attachments/assets/d0c8636a-a33f-42e0-b529-5bb5b2346587" />

> Moving onto the next question i had to figure out which IP address had the maximum connections. To figure this out i navigated to the left handed side of the Instance under
"Filter by type," and "Available fields," selected "Source_ip," and saw that the IP address of "238.163.231.224" had the maximum connections.
>
> <img width="634" height="440" alt="elas4" src="https://github.com/user-attachments/assets/4bfbdc37-174e-4cb6-8f32-22cfbe1f0369" />

> Next question i had to figure out which user was responsible for the overall maximum traffic. To figure this out i navigated to the left handed side of the Instance, selected
both "Source_ip" and "UserName," then hovered over the filter "UserName" and saw that the UserName "James" was responsible for the overall maximum traffic.
>
> <img width="611" height="785" alt="elas5" src="https://github.com/user-attachments/assets/61dc5114-ca38-4804-962a-c4c9ad741e53" />

> Next question i had to figure out which "SourceIP" had max hits under the UserName "Emanda." To figure this out i simply navigated to the left under "Filter by type," hovered
over "UserName" selected "Emanda," then hovered over "Source_ip," and saw that the IP with the max hits were "107.14.1.247."
>
> <img width="645" height="790" alt="elas6" src="https://github.com/user-attachments/assets/6de73718-c8d0-48a1-af78-7ca48a45b978" />







---

## Reflection

> This lab provided me with knowledge about how SOC analysts use the Elastic Stack (ELK) for log investigations.
