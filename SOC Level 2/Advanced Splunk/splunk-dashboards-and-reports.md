# [Advanced Splunk]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Splunk: Dashboards and Reports]  
**Date Completed**: [05//2026]

---

## 🧠 Summary

> In this lab, I gained an understanding of the importance of properly organizing data in Splunk to enable efficient searching and analysis for security investigations. I learned
how to create reports for recurring searches, allowing for consistent monitoring of event data over time. Additionally, I explored alert creation and rule building to automate the
detection of suspicious activity. I also developed skills in building dashboards to visualize data and communicate insights effectively. Overall, this lab reinforced Splunk’s
functionality as a SIEM, highlighting its role in real-time monitoring, detection, and response within a security operations environment.

---

## 🎯 Objectives
- [ ] 

---

## 🧰 Tools Used
- THM AttackBox
- Splunk
- 

---

## 📊 Analysis & Screenshots

***  ***

> In this section, I answered several questions related to investigating a specific report within Splunk. The report was titled "Web Connections by Source IP." For the first
question, I had to determine which Source_IP field value recorded the highest number of events. Upon further investigation, I identified the Source_IP value "10.0.0.1" as having
the highest number of events.
>
> <img width="616" height="619" alt="1" src="https://github.com/user-attachments/assets/476af42b-98ca-4fea-ba26-9fe03d85992d" />
> <img width="952" height="471" alt="2" src="https://github.com/user-attachments/assets/4aa61f34-74af-4f32-bd24-b0d6eec59403" />
> <img width="626" height="628" alt="3" src="https://github.com/user-attachments/assets/70041857-caf3-45da-84d1-c8a797c9c212" />
> <img width="2048" height="352" alt="4" src="https://github.com/user-attachments/assets/b35d42e7-12f7-4b4c-ab75-83bcb48d3f70" />

> For the last question, i had to further investigate the report to find a hidden flag. After investigating the query behind the report i was able to retrieve the hidden flag:
THM{splunk_report_wizard!}
>
> <img width="536" height="425" alt="5" src="https://github.com/user-attachments/assets/95be1ea3-4689-4ea6-ba69-4f78bf93f9a1" />
> <img width="591" height="346" alt="6" src="https://github.com/user-attachments/assets/6397d077-2d86-4a77-a6c4-cfbd1f4c72ba" />

*** Detecting With Alerts and Rules ***

> Moving onto this section, i had to answer a few questions related to investigating the index "web_logs." For the first question i had to figure out how many Source_IP addresses
outside of the expected range accessed:
/restricted.html
Upon further investigation of the index by using a specified query, i identified 2 Source_IP addresses.
>
> <img width="913" height="1034" alt="7" src="https://github.com/user-attachments/assets/04f97efa-1ced-47fa-8e34-4eff448c26e6" />

> For the next question, i identified a total of "189" 404 status_code recorded at
/payments.html
>
> <img width="753" height="1079" alt="8" src="https://github.com/user-attachments/assets/ca37e44f-babd-4fe6-b1ad-a80a00e57a11" />

> Finally, i identifed the highest number of 404's recieved in a given hour to be "16" with the use of a specific search query.
>
> <img width="1077" height="623" alt="9" src="https://github.com/user-attachments/assets/2025350b-a620-4d4d-9077-437a9b8efbf7" />

*** Creating Dahsboards for Summarizing Results ***

> Moving onto this section. I had to create multiple pie charts to display categorized events, and also a table to categorize events. I then had to answer a few questions. For the
first question they wanted mem to inspect one of the pie charts i created in the dashboard which was titled:
URI
I had to figure out which URI field value had the least amount of events present. Upon further investigation i was able to identify that the "/pictures.html" URI field value
had the least amount of events present.
>
> <img width="607" height="760" alt="10" src="https://github.com/user-attachments/assets/79f5ad2b-9f07-4a9c-b9be-565c127e4042" />
> <img width="757" height="569" alt="11" src="https://github.com/user-attachments/assets/4a48b877-a29a-4ab5-b54d-ffc939a7e3ae" />

> I then had to figure out how many times 172.16.0.1 recieved the status_code 200 from /payments.html after adding another statistics table to the dashboard. Upon further
investigation, i was able to discover that the IP address: 172.16.0.1 recieved the status code 200 from /payments.html 50 times.
>
> <img width="2046" height="235" alt="12" src="https://github.com/user-attachments/assets/95be1a53-a7c2-41c7-bce9-83ecca195b49" />

--- 

## Reflection

> This lab strengthened my ability to 
