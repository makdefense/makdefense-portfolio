# [Detection Engineering]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Sigma]  
**Date Completed**: [08/24/2026]

**Lab Link**: [https://tryhackme.com/room/sigma]

---

## 🧠 Summary

> In this lab, I learned about Sigma, a generic signature format used to create and share detection rules across different SIEM systems. I explored how
Sigma rules are structured, how they identify suspicious activity in logs, and how they can be converted into queries compatible with various security
platforms. This lab provided a better understanding of how Sigma helps standardize threat detection and makes detection rules more portable between SIEM
solutions.

---

## 🎯 Objectives
- [ ] Introduction to the Sigma rule language.
- [ ] Learn about Sigma Rule writing syntax and conversion to various SIEM query languages.
- [ ] Navigate through writing rules for various detections on Windows Event Logs.
- [ ] Practice writing Sigma rules for an interactive case.
      
---

## 🧰 Tools Used
- THM AttackBox
- Elastic
- uncoder.io

---

## 📊 Analysis & Screenshots

*** Rule Writing & Conversion ***

> In this section, I had to convert the provided AnyDesk installation Sigma rule into an Elastic query and then use it to analyze log data from the
launched machine through the Kibana dashboard. For the first question, I had to identify which command-line tool is used to convert Sigma rules. After
reading through this section, I identified Sigmac, a Python-based tool used to convert Sigma rules.
>
> <img width="726" height="194" alt="1" src="https://github.com/user-attachments/assets/79573ab1-d3e8-40b1-b185-5ca38078b73d" />
> <img width="964" height="656" alt="2" src="https://github.com/user-attachments/assets/8239689d-47c1-4652-9e1b-d610d2914be3" />
> <img width="878" height="176" alt="3" src="https://github.com/user-attachments/assets/97418afc-0153-45aa-815f-0ff09f7da82a" />
> <img width="1044" height="663" alt="4" src="https://github.com/user-attachments/assets/65d34552-c2cd-4831-a52a-e2d33b86574d" />
> <img width="1261" height="314" alt="5" src="https://github.com/user-attachments/assets/22cdfc2c-d844-4011-b5e3-73b29b756023" />

> Moving on, after converting the AnyDesk Sigma rule into an Elastic query, I identified the time at which the AnyDesk installation event was created. The
installation event was created at:
Jun 28, 2022 @ 22:19:00
>
> <img width="870" height="198" alt="6" src="https://github.com/user-attachments/assets/c5843bf2-f939-4795-98fa-89d70f8b0947" />
> <img width="743" height="157" alt="7" src="https://github.com/user-attachments/assets/97e4b25d-6b7f-4deb-b55d-6680e0813c7a" />
> <img width="1420" height="732" alt="8" src="https://github.com/user-attachments/assets/ddda2c05-fdcd-4fd7-9aff-d333470d7267" />

> I then identified the installed version of AnyDesk as:
7.0.10
>
> <img width="472" height="352" alt="9" src="https://github.com/user-attachments/assets/98841c71-970e-4afe-9bab-15b8f6f95abd" />

*** Practical Scenario ***

> For this section, I had to create two Sigma rules: one for scheduled tasks and another for ransomware events. I then had to convert the created Sigma
rules into Elastic queries to investigate scheduled-task and ransomware activity created by an unknown entity on Aurora's network.

After creating the scheduled-task Sigma rule, I converted it into an Elastic query. To detect the creation of the scheduled task, the appropriate detection 
value for the Sigma rule was:
\schtasks.exe
>
> <img width="472" height="352" alt="9" src="https://github.com/user-attachments/assets/bbbd459c-5fde-4a8d-ac6c-f850b35d202b" />
> <img width="669" height="367" alt="10" src="https://github.com/user-attachments/assets/fb923c78-611b-434e-a19e-a2df740f6a47" />
> <img width="470" height="212" alt="11" src="https://github.com/user-attachments/assets/4175f7a0-4222-4faf-8710-2e894bb87508" />
> <img width="1340" height="317" alt="12" src="https://github.com/user-attachments/assets/c86a5aa2-7abd-4b54-bea3-9a2dd239c3b7" />

> After entering the generated query into Elastic, I identified the name of the scheduled task as:
spawn
The time at which the task was scheduled to run was identified as:
20:10hrs
>
> <img width="858" height="646" alt="13" src="https://github.com/user-attachments/assets/26f9ac4f-cd29-49c9-9963-e99d48c80f2e" />
> <img width="854" height="492" alt="14" src="https://github.com/user-attachments/assets/b5a2746f-3a4e-4a92-9e38-57cc85fb9a8f" />

> The appropriate logsource category for the Sigma rule used to detect ransomware activity was:
file_event
>
> <img width="517" height="285" alt="15" src="https://github.com/user-attachments/assets/c1489c76-8684-4d1c-9654-727595b4a150" />

> After entering the query generated from the Sigma rule created to detect ransomware activity, I identified the name of the created file as:
YOUR_FILES.txt
>
> <img width="1172" height="350" alt="16" src="https://github.com/user-attachments/assets/961280dc-3f4c-4274-be4b-3c9825de2f37" />
> <img width="1166" height="643" alt="17" src="https://github.com/user-attachments/assets/ff312289-c97b-4f13-a5d5-2e1f40df9c32" />

> The event code associated with the activity was identified as:
11
>
> <img width="1029" height="497" alt="18" src="https://github.com/user-attachments/assets/1191db9e-1efc-4680-a985-e02498182508" />

> Finally, the contents of the created ransomware file were identified as:
T1486 - Purelocker Ransom Note
>
> <img width="1263" height="748" alt="19" src="https://github.com/user-attachments/assets/f29fd0bc-2e54-41ad-9a6c-eb6bec3b963d" />

--- 

## Reflection

> This lab strengthened my ability to understand and work with Sigma rules for detecting suspicious activity across different SIEM platforms. I gained a
better understanding of how standardized detection rules can improve threat monitoring and make it easier to translate security logic between different
systems. Overall, the lab improved my confidence in recognizing how Sigma can be applied in a real-world SOC environment.
