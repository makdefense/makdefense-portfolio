# [Windows Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Windows Logging for SOC]  
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
- THM 

---

## 📊 Analysis & Screenshots

*** Security Log: Authentication ***

> For this room, I began by answering questions under this section. For the first question, I had to investigate the "Practice-Security.evtx" file on the VM's Desktop, then figure
out which IP performed a brute-force of the THM-PC. To figure this out i first launched the "Practice-Security.evtx" file, then navigated to the top of the "Event Viewer," selected
"View," then "Sort By," then "Event ID." After doing all of this i discovered that the log with the Event ID of 4625 means that it was a failed log in. So upon further investigation
of that specific log i retrieved the IP of "10.10.53.248" that performed the brute-force of the THM-PC.
>
> <img width="716" height="372" alt="1" src="https://github.com/user-attachments/assets/c64454a0-41fb-4481-910f-ae8ddf62bb04" />
> <img width="661" height="311" alt="2" src="https://github.com/user-attachments/assets/16001e43-a7ac-43a9-952b-386549250bbf" />
> <img width="650" height="299" alt="3" src="https://github.com/user-attachments/assets/1f385a44-62a4-4823-883c-9b0ddf6a267e" />

> Moving on to the next question i had to figure out which user has been breached as a result of the attack. Upon further investigation i determined that the user "Administrator" had
been breached.

> For the last question for this section i had to figure out the Logon ID of the malicious RDP login. To figure this out i navigated to the Event with the timestamp of
"5/17/2025 10:53:41 PM" and the Event ID of 4624. I then selected it to investigate further and discovered that the Logon ID was "0x183C36D."
>
> <img width="623" height="240" alt="4" src="https://github.com/user-attachments/assets/e0fdca12-6ad1-46e6-929c-39cfb18c01da" />
> <img width="723" height="414" alt="5" src="https://github.com/user-attachments/assets/2a3a0571-430a-4eec-bb00-2c52e526ab76" />

*** Security Log: User Management ***

> Moving on to this section i had to then answer a few question related to the same "Practice-Security.evtx" file. For the first question i had to figure out which user was created
by the attacker soon after the RDP login. To figure this out i navigated, then selected the Event with the timestamp of "5/17/2025 10:54:59" and Event ID 4722. Upon further
investigation of this Event, i determined that the created user was "svc_sysrestore."
>
> <img width="636" height="172" alt="6" src="https://github.com/user-attachments/assets/89ad034b-5d18-45b3-8d25-a9d45a90f378" />
> <img width="646" height="297" alt="7" src="https://github.com/user-attachments/assets/c71c6122-1ccd-4aac-8c3c-54b0b359000a" />

> For the next question i had to figure out which two privileged groups were the backdoor user added to. To figure this out i navigated, then selected both Events with timestamp
"5/17/2025 10:55:24 PM," and "5/17/2025 10:55:12 PM" with Event ID 4732 respectively. Upon further investigation i discovered that the two privileged groups were 
"Backup Operators, Remote Desktop Users."
>
> <img width="679" height="511" alt="8" src="https://github.com/user-attachments/assets/0a9bbd32-89a2-4f04-889b-c7e19229f580" />
> <img width="708" height="555" alt="9" src="https://github.com/user-attachments/assets/3130ac9e-d2e7-411a-ad62-9433bf537231" />










--- 

## Reflection

> This lab strengthened my ability to detect post-exploitation activity by analyzing logs, filesystem artifacts, and attacker command execution patterns.
