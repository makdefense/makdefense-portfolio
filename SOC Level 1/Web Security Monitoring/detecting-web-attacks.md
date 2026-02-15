🔐 Web Security Monitoring — Attack Detection Analysis

Platform: TryHackMe
Path: SOC Level 1
Module: Detecting Web Attacks
Date Completed: Feb 14, 2026
Analyst: [Makonenn Sam]

---

🧠 Executive Summary

This lab focused on identifying web-based attacks using both log analysis and network traffic inspection. By examining HTTP access logs and packet captures, I identified multiple 
attacker behaviors including directory fuzzing, brute-force authentication attempts, and SQL injection exploitation.
The exercise demonstrated how logs and packet data serve as primary forensic evidence during incident investigations. These skills directly reflect real SOC responsibilities such 
as alert triage, intrusion detection, and attack reconstruction.

---

🎯 Objectives
- Identify indicators of common web attacks
- Analyze server logs for malicious activity
- Investigate PCAP traffic for attack evidence
- Correlate attacker behavior across data sources
- Practice detection techniques used in SOC environments

---

🧰 Tools Used

- AttackBox (Linux investigation environment)
- Wireshark (Packet analysis)
- CyberChef (Payload decoding)

---

🔎 Investigation Findings

1️⃣ Log-Based Detection Analysis

> File Investigated: access.log

Directory Fuzzing Detection

While reviewing HTTP requests, I observed multiple repetitive GET requests targeting different endpoints. This pattern is characteristic of automated directory enumeration tools.

- Indicator: Repeated endpoint probing
- User-Agent Identified:

FFUF v2.1.0

- Assessment: Attacker used automated fuzzing tool to discover hidden resources.

> <img width="473" height="263" alt="1" src="https://github.com/user-attachments/assets/5ee42159-09b8-473e-bc95-6c32d2d15ba7" />
> <img width="636" height="291" alt="2" src="https://github.com/user-attachments/assets/03ea98a8-18fe-44fb-8015-fc81c4d34ad3" />

> Brute Force Attempt Detection

Filtering for POST requests revealed multiple authentication attempts directed toward:

/login.php

- Indicator: Multiple POST login attempts
- Attack Type: Credential brute force
- Assessment: Attacker attempted password guessing.

> <img width="967" height="385" alt="3" src="https://github.com/user-attachments/assets/2aca6bee-12c4-47e4-b769-ad7e6ffe696f" />

> SQL Injection Detection

The final suspicious request contained encoded parameters targeting:

/account/changeusername.php

- Encoded payload extracted:

%25%27+OR+%271%27%3D%271

- Decoded using CyberChef:

%' OR '1'='1

- Attack Type: SQL Injection
- Tool Signature: sqlmap
- Assessment: Attacker attempted authentication bypass using SQL logic manipulation.

> <img width="1119" height="215" alt="4" src="https://github.com/user-attachments/assets/2aefd749-474d-4f0d-b37b-19034662341e" />
> <img width="1395" height="796" alt="5" src="https://github.com/user-attachments/assets/86b120f7-6ed2-4823-bb92-5b55842105e2" />


2️⃣ Network Traffic Analysis

File Investigated: traffic.pcap

> Credential Discovery via Packet Inspection

After filtering HTTP packets, packet #316 contained login credentials submitted during the brute-force attack.

- Recovered Password:

astrongpassword123

- Assessment: Successful credential compromise detected in plaintext traffic.

> <img width="568" height="430" alt="6" src="https://github.com/user-attachments/assets/7be1a4a9-557f-42a6-a69a-f179b6ff9300" />
> <img width="672" height="244" alt="7" src="https://github.com/user-attachments/assets/0f12c433-7d50-4aa2-874f-ebc862d8d84f" />
> <img width="1481" height="626" alt="8" src="https://github.com/user-attachments/assets/573a13d8-edce-4092-9569-804c64ba580f" />


> Database Extraction Evidence

Packet #442 contained SQL query results revealing sensitive data.

- Recovered Flag:

THM{dumped_the_db}

- Assessment: Indicates successful database exploitation following SQL injection.

> <img width="1251" height="107" alt="9" src="https://github.com/user-attachments/assets/7f0e7341-f1fd-4b11-a0a6-2ed32dbb82fc" />
> <img width="744" height="118" alt="10" src="https://github.com/user-attachments/assets/8461abae-d8c2-4ee9-8c74-e8c9c48d11cb" />
> <img width="736" height="489" alt="11" src="https://github.com/user-attachments/assets/aa219642-3a29-4ddd-9263-ff6360c8a424" />

---

🚨 Attack Chain Reconstruction

Based on log + traffic correlation:
- Attacker scanned directories using FFUF
- Discovered login portal
- Performed brute-force login attempts
- Exploited SQL injection vulnerability
- Extracted database data

➡️ Conclusion: This represents a full web application compromise lifecycle.

---

🧠 Skills Demonstrated

- Log analysis
- Traffic analysis
- Threat pattern recognition
- Attack chain reconstruction
- Indicator identification
- Payload decoding
- Tool fingerprinting

--- 

📌 Key Takeaway

Understanding how to analyze logs and network traffic is fundamental to detecting real-world cyberattacks. These artifacts provide the evidence required to identify attacker 
activity, determine impact, and support incident response efforts. Mastery of these techniques is essential for SOC analysts and defensive security professionals..
