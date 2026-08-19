# [Detection Engineering]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Sigma]  
**Date Completed**: [07//2026]

**Lab Link**: [https://tryhackme.com/room/sigma]

---

## 🧠 Summary

> In this lab, 

---

## 🎯 Objectives
- [ ] 
      
---

## 🧰 Tools Used
- THM AttackBox
- 

---

## 📊 Analysis & Screenshots

*** Rule Writing & Conversion ***

> In this section, i had to convert the AnyDesk Installation Sigma rule that was given into an Elastic Query, then use it to analyze log data from the
launched machine on the Kibana dashboard. But for the first question i had to identify what command line tool is used to convert Sigma rules. After reading
through this section i identified Sigmac which is Python-written tool that converts Sigma rules.
>
> <img width="726" height="194" alt="1" src="https://github.com/user-attachments/assets/79573ab1-d3e8-40b1-b185-5ca38078b73d" />
> <img width="964" height="656" alt="2" src="https://github.com/user-attachments/assets/8239689d-47c1-4652-9e1b-d610d2914be3" />
> <img width="878" height="176" alt="3" src="https://github.com/user-attachments/assets/97418afc-0153-45aa-815f-0ff09f7da82a" />
> <img width="1044" height="663" alt="4" src="https://github.com/user-attachments/assets/65d34552-c2cd-4831-a52a-e2d33b86574d" />
> <img width="1261" height="314" alt="5" src="https://github.com/user-attachments/assets/22cdfc2c-d844-4011-b5e3-73b29b756023" />

> Moving on, after converting the AnyDesk Sigma rule into an elastic query i then identified the time that the AnyDesk installation event was created. The
installation event was created:
Jun 28, 2022 @ 22:19:00
>
> <img width="870" height="198" alt="6" src="https://github.com/user-attachments/assets/c5843bf2-f939-4795-98fa-89d70f8b0947" />
> <img width="743" height="157" alt="7" src="https://github.com/user-attachments/assets/97e4b25d-6b7f-4deb-b55d-6680e0813c7a" />
> <img width="1420" height="732" alt="8" src="https://github.com/user-attachments/assets/ddda2c05-fdcd-4fd7-9aff-d333470d7267" />

> I then identified the version of AnyDesk that was installed to be:
7.0.10
>
> <img width="472" height="352" alt="9" src="https://github.com/user-attachments/assets/98841c71-970e-4afe-9bab-15b8f6f95abd" />

*** Practical Scenario ***

> For this section, i had to create two Sigma rules one for scheduled tasks, and one for ransomware events. I then had to convert those created Sigma rules
into Elastic queries to investigate the scheduled tasks, and ransomware events an unknown entity created on the network for the organization, Aurora.
After creating the scheduled task Sigma rule, i then converted it into an elastic query. To detect the creation of the scheduled task, the detection value
that would be appropriate for the Sigma rule is:
\schtasks.exe
>
> <img width="472" height="352" alt="9" src="https://github.com/user-attachments/assets/bbbd459c-5fde-4a8d-ac6c-f850b35d202b" />
> <img width="669" height="367" alt="10" src="https://github.com/user-attachments/assets/fb923c78-611b-434e-a19e-a2df740f6a47" />
> <img width="470" height="212" alt="11" src="https://github.com/user-attachments/assets/4175f7a0-4222-4faf-8710-2e894bb87508" />
> <img width="1340" height="317" alt="12" src="https://github.com/user-attachments/assets/c86a5aa2-7abd-4b54-bea3-9a2dd239c3b7" />

> After inputting the found query into Elastic, i identified the name of the scheduled task to be:
spawn
the time this task was meant to run was discovered to be:
20:10hrs
>
> <img width="858" height="646" alt="13" src="https://github.com/user-attachments/assets/26f9ac4f-cd29-49c9-9963-e99d48c80f2e" />
> <img width="854" height="492" alt="14" src="https://github.com/user-attachments/assets/b5a2746f-3a4e-4a92-9e38-57cc85fb9a8f" />

> 

















--- 

## Reflection

> This lab strengthened my ability to 
