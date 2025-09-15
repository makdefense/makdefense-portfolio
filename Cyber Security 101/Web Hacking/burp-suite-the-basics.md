# [Web Hacking]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Burp Suite: The Basics]  
**Date Completed**: [09//2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding 

---

## 🎯 Objectives
- [ ] Learn 
   
---

## 🧰 Tools Used
- THM Machine
-

---

## 📊 Analysis & Screenshots

*** Options ***

> After launching the THM Machine, then launching the Burp Suite application i then read about configuring Burp Suite settings then had a few questions to answer after familiarizing myself with the
settings.

> <img width="895" height="517" alt="burp1" src="https://github.com/user-attachments/assets/6351c24b-9613-4305-9695-1b5da5ac3e18" />

> I had to first figure out in which category within the setting i could find a reference to "cookie jar." To do this i clicked on the "settings" tab.

> <img width="179" height="50" alt="burp2" src="https://github.com/user-attachments/assets/e97f8ef1-4080-4a3b-8115-26a88802c8c6" />

> Then searched for "cookie jar" within the search bar and saw it under the category of "sessions."

> <img width="517" height="340" alt="burp3" src="https://github.com/user-attachments/assets/af6a1b0d-e2b0-4b79-b88e-5e1315b54c07" />

> I then had to figure out in which category i could find the "updates" sub-category that controls the Burp Suite update behavior. To do this i searched "updates" and saw it under the sub-
category of "Suite."

> <img width="684" height="294" alt="burp4" src="https://github.com/user-attachments/assets/1fb85fee-6ad0-4d2e-9a54-9620612bef9a" />

*** Connecting Through the Proxy (FoxyProxy) ***

> Next, i had to use the Burp Suite Proxy. To do this i had to configure my local web browser to redirect traffic through Burp Suite. I had to launch Mozilla FireFox browser then click the FoxyProxy
icon in the top right.

> <img width="366" height="410" alt="burp5" src="https://github.com/user-attachments/assets/c35a5d5d-9461-4687-925b-2a2a0511a08a" />

> Since the "Burp" proxy was already created within the FoxyProxy system and all of the options were added i moved on to the next step.

> <img width="1375" height="585" alt="burp6" src="https://github.com/user-attachments/assets/884f2185-65be-49d9-aa9d-3267c071bbc6" />

> I then had to open "Burp suite" to make sure interception was turned on and it was.

> <img width="1305" height="481" alt="burp7" src="https://github.com/user-attachments/assets/8344440b-de5b-47c1-aa6d-3c4d0b4d93ab" />

> So i went back to my Mozilla FireFox browser to test the proxy. I entered the website "http://10.201.115.162/," went back to "Burp Suite" and it showed me that i had just intercepted my first request.

> <img width="1270" height="636" alt="burp8" src="https://github.com/user-attachments/assets/92eab525-2c58-4a59-83a6-3665cc9c4c71" />

*** Site Map and Issue Definitions ***

> I was then given a practical to find a flag within "Burp Suite" after looking around the site "http://10.201.115.162/." So first i opened "Burp Suite," clicked on the "Scope" tab and inputted the site
"http://10.201.115.162/" within the "Prefix" text field, then pressed "ok."

> <img width="950" height="608" alt="burp9" src="https://github.com/user-attachments/assets/90484312-067a-48eb-b97b-f223d492d48e" />

> I then went to Mozilla FireFox and look around site "http://10.201.115.162/," then went back to "Burp Suite," and found an ususal URL after clicking on "Submit Support Ticket" within the
"http://10.201.115.162/" website in FireFox.

> <img width="640" height="349" alt="burp10" src="https://github.com/user-attachments/assets/c1e0f29a-5370-4184-9e42-97f34e497ec9" />

> After locating the unsual URL in "Burp Suite" i then copied and pasted the url into Mozilla FireFox and retrieved the flag "THM{NmNlZTliNGE1MWU1ZTQzMzgzNmFiNWVk}."

> <img width="1037" height="480" alt="burp11" src="https://github.com/user-attachments/assets/8bb10385-7aee-4a62-9233-ce5150a0d5d0" />
> <img width="549" height="225" alt="burp12" src="https://github.com/user-attachments/assets/6c6df17b-d7ed-4c55-958a-ff5dee1a0882" />

*** The Burp Suite Browser ***

> I then had to launch the "Burp Suite browser." To this i opened Burp Suite, clicked the "Proxy" tab, then clicked "Open browser." I then ran into an issue where i was given an error saying
"Your OS does not support Burp's browser running with its sandbox enabled."

> <img width="612" height="254" alt="burp13" src="https://github.com/user-attachments/assets/436b3b81-8dc5-42cb-b8e8-1e9b6e3f5ff4" />

> To fix this i clicked the settings tabs in the top right had corner, clicked on "Burp's browser," selected "Allow burp's browser to run without a sandbox," and closed the pop up.

> <img width="893" height="609" alt="burp14" src="https://github.com/user-attachments/assets/5f564e08-d17e-4ced-b4f8-ffd714c5dda8" />

> After configuring the settings i then launched the "Burp Suite Browser."

> <img width="985" height="797" alt="burp15" src="https://github.com/user-attachments/assets/50753954-3bfb-47bc-812e-68f34eb1704d" />

*** Example Attack ***

> I then had to carry about a real-world web app pen test using Burp Suite and Mozilla FireFox















---

## Reflection

> This lab provided me with knowledge and hands-on experience about 
