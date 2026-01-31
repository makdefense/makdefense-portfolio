# [Network Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Network Discovery Detection]  
**Date Completed**: [01/31/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding how attackers discover assets and how to detect that activity. This is critical because asset discovery is the first step
in nearly every cyberattack. During this phase, attackers scan networks, enumerate services, query directories, and probe cloud resources to map what exists and what is exposed.
This activity is often noisy and easier to detect than later stages such as exploitation or data theft.
Detecting asset discovery early gives defenders a strategic advantage, allowing them to contain threats, harden systems, and stop attacks before real damage occurs. Studying
attacker discovery methods also helps defenders identify unknown or misconfigured assets within their own environment, reducing the attack surface and improving overall
visibility. For SOC analysts and blue teams, detecting discovery activity is a core skill that enables early warning, more effective incident response, and stronger security
posture overall.

---

## 🎯 Objectives
- [ ] What is network discovery
- [ ] Why attackers perform network discovery
- [ ] What are the different types of network discovery
- [ ] How network discovery techniques work, and how we can detect them

---

## 🧰 Tools Used
- THM Elastic
- THM AttackBox
- THM Terminal

---

## 📊 Analysis & Screenshots

*** External vs Internal Scanning ***

> For this room, I first answered several questions related to external and internal scanning. For the first question, I needed to determine which file contained logs that
showcased internal scanning activity. To do this, I launched the TryHackMe AttackBox and opened the Terminal application. I then entered the ls command to list all directories on
the system, followed by cd Downloads and ls to view the contents of the Downloads directory.
Next, I navigated to the logs directory by entering cd logs. Once inside the directory, I ran the command head -n 2 log-session-2.csv and pressed Enter. This allowed me to view 
the first two lines of the log file, which revealed evidence of internal scanning activity within this file.

> <img width="458" height="269" alt="1" src="https://github.com/user-attachments/assets/5f1808b2-1572-4ab3-8053-99d86023d419" />
> <img width="1455" height="532" alt="2" src="https://github.com/user-attachments/assets/b9acf65c-58d7-4345-bdeb-418c37fece20" />

> Moving on to the second question in this section, I needed to determine how many log entries were associated with the internal IP performing internal scanning activity. To do
this, I entered the command syntax cat log-session-2.csv | cut -d ',' -f3 | uniq -c and pressed Enter. This allowed me to retrieve the total number of log entries, which was
2,276.

> <img width="897" height="106" alt="3" src="https://github.com/user-attachments/assets/9e1e79d8-1690-4446-a479-bd1c027bd659" />

> Moving on to the final question in this section, I needed to identify the external IP address performing external scanning activity. To determine this, I entered the command
syntax head -n 2 log-session-1.csv and pressed Enter. This allowed me to view the first two entries in the log file and identify the external IP address 203.0.113.25 as the
source of the external scanning activity, as it was scanning the destination IP address 192.168.x.x.

> <img width="1464" height="182" alt="4" src="https://github.com/user-attachments/assets/7603cdfe-ce63-45bc-90af-a2b1f606924b" />

*** Horizontal vs Vertical Scanning *** 

> Moving on to this section, I answered several questions related to horizontal and vertical scanning. For the first question, I needed to identify the IP range that was scanned
within one of the log files containing evidence of a horizontal scan. To determine this, I looked for the same source IP address targeting a single destination port across
multiple destination IP addresses in multiple events.
To analyze the logs, I entered the command cut -d ',' -f3,4,5,6 log-session-2.csv > csv2.txt and pressed Enter. I then ran cat csv2.txt and pressed Enter to view the extracted
fields. After scrolling to the end of the output, I observed evidence of possible horizontal scanning, with the scanned IP range identified as 203.0.113.0/24.

> <img width="646" height="645" alt="5" src="https://github.com/user-attachments/assets/5dce50d8-a23a-4276-9f05-e8a0455d1b35" />

> Moving on to the second question in this section, I needed to identify the IP address on which a vertical scan was performed within the same log-session-2.csv log file. To
determine this, I reviewed the log entries and identified the destination IP address 192.168.230.145, which showed evidence of vertical scanning activity.

> <img width="652" height="563" alt="6" src="https://github.com/user-attachments/assets/f4c09d18-bbcc-4c6d-ba10-f0da5da6af3e" />

> For the final question in this section, I needed to identify the ports that were scanned to identify common services on one of the IP addresses. To determine this, I reviewed
the beginning of the log file output and observed that the scanned ports were 80, 445, and 3389, which correspond to common services.

> <img width="966" height="266" alt="7" src="https://github.com/user-attachments/assets/04e86b51-db34-46e9-b1b6-83b6a791e42f" />

*** The Mechanics of Scanning *** 

> Moving on to this section, I answered several questions related to different scanning mechanics. For the first question, I needed to identify which source IP address performed
a ping sweep attack across an entire subnet. To determine this, I first navigated to the Elastic web application using the URL http://10.80.182.5:5601 and signed in with the
credentials elastic / changeme.
After logging in, I opened the left-hand menu, selected Discover, and chose All logs. I then adjusted the time filter to Search entire time range. Next, from the filter options,
I selected network.protocol and source.ip, and entered icmp into the search field before pressing Enter. This filtering allowed me to identify ICMP-based scanning activity, which
revealed the source IP address 192.168.230.127 as the system performing the ping sweep.

> <img width="647" height="251" alt="8" src="https://github.com/user-attachments/assets/042317a3-6bdf-452a-b0a3-2e725ee9cbd1" />
> <img width="694" height="527" alt="9" src="https://github.com/user-attachments/assets/f35e22e4-5cea-43ec-877b-474a119094bc" />
> <img width="451" height="477" alt="10" src="https://github.com/user-attachments/assets/af24c677-85c9-4a2b-9dd6-9924feffd237" />
> <img width="477" height="445" alt="11" src="https://github.com/user-attachments/assets/f3f81355-4159-4e2d-b797-a642abe1801d" />
> <img width="614" height="504" alt="12" src="https://github.com/user-attachments/assets/2c5f10c5-a512-44f9-910f-61eab3237855" />
> <img width="420" height="242" alt="13" src="https://github.com/user-attachments/assets/14669c08-f285-416a-8ef1-16e3982a173f" />
> <img width="952" height="439" alt="14" src="https://github.com/user-attachments/assets/21dfc5b5-c06a-44ff-b3cf-1e5ff0b737ea" />

> For the final question in this section, I needed to identify the type of scan being performed by 203.0.113.25 against 192.168.230.145. To determine this, I applied the
following filters in the Elastic interface: zeek.conn.conn_state, network.protocol, source.ip, and destination.ip. After applying these filters, the activity was identified as a
TCP SYN scan.

> <img width="341" height="226" alt="15" src="https://github.com/user-attachments/assets/819afc03-6b5a-49bd-b516-603c386eee69" />
> <img width="1148" height="183" alt="16" src="https://github.com/user-attachments/assets/c0c7ec25-5e99-455b-b107-35f7fd7f5c18" />

---

## Reflection

> This lab provided valuable insight into how attackers discover assets within a network and how to detect that activity.
