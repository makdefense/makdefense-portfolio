# [Windows Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Windows Threat 3]  
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
- 
  
---

## 📊 Analysis & Screenshots

*** Command & Control ***

> For this room, I began by answering questions under this section. I had to access the attached VM, then detect the C2 setup using Sysmon logs from the pathway of
"C:\Users\Administrator\Desktop\Practice\Task 2\Sysmon.evtx." For the first question i had to figure out what suspicious archive the user downloaded. To figure this out i first
launched the "Sysmon.evtx" file from the "Task 2" folder that was located on the VM's Desktop. Then navigated to Event ID 15 with the timestamp of 07/02/2025 20:13:50, expanded it,
and discovered the suspicious archive to be "URGENT!.zip."
>
> <img width="932" height="482" alt="1" src="https://github.com/user-attachments/assets/39aa8d35-91cf-4e84-a051-38c18dad3a0c" />
> <img width="871" height="391" alt="2" src="https://github.com/user-attachments/assets/476eb03d-b3f1-4784-86a3-6719fc64d161" />
> <img width="780" height="312" alt="3" src="https://github.com/user-attachments/assets/4ed14e28-6caf-4c90-b9a4-2a69d5029790" />
> <img width="361" height="203" alt="4" src="https://github.com/user-attachments/assets/1a5d041b-833c-4dd0-836e-d43b22decff3" />
> <img width="651" height="366" alt="5" src="https://github.com/user-attachments/assets/79ce23d7-d2f7-4fff-aed5-922c69d3d0af" />

> For the next question i had to figure out where the attackers hid the C2 malware file. To figure this out i simply filtered all Events containing the ID of 11, then navigated to
the Event 11 with the timestamp of 07/02/2025 8:14:13PM, expanded it, and discovered that the file was hidden within the pathway of
"C:\Users\Administrator\AppData\Roaming\update.exe."
>
> <img width="934" height="493" alt="6" src="https://github.com/user-attachments/assets/c6bfcc1c-584c-417d-939f-485a55e26c1b" />

> For the last question of this section i had to figure out the domain of the Command and Control server. To figure this out i filtered all DNS query Events with the ID of 22, then
selected the Event 22 with the timestamp of 07/02/2025 8:14:30PM, expanded it, and discovered the domain of the Command and Control server to be "route.m365officesync.workers.dev."
>
> <img width="770" height="542" alt="7" src="https://github.com/user-attachments/assets/bca6a139-b050-44a1-adf7-b4bb8d854558" />

*** Persistence Overview ***

> Moving on to this section, i had to answer a few questions based on detecting a persistence via a backdoored user account with the pathway of
"C:\Users\Administrator\Desktop\Practice\Task 3\Security.evtx." For the first question i had to figure out how many times did the threat actor fail to login to the Administrator.
To figure this out i first launched the "Security.evtx" file with the "Task 3" folder located on the Desktop. Upon further investigation i discovered that the threat actor failed
to login in to the Administrator 6 times.
>
> <img width="1091" height="371" alt="8" src="https://github.com/user-attachments/assets/f4f2a8e9-322f-4bd3-b2d6-5f973849ac58" />
> <img width="808" height="232" alt="9" src="https://github.com/user-attachments/assets/faa16e8a-0242-4ae0-84a2-d11fba83895f" />
> <img width="999" height="503" alt="10" src="https://github.com/user-attachments/assets/b54fe3eb-32dd-40bb-bf58-d4653f867672" />

> For the next question i had to figure out which backdoor user the attacker created after logging in successfully. To figure this out i simply navigated to Event 4720 with timestamp
of "07/02/2025 9:01:38 PM," expanded it, then discovered the backdoor user created to be "support."
>
> <img width="882" height="717" alt="11" src="https://github.com/user-attachments/assets/c8a5d5ba-09d7-4d9b-9936-0178ef1e5598" />

> For the next question i had to figure out which privileged group the backdoor user was added to. To figure this out i navigated to Event 4732 with timestamp of
"07/02/2025 9:02:29 PM," expnaded it, and discovered that the backdoor user belonged to the "Administrators" group.
>
> <img width="831" height="735" alt="12" src="https://github.com/user-attachments/assets/6044c357-6f08-4c82-a769-9c84280e026c" />

*** Persistence: Task and Services ***












--- 

## Reflection

> This lab 
