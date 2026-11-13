# [Cloud Security for SOC]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Monitoring AWS Services]  
**Date Completed**: [11/12/2026]

**Lab Link**: [https://tryhackme.com/room/monitoringawsservices]

---

## 🧠 Summary

> In this lab, I explored common attacks targeting Amazon Web Services (AWS) and learned how to identify, investigate, and defend against potential security threats within cloud
environments. I gained hands-on experience analyzing AWS security logs, identifying suspicious activities, and investigating threats such as compromised IAM credentials, unauthorized
access, privilege escalation, and potential data exfiltration. Additionally, I strengthened my understanding of AWS security best practices, including access control, monitoring, and
threat detection, to help protect cloud resources against malicious activity.

---

## 🎯 Objectives

- [ ] Learn the risks of exposed S3 and RDS, and practice the defenses
- [ ] Understand the workflows to detect insecure EC2 security groups
- [ ] Learn about the emerging Denial of Wallet attacks targeting AWS
- [ ] Practice the material in Splunk via CloudTrail and GuardDuty datasets

---


## 🧰 Tools Used
- THM AttackBox
- Splunk

---

## 📊 Analysis & Screenshots

*** S3 Attacks and Defenses ***

> For this section of the lab, I was tasked with investigating how Alex exposed the S3 bucket and how this exposure led to the security breach. I then had to answer a series of
questions related to the investigation.

For the first question, I had to determine when Alex disabled the "S3 Public Access Block" feature. Upon further investigation, I was able to identify the exact date and time:

2025-12-31 17:48:12
>
> <img width="501" height="507" alt="1" src="https://github.com/user-attachments/assets/9ece080b-0583-4678-8b59-4ff87963d02d" />
> <img width="780" height="426" alt="2" src="https://github.com/user-attachments/assets/da4221b6-0425-45fc-a98a-a9c70608f047" />
> <img width="1415" height="688" alt="3" src="https://github.com/user-attachments/assets/a93ce98d-8fa9-4880-b1d6-dd8272e00a23" />

> I then identified the Statement ID (SID) of the policy that made the S3 bucket publicly accessible as:

TempAccessDeniedDebug
>
> <img width="775" height="413" alt="4" src="https://github.com/user-attachments/assets/8f753670-9a23-484c-83f4-ec5534d42dce" />
> <img width="1094" height="782" alt="5" src="https://github.com/user-attachments/assets/f3524a97-12aa-4c20-a92c-fe66067bdfb3" />

> Upon further investigation, I identified the IP address that initiated a scan of the S3 bucket shortly after it became publicly accessible as:

212.8.250.220
>
> <img width="1296" height="1083" alt="6" src="https://github.com/user-attachments/assets/b99c20db-2170-4ff0-ab29-1e2cc1a97d99" />

> Upon further investigation, I determined that a total of 53 filenames were attempted during the S3 bucket scan. Additionally, I identified the file that was successfully exfiltrated
from the bucket as:

repo.zip
>
> <img width="1016" height="549" alt="7" src="https://github.com/user-attachments/assets/ef980db8-8350-4d24-8b37-8b921ed7c7ed" />
> <img width="1235" height="688" alt="8" src="https://github.com/user-attachments/assets/b293175e-d8da-4085-a599-f4e0a45c5392" />
> <img width="1031" height="616" alt="9" src="https://github.com/user-attachments/assets/10f56c31-45c7-46df-b5b1-6caf3c7007f7" />

*** EC2 Internet Exposure ***

> For this section of the lab, I was tasked with investigating a typical Amazon EC2 exposure scenario and answering a series of questions related to the investigation.

For the first question, I had to identify the security group Emma created and determine which potentially risky service it exposed. Upon further investigation, I identified the security 
group and the exposed service as follows:

Security Group: website-access-sg

Exposed Service: SSH (Secure Shell)
>
> <img width="1283" height="947" alt="10" src="https://github.com/user-attachments/assets/bfa02f3e-9fd3-4240-a72b-7dd46356f8e0" />
> <img width="1588" height="738" alt="11" src="https://github.com/user-attachments/assets/1f5befbf-8045-4260-ab6b-155d8aabe04f" />
> <img width="668" height="488" alt="12" src="https://github.com/user-attachments/assets/a9cfb616-aaaf-4346-9b15-b1b5f724ba66" />

> Upon further investigation, I identified the EC2 instance that was created shortly after the security group was configured and determined that it was associated with the previously
identified security group, website-access-sg. The EC2 instance ID was identified as:

i-082579354380296e6
>
> <img width="925" height="380" alt="13" src="https://github.com/user-attachments/assets/e82652a5-93fe-4409-9c00-65597bb5fa6b" />

> Upon further investigation, I analyzed the Amazon GuardDuty alert to identify the IP address responsible for attacking the EC2 instance shortly after it was exposed. Based on the
findings from the GuardDuty alert, the attacking IP address was identified as:

45.78.205.134
>
> <img width="1049" height="379" alt="14" src="https://github.com/user-attachments/assets/648b3074-94cd-44f0-b83b-2ef85229b178" />

> Upon further investigation, I identified the approximate date and time when Emma implemented the insecure rule within the security group, potentially exposing the EC2 instance to
unauthorized access. The timestamp was identified as:

2025-12-31 21:58:34
>
> <img width="1263" height="936" alt="15" src="https://github.com/user-attachments/assets/df235619-fd03-482b-8908-958bf9cbc5e0" />

*** Risks of Public Databases ***

> For this section of the lab, I was tasked with analyzing an Amazon RDS database exposure scenario and answering a series of questions related to the investigation.

For the first question, I had to identify the instance identifier of the newly created RDS database. Upon further investigation and analysis of the relevant logs within the index, I was 
able to determine that the RDS instance identifier was:

db-thm-preprod-qa
>
> <img width="1095" height="1008" alt="16" src="https://github.com/user-attachments/assets/7232d378-4ddf-4ea5-a380-3a4f86ad15eb" />

> Upon further investigation, I identified two events that indicated the RDS database had been exposed to the internet. Through analysis of the relevant logs, I was able to determine
the first eight characters of the event IDs associated with the exposure. These were identified as follows:

First Event ID: dcb54877

Second Event ID: 0a3b23c1
>
> <img width="898" height="397" alt="17" src="https://github.com/user-attachments/assets/87b53786-ee3c-4313-a34b-a07de5fa88c3" />
> <img width="1013" height="425" alt="18" src="https://github.com/user-attachments/assets/e584c8ad-da7a-4dbb-aca1-ebea20e07cd1" />
> <img width="1553" height="511" alt="19" src="https://github.com/user-attachments/assets/6ce013c3-eaec-4ec8-84ec-d84f8f037d26" />

*** Detecting Cloud Discovery ***

> For this final section of the lab, I was tasked with analyzing a discovery activity scenario originating from a compromised IAM user account and answering a series of questions
related to the investigation.

For the first question, I had to identify the second discovery command executed by the adversary. Upon further investigation and analysis of the relevant logs, I was able to determine 
that the command was:

ListAttachedUserPolicies
>
> <img width="1110" height="567" alt="20" src="https://github.com/user-attachments/assets/a669b958-8df5-482d-b3d4-f95a2cfe5ce4" />

> Upon further investigation, I analyzed the relevant IAM activity logs to identify another user account that the adversary had discovered and subsequently compromised by establishing
backdoor access. Based on my findings, the affected IAM user was identified as:

lars.andersen
>
> <img width="932" height="357" alt="21" src="https://github.com/user-attachments/assets/6786c051-21cd-4fd9-b506-dcce6b9bee6b" />

---

## Reflection

> This lab provided me with valuable hands-on experience investigating common security vulnerabilities and attack scenarios within AWS cloud environments. Throughout the lab, I
strengthened my ability to analyze security logs, identify suspicious activities, and understand how misconfigurations can expose critical cloud resources to potential threats. By
investigating publicly exposed S3 buckets, insecure EC2 security groups, exposed RDS databases, and compromised IAM accounts, I gained a deeper understanding of how adversaries discover
and exploit weaknesses within cloud infrastructure.
