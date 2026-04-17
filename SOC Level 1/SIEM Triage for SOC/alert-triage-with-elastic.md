# [SIEM Triage for SOC]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Alert Triage With Elastic]  
**Date Completed**: [04//2026]

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

*** Scenario Briefing ***

> In this section, i had to answer a few questions related to using Kibana. For the first question i had to figure out how many logs were available for analysis after inputting the
query:
_index:weblogs
then setting the time range to "Entire data range." After doing so i was able to retrieve a total of 1467 logs.
>
> <img width="626" height="562" alt="1" src="https://github.com/user-attachments/assets/51874b95-0ce7-469f-b8e7-706f6a0bc6d9" />
> <img width="625" height="468" alt="2" src="https://github.com/user-attachments/assets/c814df30-0318-4466-a808-14c994fa28ed" />

> I then figured out the field value for the client.ip in weblogs index by navigating to the left then selecting "client.ip" for the selected fields. This returned the IP address
of 203.0.113.55.
>
> <img width="662" height="274" alt="3" src="https://github.com/user-attachments/assets/7e3e0188-4ecc-4e78-89ff-45fc13225868" />
> <img width="1758" height="194" alt="4" src="https://github.com/user-attachments/assets/9c89df50-9882-48ce-b03a-79c0451ba69d" />

*** Investigating Web Attacks ***

> Moving on to this section, i had to answer questions based on an alert with the IP "203.0.113.55" and POST requests made to the page proxyLogon.ecp. For the first question i had
to figure out how many POST requests did the IP address 203.0.113.55 make to proxyLogon.ecp. To figure this out i entered the query:
_index:weblogs and client.ip:203.0.113.55 and http.request.method:POST
After submitting the query i was able to retrieve 3 POST requests.
>
> <img width="1097" height="214" alt="5" src="https://github.com/user-attachments/assets/585646ea-e330-480b-a6b3-df749ffb3f16" />
> <img width="2048" height="456" alt="6" src="https://github.com/user-attachments/assets/f1ab3000-692a-47b1-9cc9-4af510b6ca41" />

> I then discovered the user.agent that was paired with the 203.0.113.55 IP address that made the POST requests to be "python-requests/2.25.1".
>
> <img width="1037" height="217" alt="7" src="https://github.com/user-attachments/assets/b99275d0-bea7-42c7-9c19-8a8a5bb199d3" />

> I then had to answer a few questions based on another alert that occured seven minutes after the previous alert. I had to figure out how many logs contain the cmd= query parameter
in the url.path field. To figure this out i inputted the query:
_index:weblogs and client.ip:203.0.113.55 and http.request.method:GET and errorEE.aspx
After doing so i was able to retrieve a total of 20 logs.
>
> <img width="1224" height="378" alt="8" src="https://github.com/user-attachments/assets/a394c7b7-6aa4-4dc6-befe-71fb0ce4632d" />
> <img width="1136" height="262" alt="9" src="https://github.com/user-attachments/assets/a4960c96-70b7-4eef-ba5f-6571b57f8329" />

> I then figured out the command that was utilizing errorEE.aspx on Jul 20, 2025 @ 04:45:50.000 by adding client.ip, user.agent, http.request.method, url.path, and
http.response.status_code for the selected fields. This returned the command "hostname."
>
> <img width="1663" height="132" alt="10" src="https://github.com/user-attachments/assets/da942138-4010-485e-bfcb-e2b655c3ad37" />

*** Uncovering Account Activity ***

> For this section i had to answer questions based on an alert titled "Administrator Access Outside of Business Hours." For the first question i had to figure out the
"winlog.record_id" of the Administrator 4624 logon event. To figure this out i inputted the query:
@timestamp >= "2025-07-20T05:11:22" and winlog.event_id:4624 and host.name:winserv2019.some.corp and winlog.event_data.TargetUserName:Administrator
then added 5 fields to construct a table. The 5 fields were winlog.event_id, host.name, winlog.event_data.TargetUserName, winlog.logon.type, and winlog.event_data.IpAddress.
After doing so i was able to retrieve the "winlog.record_id" of 17166.
>
> <img width="2048" height="530" alt="11" src="https://github.com/user-attachments/assets/44221128-7676-4a11-8630-eaa9990f1df4" />

> I then retrieved the "process.pid" of the Sysmon 1 event that occurred on "Jul 20, 2025 @ 05:11:27.996." To get this i inputted the query:
"@timestamp >= "2025-07-20T05:11:22" and winlog.event_id:1 and user.name:Administrator"
then added 3 fields to construct a table. The 3 fields were user.name, process.parent.name, and process.command_line. After doing this i retrieved the "process.pid" of "964."
>
> <img width="1142" height="357" alt="12" src="https://github.com/user-attachments/assets/868aafae-052b-418a-8346-f70ff3c037f5" />
> <img width="1798" height="145" alt="13" src="https://github.com/user-attachments/assets/d4e76966-a93a-4e56-9f0e-61b89dbc7345" />

> For the last two questions of this section i had to answer questions based on an alert titled "New User Account Created." For the first question i had to figure out the
"winlog.event_id" for the new user account being created. To figure this out i inputted the query:
@timestamp >= "2025-07-20T05:13:10.000" and winlog.channel:Security and winlog.task:User Account Management
then added 3 fields to construct a table. The 3 fields were winlog.event_id, winlog.task, and message. After doing this i was able to retrieve the "winlog.event_id" of "4720."
>
> <img width="1338" height="495" alt="14" src="https://github.com/user-attachments/assets/36c11027-eba4-43c1-855b-4f6a15b830ee" />

> I then was able to retrieve the name of the new user account which was "svc_backup" by expanding the message.
>
> <img width="578" height="430" alt="15" src="https://github.com/user-attachments/assets/1b498d9c-5b9f-4fbc-952a-44f9791d1d50" />

*** Exposing Command Execution ***

> Moving on to the last section of the room, i had to answer questions based on an alert titled "Unusual Command-Line Behavior: Privilege Changes." For the first question i had to
figure out what command did the attacker use to add the new account to the "Remote Desktop Users" group. To figure this out i inputted the query:
@timestamp >= "2025-07-20T05:13:15" and process.parent.name:cmd.exe and user.name:Administrator
then added process.command_line, process.name, and process.parent.name as columns. After doing so i was able to retrieve the command:
net localgroup "Remote Desktop Users" svc_backup /add
>
> <img width="1301" height="584" alt="16" src="https://github.com/user-attachments/assets/743942c4-69e6-4f51-aa88-5756a63c4080" />

> I then retrieved the "winlog.record_id" of the "4732" Security Event when the attacker added the user to the Administrator group by inputting the query:
@timestamp >= "2025-07-20T05:13:15" and (winlog.event_id:4732 or process.parent.name:cmd.exe)
then adding "winlog.record_id" as a column. The "winlog.record_id" was "17254."
>
> <img width="1220" height="385" alt="17" src="https://github.com/user-attachments/assets/ee903d9c-f0af-4527-9e5e-3ed85d3c7370" />
> <img width="1589" height="169" alt="18" src="https://github.com/user-attachments/assets/ffa19113-b779-43c1-920e-c0b822b36079" />

> For the second to last question i retrieved the PowerShell command the attacker tried to run on "Jul 20, 2025 @ 05:16:14.628" by inputting the query:
@timestamp >= "2025-07-20T05:13:15" and event.module:powershell and event.code:4104
then adding the "powershell.file.script_block_text" field as a column. The PowerShell command retrieved was "net group "Domain Admins" /domain."
>
> <img width="1262" height="354" alt="19" src="https://github.com/user-attachments/assets/d2f40dec-2460-4a6b-9ad4-32e225589f6c" />
> <img width="1748" height="250" alt="20" src="https://github.com/user-attachments/assets/7249fd85-90d3-45e7-b067-5ff768aaa563" />

> Finanly i retrieved the name of the archive the attacker created using the "Rar.exe" executable by inputting the query:
process.name: "Rar.exe"
The name of the archive retrieved was "finance_it_archive.rar."
>
> <img width="1247" height="850" alt="21" src="https://github.com/user-attachments/assets/b852c0bb-8e85-45a1-8335-6c21391d811d" />
























--- 

## Reflection

> This lab strengthened my ability to 
