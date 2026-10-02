# [Active Directory for SOC]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Monitoring Active Directory]  
**Date Completed**: [10/02/2026]

**Lab Link**: [https://tryhackme.com/room/monitoringactivedirectory]

---

## 🧠 Summary

> In this lab, I learned how to monitor Active Directory activity and identify anomalies within high-volume security logs. I analyzed authentication and account-related events to
distinguish normal user behavior from potentially suspicious activity. The lab strengthened my ability to investigate large datasets, recognize unusual patterns, and use log analysis
techniques to detect possible security threats in an Active Directory environment.

---

## 🎯 Objectives
- [ ] Identify the protocols that generate AD traffic and differentiate between domain and local user authentication
- [ ] Interpret core AD Event IDs across authentication, account lifecycle, groups, and directory services
- [ ] Establish baseline activity patterns and spot anomalies using stack counting
- [ ] Configure audit policies to capture critical AD events
- [ ] Query AD logs in Splunk to investigate user activity

---

## 🧰 Tools Used
- THM AttackBox
- 

---

## 📊 Analysis & Screenshots

*** Authentication Events ***

> For this section, I had to go through the reading and then answer a question. The question required me to determine how many unique accounts requested Ticket Granting Tickets (TGTs)
in the dataset across all available time periods. After launching Splunk, I used the following query:

index=* EventCode=4768
| table _time, Account_Name, Client_Address, Ticket_Encryption_Type

Using this query, I was able to identify 14 unique accounts that requested TGTs within the dataset.
>
> <img width="726" height="479" alt="1" src="https://github.com/user-attachments/assets/c2ef061f-f298-49b7-9cdb-68cf0f285861" />
> <img width="1736" height="954" alt="2" src="https://github.com/user-attachments/assets/235cd0c3-81fc-4bd5-b318-aca1a3cb750e" />

*** Understanding Baseline Activity ***

> After going through the readings, I had to answer a question that required me to determine the most frequently requested service using Event ID 4769. After running the necessary query
in Splunk and analyzing the results, I was able to identify THM-DC$ as the most frequently requested service.
>
> <img width="1213" height="569" alt="3" src="https://github.com/user-attachments/assets/6ccd67e7-2395-4a32-8861-67707a3b002d" />
> <img width="1057" height="605" alt="4" src="https://github.com/user-attachments/assets/8f3aef4f-f412-4ac1-9aea-6547f9cb98a5" />

*** Scenario: New Employee Onboarding Audit ***

> Moving on, as part of the security onboarding verification process, I investigated the activity of a newly hired marketing employee using Splunk. The review focused on confirming that
the user account was created appropriately and that the employee’s first-day activity was consistent with normal business behavior. I examined relevant authentication and user activity
logs for unusual login attempts, suspicious access patterns, or other indicators of compromise.

The purpose of the investigation was to verify that the account had not been misused and that the observed activity aligned with the employee’s expected role and onboarding process. I 
first had to identify the name of the newly created account. Upon further investigation, I was able to determine that the newly created account was nathan.brooks.
>
> <img width="1160" height="953" alt="5" src="https://github.com/user-attachments/assets/67318113-7973-4e54-9236-9a2342e900b3" />

> I then continued the investigation to determine which user was responsible for creating the new account. After reviewing the relevant account creation events in Splunk, I identified
adm-luke.sullivan as the user who created the nathan.brooks account.
>
> <img width="776" height="312" alt="6" src="https://github.com/user-attachments/assets/ce4c0f44-43dc-430d-b22b-a92032e2ab2a" />

> I then continued the investigation by identifying the group to which the newly created user account was added. After reviewing the relevant Active Directory events in Splunk, I
determined that nathan.brooks was added to the Marketing group.
>
> <img width="1595" height="518" alt="7" src="https://github.com/user-attachments/assets/224563cc-6faf-4b22-b1c5-9e6bfb5e1014" />

> Finally, I identified the source IP address associated with nathan.brooks’s first Ticket Granting Ticket (TGT) request. After reviewing the relevant authentication events in Splunk, I
determined that the request originated from 10.5.50.12.
>
> <img width="982" height="559" alt="8" src="https://github.com/user-attachments/assets/c6653222-c678-4b6e-8f55-d7d532fae3b1" />
> <img width="1149" height="558" alt="9" src="https://github.com/user-attachments/assets/b5f13d4b-0a9d-4bc3-9dd8-b7f2f849cccc" />

---

## Reflection

> This lab strengthened my ability to analyze Active Directory logs, identify suspicious patterns, and investigate anomalies within large volumes of security data. It also improved my
confidence in distinguishing normal user activity from behavior that may indicate a potential security issue. Overall, the lab gave me more hands-on experience with the type of log
analysis and investigative thinking used in a SOC environment.
