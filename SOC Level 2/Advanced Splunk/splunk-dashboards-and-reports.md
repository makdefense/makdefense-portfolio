# [Advanced Splunk]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Splunk: Dashboards and Reports]  
**Date Completed**: [05/31/2026]

---

## 🧠 Summary

> In this lab, I gained an understanding of the importance of properly organizing data in Splunk to enable efficient searching and analysis for security investigations. I learned
how to create reports for recurring searches, allowing for consistent monitoring of event data over time. Additionally, I explored alert creation and rule building to automate the
detection of suspicious activity. I also developed skills in building dashboards to visualize data and communicate insights effectively. Overall, this lab reinforced Splunk’s
functionality as a SIEM, highlighting its role in real-time monitoring, detection, and response within a security operations environment.

---

## 🎯 Objectives
- [ ] Learn why organizing data in Splunk is crucial for analysts
- [ ] Create reports for recurring searches of event data
- [ ] Explore alert creation and rule building
- [ ] Build dashboards for the visualization of data
- [ ] Cover Splunk's functionality as a SIEM

---

## 🧰 Tools Used
- THM AttackBox
- Splunk

---

## 📊 Analysis & Screenshots

*** Creating Reports for Recurring Searches ***

> In this section, I answered several questions related to investigating a specific report within Splunk. The report was titled "Web Connections by Source IP." For the first
question, I had to determine which Source_IP field value recorded the highest number of events. Upon further investigation, I identified the Source_IP value "10.0.0.1" as having
the highest number of events.
>
> <img width="616" height="619" alt="1" src="https://github.com/user-attachments/assets/476af42b-98ca-4fea-ba26-9fe03d85992d" />
> <img width="952" height="471" alt="2" src="https://github.com/user-attachments/assets/4aa61f34-74af-4f32-bd24-b0d6eec59403" />
> <img width="626" height="628" alt="3" src="https://github.com/user-attachments/assets/70041857-caf3-45da-84d1-c8a797c9c212" />
> <img width="2048" height="352" alt="4" src="https://github.com/user-attachments/assets/b35d42e7-12f7-4b4c-ab75-83bcb48d3f70" />

> For the final question, I further investigated the report to locate a hidden flag. After analyzing the underlying query, I retrieved the flag:
THM{splunk_report_wizard!}
>
> <img width="536" height="425" alt="5" src="https://github.com/user-attachments/assets/95be1ea3-4689-4ea6-ba69-4f78bf93f9a1" />
> <img width="591" height="346" alt="6" src="https://github.com/user-attachments/assets/6397d077-2d86-4a77-a6c4-cfbd1f4c72ba" />

*** Detecting With Alerts and Rules ***

> In this section, I answered several questions related to investigating the "web_logs" index. For the first question, I determined how many Source_IP addresses outside of the
expected range accessed /restricted.html. After analyzing the data using the appropriate query, I identified 2 Source_IP addresses.
>
> <img width="913" height="1034" alt="7" src="https://github.com/user-attachments/assets/04f97efa-1ced-47fa-8e34-4eff448c26e6" />

> For the next question, I identified a total of 189 occurrences of 404 status codes recorded at /payments.html.
>
> <img width="753" height="1079" alt="8" src="https://github.com/user-attachments/assets/ca37e44f-babd-4fe6-b1ad-a80a00e57a11" />

> Finally, I identified the highest number of 404 errors received within a single hour as 16, using a specific search query.
>
> <img width="1077" height="623" alt="9" src="https://github.com/user-attachments/assets/2025350b-a620-4d4d-9077-437a9b8efbf7" />

*** Creating Dahsboards for Summarizing Results ***

> In this section, I created multiple pie charts to display categorized events, as well as a table to organize the data. I then answered several questions based on the dashboard.

For the first question, I examined a pie chart titled "URI" to determine which URI field value had the lowest number of events. I identified "/pictures.html" as having the fewest events.
>
> <img width="607" height="760" alt="10" src="https://github.com/user-attachments/assets/79f5ad2b-9f07-4a9c-b9be-565c127e4042" />
> <img width="757" height="569" alt="11" src="https://github.com/user-attachments/assets/4a48b877-a29a-4ab5-b54d-ffc939a7e3ae" />

> I then determined how many times the IP address 172.16.0.1 received a status_code 200 from /payments.html after adding a statistics table to the dashboard. I found that this
occurred 50 times.
>
> <img width="2046" height="235" alt="12" src="https://github.com/user-attachments/assets/95be1a53-a7c2-41c7-bce9-83ecca195b49" />

--- 

## Reflection

> This lab strengthened my ability to organize and analyze data within Splunk for effective security monitoring. I became more proficient in creating reports for recurring
searches, building alerts to detect suspicious activity, and designing dashboards to visualize key insights. These skills enhanced my understanding of how analysts use Splunk in a
SIEM environment to support real-time detection and investigation.
