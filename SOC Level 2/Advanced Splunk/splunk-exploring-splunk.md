# [Advanced Splunk]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Splunk: Exploring SPL]  
**Date Completed**: [05/29/2026]

---

## 🧠 Summary

> In this lab, I developed a solid understanding of how Splunk Processing Language (SPL) handles and filters log data to extract meaningful insights. I practiced chaining multiple
SPL commands to efficiently transform raw logs into structured, actionable results. Additionally, I explored data visualization techniques by creating charts and statistical
outputs to better interpret trends and patterns. Finally, I applied these skills to identify anomalies within log data, strengthening my ability to detect unusual or potentially
malicious activity in a SIEM environment.
---

## 🎯 Objectives
- [ ] Understand how SPL processes and filters log data
- [ ] Chain and apply SPL commands effectively
- [ ] Visualize log data with charts and statistics
- [ ] Apply your SPL skills to use anomaly detection

---

## 🧰 Tools Used
- THM AttackBox
- Splunk

---

## 📊 Analysis & Screenshots

*** Search & Reporting ***

> In this section, I answered several questions related to investigating the "windowslogs" index using Splunk. For the first question, I had to determine how many total events
were within the index. Using the query index=windowslogs, I identified the total number of events as:
12,256
>
> <img width="919" height="614" alt="0" src="https://github.com/user-attachments/assets/db3d6a28-3ef6-4b06-b488-e4dc8e8afbfc" />
> <img width="665" height="318" alt="1" src="https://github.com/user-attachments/assets/3412eda0-b1f2-4406-9961-f32e1d881b54" />
> <img width="446" height="294" alt="2" src="https://github.com/user-attachments/assets/8ddfb495-f283-405c-a387-2ed5d53e975f" />

> For the next question, I identified the SourceIP that recorded the highest number of events as:
172.90.12.11
>
> <img width="895" height="594" alt="3" src="https://github.com/user-attachments/assets/fd311d94-316a-4c23-ac05-22d4d698e538" />

> For the final question in this section, I identified the total number of events that occurred on 04/15/2022 from 08:05 AM to 08:06 AM as:
134
>
> <img width="784" height="528" alt="4" src="https://github.com/user-attachments/assets/0fab4880-3a32-456f-9ce1-1fb629f98802" />
> <img width="425" height="360" alt="5" src="https://github.com/user-attachments/assets/63c0cc1f-6224-491e-a3ed-3ac403232f6e" />

*** Search Operators ***

> In this section, I continued investigating the "windowslogs" index. For the first question, I determined how many events had an EventID equal to 4624. Using the query:
index=windowslogs EventID=4624
I retrieved a total of 26 events.
>
> <img width="841" height="421" alt="6" src="https://github.com/user-attachments/assets/08b7f417-56ab-4548-8e16-7a440cb4edf3" />

> Next, I identified the number of events where DestinationIp = 172.18.39.6 and DestinationPort = 135 as:
4, using the query:
index=windowslogs DestinationIp=172.18.39.6 AND DestinationPort=135
>
> <img width="947" height="506" alt="7" src="https://github.com/user-attachments/assets/53f4c25d-9a9a-4419-831c-784e4a44745b" />

> I then identified the SourceIP with the highest count as:
172.90.12.11, using the query:
index=windowslogs Hostname=Salena.Adam DestinationIp=172.18.38.5
>
> <img width="757" height="745" alt="8" src="https://github.com/user-attachments/assets/8f2c6bbc-f304-4f35-b019-eecef4c7d25b" />

> I also discovered that searching for the term "cyber"* returned:
12,256 events
>
> <img width="772" height="442" alt="9" src="https://github.com/user-attachments/assets/e960685b-c031-48a4-9c24-ebc3cd1e566d" />

*** Filtering Results ***

> In this section, I continued investigating the same index. I identified the SourceProcessId with the highest value by examining the Domain, SourceProcessId, and TargetProcessId
fields. The highest value was:
9496
>
> <img width="677" height="662" alt="10" src="https://github.com/user-attachments/assets/3f316eaa-32e2-476f-9e6d-bfccf274c7ee" />

> I then identified the TargetObject field value with the highest number of results as:
HKLM\SOFTWARE\Microsoft\SecurityManager, using the query:
index=windowslogs | regex TargetObject="Manager$"
>
> <img width="774" height="788" alt="11" src="https://github.com/user-attachments/assets/2365f8d2-a3c6-49cb-92fb-90a23bc013ce" />

*** Structuring Results ***

> In this section, I continued the investigation and answered additional questions. I identified the first AccountName in the search results as:
SYSTEM, after selecting the fields EventID, AccountName, and AccountType.
>
> <img width="617" height="630" alt="12" src="https://github.com/user-attachments/assets/2b786a3d-7eb5-45da-8fc8-d82be626470b" />

> I then identified the first EventID after applying the reverse command as:
800
>
> <img width="838" height="624" alt="13" src="https://github.com/user-attachments/assets/3323dde4-8f50-4bc8-9e51-44a08a139774" />

>For the final question in this section, I identified the password assigned to the user Alberto as:
paw0rd1, using the query:
index=windowslogs EventID=1
| table _time ParentProcessId ProcessId ParentCommandLine CommandLine
| reverse
>
> <img width="1954" height="467" alt="14" src="https://github.com/user-attachments/assets/a34cc8de-f793-4200-9cf9-9fcc586136fe" />

*** Transforming Commands ***

> In this section, I continued the investigation using transforming commands. I identified the most frequent Image field value using the top command as:
C:\Windows\System32\svchost.exe
>
> <img width="667" height="472" alt="15" src="https://github.com/user-attachments/assets/7a566f40-ba2a-4388-8b93-e6a8eb0aab2c" />

> I then identified the region where the IP addresses originated from as:
California, using the iplocation command.
>
> <img width="774" height="391" alt="16" src="https://github.com/user-attachments/assets/79660e27-47ff-4cb7-8a2d-eabe86dcedde" />

> For the final question, I used a lookup query to determine which Image field value had the highest RiskScore. The result was:
C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
>
> <img width="1885" height="455" alt="17" src="https://github.com/user-attachments/assets/e11b7004-a3ee-4e78-a596-38d427dfd7a3" />

*** Anomaly Detection ***

> In the final section, I investigated the "vpnlogs" index. I identified the user marked as an outlier using statistical analysis as:
jsmith
>
> <img width="797" height="712" alt="18" src="https://github.com/user-attachments/assets/b0ab8c22-a8ee-4cb2-aa09-432e2b1ac384" />

> I then identified the anomalous country for jsmith as:
JP
>
> <img width="664" height="361" alt="19" src="https://github.com/user-attachments/assets/52c1384e-8a31-4421-b3d6-6125655b0aa4" />

> Finally, I identified the user who logged in at an unusual time (around 3 AM) as:
njackson, using a z-score–based anomaly detection query.
>
> <img width="1308" height="605" alt="20" src="https://github.com/user-attachments/assets/9e2940c9-d834-4bbc-a147-4107678a8941" />

--- 

## Reflection

> This lab strengthened my ability to work confidently with SPL by turning raw log data into meaningful insights. I became more efficient at chaining commands together, which
improved how quickly I can filter, transform, and analyze large datasets. Building visualizations helped me better understand patterns and communicate findings more clearly, which
is critical in a SOC environment. Most importantly, applying these skills to anomaly detection improved my analytical thinking and reinforced how SPL can be used to identify
suspicious or unusual activity in real-world scenarios.
