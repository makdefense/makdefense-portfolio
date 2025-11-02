# [Cyber Threat Intelligence]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Trooper]  
**Date Completed**: [11/2/2025]

---

## 🧠 Summary

> In this lab, I learned how to identify the tactics, techniques, and procedures used by a threat group based on a given report.

---

## 🎯 Objectives
- [ ] Complete "Trooper"

---

## 🧰 Tools Used
- THM ATT&CK Navigator
- THM OpenCTI
- THM Mozilla FireFox
- THM AttackBox
- Google Chrome
  
---

## 📊 Analysis & Screenshots

*** Who's The Threat? ***

> For this room, I had to play the role of a CTI analyst again, then identify the Tactics, Techniques, and Procedures (TTP) being used by threat group "APT X," while also gathering information about
their identity and motive. I first read the report on "APT X," then I was given my first question: to figure out what kind of phishing campaign "APT X" uses as part of its TTPs. To
figure this out, I went back to the given report and discovered the phishing campaign to be "spear-phishing emails."

> <img width="887" height="314" alt="trp1" src="https://github.com/user-attachments/assets/6a7573bc-6ff6-4447-aae6-01db7d81d904" />

> Moving on to the second question, I had to identify the malware used by "APT X." To do so, I returned to the provided report and found it was "USBferry."

> <img width="452" height="231" alt="trp2" src="https://github.com/user-attachments/assets/ba7b0623-d741-475a-a14f-b4f9cba57efb" />

> Moving on to the third question, I had to figure out the STIX ID for the malware "USBFerry." To figure this out, I launched OpenCTI using the website "http://MACHINE_IP:8080," logged in using the given
THM credentials, navigated to the search bar, and typed "USBFerry," then clicked the "Enter" button.

> <img width="664" height="151" alt="trp3" src="https://github.com/user-attachments/assets/c8982293-8e5b-4414-b05a-e585062c5ee9" />

> After clicking "Enter," I navigated down, selected the entity "USBFerry," and retrieved the STIX ID of "malware--5d0ea014-1ce9-5d5c-bcc7-f625a07907d0."

> <img width="736" height="504" alt="trp4" src="https://github.com/user-attachments/assets/b399950a-9915-44e1-87d8-8707a605676e" />
> <img width="774" height="259" alt="trp5" src="https://github.com/user-attachments/assets/1a1fbbc2-6e1f-4187-b3c3-ce56fcfccf6f" />

> Moving on to the fourth question, I had to figure out which technique "APT X" used for initial access. To figure this out, I navigated to the top of the OpenCTI application, selected the
"Knowledge" tab, scrolled down, and discovered that under "Initial Access," the technique was "Replication through removable media."

> <img width="534" height="64" alt="trp6" src="https://github.com/user-attachments/assets/21ab11e3-6dfe-4c37-832d-5a2a209d5bd2" />
> <img width="953" height="144" alt="trp7" src="https://github.com/user-attachments/assets/59e7c27b-2468-4f4a-9990-b31146d43ebf" />

> Moving on to the fifth question, I had to unravel the identity of "APT X." To figure this out, I went back to the given report, clicked the "APT X" link that was highlighted in blue, and landed on
the "APT X" of "Tropic Trooper."

> <img width="450" height="158" alt="trp8" src="https://github.com/user-attachments/assets/78df3ff1-4d6e-4c85-8ceb-f1dd5ffc6d5f" />
> <img width="536" height="318" alt="trp9" src="https://github.com/user-attachments/assets/44a9e279-43e1-4c7e-b7ef-828d8ac55105" />

> Moving on to the sixth question, I then had to figure out how many Attack Pattern Techniques were associated with APT "Tropic Trooper." To figure this out, I navigated back to the OpenCTI on Mozilla
Firefox, typed "Tropic Trooper" within the search bar, clicked the "Enter" button, selected the "Tropic Trooper" entity, navigated to the top of the application, selected "Knowledge," and discovered that
there were 39 Attack Pattern Techniques.

> <img width="669" height="152" alt="trp10" src="https://github.com/user-attachments/assets/4ef5daaa-9b6e-492f-b686-6bc41839efb1" />
> <img width="960" height="298" alt="trp11" src="https://github.com/user-attachments/assets/74ab88da-6f12-433b-8d79-cf7c234c0375" />
> <img width="549" height="68" alt="trp12" src="https://github.com/user-attachments/assets/363a0b39-18c5-4e91-9f0d-44e29360e95c" />
> <img width="872" height="465" alt="trp13" src="https://github.com/user-attachments/assets/5b435785-35f2-47ee-aa4e-aa5a8e62278d" />

> For the seventh question, I had to identify the tool linked to the APT "Tropic Trooper." To figure this out, I navigated to the left of the OpenCTI application, selected "Tools" under the "Arsenal"
section, and discovered that the linked tool's name was "BITSAdmin."

> <img width="220" height="224" alt="trp14" src="https://github.com/user-attachments/assets/edcedaa3-2519-461d-b4f1-601b1ca21cd0" />
> <img width="395" height="255" alt="trp15" src="https://github.com/user-attachments/assets/0c3c6a0e-d2b5-4c88-be86-dd79dffe6f3d" />

> For question 8, I had to determine the sub-technique used by the APT under the primary technique, Valid Accounts. To figure this out, I loaded up the MITRE ATT&CK Navigator using the link
"http://MACHINE_IP:4200," navigated to "Valid Accounts," clicked the tab, and retrieved the sub-technique "Local Accounts."

> <img width="305" height="163" alt="trp16" src="https://github.com/user-attachments/assets/d4bbad1a-d91e-43de-88e9-03db3714d3a2" />
> <img width="224" height="141" alt="trp17" src="https://github.com/user-attachments/assets/3bdb73ab-ad2f-4c10-8877-6eace0cd98d4" />
> <img width="289" height="174" alt="trp18" src="https://github.com/user-attachments/assets/8cc2a880-90ae-4796-9d2d-91cab9c30799" />

> Moving on to the second-to-last question, I had to figure out which Tactics the sub-technique "Local Accounts" falls under. To figure this out, I navigated to Google Chrome on my system, typed in
"MITRE ATT&CK" into the search bar, clicked on the "MITRE ATT&CK" link, navigated down to "Local Account," which was under "Initial Access," clicked on it, and discovered that the Tactics were
"Initial Access, Persistence,  Defense Evasion, and Privilege Escalation."

> <img width="451" height="285" alt="trp19" src="https://github.com/user-attachments/assets/60dc1efd-bd6c-40ad-bc14-271bf5474951" />
> <img width="255" height="620" alt="trp20" src="https://github.com/user-attachments/assets/1ea25c9b-8b4c-4e18-8a8e-ca69cda882fb" />
> <img width="515" height="376" alt="trp21" src="https://github.com/user-attachments/assets/7b695285-c695-4193-bf9e-9ebb320b1284" />

> Finally, for the last question, I had to figure out which technique "Tropic Trooper" is known for using under the tactic "Collection." To figure this out, I navigated back to the MITRE ATT&CK
navigator website on the THM Mozilla Firefox, navigated to "Collection," and discovered that the technique "Automated Collection" was highlighted.

> <img width="133" height="239" alt="trp22" src="https://github.com/user-attachments/assets/b0145c74-cdab-4cee-bf39-ceddb6ecbc8c" />

---

## Reflection

> This lab provided me with knowledge of using cyber threat intelligence to identify a threat based on a given report.

