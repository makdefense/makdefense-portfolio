# [Windows Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Windows Threat 2]  
**Date Completed**: [02/21/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding how to detect and analyze attackers’ first actions after breaching Windows. This is important because it helps defenders
identify intrusions early and stop them before serious damage occurs. By recognizing suspicious activity and common attack patterns, analysts can respond quickly, limit impact, and
strengthen their incident response and threat detection skills.

---

## 🎯 Objectives
- [ ] Detect common Discovery techniques using Windows Event Log
- [ ] Learn how to trace the attack origin by reconstructing a process tree
- [ ] Find out what data threat actors look for and how they exfiltrate it
- [ ] See how the malicious commands are logged by running them yourself

---

## 🧰 Tools Used
- THM Attackbox
- THM Event Viewer
- THM CMD
- THM Google Chrome
  
---

## 📊 Analysis & Screenshots

*** Discovery Overview ***

> For this room, I began by answering questions under this section. I had to run discovery commands. For the first question, I had to figure out which privileged group the logged-in
user belonged to. To determine this, I opened the CMD application and entered the command net user Administrator. I then discovered that the logged-in user belonged to the group named Administrators.
>
> <img width="1165" height="529" alt="1" src="https://github.com/user-attachments/assets/39330f26-3752-4baf-b031-5c54fe7bf8d5" />

> Moving on to the last question for this section, I had to find the image field of the command I used to determine which group the logged-in user belonged to. To do this, I first
opened the Event Viewer application, then navigated to the Sysmon folder located inside the Microsoft folder. I filtered the event results by ID and selected Event 1 with the
timestamp 2/20/2026 2:35:53. I then discovered that the image field was C:\Windows\System32\net.exe.
>
> <img width="1056" height="806" alt="2" src="https://github.com/user-attachments/assets/49ea95ba-1caa-44ed-84f6-9b239d995208" />

*** Detecting Discovery ***

> In this section, I answered several questions by running a phishing attachment located at C:\Users\Administrator\Desktop\Practice\Task 3\invoice.pdf.exe. For the first question, I
had to determine the first command that invoice.pdf.exe executed. To do this, I ran the application, opened Event Viewer, and observed that the first command executed was whoami.
>
> <img width="1223" height="409" alt="3" src="https://github.com/user-attachments/assets/e7df5930-86cb-4f19-8d3c-3a8199d277b5" />
> <img width="1021" height="299" alt="4" src="https://github.com/user-attachments/assets/f56f9307-62c0-43b2-902c-7061832d8448" />

> For the next question, I had to determine which command the malware used to check for the presence of MS Defender EDR. I navigated to Event 1 in the Sysmon folder, selected the
event with the timestamp 2/21/2026 5:04:43 PM, expanded it, and discovered that the command used was:
cmd /c "tasklist /v | findstr MsSense.exe || echo No MS Defender EDR."
>
> <img width="1098" height="625" alt="5" src="https://github.com/user-attachments/assets/9a662566-a23b-4b65-aa30-0a09c3ae2ffc" />

> For the last question in this section, I had to determine to which domain the malware sent the discovered data. I navigated to Event 22, which logs DNS queries, selected the event
with timestamp 2/21/2026 5:04:46 PM, expanded it, and discovered that the domain was exfil.beecz.cafe.
>
> <img width="894" height="516" alt="6" src="https://github.com/user-attachments/assets/01d30288-b330-4107-beed-336cad70fc86" />

*** Collect Overview ***

> In this section, I answered questions using the attached VM to find data to collect. For the first question, I had to find the Facebook password saved in Chrome. To do this, I
launched Chrome, navigated to Autofill and Passwords, then Google Password Manager, then facebook.com, and discovered that the saved password was nsAghv51BBav90!.
>
> <img width="518" height="347" alt="7" src="https://github.com/user-attachments/assets/e2c0b68b-2e07-4975-9a19-544418aed93b" />
> <img width="655" height="612" alt="8" src="https://github.com/user-attachments/assets/23692cf1-8b19-4c4a-b817-3d8cb6d4cfe6" />
> <img width="1156" height="325" alt="9" src="https://github.com/user-attachments/assets/cc59fb24-cfec-44e0-a1f7-c2842c469c02" />
> <img width="1129" height="535" alt="10" src="https://github.com/user-attachments/assets/4b8783fe-e922-4659-bd5c-e7faac749da3" />
> <img width="986" height="459" alt="11" src="https://github.com/user-attachments/assets/b5d01f9b-082e-4d51-a206-7775a6933c4a" />

> For the next question, I had to find the interesting SSH key stored on disk. I launched CMD and navigated to the .ssh directory using the command chdir .ssh. I discovered that the
interesting key stored was thm-access-database.key.
>
> <img width="614" height="332" alt="12" src="https://github.com/user-attachments/assets/82c220a6-e039-462f-813f-e478d080ed87" />

> For the last question, I had to find the secret PDF file explaining THM’s internal network. I navigated to the Downloads folder and discovered that the file was named
thm-network-diagram-2025.pdf.
>
> <img width="488" height="308" alt="13" src="https://github.com/user-attachments/assets/404ca387-5a44-4dad-bd71-18b834d251b5" />
> <img width="803" height="261" alt="14" src="https://github.com/user-attachments/assets/564dba60-e23d-4d98-8839-5530cd143c23" />

*** Detecting Collection ***

>In this section, I answered questions by running a simple data-stealer sample and analyzing its actions in logs. For the first question, I had to determine which directory the
stealer created. I ran stealer.exe inside the Task5 folder, opened Event Viewer, navigated to Event 1 in Sysmon, selected the event with timestamp 2/21/2026 6:12:11 PM, expanded it,
and discovered that the directory created was staging_58f1.
>
> <img width="870" height="350" alt="15" src="https://github.com/user-attachments/assets/7326fcc7-bfb0-48e0-be8d-d8f74e92d37f" />
> <img width="823" height="348" alt="16" src="https://github.com/user-attachments/assets/23468ab7-458f-4cb0-a21a-bb60c0a3f26c" />
> <img width="801" height="258" alt="17" src="https://github.com/user-attachments/assets/77d06b23-df8d-4a52-8282-dc02c886ba54" />
> <img width="828" height="556" alt="18" src="https://github.com/user-attachments/assets/945e845d-0787-4a55-beba-a9215a8378b5" />

> For the next question, I had to determine which three file extensions the malware searched for. I navigated through the Event 1 logs in Sysmon and saw that the extensions were
docx, pdf, xlsx.
>
> <img width="885" height="639" alt="19" src="https://github.com/user-attachments/assets/212acbb7-673f-4925-9075-7ab0fd93de09" />
> <img width="940" height="628" alt="20" src="https://github.com/user-attachments/assets/6042d844-62de-4879-8a09-2309518f7de5" />

> For the second-to-last question, I had to determine which PowerShell cmdlet the malware used to get clipboard content. I navigated to Event ID 400 in the PowerShell folder,
selected the event with timestamp 2/21/2026 6:12:11 PM, expanded it, and discovered that the cmdlet used was Get-Clipboard.
>
> <img width="856" height="509" alt="21" src="https://github.com/user-attachments/assets/b4f4aa14-8755-4f36-b823-d7f9c2475a4b" />
> <img width="1148" height="523" alt="22" src="https://github.com/user-attachments/assets/259c7738-efc7-406b-b37e-88450f3574f1" />

> For the last question, I had to determine which domain the malware exfiltrated data to. I returned to the Sysmon folder in Event Viewer, navigated to Event ID 22 (DNS queries),
and discovered that the domain was collecteddata-storage-2025.s3.amazonaws.com.

*** Ingress Tool Transfer ***

> In this final section, I answered questions using the URL http://appsforfree.thm/trojan.exe. For the first question, I had to find a flag by opening the website in Chrome. After
opening it, I discovered the flag THM{just_use_web_browser}.
>
> <img width="935" height="354" alt="23" src="https://github.com/user-attachments/assets/014c2dcd-85c6-46e3-b605-80da08cce8ef" />
> <img width="550" height="217" alt="24" src="https://github.com/user-attachments/assets/f713f542-7206-4928-b304-778afc7ae3bf" />

> For the next question, I had to find a flag using CMD to download the file from the same URL with curl.exe. After downloading the file, I discovered the flag THM{curl_is_cool}.
>
> <img width="762" height="414" alt="25" src="https://github.com/user-attachments/assets/0f6ef3e2-5b2a-41e1-8534-45342ac37ed7" />

> For the second-to-last question, I repeated the process using certutil.exe and discovered the flag THM{abusing_certutil}.
>
> <img width="877" height="329" alt="26" src="https://github.com/user-attachments/assets/e5672126-36f6-42a7-9dce-c2c94ce4902f" />

> For the final question, I repeated the process using PowerShell IWR and discovered the flag THM{power_of_powershell}.
>
> <img width="1108" height="315" alt="27" src="https://github.com/user-attachments/assets/47c87105-b0be-4f32-9a4f-81f8e3bfd150" />

--- 

## Reflection

> This lab strengthened my ability to detect and analyze the first steps of threat actors after breaching Windows.
