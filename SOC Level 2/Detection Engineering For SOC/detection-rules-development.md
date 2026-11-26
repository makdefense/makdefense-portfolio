# [Detection Engineering for SOC]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Detection Rules Development]  
**Date Completed**: [11/26/2026]

**Lab Link**: [https://tryhackme.com/room/detectionrulesdevelopment]

---

## 🧠 Summary

> n this lab, I explored different types of threat detection, how to implement them using Elastic, and the process behind developing effective detection rules. I gained a deeper
understanding of detection logic, rule creation, and how to identify suspicious activities within security event data. This lab strengthened my understanding of detection engineering,
including the importance of minimizing false positives, improving detection accuracy, and developing reliable rules to identify potential security threats.

---

## 🎯 Objectives

- [ ] Understand what detection rules are and the role they play in a SOC workflow.
- [ ] Apply a structured detection research process to investigate attacker behavior before writing rules.
- [ ] Differentiate between atomic, stateful, correlation-based, and anomaly detection types, and select the appropriate type for a given scenario.
- [ ] Perform basic detection tuning to reduce false positives while preserving true positive coverage.

---


## 🧰 Tools Used
- THM AttackBox
- Elastic


---

## 📊 Analysis & Screenshots

*** The Research Process ***

> For this section of the lab, I was tasked with investigating internal reconnaissance within Elastic and answering a series of questions. To accomplish this, I first used the following
query within the Elastic application:
event.code: 1 AND (winlog.event_data.Image:*whoami* OR *net* OR *ipconfig* OR *systeminfo*)
For the first question, I had to determine which user executed the reconnaissance commands. Upon further investigation, I was able to identify the user responsible for executing these
commands as:

tryhatme.thm\sysadmin
>
> <img width="524" height="494" alt="1" src="https://github.com/user-attachments/assets/4fd6f892-f26a-4b7a-b885-924d88f9e5e7" />
> <img width="1410" height="639" alt="2" src="https://github.com/user-attachments/assets/5952c486-c9d8-48d5-84db-3cd572cc6983" />

> I then reviewed the results of the suggested query and identified the following process image path as a false positive:

C:\Windows\Microsoft.NET\Framework64\v4.0.30319\ngentask.exe
>
> <img width="1283" height="768" alt="3" src="https://github.com/user-attachments/assets/5bf51e5f-d692-4ba3-bf64-49615cd04d5e" />

> I then identified the reconnaissance tool used by the attacker that was not included in the suggested query. The executable was identified as:

nltest.exe
>
> <img width="1535" height="935" alt="4" src="https://github.com/user-attachments/assets/1237b354-7587-4f51-a17f-d4bc61bb8cc5" />

*** Atomic Detections ***

> For this section of the lab, I was tasked with building an atomic detection in Elastic by creating a custom query rule designed to identify specific suspicious activities within
security event data.
>
> <img width="1110" height="722" alt="5" src="https://github.com/user-attachments/assets/d84e48f9-315b-43fd-a60e-a5633eca5279" />
> <img width="952" height="631" alt="6" src="https://github.com/user-attachments/assets/01c44341-b28e-4a86-8e47-2c2842a7655c" />
> <img width="922" height="563" alt="7" src="https://github.com/user-attachments/assets/ed7827de-75b7-4065-b550-2c838aa29160" />
> <img width="568" height="583" alt="8" src="https://github.com/user-attachments/assets/109d9939-1a24-4df4-8378-c42d1c5057a8" />
> <img width="1249" height="711" alt="9" src="https://github.com/user-attachments/assets/9995c728-ecd9-4245-af05-4d0455ce278d" />
> <img width="1195" height="773" alt="10" src="https://github.com/user-attachments/assets/3677f4cb-3779-4e08-b014-aa5e91751320" />
> <img width="1197" height="438" alt="11" src="https://github.com/user-attachments/assets/652fe65d-a676-419d-89a5-cd32370e2366" />
> <img width="682" height="486" alt="12" src="https://github.com/user-attachments/assets/d37f9d29-a40c-46e0-985f-e1c1618b4e4b" />
> <img width="693" height="358" alt="13" src="https://github.com/user-attachments/assets/a22fbe38-b711-4030-aa10-c09e46099121" />

*** Stateful Detections ***

> Moving on to this section of the lab, I was tasked with creating a threshold rule in Elastic and defining a query to detect suspicious activity. After creating the rule and defining the
query, I was required to answer a series of questions. For the first question, I had to determine how many alerts were generated in relation to a password-spraying pattern. Upon reviewing
the results, I was able to identify a total of one alert.
>
> <img width="845" height="351" alt="14" src="https://github.com/user-attachments/assets/42df07ee-a3e2-4710-891b-e201f7b27448" />
> <img width="726" height="671" alt="15" src="https://github.com/user-attachments/assets/677d7639-cb13-44db-a148-d70ae0950fc6" />
> <img width="1330" height="362" alt="16" src="https://github.com/user-attachments/assets/914dc0c0-f8d5-44cd-a617-5b542661a2f3" />
> <img width="1179" height="813" alt="17" src="https://github.com/user-attachments/assets/34828429-76e9-495a-a3f3-c79e514eaecf" />
> <img width="1078" height="303" alt="18" src="https://github.com/user-attachments/assets/ddd813e0-d559-491d-8770-c4650ab0cd4e" />
> <img width="1162" height="435" alt="19" src="https://github.com/user-attachments/assets/14f8d576-ea1c-46ad-a40b-ae9b7b7ce1c4" />
> <img width="606" height="790" alt="20" src="https://github.com/user-attachments/assets/c62bddfa-5ba8-4224-82fb-94d7eeed93c2" />
> <img width="784" height="354" alt="21" src="https://github.com/user-attachments/assets/fdc77107-17cb-4472-8b79-1ce3c28f5a51" />

> I then identified the attacker's IP address and determined the total number of failed authentication attempts originating from that IP address.
- Attacker IP address: 5.62.18.132
- Total failed authentication attempts: 50
>
> <img width="628" height="344" alt="22" src="https://github.com/user-attachments/assets/db7a5c9c-ee23-40ed-9a32-10fcbc4c971a" />
> <img width="801" height="514" alt="23" src="https://github.com/user-attachments/assets/d83f0f97-0836-4340-a3a3-271b84f0592c" />

> Upon further investigation, I determined that the attacker attempted to authenticate using a total of 10 distinct usernames.
>
> <img width="840" height="531" alt="24" src="https://github.com/user-attachments/assets/2b4f01d9-685d-4d69-ab72-a16645a64cc2" />

*** Correlation-Based Detections ***

> For this section of the lab, I was tasked with building an event correlation rule within Elastic. After creating the rule, I was required to answer a series of questions. For the first
question, I had to determine which field would be most appropriate to configure for alert suppression. After experimenting with the rule's configuration settings, I identified the
following field as the most suitable option:

source.ip
>
> <img width="572" height="371" alt="25" src="https://github.com/user-attachments/assets/fa5600c0-e308-4af2-b0b7-5ba8508863c9" />
> <img width="1214" height="929" alt="26" src="https://github.com/user-attachments/assets/e44e8548-8677-437f-b5bf-daf30c7d2ac2" />
> <img width="1124" height="599" alt="27" src="https://github.com/user-attachments/assets/c472ab6a-0b46-445d-a190-3d6eb9f391ef" />
> <img width="1126" height="706" alt="28" src="https://github.com/user-attachments/assets/96c86931-e8b1-455a-b092-316c8832db5a" />
> <img width="1101" height="221" alt="29" src="https://github.com/user-attachments/assets/20cd2438-003d-470a-b4a6-30a87521f39a" />
> <img width="590" height="1010" alt="30" src="https://github.com/user-attachments/assets/5119847a-1f52-44e1-9c40-d574b8c51244" />

> After removing the with runs condition from the EQL sequence to reduce the number of duplicate alerts, I determined that my detection rule would become more susceptible to generating
false-positive alerts.

*** Detection Tuning ***

> For this final section of the lab, I was tasked with tuning the atomic reconnaissance rule by converting it into a threshold rule. After completing the configuration, I was required to
determine the attacker's Logon ID, which I identified as:

0x557e9
>
> <img width="1112" height="566" alt="31" src="https://github.com/user-attachments/assets/6017baeb-fd4a-458f-80a3-54075b451d7d" />
> <img width="1149" height="606" alt="32" src="https://github.com/user-attachments/assets/5a9ea7ea-162a-42aa-828a-07a49fdd39ee" />
> <img width="1089" height="216" alt="33" src="https://github.com/user-attachments/assets/d6c7a7f1-fa12-4d16-89ec-33c90b696899" />
> <img width="744" height="867" alt="34" src="https://github.com/user-attachments/assets/b745e80e-1a1a-44dc-9574-f2bb3a32b673" />

---

## Reflection

> This lab reinforced my understanding of how effective detection rules play a critical role in identifying and responding to security threats. I learned that detection engineering
requires more than simply creating rules; it involves understanding attacker behavior, analyzing security event data, and continuously refining detection logic to minimize false
positives. Working with Elastic strengthened my technical and analytical skills while highlighting the importance of balancing detection accuracy with operational efficiency. The
knowledge gained from this lab will help me develop more effective detection strategies and improve my capabilities as a future SOC analyst and cybersecurity professional.
