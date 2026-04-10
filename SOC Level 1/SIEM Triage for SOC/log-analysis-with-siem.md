# [SIEM Triage for SOC]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Log Analysis with SIEM]  
**Date Completed**: [04/09/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of 
---

## 🎯 Objectives
- [ ] 
      
---

## 🧰 Tools Used
- THM AttackBox
- 

---

## 📊 Analysis & Screenshots

*** Windows Logs ***

> In this section, i had to answer a few questions by playing the role of a SOC L1 analyst, and investigate an alert recieved indicating a suspicious network connection using port
5678 on the WIN-105 host. I had to use Splunk for my investigation by using the query: index=task4. For the first question i had to figure out which IP address the connection was
established with. To figure this out i first launched Splunk, then inputted the query: index=task4 to verify the task is in Splunk. After doing so i then entered the full query:

index=task4 ComputerName=WIN-105 DestinationPort=5678
| table Time host User EventType EventCode Image SourceIp SourcePort DestinationIP DestinationPort Message 
After entering this i was able to discover the IP address of "10.10.114.80."
>
> <img width="585" height="381" alt="1" src="https://github.com/user-attachments/assets/23c523d5-66e2-49cd-b071-113d7bd3fcb6" />
> <img width="546" height="295" alt="2" src="https://github.com/user-attachments/assets/b3787c25-f0b4-44b5-8de1-2a5ad607c8e6" />
> <img width="977" height="187" alt="3" src="https://github.com/user-attachments/assets/189a1b33-68da-4214-8e53-7bb2b717b3c1" />
> <img width="765" height="304" alt="4" src="https://github.com/user-attachments/assets/fdf5f102-d9b0-40fd-bb91-f2783a89ea5d" />

> I then discovered the process that initiated the suspicious connection which was "SharePoInt.exe."
>
> <img width="401" height="279" alt="5" src="https://github.com/user-attachments/assets/04ae6963-04e4-4a0e-b705-eaef34000ff5" />

> Then to find the MD5 hash of the malicious process i entered the query:
index=task4 "C:\\Windows\\Temp\\SharePoInt.exe"
Which returned the MD5 of "770D14FFA142F09730B415506249E7D1" in an event.
>
> <img width="596" height="300" alt="6" src="https://github.com/user-attachments/assets/ee20441e-e395-45dc-9009-b55d108a17e7" />
> <img width="616" height="777" alt="7" src="https://github.com/user-attachments/assets/3c668bd1-ff03-4e53-8602-7db91e0a381a" />

> I then discovered the name of the scheduled task that was created on the system in an event which was called "Office365 Install."
>
> <img width="677" height="623" alt="8" src="https://github.com/user-attachments/assets/95bb0432-465d-42da-8700-3bde1789040a" />

*** Linux Logs ***

> Moving onto this section, i had to answer a few questions by again playing the role of a SOC L1 Analyst by investigating an alert indicating possible persistence through the
creation of a new remote-ssh user on an Ubuntu server. For the first question i had to figure out the timestamp of the remote-ssh account creation. I entered the query:
index=task5
| search "remote-ssh"
Which returned the timestamp of 2025-08-12 09:52:57.
>
> <img width="663" height="569" alt="9" src="https://github.com/user-attachments/assets/3ddad69f-0ed9-4171-a0e5-b1de4e8db2b4" />

> I then discovered the user that successfully escalated their privileges to root by entering the query:
index=task5 source="auth.log" *su*
Which returned the user "jack-brown."
>
> <img width="542" height="340" alt="10" src="https://github.com/user-attachments/assets/7d9a0c97-3f9d-4c3f-8d33-269454ab66a6" />
> <img width="1221" height="98" alt="11" src="https://github.com/user-attachments/assets/10ceadd7-150a-4236-b64d-f49a8a907185" />

> I then discovered the source IP address the user successfully logged into the system with by inputting query:
index=task5 "jack-brown" "ssh"
| table _time _raw
Which returned the IP address of "10.14.94.82"
>
> <img width="1428" height="475" alt="12" src="https://github.com/user-attachments/assets/fa09554a-1800-411b-8b8d-a96781d2d932" />

> Prior to the successful login there were 4 failed login attempts according to my investigation.
>
> <img width="1027" height="126" alt="13" src="https://github.com/user-attachments/assets/40c61ab5-11cf-4297-994a-79db24f510ab" />

> I finally discovered whcih port the persistence mechanism configured was connected to by inputting the query:
index=task5 source="syslog" *port*
| table _time _raw
Which returned the port "7654."
>
> <img width="904" height="591" alt="14" src="https://github.com/user-attachments/assets/3617510c-2332-4487-9eb1-8f3c0c748aa8" />

*** Web Application Logs ***

> Moving onto the last section of the room, my task was to investigate the logs of an alert that was indicating a spike in activity on the organization's web server as a SOC L1
Analyst. For the first question i had to figure out which URl path had the highest number of requests. I entered the query: index=task6 to confirm all events, then navigated to the
left, selected the "Method" filter, then "POST," the "uri," which then returned "/wp-login.php" for the URl with the highest reuqests.
>
> <img width="629" height="320" alt="15" src="https://github.com/user-attachments/assets/88cf899f-acb2-475b-a590-d0decf39628e" />
> <img width="875" height="485" alt="16" src="https://github.com/user-attachments/assets/54b7ced7-fd07-4c55-9b1a-12d9ff33a649" />
> <img width="863" height="531" alt="17" src="https://github.com/user-attachments/assets/0747fdac-a2dd-4df1-83ed-49ca8ee45f20" />

> I then discovered the IP address for the source activity to be "10.10.243.134" and the tool the threat actor used which was "WPScan."
>
> <img width="1093" height="124" alt="18" src="https://github.com/user-attachments/assets/af71fe2b-3fc7-4956-b556-061b47016218" />

> Finally i determined the activity was classified as "Brute Force" due to the high count of requests being a total of 583. I figured this out by entering the query:
index="task6" method=POST uri="/wp-login.php"
| bin _time span=5m
| stats values(referer_domain) as referer_domain values(status) as status values(useragent) as UserAgent values(uri_path) as uri_path count by clientip _time
| where count > 25
| table referer_domain clientip UserAgent uri_path count status
>
> <img width="1264" height="403" alt="19" src="https://github.com/user-attachments/assets/9f071d3f-b984-4ab7-8bca-f934f89a052a" />

--- 

## Reflection

> This lab strengthened my ability to 
