# [Cloud Security for SOC]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Monitoring AWS Logins]  
**Date Completed**: [11/08/2026]

**Lab Link**: [https://tryhackme.com/room/monitoringawslogins]

---

## 🧠 Summary

> In this lab, I explored AWS authentication mechanisms, common Identity and Access Management (IAM) threats, and various SIEM detection options. I gained a better understanding of how
AWS manages user authentication, permissions, and access to cloud resources. I also examined common IAM security threats, including compromised credentials, privilege escalation, and
unauthorized access. Additionally, I explored how AWS security logs can be analyzed through SIEM platforms to identify suspicious authentication activity, detect potential threats, and
support security investigations.

---

## 🎯 Objectives

- [ ] Understand the concept of IAM, access keys, roles, and policies
- [ ] Learn how CloudTrail logs different methods of logins in AWS
- [ ] Explore real-world cloud breaches and learn how to avoid them
- [ ] Practice the acquired knowledge in a series of mini-challenges

---


## 🧰 Tools Used
- THM AttackBox
- Splunk

---

## 📊 Analysis & Screenshots

*** Monitoring Console Logins ***

> For this section of the lab, I investigated AWS authentication events using a Splunk instance. I began my investigation by executing the index=task3 eventName=* query to retrieve
relevant events for analysis. I was then tasked with answering a series of questions based on the collected log data. For the first question, I had to determine how many times Thomas
failed to log in to the AWS Management Console. Upon further investigation and analysis of the authentication logs, I identified a total of 11 failed login attempts associated with
Thomas.
>
> <img width="684" height="449" alt="1" src="https://github.com/user-attachments/assets/c0c7538b-f79f-47e3-b0d4-9db108bd523a" />
> <img width="1078" height="1114" alt="2" src="https://github.com/user-attachments/assets/fe799a1d-6aa8-42e7-ac6b-7f00a914c096" />

> The other user who successfully logged in to the AWS Management Console without multi-factor authentication (MFA) was identified as otake.nao.
>
> <img width="1027" height="533" alt="3" src="https://github.com/user-attachments/assets/1e3447a2-291a-4042-8a48-2d465928cc1b" />
> <img width="738" height="714" alt="4" src="https://github.com/user-attachments/assets/c23ef459-fc9b-4df7-add6-4817d7019030" />


*** Monitoring Access Keys ***

> Moving on to this section of the lab, I investigated the compromise of michael.turner's AWS access key using the Splunk query index=task4. I was then tasked with answering a series of
questions based on the collected log data. For the first question, I had to identify the access key ID associated with Michael that was used during the attack. Upon further
investigation and analysis of the logs, I identified the compromised access key ID as AKIAVZZK4G6EW3NCJENS.
>
> <img width="742" height="552" alt="5" src="https://github.com/user-attachments/assets/92500074-d355-4a18-b523-92a682aa4250" />
> <img width="1078" height="671" alt="6" src="https://github.com/user-attachments/assets/5ac6af8c-1c9a-4766-8527-c4be84095519" />

> I then continued my investigation by analyzing the AWS logs to identify the S3 bucket that the attackers had accessed using the compromised access key. Upon further analysis, I
identified the S3 bucket as ocr-passport-scan.
>
> <img width="762" height="596" alt="7" src="https://github.com/user-attachments/assets/d0da211f-7fb3-43de-a4b7-80f5b7a25892" />

> I then continued my investigation by analyzing the AWS logs to determine the total number of files that were exfiltrated and deleted by the adversary. Upon further analysis of the
logs, I identified a total of 26 files that had been exfiltrated and subsequently deleted by the attacker.
>
> <img width="1190" height="897" alt="8" src="https://github.com/user-attachments/assets/2b3ba376-023b-4255-a277-2f5d64c14bdc" />

> I then continued my investigation by analyzing the AWS logs to identify the file that was uploaded to the S3 bucket following the attack. Upon further examination of the logs, I
identified the uploaded file as WHERE-ARE-MY-FILES.README.
>
> <img width="1524" height="525" alt="9" src="https://github.com/user-attachments/assets/4b5914e3-59ec-4dba-acae-eb5fdd4ffa30" />
> <img width="1054" height="830" alt="11" src="https://github.com/user-attachments/assets/d3d90124-99ea-47f7-8230-043a27ce3a8d" />

> I then continued my investigation by analyzing the AWS logs to determine which AWS service was most frequently used by the user who did not authenticate using access keys. Upon
further examination of the logs, I identified Amazon Bedrock as the most frequently accessed AWS service associated with this user.
>
> <img width="1119" height="1103" alt="12" src="https://github.com/user-attachments/assets/2429f94f-54b7-4fea-bed8-209dc46f6acf" />

*** Detecting IAM Role Abuse ***

> Moving on to this section of the lab, I was tasked with investigating AWS activity using a Splunk instance and the query index=task5. I then had to answer a series of questions based
on the collected log data. For the first question, I had to determine which EC2 instance ID was associated with the UserAvatarsProcessor IAM role. Upon further investigation and
analysis of the logs, I identified the EC2 instance ID as i-0d2b8acdedc371589.
>
> <img width="800" height="711" alt="13" src="https://github.com/user-attachments/assets/19585f27-38b8-4979-a3e6-c23597a728e4" />
> <img width="1272" height="944" alt="14" src="https://github.com/user-attachments/assets/39914b0a-b488-4acd-8499-939d4ba0a1c1" />

> I then continued my investigation by analyzing the AWS logs to identify the session name used after an individual assumed the EU-RemoteSupport IAM role. Upon further examination of
the logs, I identified the session name as SecretSession.

> I then continued my investigation by analyzing the AWS logs to identify the user who assumed the EU-RemoteSupport IAM role and used the session name SecretSession. Upon further
examination of the logs, I identified the user as sarah.braun.

*** Detecting IAM Changes ***

> For this final section of the lab, I was tasked with auditing logs related to an insecure integration between Splunk and AWS CloudTrail using the Splunk query index=task6. I then had
to answer a series of questions based on the collected log data. For the first question, I had to identify the Amazon Resource Name (ARN) used by the Splunk integration for
authentication. Upon further investigation and analysis of the logs, I identified the ARN as arn:aws:iam::398985017225.
>
> <img width="872" height="522" alt="16" src="https://github.com/user-attachments/assets/0e464991-e59f-4c99-b3cf-8770e9127dcf" />
> <img width="1196" height="558" alt="17" src="https://github.com/user-attachments/assets/95f79216-5ed1-49c0-8322-9504023805ab" />

> Finally, I continued my investigation by analyzing the AWS CloudTrail logs to determine when the overprivileged integration access key was created. Upon further examination of the
logs, I identified the creation timestamp as 2025-12-29 19:59:23.
>
> <img width="1011" height="727" alt="18" src="https://github.com/user-attachments/assets/38d6bfa0-2ed9-4b57-884d-9f96acc997cd" />

---

## Reflection

> This lab strengthened my knowledge of AWS authentication, Identity and Access Management (IAM) security, and the importance of monitoring authentication activity within cloud
environments. It helped me better understand how attackers can exploit misconfigured permissions, compromised credentials, and weak access controls to gain unauthorized access to AWS
resources. Additionally, I gained a deeper appreciation for how SIEM platforms can be used to analyze authentication logs, identify suspicious behavior, and detect potential security
threats. Overall, this lab improved my understanding of cloud security monitoring and reinforced the importance of proactive threat detection and incident response in AWS environments.
