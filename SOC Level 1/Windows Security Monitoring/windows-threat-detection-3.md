# [Windows Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Windows Threat 3]  
**Date Completed**: [02/23/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding how threat actors maintain access to breached Windows systems. This is important because it helps defenders find hidden
persistence mechanisms, fully remove attackers, and prevent reinfection. Understanding these techniques strengthens incident response, improves detection skills, and ensures systems
are truly secure after a compromise.

---

## 🎯 Objectives
- [ ] Remind the concept of Command and Control (C2)
- [ ] Learn why and how threat actors maintain control of their victims
- [ ] Use Windows event logs to uncover various persistence methods
- [ ] See how the learned techniques work in a hands-on environment
      
---

## 🧰 Tools Used
- THM Attackbox
- THM Event Viewer
- THH CMD
  
---

## 📊 Analysis & Screenshots

*** Command & Control ***

> For this room, I began by answering questions in this section. I accessed the attached VM and detected the C2 setup using Sysmon logs from the path
C:\Users\Administrator\Desktop\Practice\Task 2\Sysmon.evtx.

For the first question, I had to determine what suspicious archive the user downloaded. To do this, I launched the Sysmon.evtx file from the Task 2 folder located on the VM’s 
Desktop. I navigated to Event ID 15 with the timestamp 07/02/2025 20:13:50, expanded it, and discovered that the suspicious archive was URGENT!.zip.
>
> <img width="932" height="482" alt="1" src="https://github.com/user-attachments/assets/39aa8d35-91cf-4e84-a051-38c18dad3a0c" />
> <img width="871" height="391" alt="2" src="https://github.com/user-attachments/assets/476eb03d-b3f1-4784-86a3-6719fc64d161" />
> <img width="780" height="312" alt="3" src="https://github.com/user-attachments/assets/4ed14e28-6caf-4c90-b9a4-2a69d5029790" />
> <img width="361" height="203" alt="4" src="https://github.com/user-attachments/assets/1a5d041b-833c-4dd0-836e-d43b22decff3" />
> <img width="651" height="366" alt="5" src="https://github.com/user-attachments/assets/79ce23d7-d2f7-4fff-aed5-922c69d3d0af" />

> For the next question, I had to determine where the attackers hid the C2 malware file. To do this, I filtered all events with Event ID 11, navigated to the event with timestamp
07/02/2025 8:14:13 PM, expanded it, and discovered that the file was hidden in the path
C:\Users\Administrator\AppData\Roaming\update.exe.
>
> <img width="934" height="493" alt="6" src="https://github.com/user-attachments/assets/c6bfcc1c-584c-417d-939f-485a55e26c1b" />

> For the last question in this section, I had to determine the domain of the Command and Control server. I filtered all DNS query events with Event ID 22, selected the event with
timestamp 07/02/2025 8:14:30 PM, expanded it, and discovered that the domain was
route.m365officesync.workers.dev.
>
> <img width="770" height="542" alt="7" src="https://github.com/user-attachments/assets/bca6a139-b050-44a1-adf7-b4bb8d854558" />

*** Persistence Overview ***

> In this section, I answered questions based on detecting persistence via a backdoored user account from the path
C:\Users\Administrator\Desktop\Practice\Task 3\Security.evtx.

For the first question, I had to determine how many times the threat actor failed to log in to the Administrator account. I launched the Security.evtx file from the Task 3 folder 
located on the Desktop. After investigation, I discovered that the threat actor failed to log in to the Administrator account six times.
>
> <img width="1091" height="371" alt="8" src="https://github.com/user-attachments/assets/f4f2a8e9-322f-4bd3-b2d6-5f973849ac58" />
> <img width="808" height="232" alt="9" src="https://github.com/user-attachments/assets/faa16e8a-0242-4ae0-84a2-d11fba83895f" />
> <img width="999" height="503" alt="10" src="https://github.com/user-attachments/assets/b54fe3eb-32dd-40bb-bf58-d4653f867672" />

> For the next question, I had to determine which backdoor user the attacker created after successfully logging in. I navigated to Event 4720 with timestamp 07/02/2025 9:01:38 PM,
expanded it, and discovered that the backdoor user created was support.
>
> <img width="882" height="717" alt="11" src="https://github.com/user-attachments/assets/c8a5d5ba-09d7-4d9b-9936-0178ef1e5598" />

> For the next question, I had to determine which privileged group the backdoor user was added to. I navigated to Event 4732 with timestamp 07/02/2025 9:02:29 PM, expanded it, and
discovered that the backdoor user belonged to the Administrators group.
>
> <img width="831" height="735" alt="12" src="https://github.com/user-attachments/assets/6044c357-6f08-4c82-a769-9c84280e026c" />

*** Persistence: Task and Services ***

> In this section, I uncovered two backdoors left by attackers using Security and Sysmon logs located at
C:\Users\Administrator\Desktop\Practice\Task 4\.

For the first question, I had to determine which Windows service was created to persist the Nessie malware. I opened the Task 4 folder on the Desktop, navigated to Event 4697 with 
timestamp 07/02/2025 7:09:16 PM, expanded it, and saw that the created service was Data Protection Services.
>
> <img width="1129" height="357" alt="13" src="https://github.com/user-attachments/assets/2d5431d3-7be6-4543-9de6-1c27baec0ddf" />
> <img width="722" height="753" alt="14" src="https://github.com/user-attachments/assets/a1c49424-0bb2-416a-8e52-07c1c44c7111" />

> For the next question, I had to determine which scheduled task was created to persist the Troy malware. I navigated to Event 4698 with timestamp 07/02/2025 7:10:09 PM, expanded
it, and discovered that the scheduled task was AmazonSync.
>
> <img width="647" height="720" alt="15" src="https://github.com/user-attachments/assets/c05fd1c6-0b24-45ac-b07c-e7e83012763f" />

> For the last question, I had to retrieve the hidden flag after running the Troy malware. I launched troy.exe, which was stored in the Program Files folder, entered the parent
command line:
C:\Windows\system32\svchost.exe -k netsvcs -p -s Schedule,
then pressed Enter. After doing so, I retrieved the hidden flag:
THM{c2_is_on_schedule!}
>
> <img width="740" height="412" alt="16" src="https://github.com/user-attachments/assets/944ba59f-c66b-4bed-aebe-797605ba83e8" />
> <img width="1032" height="451" alt="17" src="https://github.com/user-attachments/assets/35718f3b-99c6-4a71-a925-0af7c722e170" />
> <img width="1026" height="322" alt="18" src="https://github.com/user-attachments/assets/a4a82016-a960-4017-9617-08a7be384b48" />
> <img width="1104" height="876" alt="19" src="https://github.com/user-attachments/assets/374f3475-4bb0-45e2-8858-69f83eb6cfeb" />

*** Persistence: Run Keys and Startup ***

> In this section, I answered questions related to uncovering newly learned backdoors located at
C:\Users\Administrator\Desktop\Practice\Task 5\.

For the first question, I had to determine the parent process image of the Odin malware. I launched the Task 5 folder on the Desktop, navigated to the Sysmon log, selected Event 1 
with timestamp 07/04/2025 10:16:49 PM, expanded it, and discovered that the parent process image was
C:\Windows\explorer.exe.
>
> <img width="931" height="362" alt="20" src="https://github.com/user-attachments/assets/58fcddc3-1bfc-4c2e-84bb-d02ffa03c337" />
> <img width="956" height="761" alt="21" src="https://github.com/user-attachments/assets/66eecd74-3f45-48cd-ab44-cd6b7c6cc8ea" />

> For the next question, I had to determine the last line that the Odin malware output. I navigated to Event 1 with timestamp 07/04/2025 10:16:49 PM, expanded it, and discovered
that the last line was:
"Done doing bad stuff!"
>
> <img width="866" height="699" alt="22" src="https://github.com/user-attachments/assets/d03a7c54-e922-424a-a273-f34346c46b39" />

> For the last question, I had to retrieve the hidden flag after running the Kitten malware. I located the malware, launched it, and entered the run key basket, which allowed me to
retrieve the flag:
THM{persisting_in_basket!}
>
> <img width="821" height="757" alt="23" src="https://github.com/user-attachments/assets/f00aabea-8cf8-48e5-892a-f95969c5f162" />
> <img width="809" height="390" alt="24" src="https://github.com/user-attachments/assets/4f9efbc6-d73c-4654-944c-afd8964f819b" />
> <img width="930" height="379" alt="25" src="https://github.com/user-attachments/assets/04e9be7d-ac6f-4c99-af46-648b348d7b81" />
> <img width="826" height="408" alt="26" src="https://github.com/user-attachments/assets/64666d89-be30-4643-a5c5-6b387f7ed290" />
> <img width="1019" height="580" alt="27" src="https://github.com/user-attachments/assets/970d00fe-c122-403b-9c74-70d5d95b8e5d" />

--- 

## Reflection

> This lab strengthened my ability to understand how threat actors maintain access to breached Windows hosts.
