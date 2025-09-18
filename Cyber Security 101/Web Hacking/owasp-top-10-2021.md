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

***  Cryptographic Failures (Challenge) ***

> After reading through the Cryptographic Failure section i was then given a challenge to connect to the web application at "http://10.201.48.55:81/" and answer some questions.
>
> <img width="1098" height="285" alt="owasp3" src="https://github.com/user-attachments/assets/139933b5-0054-44e4-9c00-ed445f973da5" />

> For the first question i had to figure out the name of a specific directory that contained sensitive data in which a developer indicated with a note. To do this i right-clicked on the website and
selected "View Page Source," clicked on "/login.php" and saw that the sensitve data was located within the directory called "/assets."
>
> <img width="932" height="624" alt="owasp4" src="https://github.com/user-attachments/assets/1b70b5ff-d5a0-48ad-a2cd-1f617eb53470" />

> Next i had to figure out which file that stood out within the directory that would likely contain sensitve information. So what i did was just went to the top of the searchbar and added
"/assets" to the website "http://10.201.48.55:81/," and saw the file that stood out to be called "webapp.db."
>
> <img width="551" height="443" alt="owasp5" src="https://github.com/user-attachments/assets/d8d9ebee-5b95-448f-951e-519f41df6f58" />

> I then had to use the same file to figure out the password hash of the admin user. To do this i first downloaded the file to the linux terminal by clicking on it in Mozilla FireFox, then went back
to the terminal and inputted the command "sqlite3 webapp.db" to access the sqlite database.
>
> <img width="787" height="183" alt="owasp6" src="https://github.com/user-attachments/assets/f87f3cde-42f4-48b8-93be-3f8c66649957" />

> I then inputted the command ".tables" to see all the tables within the "webapp.db" databse.
>
> <img width="171" height="41" alt="owasp7" src="https://github.com/user-attachments/assets/f2cb9894-f044-4e6d-afbe-744976ddd0c1" />

> Next i had to dump all the data from the "users" table by first inputting the command "PRAGMA table_info(users);" to see the information within the table.
>
> <img width="331" height="96" alt="owasp8" src="https://github.com/user-attachments/assets/c7d849db-7314-49be-b78e-b55d607ee247" />

> Then inputted the command "SELECT * FROM users;" then "enter" to dump the information from the table, and saw that the password hash for the user "admin" was "6eea9b7ef19179a06954edd0f6c05ceb."
>
> <img width="718" height="131" alt="owasp9" src="https://github.com/user-attachments/assets/9812b4c1-981f-4aca-a954-eccbc21f2bf0" />

> Following, i had to crack the password hash of the user "admin." To do this i just copied and pasted the hash into the free password hash cracker "CrackStation" and clicked submit and saw that the
plaintext password was "qwertyuiop"
>
> <img width="1128" height="442" alt="owasp10" src="https://github.com/user-attachments/assets/dc2c2070-7f6b-4a29-853d-add4c53974a5" />

> Finally, i had to find a flag within the website "http://10.201.48.55:81/" by using the log in credentials i retrieved for the user "admin."
>
> <img width="1015" height="410" alt="owasp11" src="https://github.com/user-attachments/assets/76467938-2c13-4012-ba7f-245ea588d777" />

> After inputting the login credentials and clicking login, i retrieved the flag "THM{Yzc2YjdkMjE5N2VjMzNhOTE3NjdiMjdl}."
>
> <img width="1002" height="407" alt="owasp12" src="https://github.com/user-attachments/assets/bc943869-e6b8-46fb-90c3-01c04c197a2d" />

*** ***












---


## Reflection

> This lab provided me with knowledge and hands-on experience with Burp Suite for web application pentesting.

