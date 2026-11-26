# [Detection Engineering for SOC]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Detection Rules Development]  
**Date Completed**: [11//2026]

**Lab Link**: [https://tryhackme.com/room/detectionrulesdevelopment]

---

## 🧠 Summary

> In this lab, 

---

## 🎯 Objectives

- [ ] Understand what detection rules are and the role they play in a SOC workflow.
- [ ] Apply a structured detection research process to investigate attacker behavior before writing rules.
- [ ] Differentiate between atomic, stateful, correlation-based, and anomaly detection types, and select the appropriate type for a given scenario.
- [ ] Perform basic detection tuning to reduce false positives while preserving true positive coverage.

---


## 🧰 Tools Used
- THM AttackBox


---

## 📊 Analysis & Screenshots

*** The Research Process ***

> For this section of the lab, i was tasked with researching internal reconnaissance within Elastic, then had to answer a select set of questions. To go about this i first used the
query:
event.code: 1 AND (winlog.event_data.Image:*whoami* OR *net* OR *ipconfig* OR *systeminfo*)
within the Elastic application. For the first question i had to figure out what user executed the recon commands. Upon further investigation i was able to determine that the user that
executed those commands were:
tryhatme.thm\sysadmin
>
> <img width="524" height="494" alt="1" src="https://github.com/user-attachments/assets/4fd6f892-f26a-4b7a-b885-924d88f9e5e7" />
> <img width="1410" height="639" alt="2" src="https://github.com/user-attachments/assets/5952c486-c9d8-48d5-84db-3cd572cc6983" />

> I then identified the image of a false-positive that was identified in the results of the suggested query to be:
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\ngentask.exe
>
> <img width="1283" height="768" alt="3" src="https://github.com/user-attachments/assets/5bf51e5f-d692-4ba3-bf64-49615cd04d5e" />

> The executable name of the recon tool used by the attacker that is missing in the suggested query was identified as:
nltest.exe
>
> <img width="1535" height="935" alt="4" src="https://github.com/user-attachments/assets/1237b354-7587-4f51-a17f-d4bc61bb8cc5" />

*** Atomic Detections ***

> For this section, i was tasked with building an atomic detection with elastic which was basically to create a custom query rule.
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

> Moving onto this section, i was tasked with creating a threshold rule then defining a query. I then had to answer a select set of questions after creating the rule and defining the
query. For the first question i had to figure out how many alerts were generated related to a password spraying pattern. Upon creating the rule and defining the query i was able to
identify 1 alert.
>
> <img width="845" height="351" alt="14" src="https://github.com/user-attachments/assets/42df07ee-a3e2-4710-891b-e201f7b27448" />
> <img width="726" height="671" alt="15" src="https://github.com/user-attachments/assets/677d7639-cb13-44db-a148-d70ae0950fc6" />
> <img width="1330" height="362" alt="16" src="https://github.com/user-attachments/assets/914dc0c0-f8d5-44cd-a617-5b542661a2f3" />
> <img width="1179" height="813" alt="17" src="https://github.com/user-attachments/assets/34828429-76e9-495a-a3f3-c79e514eaecf" />
> <img width="1078" height="303" alt="18" src="https://github.com/user-attachments/assets/ddd813e0-d559-491d-8770-c4650ab0cd4e" />
> <img width="1162" height="435" alt="19" src="https://github.com/user-attachments/assets/14f8d576-ea1c-46ad-a40b-ae9b7b7ce1c4" />
> <img width="606" height="790" alt="20" src="https://github.com/user-attachments/assets/c62bddfa-5ba8-4224-82fb-94d7eeed93c2" />
> <img width="784" height="354" alt="21" src="https://github.com/user-attachments/assets/fdc77107-17cb-4472-8b79-1ce3c28f5a51" />





















---

## Reflection

> 
