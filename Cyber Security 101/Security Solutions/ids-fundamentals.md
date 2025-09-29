# [Security Solutions]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [IDS Fundamentals]  
**Date Completed**: [09/28/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding the types of IDS and their detection capabilities, which is that it helps you pick the right tool, interpret alerts correctly, reduce false
positives, and design responses that actually stop intrusions. IDS knowledge is core for detection engineers, SOC analysts, and incident responders. Next, I learned the importance of working with Snort IDS, which teaches you packet-level detection, rule-writing, alert tuning, and real-world deployment skills that are core to network defense and SOC work. I then learned about the importance of
understanding default and custom rules in Snort IDS, which is that default rules give you broad, ready-made coverage for known threats. Custom rules let you adapt detection to your environment, reduce
noise, and catch threats the defaults miss. Knowing both is how you go from "losts of noisy alerts" to "meaningful, actionable detections." Finally, I learned about the importance of understanding how to
make a custom rule in Snort IDS, which is that custom Snort rules let you detect threats unique to your environment, cut noise, and turn raw network traffic into actionable alerts - skills that make you a
better defender and a more valuable SOC engineer.

---

## 🎯 Objectives
- [ ] Learn about Types of IDS and their detection capabilities
- [ ] Learn the Working of Snort IDS
- [ ] Learn about Default and custom rules in Snort IDS
- [ ] Learn how to Make a custom rule in Snort IDS

---

## 🧰 Tools Used
- THM AttackBox Linux
- THM Snort
  
---

## 📊 Analysis & Screenshots

*** Snort Usage ***

> After reading the sections within the IDS Fundamentals, I was given a practical to investigate a PCAP file using Snort due to an attack on their network. For the first question, I had to figure out the
IP Address of the machine that tried to connect to the subject machine using SSH. To do so, I first had to get into the directory that contained the PCAP file, so I input the command
"cd /etc/snort/," then pressed "enter," then "ls" to confirm that the "Intro_to_IDS.pcap" file was there, and it was. Next, I input the command syntax
"sudo snort -q -l /var/log/snort -r Intro_to_IDS.pcap -A console -c /etc/snort/snort.conf," then "enter" which gave me the IP address of "10.11.90.211".

> <img width="1199" height="230" alt="ids1" src="https://github.com/user-attachments/assets/875277ce-8309-4d5a-b384-5ca5bc4820a0" />

> For my next question, I had to determine the other rule message, besides the SSH message, detected within the PCAP file. To do so, I entered the command "ls" and then pressed "Enter" to locate the "local.rules" file.
After locating the file, I then entered the command "nano local.rules," then "enter" to retrieve the info that was used to create the file using nano. 

> <img width="598" height="287" alt="ids2" src="https://github.com/user-attachments/assets/59e1b9b5-0329-4c8b-9930-c32dd36e294a" />

> After opening it with nano, I saw the other rule message to be "Ping Detected," and at the same time, I also had to retrieve the SID of the rule that detects SSH. Further looking into the details within
nano, I found the SID to be "1000002."

> <img width="967" height="362" alt="ids3" src="https://github.com/user-attachments/assets/6a2b11f5-ebf5-4172-810b-429c841d9fb7" />

---

## Reflection

> This lab provided me with knowledge of the fundamentals of IDS, along with hands-on experience working with Snort.
