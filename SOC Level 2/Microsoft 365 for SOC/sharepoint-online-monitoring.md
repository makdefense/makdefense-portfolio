# [Microsoft 365 for SOC]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [SharePoint Online Monitoring]  
**Date Completed**: [11//2026]

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

> For this section, i was tasked to investigate a Splunk instance, then answer a select set of questions. For the first question i had to figure out what was the EventID that confirms
Emily's login to Sharepoint. Upon launch Splunk, and using the correct query i was able to identify the EventID as:
22192ff2-272a-458c-8fac-7155db417700
>
> <img width="539" height="423" alt="1" src="https://github.com/user-attachments/assets/2ad9e552-14e7-45de-88c2-2678f7defdcc" />
> <img width="1466" height="1174" alt="2" src="https://github.com/user-attachments/assets/9b4c425f-1e1c-416e-8b0d-774c2e77536b" />

> After going through the Sharepoint logs i was able to identify the PDF file Emily uploaded to the SharePoint. Which was:
Instructions.pdf
>
> <img width="1206" height="745" alt="3" src="https://github.com/user-attachments/assets/93331d00-a7a7-457a-90ac-622501f850f1" />
> <img width="1080" height="576" alt="4" src="https://github.com/user-attachments/assets/837e89c7-545f-43be-887d-3b585a012d1d" />

> Emily then shared the file with an external user. The email address of that external user was identified as:
ahmad.khan@opendoor.thm
>
> <img width="1638" height="1238" alt="5" src="https://github.com/user-attachments/assets/19dd37d4-02c9-4340-8d74-6384b2076d61" />

*** Real-World Scenario ***

> Moving onto this section, my job was to investigate the "index=challenge," which consists of a suspicious OneNote file that was shared by Emma, then answer a select set of questions.
For the first question i had to figure out when did Michael open the file that was shared to him by Emma. Upon further investigation, i was able to identify that Michael opened the
file at:
2026-02-03 12:49:44
>
> <img width="1698" height="1241" alt="6" src="https://github.com/user-attachments/assets/b3f2303f-12f6-4f90-822a-6ab7802ad594" />

> The three external emails Emma shared the file to was identified as:
li.wang@tryhatme.thm, susan.moore@deceptitech.thm, william.baker@probablyfine.thm
>
> <img width="1201" height="422" alt="7" src="https://github.com/user-attachments/assets/eebd3a70-1780-4d7b-975b-a69e1130adf1" />
> <img width="1238" height="566" alt="8" src="https://github.com/user-attachments/assets/2a959836-e1ee-458a-8a27-ded2bc7ff9af" />

> For the user that accessed the file which was Susan, the correlationID value that proved the sharing link has been opened was identified as:
945ff3a1-e059-0000-b054-6e5ee5ff2a81
>
> <img width="1541" height="675" alt="9" src="https://github.com/user-attachments/assets/c557ffcd-441c-44c6-9f4c-71bc4bc6777a" />
> <img width="1237" height="805" alt="10" src="https://github.com/user-attachments/assets/9d12c096-a488-4c34-9b3d-be1fef61fa12" />
> <img width="1009" height="1090" alt="11" src="https://github.com/user-attachments/assets/f4dda70b-28b0-416a-8c84-0bc78ad777b7" />

> The powerpoint presentation file that the attackers exfiltrated after reviewing Emma's SharePoint was identified as:
THM PoC B2E.pptx

> The malicious login was performed from the city Amsterdam according to the Entra ID logs
>
> <img width="941" height="398" alt="12" src="https://github.com/user-attachments/assets/ef77e620-18b0-4b4a-9516-239ed2473410" />
> <img width="1105" height="577" alt="13" src="https://github.com/user-attachments/assets/53304dce-a815-4e26-bb03-c7cfbfb3f5b2" />

---

## Reflection

> This lab strengthened my understanding of Microsoft 365 security monitoring, cloud-based threat detection, and the importance of protecting sensitive organizational information within
SharePoint environments.
