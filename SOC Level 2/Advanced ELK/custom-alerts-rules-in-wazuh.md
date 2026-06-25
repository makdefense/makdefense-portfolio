# [Advanced ELK]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Custom Alert Rules in Wazuh]  
**Date Completed**: [06//2026]

**Lab Link**: [https://tryhackme.com/room/customalertrulesinwazuh]

---

## 🧠 Summary

> In this lab, I learned how to 

---

## 🎯 Objectives
- [ ] 
      
---

## 🧰 Tools Used
- THM AttackBox
- Wazuh

---

## 📊 Analysis & Screenshots

*** Decoders ***

> In this section, i started off by testing decoders within Wazuh. After running a "Sysmon" decoder within Wazuh, i was tasked to answer a few questions. For the first question
i had to figure out the value of the "sysmon.commandLine" within the Sysmon Log. Upon further investigation i was able to retrieve the value of the "system.commandLine" to be:
"C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" "-file" "C:\Users\Alberto\Desktop\test.ps1"
>
> <img width="917" height="709" alt="1" src="https://github.com/user-attachments/assets/e958fe82-66f2-4ad3-97fb-5cf228dd41d3" />
> <img width="1050" height="719" alt="2" src="https://github.com/user-attachments/assets/51c1a1b8-328b-45bd-95ff-8e4157e93a89" />
> <img width="1491" height="631" alt="3" src="https://github.com/user-attachments/assets/2c2c6e17-19be-4402-b29f-c0d25d34cf97" />
> <img width="1494" height="863" alt="4" src="https://github.com/user-attachments/assets/5fa0a283-408b-4aeb-ad8c-00037072a2f7" />

> I then determined that the extracted value if the regex was set to "User: \S*" would be:
WIN-P57C9KN929H\Alberto
>
> <img width="1008" height="487" alt="5" src="https://github.com/user-attachments/assets/d19bb5f2-f796-4c6e-b0a0-01e9b68b9ae0" />

*** Rules ***

> After going through this section, understanding rules and testing rules within Wazuh i was tasked to answer a few questions. For the first question, after analyzing the ruleset
Test results, i was able to retrieve the <mitre> ID of rule id 184666 as:
T1055
>
> <img width="426" height="267" alt="6" src="https://github.com/user-attachments/assets/12f85a75-10f3-4c05-8bc7-007924cbf17b" />

> According to the Wazuh documentation, i was able to discover the description of the rule with a classification level of 12 to be:
High importance event
>
> <img width="817" height="286" alt="7" src="https://github.com/user-attachments/assets/bcdfdb7f-642d-480c-9f0f-b2e455109222" />

> After changing the value of "sysmon.image" to "taskhost.exe" in the Ruleset Test page, and refreshing the page. I was able to identify the ID of the rule triggered to be:
184736
>
> <img width="700" height="296" alt="8" src="https://github.com/user-attachments/assets/e26f0066-ccb6-482c-93d5-d3f99c3e89b0" />
> <img width="1239" height="809" alt="9" src="https://github.com/user-attachments/assets/7a41a218-2d6d-4762-9b8c-e55d3e9c608a" />

*** Rule Order ***

> After going through this section, testing the rule order. I was able to identify the rule ID of the parent of 184717 to be:
184716
within the sysmon_rule.xml file.
>
> <img width="880" height="343" alt="10" src="https://github.com/user-attachments/assets/d13e002e-4113-43bd-b102-dd3e5da554f9" />

*** Custom Rules ***

> Going through this section, adding local rules, i was able to identify the regex field name used in the local_rules.xml to be:
audit.cwd
>
> ![Uploading 11.png…]()













--- 

## Reflection

> This lab strengthened my ability to

