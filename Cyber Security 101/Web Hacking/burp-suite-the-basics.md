# [Web Hacking]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Burp Suite: The Basics]  
**Date Completed**: [09/15/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding the various tools within the Burp Suite framework, which gives you a complete toolkit for exploring, attacking, and defending web
applications. Each tool builds different skills (manual testing, automation, analysis), and mastering them prepares you for both real-world security work and certifications. I then learned about the
importance of understanding how to navigate and configure Burp Suite, which is it ensures you capture all relevant traffic, avoid errors, customize testing to your goals, and work efficiently. It's the
foundation that makes all Burp Suite's other tools truly useful.

---

## 🎯 Objectives
- [ ] Learn about the various tools within the Burp Suite framework
- [ ] Learn how to navigate and configure Burp Suite
   
---

## 🧰 Tools Used
- THM Machine
- THM Burp Suite
- THM Mozilla FireFox

---

## 📊 Analysis & Screenshots

*** Options ***

> After launching the THM Machine, then launching the Burp Suite application, I then read about configuring Burp Suite settings, and then had a few questions to answer after familiarizing myself with the
settings.

> <img width="895" height="517" alt="burp1" src="https://github.com/user-attachments/assets/6351c24b-9613-4305-9695-1b5da5ac3e18" />

> I had to first figure out in which category within the setting I could find a reference to "cookie jar." To do this, I clicked on the "settings" tab.

> <img width="179" height="50" alt="burp2" src="https://github.com/user-attachments/assets/e97f8ef1-4080-4a3b-8115-26a88802c8c6" />

> Then searched for "cookie jar" within the search bar and saw it under the category of "sessions."

> <img width="517" height="340" alt="burp3" src="https://github.com/user-attachments/assets/af6a1b0d-e2b0-4b79-b88e-5e1315b54c07" />

> I then had to determine which category contained the "updates" sub-category that controls the Burp Suite update behavior. To do this, I searched "updates" and saw it under the sub-
category of "Suite."

> <img width="684" height="294" alt="burp4" src="https://github.com/user-attachments/assets/1fb85fee-6ad0-4d2e-9a54-9620612bef9a" />

*** Connecting Through the Proxy (FoxyProxy) ***

> Next, I had to use the Burp Suite Proxy. To do this, I had to configure my local web browser to redirect traffic through Burp Suite. I had to launch the Mozilla Firefox browser, then click the FoxyProxy
icon in the top right.

> <img width="366" height="410" alt="burp5" src="https://github.com/user-attachments/assets/c35a5d5d-9461-4687-925b-2a2a0511a08a" />

> Since the "Burp" proxy was already created within the FoxyProxy system and all of the options were added, I moved on to the next step.

> <img width="1375" height="585" alt="burp6" src="https://github.com/user-attachments/assets/884f2185-65be-49d9-aa9d-3267c071bbc6" />

> I then opened "Burp Suite" to ensure interception was turned on, which it was.

> <img width="1305" height="481" alt="burp7" src="https://github.com/user-attachments/assets/8344440b-de5b-47c1-aa6d-3c4d0b4d93ab" />

> So I went back to my Mozilla Firefox browser to test the proxy. I entered the website "http://10.201.115.162/" and then returned to "Burp Suite," where I saw that I had just intercepted my first request.

> <img width="1270" height="636" alt="burp8" src="https://github.com/user-attachments/assets/92eab525-2c58-4a59-83a6-3665cc9c4c71" />

*** Site Map and Issue Definitions ***

> I was then given a practical to find a flag within "Burp Suite" after looking around the site "http://10.201.115.162/." So first, I opened "Burp Suite," clicked on the "Scope" tab, and input the site
Entered "http://10.201.115.162/" within the "Prefix" text field and then pressed "ok."

> <img width="950" height="608" alt="burp9" src="https://github.com/user-attachments/assets/90484312-067a-48eb-b97b-f223d492d48e" />

> I then went to Mozilla Firefox and looked around the site "http://10.201.115.162/," then went back to "Burp Suite," and found an unusual URL after clicking on "Submit Support Ticket" within the
"http://10.201.115.162/" website in Firefox.

> <img width="640" height="349" alt="burp10" src="https://github.com/user-attachments/assets/c1e0f29a-5370-4184-9e42-97f34e497ec9" />

> After locating the unusual URL in "Burp Suite," I then copied and pasted the URL into Mozilla Firefox and retrieved the flag "THM{NmNlZTliNGE1MWU1ZTQzMzgzNmFiNWVk}."

> <img width="1037" height="480" alt="burp11" src="https://github.com/user-attachments/assets/8bb10385-7aee-4a62-9233-ce5150a0d5d0" />
> <img width="549" height="225" alt="burp12" src="https://github.com/user-attachments/assets/6c6df17b-d7ed-4c55-958a-ff5dee1a0882" />

*** The Burp Suite Browser ***

> I then had to launch the "Burp Suite browser." To do this, I opened Burp Suite, clicked the "Proxy" tab, then clicked "Open browser." I then ran into an issue where I was given an error saying
"Your OS does not support Burp's browser running with its sandbox enabled."

> <img width="612" height="254" alt="burp13" src="https://github.com/user-attachments/assets/436b3b81-8dc5-42cb-b8e8-1e9b6e3f5ff4" />

> To fix this, I clicked the settings tab in the top right-hand corner, clicked on "Burp's browser," selected "Allow Burp's browser to run without a sandbox," and closed the pop-up.

> <img width="893" height="609" alt="burp14" src="https://github.com/user-attachments/assets/5f564e08-d17e-4ced-b4f8-ffd714c5dda8" />

> After configuring the settings, I then launched the "Burp Suite Browser."

> <img width="985" height="797" alt="burp15" src="https://github.com/user-attachments/assets/50753954-3bfb-47bc-812e-68f34eb1704d" />

*** Example Attack ***

> I then had to conduct a real-world web app penetration test using Burp Suite and Mozilla Firefox. To do this, I first turned off interception within Burp Suite, went to Mozilla Firefox, searched the
website "http://10.201.101.208/ticket/," landed on the "Support" page, inputted "pentester@thm.com," "Test Attack" for the message, and clicked "Submit Query."

> <img width="982" height="623" alt="burp16" src="https://github.com/user-attachments/assets/baf6a84b-fb4f-435f-aee9-0e5117a6f04f" />
> <img width="942" height="437" alt="burp17" src="https://github.com/user-attachments/assets/1582088f-eb20-4519-9171-b32c3d613bed" />

> I then went back to "Burp Suite," turned on Interception, went to the "Raw" tab, went to the "email" line of code, and changed the code from "pentester@thm.com" to
"<script>alert("Succ3ssful XSS")</script>"

> <img width="1108" height="402" alt="burp18" src="https://github.com/user-attachments/assets/595afb4a-890c-4912-a64f-bef848d50cf8" />
> <img width="1149" height="970" alt="burp19" src="https://github.com/user-attachments/assets/d49599af-e65b-4d6c-bc7a-3b9f493b27b2" />

> I then clicked forward to send the update to Mozilla Firefox, turned off interception, and got the pop-up of "Succ3ssful XSS" meaning I successfully carried out a successful cross-site scripting
attack.

> <img width="541" height="184" alt="burp20" src="https://github.com/user-attachments/assets/ee871bb8-bd72-4c55-b2af-4d8997c01c7d" />
> <img width="1676" height="455" alt="burp21" src="https://github.com/user-attachments/assets/3ff9ea91-7876-414e-9fe0-06c28aa3a973" />
---

## Reflection

> This lab provided me with knowledge and hands-on experience with Burp Suite for web application pentesting.

