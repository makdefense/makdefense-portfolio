# [Networking]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Nmap: The Basics]  
**Date Completed**: [08/14/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding Nmap basics, as it is one of the most widely used tools for network reconnaissance and security auditing. Knowing its fundamentals
gives you a foundation for identifying vulnerabilities and understanding network structures. Next, I learned about the importance of understanding Host Discovery while using Nmap, which is the first
step in understanding what devices exist and respond on a network - before you waste time scanning ports or services. I then learned about the importance of understanding Port Scanning while using
Nmap is a tool that reveals the doors and entry points into a system or network, which is crucial for both defending and attacking in cybersecurity. Then I learned about the importance of understanding
Version Detection while using Nmap, which goes beyond just finding open ports - it tells you exactly what software and version is running on those ports, which is critical for assessing risk. Furthermore,
learning about the Timing while using Nmap is essential because it teaches you how to control the speed, stealth, and reliability of your scans - skills that are essential in both penetration testing and defensive
security work. Finally, I learned the importance of understanding Output while using Nmap, which is that scanning is only half the job - being able to read, save, and share the results is what makes the data
actionable.


---

## 🎯 Objectives
- [ ] Learn about Nmap basics
- [ ] Learn about Host Discovery
- [ ] Learn about Port Scanning
- [ ] Learn about Version Detection
- [ ] Learn about Timing
- [ ] Learn about Output
     
---

## 🧰 Tools Used
- THM AttackBox
- THM Linux
- THM FireFox
  
---

---

## 📊 Analysis & Screenshots

> I first read up on the "Nmap: The Basics - Introduction then after launching Attackbox, I was given a practical to figure out the last IP address that will be scanned when the scan target is
192.168.0.1/27. To do this, I input the command "nmap -sL 192.168.0.1/27," then pressed enter, which then displayed the last IP address to be "192.168.0.31"
> <img width="742" height="496" alt="nmap1" src="https://github.com/user-attachments/assets/e7cb2cd3-3392-4eff-a912-a97fd4781363" />

> I was given another practical to figure out how many TCP ports were open on the target system at "10.201.25.77." To do this, I input the command "nmap -sT 10.201.25.77," then pressed "enter."
This then displayed six open TCP ports.
> <img width="735" height="289" alt="nmap2" src="https://github.com/user-attachments/assets/553f5346-acbe-4b72-92f2-8e8f48f6df55" />

> Next, I then had to find a flag by finding the listening web server on IP address: 10.201.25.77 and accessing it with my browser. To do this, I launched Firefox within the THM AttackBox, then input
"http://10.201.25.77:8008," then pressed the "enter" button. This displayed the main page along with the flag "THM{SECRET_PAGE_38B9P6}."
> <img width="659" height="399" alt="nmap3" src="https://github.com/user-attachments/assets/a454c0c6-7a88-4a6d-8c0e-6d6fa51b74f7" />

> I then had to find the name and detected version of the web server running on "10.201.25.77." To do this, I input the command "nmap -sV 10.201.25.77," then pressed "enter." This displayed the detected
version name as "lighttpd 1.4.74."
> <img width="725" height="294" alt="nmap4" src="https://github.com/user-attachments/assets/438d20da-876a-4f2d-9fbb-ed8fff2f9034" />


---

## Reflection

> This lab provided me with knowledge about Nmap basics, Host Discovery, Port Scanning, Version Detection, Timing, and Output within the Nmap command.


