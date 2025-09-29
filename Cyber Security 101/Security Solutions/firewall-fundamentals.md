# [Security Solutions]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Firewall Fundamentals]  
**Date Completed**: [09/28/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding the types of firewalls, which is that it is the first line that shapes what traffic is allowed, where threats are stopped, and how you design
network security - knowing the difference helps you pick, configure, and defend systems correctly. Next, I learned about the importance of understanding the firewall rules and their components, which is
that firewall rules control who talks to what, how, and when. Knowing them prevents breaches, reduces attack surface, speeds troubleshooting, and ensures your network and apps stay reachable only in the
ways you intend. For SOC/ops roles, it's core daily knowledge.

---

## 🎯 Objectives
- [ ] Learn about The types of firewalls
- [ ] Learn about The firewall rules and its components

---

## 🧰 Tools Used
- THM Windows
- THM AttackBox
- THM Linux Terminal
  
---

## 📊 Analysis & Screenshots

*** Windows Defender Firewall ***

> After reading the sections in Firewall Fundamentals, I was given a lab at the end to examine some rules created by a security team for a critical Windows system. For the first question, I had to figure
out the name of the rule that was created to block all incoming traffic on the SSH port. To do so, I first had to open the Windows system, then go to the search bar and search for
"Windows Defender Firewall."

> <img width="540" height="343" alt="wfw1" src="https://github.com/user-attachments/assets/ed37e0a4-0d71-4caa-af30-ab1627aa0cb6" />

> After opening the application, I had to go to the left column and select "Inbound Rules."

> <img width="200" height="151" alt="wfw2" src="https://github.com/user-attachments/assets/c8a228e3-072b-43db-a6e2-cf82d829ea9b" />

> After selecting "Inbound Rules," I saw the name of the rule created by the team, which was titled "Core Op."

> <img width="434" height="525" alt="wfw3" src="https://github.com/user-attachments/assets/865d1c5a-b41d-4abd-b8aa-89cf97e504e7" />

> I then had to determine the name of the rule that was created to allow SSH from a single IP address. To do so, I just scrolled through the "Inbound Rules" and saw the name of the rule created
by the security team to be "Infra Team."

> <img width="422" height="445" alt="wfw4" src="https://github.com/user-attachments/assets/649252f0-c562-4a38-94bd-b42db0e4b5cb" />

> I then had to figure out the IP address that was allowed under the "Infra Team" rule. To figure this out, I just selected the "Infra Team" rule, then went to the right column and selected "Properties,"
and saw that the IP address allowed under the rule was "192.168.13.7".

> <img width="437" height="547" alt="wfw5" src="https://github.com/user-attachments/assets/09e0cd2b-25bd-43eb-9955-ba15541c8280" />

*** Linux iptables Firewall ***

> For this practical, I had to use Linux Terminal within the THM Attackbox to issue a rule with "ufw" that would deny all outgoing traffic from the machine as a default policy. To do so, I first
launched the Linux Terminal, then input the command "sudo ufw status" to check the status of the "ufw," and I saw that it was "inactive."
> So, to enable it, I input the command "sudo ufw enable," then pressed "Enter" to activate the Firewall.
> To finally deny all outgoing traffic, I input the command "sudo ufw default deny outgoing," then "enter."

>  <img width="664" height="223" alt="wfw6" src="https://github.com/user-attachments/assets/f152c37f-4487-42e0-9c83-cc798a3f2c5b" />

---

## Reflection

> This lab provided me with knowledge about firewalls and hands-on expertise with the built-in firewalls of Windows and Linux.
