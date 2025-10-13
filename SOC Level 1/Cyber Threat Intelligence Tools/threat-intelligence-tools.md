# [Cyber Threat Intelligence]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Threat Intelligence Tools]  
**Date Completed**: [10//2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding 

---

## 🎯 Objectives
- [ ] Learn about 

---

## 🧰 Tools Used
- THM 
  
---

## 📊 Analysis & Screenshots

*** PhishTool ***

> After reading the sections within Threat Intelligence, i was given my first task which was to analyze a suspicious email called "Email1.eml" which was store on the THM AttackBox Desktop.
>
> <img width="482" height="353" alt="tit7" src="https://github.com/user-attachments/assets/81cca89e-cd19-40f1-b104-654bf5206bdd" />

> For the first question i had to figure out the social media platform the attacker was trying to pose as within the email. To figure this out i just open the email with the application "ThunderBird"
which was located on the THM AttackBox and saw that the attacker was trying to pose as "LinkedIn."
>
> <img width="653" height="212" alt="tit8" src="https://github.com/user-attachments/assets/2191ba0d-9da7-4d73-b547-69222717c00c" />

> For the next question i had to figure out the senders email address. To figure this out i simply just navigated to the top of the email within the ThunderBird application and saw that the sender's
email address was "darkabutla@sc500.whpservers.com."
>
> <img width="408" height="113" alt="tit9" src="https://github.com/user-attachments/assets/f3bc7bcd-4e21-447b-90b5-67d446552167" />

> For the next question i had to figure out the recipient's email address. To figure this out i did the same thing navigated to the top of the email within the ThunderBird application and saw that the
reciever's email address was "cabbagecare@hotsmail.com."
>
> <img width="547" height="80" alt="tit10" src="https://github.com/user-attachments/assets/03c05299-c18c-4d95-9ef1-05244e11d908" />

> For the last question for this task i had to figure out the Originating IP address then Defang the IP address. So to go about this the first thing i did was navigated to the Desktop, double-clicked on
the emails folder, then right-clicked on "Email1.eml," and selected open with "Pluma."
>
> <img width="645" height="323" alt="tit11" src="https://github.com/user-attachments/assets/a02d4aea-1fa2-4871-b868-c85f75be1ade" />

> After opening the email file with Pluma i then navigated to the IP address that was under received by which was the IP address of "204.93.183.11."
> 
> <img width="417" height="220" alt="tit12" src="https://github.com/user-attachments/assets/57745a93-84dc-40e7-90cb-528d7391bd74" />

> I then went to Google Chrome and launched CyberChef, searched "Defang" within the input field under Operations, and selected "Defang IP addresses."
>
> <img width="1024" height="269" alt="tit13" src="https://github.com/user-attachments/assets/983ae7f9-d9ed-4274-b459-c08270649d39" />

> I then navigated to the right area of CyberChef, copied and pasted the IP address "204.93.183.11" within the input field and retrieved the defanged IP address of "204[.]93[.]183[.]11."
>
> <img width="256" height="722" alt="tit14" src="https://github.com/user-attachments/assets/7eccb852-3cf7-473d-8df2-54653abbeb6b" />

*** Cisco Talos Intelligence ***

> For my next task i had to use information that i gathered from inspecting "Email1.eml" to answer a few questions using Cisco Talos Intelligence. For the first question i had to figure out the listen
domain of the IP address of "204.93.183.11." To figure this out i navigated to the website "https://talosintelligence.com/," then copied and pasted the IP address "204.93.183.11" into the input field
that was under "Intelligence Center."
>
> <img width="1058" height="340" alt="tit15" src="https://github.com/user-attachments/assets/447cf5b5-7208-4125-8c92-f709523d8183" />

> After clicking the search button i navigated to the button where the details of the IP address was listed and saw that the listed domain was "scnet.net."
>
> <img width="526" height="122" alt="tit16" src="https://github.com/user-attachments/assets/1c8e09bc-2999-4ba6-8860-29310220f88a" />

> For the next question i had to figure out the customer's name of the IP address. To figure this out in Google Chrome i searched the website "https://www.whois.com/whois/," then inputted the IP address
"204.93.183.11" within the input field under "Whois search for Domain and IP," and clicked the search button.
>
> <img width="1207" height="567" alt="tit17" src="https://github.com/user-attachments/assets/fc8e8146-36e3-4067-be35-12c852ffb8c1" />

> After clicking the search button i then scroll down to retrieve the "CustName" which was "Complete Web Reviews."
>
> <img width="701" height="281" alt="tit18" src="https://github.com/user-attachments/assets/2efa97f8-2653-46d5-8204-022f97efa6fc" 

*** Scenario 1 ***

> For my next scenario i had to analyze another suspicious email called "Email2.eml" which was located on the THM AttackBox Desktop in the Emails folder and answer a few questions.
>
> <img width="736" height="369" alt="Screenshot 2025-10-12 at 10 29 32 PM" src="https://github.com/user-attachments/assets/0ade5264-a3b4-46e8-a39b-87776d918353" />

> For the first question i had to figure the recipient's email address. To figure this out i navigated to the "Email2.eml" file, double-clicked it to open it with ThunderBird, navigated to the top and
saw that the recipient's email address was "chris.lyons@supercarcenterdetroit.com."
>
> <img width="558" height="319" alt="tit20" src="https://github.com/user-attachments/assets/aa9659c3-372f-4bf7-809d-c0b7da24e607" />

> For the last question for this scenario i had to figure out which Detection Alias can the email file "Email2.eml" be identified by, from the information given by VirusTotal. To figure this out i first
went back to the VM on THM, launched the Terminal application, inputted the command "ls," then "enter" to list all directories. After locating the Desktop directory, i then inputted the command "cd
Desktop," then "Enter," then "ls," then "Enter" to list all files within the Desktop directory. After locating the "Emails" directory i inputted the command "cd Emails," then "Enter," then "ls," then
"Enter" to list all files within the "Emails" directory. After locating the file "Email2.eml," i then inputted the command "sha256sum Email2.eml," then "enter" to retrieve the hash of the email file
which was "97028b1b198af6da1043b78e40e1efe519fe3def754cd9d1f29380ca11e5c361."
>
> <img width="739" height="347" alt="tit21" src="https://github.com/user-attachments/assets/60775c41-a540-4861-9ce8-c7e8447e9598" />

> I then went to Google Chrome and navigated to "https://www.virustotal.com/gui/home/upload," copied and pasted the hash "97028b1b198af6da1043b78e40e1efe519fe3def754cd9d1f29380ca11e5c361" into the input
field above.
>
> <img width="670" height="166" alt="tit22" src="https://github.com/user-attachments/assets/0166d5b0-7c1f-4b1d-95ad-1e1abf087665" />

> After pressing the "Enter" key on the keyboard i navigated through the information given by "Virus Total" and saw the Detection Alias to be "HIDDENEXT/Worm.Gen."
>
> <img width="750" height="702" alt="tit23" src="https://github.com/user-attachments/assets/321c80c5-a42b-48ac-856b-b479b6e2a463" />

*** Scenario 2 ***

> For my next scenario i had to analyze another suspicious email called "Email3.eml" which was located on the THM AttackBox Desktop in the Emails folder and answer a few questions.
>
> <img width="715" height="374" alt="tit24" src="https://github.com/user-attachments/assets/a9eff8b9-98dd-4fa0-b0bd-7605800ec4d7" />

> For the first question i had to figure out the name of the attachment that was on the "Email3.eml." To figure this out i just double-clicked on the email file to open up the file with ThunderBird,
clicked on the attached file at the bottom of the email, and saw that the name of the file was "Sales_Receipt 5606.xls."
>
> <img width="812" height="601" alt="tit25" src="https://github.com/user-attachments/assets/1719c96f-7f9e-429c-8279-eaeb12c9a67b" />

> For the last question i had to figure out the malware family that was associated with the "Email3.eml" file. To figure this out i had to retrieve the SHA256 hash. To get this i launched the
"Terminal" application that was on the THM AttackBox, then inputted the command "ls," then "enter" to list all the directories. After locating the Desktop directory, i then inputted the command "cd
Desktop," then "Enter," then "ls," then "Enter" to list all the files within the Desktop directory. After locating the "Emails" directory i inputted the command "cd Emails," then "Enter," then "ls,"
then "Enter" to list all files within the "Emails" directory. After locating the file "Email3.eml," i then inputted the command "sha256sum Email3.eml," then "enter" to retrieve the hash of the email
file which was "f4d97603256a36e81bfe7ef5e0ccaee44f77de6bb041fa41f0b3a0db53f4aba9."
>
> <img width="756" height="393" alt="tit27" src="https://github.com/user-attachments/assets/2f93f628-3d32-484a-a04e-fef90001d3e7" />

> I then went to Google Chrome and navigated to "https://www.virustotal.com/gui/home/upload," copied and pasted the hash "f4d97603256a36e81bfe7ef5e0ccaee44f77de6bb041fa41f0b3a0db53f4aba9," into the
input field above.
>
> <img width="688" height="192" alt="tit28" src="https://github.com/user-attachments/assets/f67a031b-99be-4136-a333-d2214ea00961" />

> After pressing the "Enter" key on the keyboard i navigated through the information given by "Virus Total" and saw the malware family associated with the attachment on "Email3.eml" to be "Dridex."
>
> <img width="650" height="253" alt="tit29" src="https://github.com/user-attachments/assets/c6728e0b-1f35-4795-99b3-67d00ace13ba" />

---

## Reflection

> This lab provided me with knowledge about the 

