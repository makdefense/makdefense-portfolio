# [Advanced ELK]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Elastic: Query Languages]  
**Date Completed**: [06/27/2026]

**Lab Link**: [https://tryhackme.com/room/advancedelkqueries]

---

## 🧠 Summary

> In this lab, I learned how to search large datasets efficiently using advanced queries in Kibana. The room focused on improving my ability to filter, search, and analyze data
within Kibana by using more precise query techniques.

I practiced working with structured data, narrowing down search results, and identifying relevant information from large volumes of logs. This helped me better understand how 
analysts use Kibana to investigate security events, find patterns, and quickly locate important details during an investigation.

This lab reinforced the importance of efficient searching when working with large datasets. It also helped strengthen my confidence in using Kibana as a security analysis tool 
for log investigation, threat hunting, and incident response workflows.

---

## 🎯 Objectives
- [ ] Understand the query languages available in Kibana and when to use them
- [ ] Build advanced searches using operators, special characters, and flexible matching techniques
- [ ] Accurately filter and search structured and nested data within events
- [ ] Refine search results by controlling how terms are matched within fields and log messages
- [ ] Apply pattern-based searches to uncover variations and related activity
      
---

## 🧰 Tools Used
- THM AttackBox
- Elastic

---

## 📊 Analysis & Screenshots

*** Navigating Nested Data ***

> After reviewing this section, I had to conduct an investigation using Elastic by querying a large dataset titled "incidents." I then had to answer a few questions. For the
first question, I had to figure out how many incidents involved the file:
marketing_strategy_2023_07_23.pptx
After selecting the "incidents" dataset and entering the query "marketing_strategy_2023_07_23.pptx", I discovered that a total of 4 incidents contained the file
marketing_strategy_2023_07_23.pptx.
>
> <img width="934" height="772" alt="1" src="https://github.com/user-attachments/assets/a29a9cd6-2b98-40ea-b517-73bb1d986673" />
> <img width="690" height="682" alt="2" src="https://github.com/user-attachments/assets/68cafb90-e229-447f-a7a8-a44ebd89b757" />
> <img width="1085" height="511" alt="3" src="https://github.com/user-attachments/assets/9687d5de-bbec-4446-84d7-a1630e3b8a47" />

> I then figured out how many incidents involved files on a "File Server" with names that start with "marketing_strategy" by using the affected_systems.affected_files.file_name
field and conducting a wildcard search. The total number of incidents retrieved was:
135
>
> <img width="1332" height="705" alt="4" src="https://github.com/user-attachments/assets/3efbf1e9-2474-4e4e-b916-cfdabbc71064" />

> Moving on, I discovered the "Web Server" that had a true positive incident where both the admin and IT users were logged in. The "Web Server" was identified as:
web-server-77
>
> <img width="2004" height="658" alt="5" src="https://github.com/user-attachments/assets/fbc8441b-4603-4a1a-b699-afa043b96345" />

*** Investigating With Regular Expressions ***

> For this section, I had to use regex for incident hunting along with Lucene query syntax within Elastic. I had to investigate the "incidents" index pattern and answer a select
set of questions. For the first question, I had to figure out how many events existed where a client_list file was affected by ransomware. The total number of events discovered
was:
69

> After investigating the affected_systems.affected_files.file_name field using the regex:
/.*project.*/
I was able to retrieve the affected system name on the latest managed event by "EVenis" as:
web-server-37

*** Defining Ranges and Boundaries ***

> I then continued my investigation with the "incidents" index pattern. I identified a total of 52 "Data Leak" incidents that had a severity_level of 9 or higher.
>
> <img width="1001" height="537" alt="6" src="https://github.com/user-attachments/assets/2c536d83-940a-47ea-b50d-243a684aeb76" />

> A total of 65 events occurred on an Email Server or Web Server and were investigated by AJohnston on or before December 1, 2022.
>
> <img width="2048" height="507" alt="7" src="https://github.com/user-attachments/assets/d296015a-c922-444e-916f-cdc2e8d0a3a5" />

> The analyst who stated that the "Data Leak" on file-server-65 was a false positive was identified as:
JLim
>
> <img width="2048" height="795" alt="8" src="https://github.com/user-attachments/assets/07b2d913-6d50-4db2-9c1f-3739be624a6f" />

*** Searching Variants and Proximity ***

> After going through this section, I had to find incidents using fuzzy and proximity searches, then answer a few questions. I first identified the total number of incidents
handled by "JLim" in which the word "true" appeared with a single-character difference. The total number of incidents was:
110
>
> <img width="1219" height="483" alt="9" src="https://github.com/user-attachments/assets/668d1c2f-4964-4f44-a585-adb0d754672f" />

> After trying a proximity search on the incident_comments field, I identified a total of 33 events that contained "data-leak" and "true-negative" within three words of each
other.
>
> <img width="1279" height="702" alt="10" src="https://github.com/user-attachments/assets/bde247f9-77e1-4e35-bf6f-7d367129faa4" />

> Finally, I identified a total of 40 incidents handled by AJohnston that contained "detected" and "negative" within two positions of each other.
>
> <img width="1354" height="632" alt="11" src="https://github.com/user-attachments/assets/1b5583b3-3b75-49ea-b8f9-aeb6e6b16977" />

--- 

## Reflection

> This lab strengthened my ability to search and analyze large datasets in Kibana using advanced query techniques. It helped me better understand how to narrow down results,
filter logs, and locate specific information more efficiently during an investigation.

I also improved my ability to work with structured data and identify patterns that may be useful for security analysis, threat hunting, and incident response. This lab reinforced 
the importance of writing precise queries when working with large amounts of log data, especially in a SOC environment where speed and accuracy are important.
