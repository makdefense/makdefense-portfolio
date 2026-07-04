# [THM Elastic Investigations]

**TryHackMe Path**: [Challenge]  
**Lab Topic**: [Slingshot]  
**Date Completed**: [07/04/2026]

**Lab Link**: [https://tryhackme.com/room/slingshot]

---

## 🧠 Summary

> In this challenge, I investigated an attack against a web server by identifying the reconnaissance, enumeration, exploitation, privilege escalation, and data access activity
performed by the attacker. The attacker first used reconnaissance and enumeration techniques to gather information about the target system, including discovering open services,
reviewing web directories, and identifying exposed application paths. These steps helped the attacker understand the structure of the web server and locate potential weaknesses.

The attacker then exploited vulnerabilities on the web server, likely involving exposed or poorly secured web functionality that allowed unauthorized access. After gaining an 
initial foothold, the attacker escalated their privileges and obtained administrative access by taking advantage of weak security controls, misconfigurations, or credentials 
discovered during the investigation.

Once administrative access was achieved, the attacker accessed sensitive data stored on the server. This may have included user credentials, configuration files, internal 
documents, or other confidential information. The investigation focused on tracing how the attacker moved through the environment, what vulnerabilities were abused, and what 
sensitive data may have been accessed or exfiltrated.

---

## 🎯 Objectives
- [ ] What reconnaissance and enumeration techniques were used?
- [ ] What vulnerabilities were exploited on the web server?
- [ ] How did the attacker gain administrative access?
- [ ] What sensitive data was accessed or exfiltrated?
      
---

## 🧰 Tools Used
- THM AttackBox
- Elastic

---

## 📊 Analysis & Screenshots

*** The Slingshot Investigation ***

> In this section, I was given a data view to investigate titled "apache logs" within Elastic. I had to play the role of an analyst investigating suspicious activity involving
Slingway Inc.'s e-commerce website. I then had to answer a few questions. For the first question, I had to identify the attacker's IP address. After further investigation, I was
able to identify the attacker's IP address as:
10.0.2.15
>
> <img width="742" height="620" alt="1" src="https://github.com/user-attachments/assets/b77e90fd-b854-482c-8948-41accd8ced7c" />
> <img width="600" height="550" alt="2" src="https://github.com/user-attachments/assets/09dcde66-f2a5-48c7-93bf-3f34a86729aa" />
> <img width="1133" height="781" alt="3" src="https://github.com/user-attachments/assets/d20fb4b8-3f8e-44fc-8036-dd0d6a94ac9a" />

> The first scanner that the attacker ran against the web server was discovered to be:
Nmap Scripting Engine
>
> <img width="1455" height="814" alt="4" src="https://github.com/user-attachments/assets/4746cbd2-2400-40f1-93bd-032be41b646c" />

> The User-Agent of the directory enumeration tool that the attacker used on the web server was identified as:
Mozilla/5.0 (Gobuster)
>
> <img width="706" height="531" alt="5" src="https://github.com/user-attachments/assets/e3d14912-f076-4833-8da8-691d992cd480" />

> In total, the attacker received 1,867 responses while enumerating the web server.
>
> <img width="1151" height="572" alt="6" src="https://github.com/user-attachments/assets/13bbaf41-a55c-4123-9ce2-4f886612c633" />

> One of the flags identified in one of the directories during enumeration was discovered to be:
a76637b62ea99acda12f5859313f539a
>
> <img width="1807" height="885" alt="7" src="https://github.com/user-attachments/assets/e673c2d6-b9d3-4371-8bfa-e15204bd0914" />

> The login page that the attacker discovered using the directory enumeration tool was identified as:
/admin-login.php
>
> <img width="1148" height="641" alt="8" src="https://github.com/user-attachments/assets/fe9ec586-7e6e-4a86-ae74-aeb151ad934e" />

> The User-Agent of the brute-force tool that the attacker used on the admin panel was discovered to be:
Mozilla/4.0 (Hydra)
>
> <img width="1933" height="707" alt="9" src="https://github.com/user-attachments/assets/ff9f1f7e-dd80-4ad9-8125-f05b999ea286" />

> I then identified the username and password combination the attacker used to gain access to the admin page as:
admin:thx1138
This was discovered after decoding the Base64 string in CyberChef.
>
> <img width="1744" height="870" alt="10" src="https://github.com/user-attachments/assets/a1a172e2-20c6-499f-9514-810c4dd736e9" />
> <img width="1540" height="733" alt="11" src="https://github.com/user-attachments/assets/f6d2490b-c241-4298-9018-fcf024d48aec" />

> The flag that was included in the file the attacker uploaded to the /admin/upload.php directory was identified as:
THM{ecb012e53a58818cbd17a924769ec447}
>
> <img width="1821" height="893" alt="12" src="https://github.com/user-attachments/assets/b0a93c23-7d77-4e1c-9a20-a859c3f85d5f" />

> The first command the attacker ran using the web shell was identified as:
whoami
>
> <img width="1677" height="902" alt="13" src="https://github.com/user-attachments/assets/11b1f7a2-6e57-4702-bbca-a49a2fe62ab6" />
> <img width="498" height="461" alt="14" src="https://github.com/user-attachments/assets/2a2c9db8-8814-4a03-bedf-529cb0640c58" />

> The file that was accessed via LFI to retrieve database credentials was identified as:
config-db.php
The name of the database the attacker exported via "/phpmyadmin?" was discovered to be:
customer_credit_cards
>
> <img width="1804" height="909" alt="15" src="https://github.com/user-attachments/assets/d7fb5e01-3eda-4a1f-9480-6fdcd24b0edf" />

> The flag that the attacker inserted into the database using import.php was identified as:
c6aa3215a7d519eeb40a660f3b76e64c
>
> <img width="1680" height="930" alt="16" src="https://github.com/user-attachments/assets/8e636f44-cbf3-4615-b011-d1a2dee1ae5e" />

--- 

## Reflection

> This lab strengthened my ability to investigate web-based attacks by analyzing reconnaissance, enumeration, exploitation, privilege escalation, and data access activity. I
practiced identifying how an attacker gathers information about a target, discovers exposed services or directories, and uses that information to find weaknesses in a web server.

The lab also helped me better understand how web vulnerabilities can lead to unauthorized access and how attackers may escalate privileges after gaining an initial foothold. By 
reviewing the attacker’s actions, I was able to connect each phase of the attack to the evidence found in the logs and system activity.

Overall, this challenge improved my ability to follow an attack timeline, recognize suspicious behavior, and explain how sensitive data may have been accessed or exfiltrated. It 
also reinforced the importance of proper web server hardening, secure configurations, strong authentication, and continuous monitoring.
