# [Windows Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Windows Threat 2]  
**Date Completed**: [02//2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding

---

## 🎯 Objectives
- [ ] 

---

## 🧰 Tools Used
- THM Attackbox
  
---

## 📊 Analysis & Screenshots

*** Discovery Overview ***

> For this room, I began by answering questions under this section. I had to run discovery commands. For the first question i had to figure out which privileged group does the logged
in user belong to. To figure this out i opened the "CMD" application, then inputted the command "net user Administrator." I then discovered that the logged in user belong to the
group named "Administrators."
>
> <img width="1165" height="529" alt="1" src="https://github.com/user-attachments/assets/39330f26-3752-4baf-b031-5c54fe7bf8d5" />

> Moving on to the last question for this section, i had to figure out the "image" field of the command i used to figure out which group the logged in user was in. To figure this out
i first opeded the Event Viewer application, then navigated to the folder "Sysmon" located in the Microsoft folder, then filtered the Event results by ID, then selected Event 1 with
the timestamp of "2/20/2026 2:35:53." I then discovered the "image" field to be "C:\Windows\System32\net.exe."
>
> <img width="1056" height="806" alt="2" src="https://github.com/user-attachments/assets/49ea95ba-1caa-44ed-84f6-9b239d995208" />

*** Detecting Discovery ***

> Moving on to this section, i had to answer a few questions by running a phishing attachment with the pathway of "C:\Users\Administrator\Desktop\Practice\Task 3\invoice.pdf.exe."
For the first question i figure out the first command the "invoice.pdf.exe" executes. To figure this out i ran the "invoice.pdf.exe" application. Opened the Event Viewer application,
and saw that the first command the application executes is "whoami."
>
> <img width="1223" height="409" alt="3" src="https://github.com/user-attachments/assets/e7df5930-86cb-4f19-8d3c-3a8199d277b5" />
> <img width="1021" height="299" alt="4" src="https://github.com/user-attachments/assets/f56f9307-62c0-43b2-902c-7061832d8448" />

> For the next question i had to figure out which command did the malware use to check the presence of the MS Defender EDR. To figure this out within the Event Viewer application,
then navigated to Event 1 within the Sysmon folder, selected Event 1 with the timestamp of "2/21/2026 5:04:43 PM," expanded it, to then discover the command used to be
cmd /c "tasklist /v | findstr MsSense.exe || echo No MS Defender EDR."
>
> <img width="1098" height="625" alt="5" src="https://github.com/user-attachments/assets/9a662566-a23b-4b65-aa30-0a09c3ae2ffc" />

> For the last question of this section i had to figure out to which domain did the malware send the discovered data. To figure this out i navigated to Event 22 which was specifically
for DNS queries, selected the Event 22 with the timestamp of "2/21/2026 5:04:46 PM," expanded it, then discovered the domain to be "exfil.beecz.cafe."
>
> <img width="894" height="516" alt="6" src="https://github.com/user-attachments/assets/01d30288-b330-4107-beed-336cad70fc86" />

*** Collect Overview ***

> Moving on to this section, i had to answer a few questions by using the attached VM to try to find data to collect. For the first question i had to figure out the Facebook
password the user saved in Chrome. To figure this out i first launched Chrome, then navigated to "Autofills and passwords," then "Google Passsword Manager," then "facebook.com,"
then discovered that the Facebook password the user saved in Chrome to be "nsAghv51BBav90!."
>
> <img width="518" height="347" alt="7" src="https://github.com/user-attachments/assets/e2c0b68b-2e07-4975-9a19-544418aed93b" />
> <img width="655" height="612" alt="8" src="https://github.com/user-attachments/assets/23692cf1-8b19-4c4a-b817-3d8cb6d4cfe6" />
> <img width="1156" height="325" alt="9" src="https://github.com/user-attachments/assets/cc59fb24-cfec-44e0-a1f7-c2842c469c02" />
> <img width="1129" height="535" alt="10" src="https://github.com/user-attachments/assets/4b8783fe-e922-4659-bd5c-e7faac749da3" />
> <img width="986" height="459" alt="11" src="https://github.com/user-attachments/assets/b5d01f9b-082e-4d51-a206-7775a6933c4a" />

> For the next question i had to figure out the interesting SSH key the user stores on the disk. To figure this out i launched the CMD application, then navigated to the ssh
directory by inputting the command "chdir .ssh." To discover the interesting key stored to be "thm-access-database.key."
>
> <img width="614" height="332" alt="12" src="https://github.com/user-attachments/assets/82c220a6-e039-462f-813f-e478d080ed87" />

> Moving on to the last question i had to figure out i had to figure out the secret PDF file explaining THM's internal network. To figure this out, i navigated to the "Downloads"
folder, and discovered that the secret PDF file was "thm-network-diagram-2025.pdf."
>
> <img width="488" height="308" alt="13" src="https://github.com/user-attachments/assets/404ca387-5a44-4dad-bd71-18b834d251b5" />
> <img width="803" height="261" alt="14" src="https://github.com/user-attachments/assets/564dba60-e23d-4d98-8839-5530cd143c23" />

*** Detecting Collection ***

> For this section, i had to answer a few questions by running a simple data stealer sample and analyzing its actions in logs. For the first question i had to figure out what
directory does the stealer create. To figure this out i first ran the "stealer.exe" application within the "Task5" folder. Then launched the Event Viewer application, navigated to
Event 1 within the Sysmon folder, then selected the Event 1 with the timestamp of "2/21/2026 6:12:11 PM," expanded it, to the discover the directory created to be "staging_58f1."
>
> <img width="870" height="350" alt="15" src="https://github.com/user-attachments/assets/7326fcc7-bfb0-48e0-be8d-d8f74e92d37f" />
> <img width="823" height="348" alt="16" src="https://github.com/user-attachments/assets/23468ab7-458f-4cb0-a21a-bb60c0a3f26c" />
> <img width="801" height="258" alt="17" src="https://github.com/user-attachments/assets/77d06b23-df8d-4a52-8282-dc02c886ba54" />
> <img width="828" height="556" alt="18" src="https://github.com/user-attachments/assets/945e845d-0787-4a55-beba-a9215a8378b5" />

> For the next question i had to figure out which three file extensions does the malware search for. To figure this out i just navigated through the Event 1 logs within Sysmon,
and saw that the file extensions the malware searched for was "docx, pdf, xlsx."
>
> <img width="885" height="639" alt="19" src="https://github.com/user-attachments/assets/212acbb7-673f-4925-9075-7ab0fd93de09" />
> <img width="940" height="628" alt="20" src="https://github.com/user-attachments/assets/6042d844-62de-4879-8a09-2309518f7de5" />

> For the second-to-last question i had to figure out the Powershell cmdlet does the malware use to get clipboard content. To figure this out i navigated to the Event with ID
400 within Powershell folder, selected the Event 400 with the timestamp of "2/21/2026 6:12:11 PM," expanded it, and discovered that the PowerShell cmdlet used to be "Get-ClipBoard."
>
> <img width="856" height="509" alt="21" src="https://github.com/user-attachments/assets/b4f4aa14-8755-4f36-b823-d7f9c2475a4b" />
> <img width="1148" height="523" alt="22" src="https://github.com/user-attachments/assets/259c7738-efc7-406b-b37e-88450f3574f1" />

> For the last question i had to figure out which domain does the malware exfiltrate data to. To figure this out i simply went back to Sysmon folder with Event Viewer, navigated
to Event with ID 22 which was DNS queries, and upon further investigation i discovered that the domain was "collecteddata-storage-2025.s3.amazonaws.com."

*** Ingress Tool Transfer ***

> For this last section of the room, i had to answer a few questions by using the URL "http://appsforfree.thm/trojan.exe." For the first question i had to figure out a flag by
running the website in Chrome. After running the webstie in chrome i discovered the flag to be "THM{just_use_web_browser}."
>
> <img width="935" height="354" alt="23" src="https://github.com/user-attachments/assets/014c2dcd-85c6-46e3-b605-80da08cce8ef" />
> <img width="550" height="217" alt="24" src="https://github.com/user-attachments/assets/f713f542-7206-4928-b304-778afc7ae3bf" />

> For the next question, i had to figure out a flag by using CMD to download the file from the same "http://appsforfree.thm/trojan.exe" URL using curl.exe. After downloading the
file i discovered the flag to be "THM{curl_is_cool}."
>
> <img width="762" height="414" alt="25" src="https://github.com/user-attachments/assets/0f6ef3e2-5b2a-41e1-8534-45342ac37ed7" />

> For the second to last question, i had to do the same thing but this time using certutil.exe. After downloading the file i discovered the flag to be "THM{abusing_certutil}."
>
> <img width="877" height="329" alt="26" src="https://github.com/user-attachments/assets/e5672126-36f6-42a7-9dce-c2c94ce4902f" />

> For the last question, i had to do the same thing again but this time using PowerShell IWR. After downloading the file i discovered the flag to be "THM{power_of_powershell}."
>
> <img width="1108" height="315" alt="27" src="https://github.com/user-attachments/assets/47c87105-b0be-4f32-9a4f-81f8e3bfd150" />

--- 

## Reflection

> This lab 
