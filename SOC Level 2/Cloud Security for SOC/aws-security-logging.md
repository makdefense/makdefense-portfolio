# [Cloud Security for SOC]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [AWS Security Logging]  
**Date Completed**: [11/08/2026]

**Lab Link**: [https://tryhackme.com/room/awssecuritylogging]

---

## 🧠 Summary

> In this lab, I explored various AWS log sources and learned how they support Security Operations Center (SOC) teams in monitoring cloud environments, detecting suspicious activity, and
investigating security incidents. I gained a better understanding of how AWS logging services provide visibility into user actions, API activity, network traffic, and potential security
threats.

---

## 🎯 Objectives

- [ ] Explore control plane, managed services, and workload security
- [ ] Practice using CloudTrail and GuardDuty for threat detection
- [ ] Learn about cloud log sources, such as CloudFront and S3 logs
- [ ] Gain a broad overview of how to log and monitor AWS as a SOC

---


## 🧰 Tools Used
- THM AttackBox
- Splunk

---

## 📊 Analysis & Screenshots

*** Covering AWS Control Plane ***

> For this section, I had to investigate the Splunk instance by starting with the index=aws eventName=ConsoleLogin query. After completing my investigation, I was given a few questions
to answer. For the first question, I had to determine which IP address the user jeff.harrison used to log in to AWS. Upon further investigation, I was able to determine that Jeff logged
in from the IP address 149.40.62.48.
>
> <img width="539" height="423" alt="1" src="https://github.com/user-attachments/assets/9460af21-28a8-43a0-b11a-f04ff91b325b" />
> <img width="726" height="595" alt="2" src="https://github.com/user-attachments/assets/fc5592b6-c3c1-40bf-bbb8-20e702341181" />
> <img width="1016" height="971" alt="3" src="https://github.com/user-attachments/assets/09495159-8b70-4bc4-ad71-77e93d32c743" />

> Moving on to the next question, I identified that the AWS account ID associated with Jeff Harrison's login was 398985017225.
>
> <img width="1137" height="601" alt="4" src="https://github.com/user-attachments/assets/ebbb38c6-c557-4e03-81d7-14d96810b80a" />

> Upon further investigation, I identified that the S3 bucket created by jeff.harrison after logging into AWS was named prod-website-thm.
>
> <img width="1119" height="573" alt="5" src="https://github.com/user-attachments/assets/33b1dacc-b1a6-47d2-85e9-32850654f9ea" />

*** CloudTrail and GuardDuty ***

> Moving on to this section, I had to continue investigating the AWS index within Splunk using both CloudTrail logs and GuardDuty alerts to answer a series of questions. After locating
the "AnomalousBehavior" GuardDuty alert in the logs, I was able to determine that the suspicious activity originated from a VPN service identified as ProtonVPN.
>
> <img width="985" height="643" alt="6" src="https://github.com/user-attachments/assets/1f026405-93a7-421c-bf14-c305938f07d9" />
> <img width="1656" height="753" alt="7" src="https://github.com/user-attachments/assets/84b88c2d-d017-4f10-8479-0b00d8f2f8c8" />

> After analyzing two additional alerts associated with the EC2 instance i-04fa0268276e1f763, I was able to identify the file path of the detected malware and the domain it queried. The
malware was located at /home/ubuntu/xmrig-6.24.0/xmrig, and the associated domain was identified as donate.v2.xmrig.com.
>
> <img width="1370" height="803" alt="8" src="https://github.com/user-attachments/assets/0d5984de-7793-4e46-8c01-8e67b82f64d1" />
> <img width="1077" height="486" alt="9" src="https://github.com/user-attachments/assets/52495f5e-62a8-4cf9-9ee2-c8b94b346fdc" />
> <img width="1470" height="620" alt="10" src="https://github.com/user-attachments/assets/dbdbb191-588e-4e47-9cc1-be242be1fb72" />

> Upon further investigation, I was able to identify the entity responsible for creating the infected EC2 instance. The entity was associated with the following Amazon Resource Name
(ARN): arn:aws:iam::398985017225:root.
>
> <img width="890" height="474" alt="11" src="https://github.com/user-attachments/assets/32403803-b0b0-4338-93b4-6ee79ba9acd5" />
> <img width="749" height="415" alt="12" src="https://github.com/user-attachments/assets/c39199cf-609d-44a4-b3b5-35138d64ee16" />

> Upon further investigation, I was able to identify two potentially risky ports that were exposed by the user on the EC2 instance. These were port 22 (SSH) and port 3389 (RDP), both of
which could pose security risks if exposed to unauthorized access.
>
> <img width="1078" height="954" alt="13" src="https://github.com/user-attachments/assets/ad3de036-e248-4352-a74a-3819fd970dd1" />
> <img width="880" height="680" alt="14" src="https://github.com/user-attachments/assets/4bfcd0b7-2b7b-4e73-b4e7-9e85aa3c0be7" />

*** Covering Managed Services ***

> For this final section, I had to continue my investigation using CloudFront and S3 logs to answer a series of questions. For the first question, I began by analyzing the CloudFront
logs to determine which IP address had accessed the admin portal. Upon further investigation, I was able to identify the IP address associated with the login as 168.84.119.124.
>
> <img width="1159" height="579" alt="15" src="https://github.com/user-attachments/assets/5a62e985-1b5b-4c21-b8f0-7ca04a701fea" />

> For the next question, I had to determine how many unique IP addresses searched for the keyword "tryhackme". Upon further investigation and analysis of the CloudFront logs, I was able
to identify a total of 14 unique IP addresses that searched for this keyword.
>
> <img width="1091" height="857" alt="16" src="https://github.com/user-attachments/assets/2470ce7b-47ba-483f-8ad4-347cac2b45e4" />

> Moving on to the S3 logs, I continued my investigation to identify a file of interest that had been accessed. Upon further analysis, I was able to determine that the file was named
backup.tar.gz.
>
> <img width="1223" height="1137" alt="17" src="https://github.com/user-attachments/assets/6dba0261-eead-4549-ad50-afdb25ffdb1d" />

---

## Reflection

> This lab strengthened my knowledge of cloud security monitoring, log analysis, and threat detection, highlighting the importance of AWS logs in identifying and responding to security
incidents.
