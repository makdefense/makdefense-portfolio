# [Web Hacking]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [OWASP Top 10 - 2021]  
**Date Completed**: [09//2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding 

## 🎯 Objectives
- [ ] Learn about 
   
---

## 🧰 Tools Used
- THM Machine
- 

---

## 📊 Analysis & Screenshots

*** Broken Access Control (IDOR Challenge) ***

> After launching the THM Machine, I was given a task to do an IDOR challenge under the Broken Access Control section. I had to find a flag that was within the other users' notes. To do this i first
opened "Mozilla FireFox" and went to the website "http://10.201.106.172" and used the login credentials of the username "noot" and password "test1234."
>
> <img width="1036" height="738" alt="owasp1" src="https://github.com/user-attachments/assets/d631af1a-2057-42d9-adff-dbc54529b23a" />

> Then to find the flag i just went to the searchbar in Mozilla FireFox and changed the website from "http://10.201.106.172/note.php?note_id=1" to "http://10.201.106.172/note.php?note_id=0" and it
retrieved the flag of "flag{fivefourthree}"
>
>  <img width="1080" height="684" alt="owasp2" src="https://github.com/user-attachments/assets/0e213d12-fa97-4894-b305-1dc821ee6119" />



---


## Reflection

> This lab provided me with knowledge and hands-on experience with Burp Suite for web application pentesting.

