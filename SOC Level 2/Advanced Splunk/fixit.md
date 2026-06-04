# [Advanced Splunk]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Fixit]  
**Date Completed**: [06/04/2026]

---

## 🧠 Summary

> In this challenge, I worked with Splunk to process and analyze log data across multiple stages. I began by fixing event boundaries to ensure incoming logs were properly
segmented into individual events, improving data accuracy and search reliability.

Next, I extracted custom fields from the events using regular expressions, transforming raw log data into structured and searchable information. This allowed for more efficient 
querying and better visibility into key attributes such as users, IPs, and actions.

Finally, I analyzed the processed event data to uncover patterns and identify network activity, demonstrating how properly structured logs can support effective monitoring and 
investigation in a SOC environment.

---

## 🎯 Objectives
- [ ] Fix event boundaries for the incoming logs
- [ ] Extract custom fields from the available events
- [ ] Analyze event data to uncover network activity 
  
---

## 🧰 Tools Used
- THM AttackBox
- Splunk
- Command Line

---

## 📊 Analysis & Screenshots

*** The Fixit Challenge ***

> In this section, I completed a challenge by answering multiple questions related to log parsing and analyzing specific logs in Splunk. For the first question, I had to determine
the full path to the Fixit app directory within my instance. After further investigation, I discovered the full path to be:
/opt/splunk/etc/apps/fixit
>
> <img width="1448" height="398" alt="1" src="https://github.com/user-attachments/assets/1e28678b-fe7d-40d7-b1f8-5144740f82f3" />

> Moving on to the next question, I identified the full path of the network-logs script by analyzing the inputs.conf configuration file of the Fixit app. Upon investigation, I
discovered the full path to be:
/opt/splunk/etc/apps/fixit/bin/network-logs
>
> <img width="686" height="109" alt="2" src="https://github.com/user-attachments/assets/7bf17114-fa96-4c81-b298-66479f056e3c" />
> <img width="812" height="327" alt="3" src="https://github.com/user-attachments/assets/8f1bd3e1-7b7e-49db-b4f2-7284ba434ab4" />

> I then identified the regex pattern used to define the start of each event within my instance as:
^\[Network-log\]:
>
> <img width="609" height="477" alt="4" src="https://github.com/user-attachments/assets/1c8bcedf-d0cd-4f8b-a5a9-64bee6730d68" />
> <img width="512" height="375" alt="5" src="https://github.com/user-attachments/assets/e7542512-4b1f-4f14-8a11-71a48e7749c1" />

> After editing the props.conf configuration file and extracting the relevant fields, I discovered a total of 28 Username field values within the generated events.
>
> <img width="981" height="95" alt="6" src="https://github.com/user-attachments/assets/b78bd78f-21a5-497a-b74f-0b2111d08973" />
> <img width="640" height="281" alt="7" src="https://github.com/user-attachments/assets/bcd7f436-694d-4498-ab58-deda5f013839" />
> <img width="1138" height="812" alt="8" src="https://github.com/user-attachments/assets/dd34abb3-26ff-480c-a1d3-74a45d82042a" />
> <img width="1101" height="654" alt="9" src="https://github.com/user-attachments/assets/c6bfb5f1-9ed1-41a4-9fe6-21d718a02364" />
> <img width="1002" height="802" alt="10" src="https://github.com/user-attachments/assets/afb7b904-f46f-411b-98e0-d78dc26d92f0" />
> <img width="662" height="682" alt="11" src="https://github.com/user-attachments/assets/0f24046e-73d1-43b2-84aa-d94b67aca19f" />
> <img width="1261" height="715" alt="12" src="https://github.com/user-attachments/assets/4209075e-1979-4e5f-9a66-cdaf08474690" />

> I then identified the domain Cybertees.THM in the log data after extracting the relevant fields, along with a total of 12 URI field values.
>
> <img width="1171" height="665" alt="13" src="https://github.com/user-attachments/assets/ef658850-eff7-4ef1-909a-a8626e09e18a" />
> <img width="1189" height="948" alt="14" src="https://github.com/user-attachments/assets/7568371a-c632-42be-aeac-8e34ff14041b" />
> <img width="1429" height="738" alt="15" src="https://github.com/user-attachments/assets/5731f371-e453-4009-836d-4682dec88e0d" />
> <img width="790" height="952" alt="16" src="https://github.com/user-attachments/assets/353c23d8-b1a9-44b5-a865-c32a36586cd3" />

> After further analyzing the traffic, I discovered that two /products pages appeared in the data.
>
> <img width="946" height="901" alt="17" src="https://github.com/user-attachments/assets/05d15e25-33ac-49b5-b49d-a4963d2fabdf" />

> I also identified that the /sales/ URI field value appeared in the event data without a file extension.

> Moving forward, I identified Robert Wilson as the most active user on the network.
>
> <img width="791" height="917" alt="18" src="https://github.com/user-attachments/assets/9cf9d8df-fed2-40cf-b799-b06269519ea9" />

> Through further investigation, I identified three unique IP ranges represented in the observed network traffic.
>
> <img width="1280" height="724" alt="19" src="https://github.com/user-attachments/assets/c98f9ba9-b728-4001-9393-6d2c4733b384" />
> <img width="1424" height="777" alt="20" src="https://github.com/user-attachments/assets/2478f0fa-05e7-4563-a7ed-d841019545f7" />
> <img width="1093" height="662" alt="21" src="https://github.com/user-attachments/assets/558d6bfe-8f81-4347-bfa8-ce91ed0653be" />
> <img width="971" height="969" alt="22" src="https://github.com/user-attachments/assets/70bcd7eb-0995-4c92-9ab5-0679c79ab301" />

> For the final question, I determined that the user Sarah Hall accessed the file secret-document.pdf on the client’s server.
>
> <img width="1480" height="853" alt="23" src="https://github.com/user-attachments/assets/d4c8e929-782b-4212-8fd8-6fe8202f2540" />

--- 

## Reflection

> This lab strengthened my ability to work with Splunk to properly structure and analyze log data for security investigations. I gained hands-on experience fixing event
boundaries, ensuring that incoming logs were correctly segmented into individual events, which improved overall data accuracy and search performance.

I also enhanced my ability to extract custom fields using regular expressions, allowing me to transform raw, unstructured logs into meaningful and searchable data. This process 
improved my efficiency in identifying key attributes such as users, systems, and actions within large datasets.

Additionally, I developed stronger analytical skills by examining the processed events to uncover network activity and patterns. This reinforced the importance of well-structured 
data in detecting potential security issues and conducting effective investigations.

Overall, this lab improved my confidence in handling log data end-to-end, from ingestion and parsing to analysis, and better prepared me for real-world SOC environments where 
accurate data interpretation is critical.
