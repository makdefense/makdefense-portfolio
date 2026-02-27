# [Linux Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Linux Threat Detection 1]  
**Date Completed**: [02/27/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding how attackers break into Linux systems and how to detect this activity in logs. Learning how real intrusions occur and how
to identify them early is critical for defenders. Since Linux runs many critical servers, analyzing logs helps identify login attacks, suspicious activity, and signs of compromise
before damage occurs. This skill is essential for SOC analysts because it builds real-world detection capability and prepares you to investigate actual security incidents.
---

## 🎯 Objectives
- [ ] Understand the role and risk of SSH in Linux environments
- [ ] Learn how Internet-exposed services can lead to breaches
- [ ] Utilize process tree analysis to identify the origin of the attack
- [ ] Practice detecting Initial Access techniques in realistic labs
      
---

## 🧰 Tools Used
- THM Attackbox
- THM Terminal

---

## 📊 Analysis & Screenshots

*** Initial Access SSH ***

> In this section, I answered several questions using SSH logs located at /var/log/auth.log. For the first question, I had to determine when the ubuntu user logged in via SSH for
the first time. To do this, I entered the following command:

cat /var/log/auth.log | grep "Accepted"


After reviewing the results, I discovered that the ubuntu user successfully logged in via SSH for the first time on 2024-10-22.
>
> <img width="1253" height="843" alt="1" src="https://github.com/user-attachments/assets/78a7f6d0-2672-49d9-9475-44faceb14885" />

> For the last question in this section, I had to determine whether the ubuntu user used SSH keys instead of a password on that date. After further investigation of the SSH logs,
I confirmed that the ubuntu user authenticated using SSH keys rather than a password.
>
> <img width="1485" height="407" alt="2" src="https://github.com/user-attachments/assets/bd92467e-0bb1-49a2-8cd1-4a89c079009d" />

*** Detecting SSH Attacks ***

> In this section, I answered questions related to uncovering a breach that began via SSH password brute force. For the first question, I had to determine when the SSH password
brute-force attack started. To do this, I entered the following command:

cat /var/log/auth.log | grep "Failed"


After reviewing the output, I discovered that the SSH password brute-force attack began on 2025-08-21.
>
> <img width="1280" height="251" alt="3" src="https://github.com/user-attachments/assets/217e036e-fa2c-4370-98fe-a90ae3ffb46a" />

> For the next question, I had to determine which four users the botnet attempted to breach. After further analysis of the logs, I identified the four targeted users as:

root

roy

sol

user

> For the final question in this section, I had to determine which IP address successfully breached the root user account. By reviewing the “Accepted” login entries, I discovered
that the IP address 91.224.92.79 successfully logged in as the root user.
>
> <img width="1335" height="862" alt="4" src="https://github.com/user-attachments/assets/379e7e6b-378b-4ba2-90ee-f2945ebe0688" />

*** Initial Access via Services ***

> In this section, I answered questions based on analyzing the TryPingMe web logs. For the first question, I had to determine the path to the Python file that the attacker
attempted to access. To do this, I entered:

cat /var/log/nginx/access.log


After reviewing the results, I identified the path to the Python file as:

/opt/trypingme/main.py
>
> <img width="1156" height="372" alt="5" src="https://github.com/user-attachments/assets/3ceba23b-77de-4efd-bc1a-099f600fbc82" />

> For the final question in this section, I had to determine the hidden flag within the Python file. To do this, I entered:

cat /opt/trypingme/main.py


After reviewing the contents, I discovered the hidden flag:

THM{i_am_vulnerable!}
>
> <img width="642" height="602" alt="6" src="https://github.com/user-attachments/assets/8cd99095-2025-476b-baf7-9b7f818141ff" />

*** Detecting Service Breach ***

> In the final section of this room, I answered hands-on investigation questions using auditd to analyze the TryPingMe breach. For the first question, I had to determine the PPID
of the suspicious whoami command. To do this, I entered:

ausearch -i -x whoami


After reviewing the results, I discovered that the PPID of the suspicious whoami command was 1018.
>
> <img width="999" height="188" alt="7" src="https://github.com/user-attachments/assets/a4df0975-d9e8-43f5-8089-663f6e8bd52c" />

> For the second question, I had to determine the PID of the TryPingMe application. To do this, I entered:

ausearch -i --pid 1018


After reviewing the results, I determined that the PID of the TryPingMe application was 577.
>
> <img width="1051" height="188" alt="8" src="https://github.com/user-attachments/assets/e5b6f5d5-0c8a-402e-b380-4768ea1d13e8" />

> For the final question, I had to determine which program the attacker used to open a reverse shell. To do this, I entered:

ausearch -i --pid 577


After analyzing the output, I discovered that the attacker used Python to open the reverse shell.
>
> <img width="1061" height="208" alt="9" src="https://github.com/user-attachments/assets/af75d6f0-5c26-48ec-9259-cbc5ec17eba1" />

--- 

## Reflection

> This lab strengthened my ability to understand how attackers break into Linux systems and how to detect this activity through log and process analysis.
