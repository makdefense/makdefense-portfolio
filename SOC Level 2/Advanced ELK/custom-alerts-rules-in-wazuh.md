# [Advanced ELK]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Custom Alert Rules in Wazuh]  
**Date Completed**: [06//2026]

**Lab Link**: [https://tryhackme.com/room/customalertrulesinwazuh]

---

## 🧠 Summary

> In this lab, I learned how to create custom rules in Wazuh to improve detection and alerting within a security environment. The room focused on understanding how Wazuh rules
work, how alerts are generated, and how custom rule logic can be used to detect specific events or suspicious activity.

I practiced analyzing logs, identifying important fields, and building rules that match certain patterns or behaviors. This helped me better understand how security teams can 
tune Wazuh to their environment, reduce noise, and create more meaningful alerts for incident detection and response.

This room reinforced the importance of rule creation in a SIEM/XDR platform and showed how custom detections can help organizations monitor activity more effectively based on 
their own systems, threats, and security needs.

---

## 🎯 Objectives
- [ ] Learn how important data is extracted from logs using Decoders
- [ ] Learn how alerts are triggered using custom Wazuh Rules
- [ ] Learn how to add new rules to extend detection capabilities
- [ ] Learn how to simulate a real-world attack to test existing rules
      
---

## 🧰 Tools Used
- THM AttackBox
- Wazuh

---

## 📊 Analysis & Screenshots

*** Decoders ***

> In this section, I started by testing decoders within Wazuh. After running a "Sysmon" decoder within Wazuh, I was tasked with answering a few questions. For the first question,
I had to figure out the value of sysmon.commandLine within the Sysmon log. Upon further investigation, I was able to retrieve the value of sysmon.commandLine as:
"C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" "-file" "C:\Users\Alberto\Desktop\test.ps1"
>
> <img width="917" height="709" alt="1" src="https://github.com/user-attachments/assets/e958fe82-66f2-4ad3-97fb-5cf228dd41d3" />
> <img width="1050" height="719" alt="2" src="https://github.com/user-attachments/assets/51c1a1b8-328b-45bd-95ff-8e4157e93a89" />
> <img width="1491" height="631" alt="3" src="https://github.com/user-attachments/assets/2c2c6e17-19be-4402-b29f-c0d25d34cf97" />
> <img width="1494" height="863" alt="4" src="https://github.com/user-attachments/assets/5fa0a283-408b-4aeb-ad8c-00037072a2f7" />

> I then determined that if the regex was set to User: \S*, the extracted value would be:
WIN-P57C9KN929H\Alberto
>
> <img width="1008" height="487" alt="5" src="https://github.com/user-attachments/assets/d19bb5f2-f796-4c6e-b0a0-01e9b68b9ae0" />

*** Rules ***

> After going through this section, understanding rules, and testing rules within Wazuh, I was tasked with answering a few questions. For the first question, after analyzing the
Ruleset Test results, I was able to retrieve the <mitre> ID of rule ID 184666 as:
T1055
>
> <img width="426" height="267" alt="6" src="https://github.com/user-attachments/assets/12f85a75-10f3-4c05-8bc7-007924cbf17b" />

> According to the Wazuh documentation, I was able to discover that the description of the rule with a classification level of 12 was:
High importance event
>
> <img width="817" height="286" alt="7" src="https://github.com/user-attachments/assets/bcdfdb7f-642d-480c-9f0f-b2e455109222" />

> After changing the value of sysmon.image to taskhost.exe on the Ruleset Test page and refreshing the page, I was able to identify the ID of the triggered rule as:
184736
>
> <img width="700" height="296" alt="8" src="https://github.com/user-attachments/assets/e26f0066-ccb6-482c-93d5-d3f99c3e89b0" />
> <img width="1239" height="809" alt="9" src="https://github.com/user-attachments/assets/7a41a218-2d6d-4762-9b8c-e55d3e9c608a" />

*** Rule Order ***

> After going through this section and testing the rule order, I was able to identify the parent rule ID of 184717 as:
184716
This was found within the sysmon_rule.xml file.
>
> <img width="880" height="343" alt="10" src="https://github.com/user-attachments/assets/d13e002e-4113-43bd-b102-dd3e5da554f9" />

*** Custom Rules ***

> While going through this section and adding local rules, I was able to identify the regex field name used in the local_rules.xml file as:
audit.cwd
>
> <img width="990" height="222" alt="13" src="https://github.com/user-attachments/assets/52ea782c-bbbe-4103-bda6-d2c813a11534" />
> <img width="940" height="608" alt="11" src="https://github.com/user-attachments/assets/0c9350fd-b10a-46f8-b4cd-955b909760ec" />
> <img width="1501" height="813" alt="12" src="https://github.com/user-attachments/assets/0187e9f5-916b-4a82-8287-fba756ebd133" />

> After looking at the added log within Wazuh, the current working directory from which the cwd command was executed was discovered to be:
/var/log/audit
>
> <img width="932" height="645" alt="14" src="https://github.com/user-attachments/assets/d322eb51-e77a-4e20-aa3a-0064b1e97e5c" />

*** Fine-Tuning ***

> After going through this section, fine-tuning the custom rule by adding more child rules, and testing the updated custom rules within Wazuh, I was able to figure out that when
the filename in the logs was test.php, the rule ID triggered was:
100003
>
> <img width="467" height="164" alt="15" src="https://github.com/user-attachments/assets/3c1f7430-f104-4233-80b2-ee54c278e4d3" />

> Finally, if the filename in the logs was malware-checker.sh, the rule classification level in the generated alert was:
12
>
> <img width="417" height="166" alt="16" src="https://github.com/user-attachments/assets/e0569ef8-41d4-44af-9814-2eec304e8c37" />

--- 

## Reflection

> This lab strengthened my ability to create and customize Wazuh rules for detecting security events within an environment. It helped me better understand how Wazuh processes
logs, matches rule conditions, and generates alerts based on specific activity.

I also improved my ability to analyze log data, identify important fields, and build detection logic that can be used to monitor suspicious behavior. This lab reinforced the 
importance of tuning SIEM/XDR rules to reduce noise, improve alert quality, and support more effective incident detection and response.

