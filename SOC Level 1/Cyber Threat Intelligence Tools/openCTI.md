# [Cyber Threat Intelligence]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [OpenCTI]  
**Date Completed**: [10/23/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding 

---

## 🎯 Objectives
- [ ] Learn about OpenCTI and how is it used
- [ ] Learn how to navigate through the platform
- [ ] Learn about what functionalities will be important during a security threat analysis

---

## 🧰 Tools Used
- THM AttackBox
- THM OpenCTI
  
---

## 📊 Analysis & Screenshots

*** OpenCTI Dashboard 1 ***

> After reading through the section "OpenCTI Dashboard 1" i was tasked with a minipractical to do. For the first question i had to figure out the group that uses the 4H RAT malware. To figure this out
i had to first launch Mozilla FireFox within the THM AttackBox and navigated to the website "http://10.201.99.184:8080/" which launched the login screen for OpenCTI.

> <img width="735" height="728" alt="opencti" src="https://github.com/user-attachments/assets/e215285b-cd72-43cf-8046-5532c15dc6f6" />

> After using the login credentials "info@tryhack.io" and "TryHackMe1234" to login to the dashboard, i then navigated to the left an clicked "Arsenal," then saw that the group "Putter Panda" uses the
"4H RAT" malware.

> <img width="199" height="212" alt="cti2" src="https://github.com/user-attachments/assets/1c8bab84-b3fb-42b4-906f-b2b93644d62a" />
> <img width="488" height="245" alt="cti3" src="https://github.com/user-attachments/assets/e4df6d06-1b0c-476a-98a1-ea807173042c" />

> Moving onto the next qeustion i had to figure out what kill-chain phase is linked with the "Command-Line Interface" Attack Pattern. To figure this out i simply navigated to the top of the application,
selected "attack patterns, searched "command-line," and saw that the kill-chain phase "execution-ics" popped up.

> <img width="357" height="158" alt="cti4" src="https://github.com/user-attachments/assets/c64da994-8d07-4c75-b8a8-e9deacf52b24" />
> <img width="533" height="130" alt="cti5" src="https://github.com/user-attachments/assets/0edc1f5a-50e8-49ee-90c1-b96df3eb02f3" />
> <img width="501" height="236" alt="cti6" src="https://github.com/user-attachments/assets/1cd614ce-9f55-438c-b908-1dfab69df553" />

> For the last question i had to figure out i had to figure out which tab would house the indicators. To figure this out i simply just navigated around the application and saw that the tab
"Observations" within the "Activities" category housed the "Indicators."

> <img width="878" height="229" alt="cti7" src="https://github.com/user-attachments/assets/fa71fa20-fd73-4aba-a97e-3c06b3058751" />

*** OpenCTI Dashboard 2 ***

> Moving onto the next mini practical for the first question i had to figure out which intrusion sets are associated with the Cobalt Strike malware with a Good confidence level. To figure this out i first
navigated to the "Arsenal" tab, searched "Cobalt Strike," and selected it.
>
> <img width="220" height="215" alt="cti8" src="https://github.com/user-attachments/assets/1b5f4c36-03bb-40dc-bfa1-0fdd4c273610" />
> <img width="481" height="347" alt="cti9" src="https://github.com/user-attachments/assets/da8e5949-6a95-49d7-8aa3-0b3054847f04" />

> I then scrolled down to the "Last Used Relationships," selected the first Intrusion Set labelled "Good" which was "FIN7."
>
> <img width="942" height="225" alt="cti10" src="https://github.com/user-attachments/assets/760b3a58-b14e-4922-8e45-26adf4d81660" />

> Next i navigated to the right and selected "Intrusion Sets," and saw the two intrusion sets "CopyKittens" and "FIN7" labelled "Good."
>
> <img width="233" height="416" alt="cti11" src="https://github.com/user-attachments/assets/aed234d8-b030-4797-8506-443103a4eb4e" />
> <img width="1514" height="800" alt="cti12" src="https://github.com/user-attachments/assets/271e0d30-ff60-48f2-8e9b-5e82e7fd9a15" />

*** Investigative Scenario ***

> For this practical i had to play the role of a SOC analyst and look into both "CaddyWiper" malware and "APT37" group with OpenCTI and answer questions. For the first question i had to figure out the
earliest date recorded related to CaddyWiper. To figure this out i navigated to the left of the dashboard, selected "Arsenal," searched for "CaddyWiper," and selected it.
>
> <img width="200" height="219" alt="cti13" src="https://github.com/user-attachments/assets/f4dd46a2-85e3-42a4-8396-52d0b9af806f" />
> <img width="601" height="320" alt="cti14" src="https://github.com/user-attachments/assets/2f955222-07ec-4f8b-a3ba-20959b0323ca" />

> I then scrolled down to "LATEST REPORTS ABOUT THIS ACTIVITY," selected "Ciso CaddyWiper," and saw that the earliest datw was 2022/03/15
>
> <img width="963" height="503" alt="cti15" src="https://github.com/user-attachments/assets/7405ee8c-ff70-47ec-81a4-b1c3f7d0003a" />

> For the next question i had to figure out the Attack Technique used by the "CaddyWiper" malware for execution. To figure this out i navigated to the top of the dashboard, selected "Knowledge," then
scrolled all the way down to the first Attack Technique and saw that it was "Native API."
>
>  <img width="713" height="188" alt="cti16" src="https://github.com/user-attachments/assets/075daa0c-5e5f-4e19-979a-50a47e41ab5c" />
> <img width="1003" height="275" alt="cti17" src="https://github.com/user-attachments/assets/66593ebf-fd16-4e70-ba9e-0d5edb0a4402" />

> Next question i had to fiugre out how many malware relations were linked to this Attack Technique. To figure this out i selected "Native API," navigated to the top of the dashboard, selected "knowledge,"
and saw under "DISTRIBUTION OF RELATIONS" the total number of malware relations were 113.
>
> <img width="1434" height="531" alt="cti18" src="https://github.com/user-attachments/assets/22a0e9f0-8412-4919-9628-b091e9d49a6d" />

> For the next question i had to figure out the three tools that were used by the Attack Technique "Native Api" in 2016. To figure this out i navigated to the right of the dashboard, selected "Tools,"
then selected "Knowledge," and this retrieved the three tools "BloodHound, Empire, ShimRatReporter."
>
> <img width="276" height="365" alt="cti19" src="https://github.com/user-attachments/assets/17492e55-f54e-4bcc-a93d-c2bd4bcb39b5" />
> <img width="1669" height="560" alt="cti20" src="https://github.com/user-attachments/assets/4006abf3-48ad-4e16-a7cb-72ed72c7514d" />

> For the next question i had to figure out which country APT37 was associated with. To figure this out i simply navigated to the left side of the dashboard, selected "Arsenal," searched "APT37," selected
the malware "BLUELIGHT," navigated to the right and selected "APT37," and saw that it was associated with North Korea.
>
> <img width="186" height="499" alt="cti21" src="https://github.com/user-attachments/assets/e5f5c15f-2012-4494-a50a-3a74638400a0" />
> <img width="587" height="281" alt="cti22" src="https://github.com/user-attachments/assets/bf2cfc78-a449-45a0-9b5c-0ac5bb0ca2de" />
> <img width="737" height="282" alt="cti23" src="https://github.com/user-attachments/assets/90d096a5-3ca9-4372-a955-b5526921b405" />
> <img width="849" height="396" alt="cti24" src="https://github.com/user-attachments/assets/ca6e8253-d6e9-49f9-a9d9-2ac40b656eaf" />

> For the final question i had to figure out which Attack Techniques are used by Native API for initial access. To figure this out i navigated to the top of the dashboard, selected "Knowledge" tab,
scrolled down to where it said "initial-access," and saw the two techniques to be "T1189" and "T1566."
>
> <img width="751" height="263" alt="cti25" src="https://github.com/user-attachments/assets/f1be6ab7-8a02-4edc-a7f0-23ccf2c24a33" />
> <img width="1630" height="254" alt="cti26" src="https://github.com/user-attachments/assets/8cf898ee-e329-484a-8597-ec7b9a28fe8f" />

---

## Reflection

> This lab provided me with knowledge about YARA and its application for threat intelligence, forensics, and threat hunting.
