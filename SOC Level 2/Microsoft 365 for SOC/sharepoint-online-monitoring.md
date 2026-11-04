# [Microsoft 365 for SOC]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [SharePoint Online Monitoring]  
**Date Completed**: [11/04/2026]

**Lab Link**: [https://tryhackme.com/room/sharepointonlinemonitoring]

---

## 🧠 Summary

> In this lab, I explored common cyberattacks targeting Microsoft SharePoint and learned how Security Operations Center (SOC) analysts detect, investigate, and respond to suspicious
activities within SharePoint environments. I gained a deeper understanding of how attackers exploit compromised accounts, misconfigured permissions, and unauthorized file-sharing
capabilities to access sensitive information and potentially exfiltrate confidential organizational data. Additionally, I learned how to analyze SharePoint audit logs, monitor file
access and sharing activities, and identify unusual user behavior that may indicate a security incident. I also explored detection strategies for identifying indicators of compromise
(IOCs), investigating unauthorized access, and recognizing potential data exfiltration attempts.

---

## 🎯 Objectives

- [ ] Learn Entra ID and SharePoint audit log formats
- [ ] Explore how attackers exfiltrate data from SharePoint
- [ ] Discover how SharePoint can become an attack tool
- [ ] Practice the learned topics through an attack scenario

---


## 🧰 Tools Used
- THM AttackBox
- Splunk

---

## 📊 Analysis & Screenshots

*** SharePoint Logging ***

> For this section, I was tasked with investigating a Splunk instance and answering a series of questions related to the investigation. For the first question, I had to identify the
EventID that confirmed Emily's successful login to Microsoft SharePoint. After launching Splunk and executing the appropriate query, I was able to identify the EventID as:

22192ff2-272a-458c-8fac-7155db417700
>
> <img width="539" height="423" alt="1" src="https://github.com/user-attachments/assets/2ad9e552-14e7-45de-88c2-2678f7defdcc" />
> <img width="1466" height="1174" alt="2" src="https://github.com/user-attachments/assets/9b4c425f-1e1c-416e-8b0d-774c2e77536b" />

> For the next question, I had to identify the PDF file that Emily uploaded to Microsoft SharePoint. Upon further investigation and analysis of the SharePoint logs within Splunk, I was
able to determine that the uploaded file was named Instructions.pdf. This finding helped confirm the file upload activity associated with Emily's account.
>
> <img width="1206" height="745" alt="3" src="https://github.com/user-attachments/assets/93331d00-a7a7-457a-90ac-622501f850f1" />
> <img width="1080" height="576" alt="4" src="https://github.com/user-attachments/assets/837e89c7-545f-43be-887d-3b585a012d1d" />

> For the next question, I had to identify the external user with whom Emily shared the uploaded PDF file through Microsoft SharePoint. Upon further investigation and analysis of the
SharePoint logs within Splunk, I was able to determine that the external user's email address was ahmad.khan@opendoor.thm. This finding confirmed that the file had been shared with an
external recipient, highlighting the importance of monitoring external file-sharing activities to identify potential unauthorized access and data exposure within an organization's
SharePoint environment.
>
> <img width="1638" height="1238" alt="5" src="https://github.com/user-attachments/assets/19dd37d4-02c9-4340-8d74-6384b2076d61" />

*** Real-World Scenario ***

> Moving on to this section, I was tasked with investigating the index=challenge index within Splunk, which contained logs related to a suspicious OneNote file shared by Emma. Following
the investigation, I had to answer a series of questions related to the suspicious file-sharing activity. For the first question, I had to determine the exact date and time when Michael
opened the OneNote file shared with him by Emma. Upon further investigation and analysis of the Splunk logs, I was able to identify that Michael accessed the file on February 3, 2026, at
12:49:44. This finding helped establish a timeline of the suspicious file activity and provided valuable context for further investigation into potential security threats within the
SharePoint environment.
>
> <img width="1698" height="1241" alt="6" src="https://github.com/user-attachments/assets/b3f2303f-12f6-4f90-822a-6ab7802ad594" />

> For the next question, I had to identify the three external email addresses with which Emma shared the suspicious OneNote file through Microsoft SharePoint. Upon further investigation
and analysis of the Splunk logs, I was able to determine that the file was shared with the following external recipients:

li.wang@tryhatme.thm

susan.moore@deceptitech.thm

william.baker@probablyfine.thm

This finding confirmed that Emma had shared the suspicious OneNote file with three external users, highlighting the importance of monitoring external file-sharing activities to identify 
potential unauthorized access, suspicious file distribution, and possible security threats within the organization's SharePoint environment.
>
> <img width="1201" height="422" alt="7" src="https://github.com/user-attachments/assets/eebd3a70-1780-4d7b-975b-a69e1130adf1" />
> <img width="1238" height="566" alt="8" src="https://github.com/user-attachments/assets/2a959836-e1ee-458a-8a27-ded2bc7ff9af" />

> For the next question, I had to identify the CorrelationID value associated with Susan accessing the suspicious OneNote file shared by Emma. Upon further investigation and analysis of
the SharePoint logs within Splunk, I was able to determine that the CorrelationID confirming that Susan had opened the shared file link was:

945ff3a1-e059-0000-b054-6e5ee5ff2a81

This finding helped confirm that Susan had accessed the shared link and provided valuable evidence for tracking user activity, correlating related events, and investigating potential 
security threats within the SharePoint environment.
>
> <img width="1541" height="675" alt="9" src="https://github.com/user-attachments/assets/c557ffcd-441c-44c6-9f4c-71bc4bc6777a" />
> <img width="1237" height="805" alt="10" src="https://github.com/user-attachments/assets/9d12c096-a488-4c34-9b3d-be1fef61fa12" />
> <img width="1009" height="1090" alt="11" src="https://github.com/user-attachments/assets/f4dda70b-28b0-416a-8c84-0bc78ad777b7" />

> For the next question, I had to identify the PowerPoint presentation file that the attackers exfiltrated after gaining access to and reviewing Emma's Microsoft SharePoint environment.
Upon further investigation and analysis of the SharePoint logs within Splunk, I was able to determine that the exfiltrated file was named THM PoC B2E.pptx. This finding confirmed that
the attackers had accessed and exfiltrated a PowerPoint presentation from the compromised SharePoint environment, highlighting the potential risk of sensitive organizational information
being exposed to unauthorized individuals. Additionally, this discovery emphasized the importance of monitoring file access, download activities, and external sharing events to detect
potential data exfiltration and investigate security incidents.

> For the next question, I had to identify the city from which the attacker performed the malicious login. Upon further investigation and analysis of the Microsoft Entra ID sign-in logs,
I was able to determine that the suspicious authentication originated from Amsterdam, Netherlands. This finding helped establish the geographic location associated with the unauthorized
sign-in and provided valuable context for investigating the account compromise and correlating suspicious authentication activity with the previously identified SharePoint data
exfiltration.
>
> <img width="941" height="398" alt="12" src="https://github.com/user-attachments/assets/ef77e620-18b0-4b4a-9516-239ed2473410" />
> <img width="1105" height="577" alt="13" src="https://github.com/user-attachments/assets/53304dce-a815-4e26-bb03-c7cfbfb3f5b2" />

---

## Reflection

> This lab strengthened my understanding of Microsoft 365 security monitoring, cloud-based threat detection, and the importance of protecting sensitive organizational information within
SharePoint environments.
