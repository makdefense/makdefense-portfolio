# [Linux Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Linux Logging for SOC]  
**Date Completed**: [02/23/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding key Linux log sources and how to use them in SOC triage. Logs provide the evidence needed to detect, investigate, and
respond to security incidents. Knowing how to analyze them helps analysts quickly determine whether activity is malicious, assess severity, and take appropriate action. This
skill builds real investigative ability and is essential for cybersecurity professionals, especially SOC analysts.

---

## 🎯 Objectives
- [ ] Explore authentication, runtime, and system logs on Linux
- [ ] Learn the commands and pitfalls when working with logs
- [ ] Uncover how tools like auditd monitor and report the events
- [ ] Practice every learned log source in the attached VM
      
---

## 🧰 Tools Used
- THM Attackbox

  
---

## 📊 Analysis & Screenshots

*** Working With Text Logs ***

> In this section, I answered several questions using the /var/log/syslog file on the attached VM. For the first question, I had to determine which time server domain the VM
contacted to synchronize its time. To do this, I launched the attached VM and entered the command:

cat /var/log/syslog | grep timesync

After pressing Enter, I was able to retrieve the time server domain: ntp.ubuntu.com.
>
> <img width="1349" height="287" alt="1" src="https://github.com/user-attachments/assets/63b07a5e-65a4-4887-9411-a41fb56e1c72" />

> For the last question in this section, I had to identify the kernel message from Yama in /var/log/syslog. To find this, I entered:

grep -i yama /var/log/syslog

After pressing Enter, I retrieved the kernel message: "Becoming mindful."
>
> <img width="1252" height="272" alt="2" src="https://github.com/user-attachments/assets/bc83571c-3d8c-4f98-9494-2ab9279a690b" />

*** Authentication Logs ***

> In this section, I answered questions using the /var/log/auth.log file. For the first question, I needed to identify which IP address failed to log in to multiple user accounts
via SSH. To find this, I entered:

cat /var/log/auth.log | grep 'sshd' | grep -E 'Accepted|Failed'

After executing the command, I identified the IP address: 10.14.94.82.
>
> <img width="1356" height="404" alt="3" src="https://github.com/user-attachments/assets/48966abb-f179-4680-9d10-81a28e2406fb" />

> For the final question in this section, I needed to determine which user was created and added to the sudo group. To do this, I ran:

cat /var/log/auth.log | grep -E '(passwd|useradd|usermod|userdel)\['

After executing the command, I identified the created user as: xerxes.
>
> <img width="1413" height="233" alt="4" src="https://github.com/user-attachments/assets/d96a94b3-59b4-4d1c-ace9-6fae9aabfd81" />

*** Common Linux Logs ***

> In this section, I answered the first question using the VM’s package manager logs. I needed to determine which version of unzip was installed. To do this, I entered:

cat /var/log/dpkg.log

After executing the command, I identified the installed version as: 6.0-28ubuntu4.1.
>
> <img width="978" height="252" alt="5" src="https://github.com/user-attachments/assets/19213fec-1c1a-4315-9b4a-1b673004a553" />

> For the next question, I had to find a hidden flag within one of the users’ bash history files. To do this, I entered:

sudo grep -i 'THM{' /root/bash/.bash_history

After running the command, I retrieved the hidden flag: THM{note_to_remember}.
>
> <img width="796" height="100" alt="6" src="https://github.com/user-attachments/assets/e6c55157-a058-4962-bb46-3c80864cd646" />

*** Using Auditd***

> In this section, I investigated the file secret.thm to determine when it was first opened. To do this, I entered:

ausearch -i -k file_thmsecret

After executing the command, I discovered that the file was first opened on 08/13/25 at 18:36:54.
>
> <img width="1157" height="508" alt="7" src="https://github.com/user-attachments/assets/f4fb72e0-8593-43f4-a25f-b413692efe4d" />

> Next, I needed to identify the original file name downloaded from GitHub using wget. To do this, I entered:

ausearch -i -k proc_wget

After executing the command, I discovered that the downloaded file name was:
naabu_2.3.5_linux_amd64.zip
>
> <img width="1499" height="858" alt="8" src="https://github.com/user-attachments/assets/78f2e2e5-5edd-47f8-8c19-a4fbabfd320b" />

> For the final question, I had to determine the network range scanned using the downloaded tool. To find this, I entered:

ausearch -i | grep naabu

After executing the command, I identified the scanned network range as:
192.168.50.0/24
>
> <img width="1087" height="365" alt="9" src="https://github.com/user-attachments/assets/de3b1358-cdcf-4eaf-b9b7-2b84bf71400c" />

--- 

## Reflection

> This lab strengthened my ability to explore key Linux log sources and use them effectively during SOC triage.
