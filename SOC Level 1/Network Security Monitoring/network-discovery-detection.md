# [Network Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Network Discovery Detection]  
**Date Completed**: [01//2026]

---

## 🧠 Summary

> In this lab, I learned the importance 

---

## 🎯 Objectives
- [ ] What is network discovery
- [ ] Why attackers perform network discovery
- [ ] What are the different types of network discovery
- [ ] How network discovery techniques work, and how we can detect them

---

## 🧰 Tools Used
- THM 

---

## 📊 Analysis & Screenshots

*** External vs Internal Scanning ***

> For this room, I first answered a few questions within this section related to external and internal scanning. For the first question i had to figure out which file contains
logs that showcase internal scanning activity. To figure this out i launched the THM AttackBox, then launced the "Terminal" application, then inputted the command "ls" to list
all the directories on the system, then inputted "cd Downloads," then "ls" to list all the results within the "Downloads" directory. I then navigated to the "logs" directory by
inputting "cd logs," then inputted "head -n2 log-session-2.csv," then "enter." Which led me to discover internal scanning activity within this file.
>
> <img width="458" height="269" alt="1" src="https://github.com/user-attachments/assets/5f1808b2-1572-4ab3-8053-99d86023d419" />
> <img width="1455" height="532" alt="2" src="https://github.com/user-attachments/assets/b9acf65c-58d7-4345-bdeb-418c37fece20" />

> Moving onto the second question within this section. I had to figure out how many log entries are present for the internal IP performing internal scanning activity. To figure
this out i inputted the command synthax "cat log-session-2.csv | cut -d ',' -f3 | uniq -c," then "enter." Which led me to retrieve the total log entries to be "2276."
>
> <img width="897" height="106" alt="3" src="https://github.com/user-attachments/assets/9e1e79d8-1690-4446-a479-bd1c027bd659" />

> Moving onto the last question of this section. I had to figure out the external IP address that is performing external scanning activity. To figure this out I inputted the
command synthax "head -n2 log-session-1.csv," then "enter." Which led me to retrieve the external IP address of "203.0.113.25" performing external scanning activity because it was
scanning our destination IP "192.168..."
>
> <img width="1464" height="182" alt="4" src="https://github.com/user-attachments/assets/7603cdfe-ce63-45bc-90af-a2b1f606924b" />

*** Horizontal vs Vertical Scanning *** 

> Moving on to this section, i had to answer a few questions related to Horizontal and Vertical Scanning. For the first question i had to figure out the IP range scanned within
one of the log files containing evidence of a horizontal scan. To figure this out i had to see the same source IP address, a single destination port, but multiple destination IP
addresses across multiple events. I then inputted the command "cut -d’,’ -f3,4,5,6 log-session-2.csv > csv2.txt," then "enter," then "cat csv2.txt," then "enter," then scrolled
all the way down to the end of the results and saw evidence of possible horizontal scanning with the IP range scanned to be "203.0.113.0/24."
>
> <img width="646" height="645" alt="5" src="https://github.com/user-attachments/assets/5dce50d8-a23a-4276-9f05-e8a0455d1b35" />

> Moving onto the second question within this section. I had to figure out the IP address on which a vertical scan was performed within the same "log-session-2.csv" log file.
To figure this out, i simply scrolled up to find the IP which was "192.168.230.145."
>
> <img width="652" height="563" alt="6" src="https://github.com/user-attachments/assets/f4c09d18-bbcc-4c6d-ba10-f0da5da6af3e" />

> For the last question of this section i had to figure out the ports that were scanned to host common services on one of the IP addresses. To figure this out i navigated to the
head of the output log file, and saw the various ports to be "80, 445, 3389."
>
> <img width="966" height="266" alt="7" src="https://github.com/user-attachments/assets/04e86b51-db34-46e9-b1b6-83b6a791e42f" />

*** The Mechanics of Scanning *** 

> Moving onto this section, i had to answer a few questions related to the different mechanics of scanning. For the first question i had to figure out which source IP performs
a ping sweep attack across a whole subnet. To figure this out,








---

## Reflection

> This lab 
