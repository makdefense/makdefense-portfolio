# [Security Solutions]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Introduction to SIEM]  
**Date Completed**: [09/28/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding what SIEM is, how it works, and that it is the backbone of modern detection and response. Knowing it gives you centralized visibility
across systems, speeds up threat detection and investigations, helps meet compliance/retention rules, and makes you valuable in any SOC or security operations role. Next, I learned the importance of
understanding why SIEM is needed, which is because modern IT environments produce too many, too different logs for a human to monitor. SIEM centralizes those logs, normalizes and enriches them, and
correlates events so you can find real threats, build accurate timelines, meet compliance, and respond faster. Without SIEM, you'd be hunting across dozens of consoles, missing multi-step attacks, and
drowning in false positives. I then learned about the importance of understanding network visibility, which is the ability to see and understand the traffic, flows, devices, and connections
moving across your network. It is critical because it enables you to spot, prove, and stop problems and attacks that you can't see from a single host. Following, I learned the importance of understanding
what log sources are, and how log ingestion is done, which is that logs are the raw evidence for detection, investigation, troubleshooting, and compliance. Ingestion is what turns raw logs into
searchable, timely data you can actually use. Finally, I learned about the importance of understanding what the capabilities a SIEM provides, which is that if you know the features, you can design
detections, tune alerts, run faster investigations, prove compliance, and automate responses - instead of just clicking around a console.

---

## 🎯 Objectives
- [ ] Learn about What is SIEM, and how does it work?
- [ ] Learn Why is SIEM needed?
- [ ] Learn about What is Network Visibility?
- [ ] Learn about What are Log Sources, and how is log ingestion done?
- [ ] Learn about What are the capabilities a SIEM provides?

---

## 🧰 Tools Used
- THM Static Site
  
---

## 📊 Analysis & Screenshots

*** Lab Work ***

> After reading the sections in Introduction to SIEM, I was given a Lab at the end, which required analyzing suspicious activity within a sample dashboard. First, I had to launch the Static Site within
THM, which then brought me to the dashboard, where I was prompted with a pop-up called "Instructions."

> <img width="565" height="236" alt="siem1" src="https://github.com/user-attachments/assets/20a68f54-bf34-4e2a-ac81-58bc7a6895db" />

> After clicking the "Start Activity" button, I was prompted with another pop-up that included a button labeled "Start Suspicious Activity."

> <img width="403" height="209" alt="siem2" src="https://github.com/user-attachments/assets/f751c70a-8823-41a7-bcb7-edd70775bce5" />

> After clicking the "Start Suspicious Activity" button, I figured out the cause of the alert, which was "cudominer.exe."

> <img width="338" height="124" alt="siem3" src="https://github.com/user-attachments/assets/a16f0a1d-b66d-42e2-b2e8-bdac1ce6993a" />

> I then had to find the event that caused the alert, after being shown a pop-up with a button titled "Find Event." I clicked it and was shown several events.

> <img width="565" height="245" alt="siem4" src="https://github.com/user-attachments/assets/d7c7ee95-61d9-49bc-a767-4f9c3c0d4c2e" />

> After clicking through all the events, I found the name of the user that was responsible for the event that caused the alert, which was "chris.fort," and the hostname of the suspect user was "HR_02."

> <img width="345" height="184" alt="siem5" src="https://github.com/user-attachments/assets/c4b73f2d-f615-4e80-8c50-f57399486140" />

> I then had to examine the rule and the suspicious process to pinpoint the term that matched the rule that caused the alert. After clicking the "Proceed" button on the pop-up, the term that matched the
rule was "miner."

> <img width="728" height="362" alt="siem6" src="https://github.com/user-attachments/assets/f63e4cb1-7928-4a7a-a0a9-abeadceb9840" />
> <img width="682" height="338" alt="siem7" src="https://github.com/user-attachments/assets/14d1ea90-1555-48b2-9d2b-3880ddb81c5b" />

> I then had to retrieve a flag by selecting the right action for the event. After selecting "True-positive and isolate the host," I retrieved the flag "THM{000_SIEM_INTRO}."

> <img width="792" height="338" alt="siem8" src="https://github.com/user-attachments/assets/08032af8-aadd-468b-935d-1d8019695bf6" />

---

## Reflection

> This lab provided me with knowledge about Security Information and Event Management.
