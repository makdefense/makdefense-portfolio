# [Linux Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Linux Threat Detection 2]  
**Date Completed**: [02/28/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding the first actions attackers take after breaching a Linux server and how to detect them. These early steps reveal their
presence and intent. By detecting reconnaissance commands, privilege checks, and suspicious processes in logs, defenders can stop an attack before it escalates to data theft or
system takeover. This skill is essential for SOC analysts because it enables early intrusion detection and real-world incident response.

---

## 🎯 Objectives
- [ ] Explore how to identify Discovery commands in logs
- [ ] Learn common threats endangering Linux servers
- [ ] Know how attackers upload malware onto their victims
- [ ] Practice your skills by uncovering a real cryptominer attack
      
---

## 🧰 Tools Used
- THM Attackbox
- THM Terminal

---

## 📊 Analysis & Screenshots

*** Discovery Overview ***

> In this section, I answered several questions related to testing discovery commands. For the first question, I had to determine the output of running the command:

systemd-detect-virt


After launching the VM and running the command, I discovered the output was "amazon."
>
> <img width="574" height="123" alt="1" src="https://github.com/user-attachments/assets/8465e5aa-89c6-4232-b49d-0876ea6ef539" />

> Moving on to the last question of this section, I had to look for EDR or antivirus processes by running:

ps aux


After running the command, I discovered that the full path of the detected antimalware binary was:

/var/lib/ultrasec/malscan
>
> <img width="604" height="146" alt="2" src="https://github.com/user-attachments/assets/81fa4ea7-8c5f-42cd-8b85-9343d6e22380" />
> <img width="643" height="219" alt="3" src="https://github.com/user-attachments/assets/35e51dc3-17e0-4e99-a64e-8e3e6a6c710f" />

*** Detecting Discovery ***

> In this section, I answered questions related to an imaginary SIEM alert about a spike in discovery commands. For the first question, I had to determine the path of the script
that initiated the hostname command. To do this, I ran:

ausearch -i -x hostname
ausearch -i --pid 3771


After reviewing the results, I determined that the script path was:

/home/itsupport/debug.sh
>
> <img width="886" height="206" alt="4" src="https://github.com/user-attachments/assets/e3c1a5d6-e9f4-4c34-aec6-7fdeb7231ef9" />
> <img width="1145" height="217" alt="5" src="https://github.com/user-attachments/assets/6ec8d95c-74e2-491d-9994-00d5ffc34393" />

> For the second question, I had to determine the last discovery command launched by the script identified in the previous question. To do this, I ran:

ausearch -i --ppid 3771


After analyzing the output, I determined that the last discovery command executed by the script was:

ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu
>
> <img width="842" height="174" alt="6" src="https://github.com/user-attachments/assets/df3239ff-0566-432f-8aa0-e10de7b6cc16" />
> <img width="1364" height="230" alt="7" src="https://github.com/user-attachments/assets/74d357a7-ef7e-437a-b1a1-20f311b2429e" />

> For the final question, I had to determine the email address of the script author by examining the script contents. To do this, I ran:

cat debug.sh


After reviewing the file, I discovered that the email address of the script author was:

greg@tryhackme.thm
>
> <img width="704" height="377" alt="8" src="https://github.com/user-attachments/assets/2a85b6fc-9c3b-4fb6-8f29-24eb5136eb65" />

*** Motivation For Attacks ***

> In this section, I answered questions related to commands on the VM that may indicate Ingress Tool Transfer. For the first question, I had to determine which domain the Elastic
agent was downloaded from. To do this, I first escalated privileges using:

sudo su


Then I ran:

ausearch -i -x wget


After reviewing the results, I identified the domain:

artifacts.elastic.co
>
> <img width="1302" height="241" alt="9" src="https://github.com/user-attachments/assets/74845f0e-8413-4c09-b798-c6a4e4960bdb" />

> For the next question, I had to determine the full path of the downloaded helper.sh script. To do this, I ran:

ausearch -i -x curl


After reviewing the results, I identified the file path as:

/var/tmp/helper.sh
>
> <img width="1414" height="171" alt="10" src="https://github.com/user-attachments/assets/b0d80e98-bb4b-4088-b62f-06b590c667a3" />

> For the last question, I had to determine which of the downloaded files was more likely to be malicious when downloaded using curl or wget. Based on analysis, I determined that
files downloaded with curl were more likely to be malicious.

*** Dota3: First Actions ***

> In this section, I answered questions related to logs located in the directory:

/home/ubuntu/scenario


For the first question, I had to determine which IP address successfully brute-forced the exposed SSH service. To do this, I ran:

cat /home/ubuntu/scenario/auth.log | grep "Accepted"


After reviewing the output, I identified the IP address:

45.9.148.125
>
> <img width="1194" height="166" alt="11" src="https://github.com/user-attachments/assets/f91e7130-317c-4448-90ee-160e106862e8" />

> For the next question, I had to determine which command the attacker used to list the last logged-in users. I ran:

cat audit.log | grep "last"


After reviewing the results, I discovered that the command used was:

last
>
> <img width="929" height="143" alt="12" src="https://github.com/user-attachments/assets/c51f2028-c5b5-40f8-9d68-5220ba5668d8" />

> For the last question, I had to determine which three EDR processes the attacker searched for using egrep. To do this, I ran:

cat audit.log | grep "egrep"


After analyzing the output, I discovered that the three EDR processes were:

ds_agent, falcon, sentinel
>
> <img width="1383" height="510" alt="13" src="https://github.com/user-attachments/assets/82955d46-f6e2-4f81-9958-3139dc2ccc09" />

*** Dota3: Miner Setup ***

> In the final section, I answered questions related to the same logs in:

/home/ubuntu/scenario


For the first question, I had to determine the name of the malicious archive that was transferred via SCP. To do this, I ran:

cat audit.log | grep tar


After reviewing the results, I identified the malicious archive name:

kernupd.tar.gz
>
> <img width="1182" height="299" alt="14" src="https://github.com/user-attachments/assets/1ae92eb6-aba6-4d65-8c0d-f8ef6c6fd79d" />

> For the last question, I had to determine the IP range the attacker scanned for exposed SSH services. I ran:

cat audit.log | grep "10.10"


After reviewing the output, I determined that the scanned IP range was:

10.10.12.1–10.10.12.10
>
> <img width="1117" height="262" alt="15" src="https://github.com/user-attachments/assets/b4d4e372-67f1-4e7e-ad72-506da23ba209" />

--- 

## Reflection

> This lab strengthened my ability to understand the first actions attackers take after breaching a Linux server and how to detect them through log analysis.
