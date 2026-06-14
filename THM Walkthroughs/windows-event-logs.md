# [THM Walkthrough]

**TryHackMe Path**: [Walkthrough]  
**Lab Topic**: [Windows Event Logs]  
**Date Completed**: [06/14/2026]

**Lab Link**: [https://tryhackme.com/room/windowseventlogs]

---

## 🧠 Summary

> In this lab, I explored the fundamentals of Windows Event Logs and learned how to query and analyze event data using native Windows logging tools. I gained hands-on experience
navigating different event log categories, understanding the types of information they contain, and identifying key events related to system activity, authentication, and
security monitoring.

Throughout the lab, I worked with tools such as Event Viewer and PowerShell cmdlets like Get-WinEvent to search, filter, and investigate event logs. I also learned how to use 
filtering techniques, XPath queries, and event IDs to efficiently locate relevant events and extract meaningful information from large datasets.

This lab reinforced the importance of Windows Event Logs as a critical source of forensic and security data, improving my ability to investigate system activity, detect 
suspicious behavior, and support incident response efforts in real-world SOC environments.

---

## 🎯 Objectives
- [ ] Complete Windows Event Logs Walkthrough
      
---

## 🧰 Tools Used
- THM AttackBox
- Event Viewer
- Powershell

---

## 📊 Analysis & Screenshots

*** Event Viewer ***

> In this section, I learned how to use Event Viewer to examine Windows events. I also answered several questions by analyzing the Microsoft-Windows-PowerShell/Operational log.
For the first question, I had to determine the Event ID of the earliest recorded event. After conducting further investigation, I identified Event ID 4103 as the earliest
recorded event.
>
> <img width="400" height="161" alt="1" src="https://github.com/user-attachments/assets/0b119eb8-92d0-4479-8b60-d6d72d59c8b5" />
> <img width="803" height="638" alt="2" src="https://github.com/user-attachments/assets/31774cd0-4f32-4a96-9919-f1aabc08339d" />
> <img width="997" height="539" alt="3" src="https://github.com/user-attachments/assets/bdfdad92-798b-47aa-b41d-97c78c8286e3" />
> <img width="911" height="434" alt="4" src="https://github.com/user-attachments/assets/75ec761e-62bd-4716-99e1-5e69df4a6873" />
> <img width="909" height="536" alt="5" src="https://github.com/user-attachments/assets/f56ab063-b93e-4298-8d80-191ffb7b5c6b" />
> <img width="1389" height="382" alt="6" src="https://github.com/user-attachments/assets/c157c3fd-574a-4084-bb42-49dc42d2c8b0" />

> Moving on, I identified the task category for Event ID 4104 as:
Execute a Remote Command
>
> <img width="653" height="236" alt="7" src="https://github.com/user-attachments/assets/7648250a-5d6a-4457-b5b1-8fc2419bbcdc" />

> I then identified the task category for Event ID 800 as:
Pipeline Execution Details
>
> <img width="754" height="308" alt="8" src="https://github.com/user-attachments/assets/ad8a6fed-35bf-4eb6-9154-b93a041e3684" />

*** wevtutil.exe ***

> In this section, I used the wevtutil.exe tool on the VM. I then answered several questions related to its functionality. For the first question, I had to determine how many log
names existed on the machine. To do this, I entered the command:

wevtutil.exe el | Measure-Object

This allowed me to identify a total of 1,071 log names.
>
> <img width="642" height="263" alt="9" src="https://github.com/user-attachments/assets/79225271-4c44-432e-bc37-0ac17c64c3df" />

> I then discovered that the sources that can be read when using the query-events command are:

Event Log, Log File, Structured Query
>
> <img width="815" height="334" alt="10" src="https://github.com/user-attachments/assets/ecb4d805-001e-47e7-8c50-c14ef7eb49bf" />

> The option used to provide a path to a log file is:

/lf
>
> <img width="789" height="414" alt="11" src="https://github.com/user-attachments/assets/ac32b277-be92-4751-85f2-d61ba06a185a" />

> I discovered that the value for /q is:

XPath Query
>
> <img width="560" height="245" alt="12" src="https://github.com/user-attachments/assets/361bccea-c68a-4bdf-ab00-a3718d49a424" />

> Based on the command:

wevtutil qe Application /c:3 /rd /f

I identified the log name as:

Application
>
> <img width="807" height="678" alt="13" src="https://github.com/user-attachments/assets/5868441b-08bd-460d-b143-0e76e77b1e90" />

> I identified that the /rd option is used for:

Event Read Direction
>
> <img width="581" height="271" alt="14" src="https://github.com/user-attachments/assets/27938e0b-6f5e-4afd-a205-44d334f601d8" />

> Finally, I identified that the /c option is used for:

Maximum Number of Events to Read
>
> <img width="684" height="207" alt="15" src="https://github.com/user-attachments/assets/3a5fab0b-2dbf-4664-a206-358c80e0672c" />

*** Get-WinEvent ***

> In this section, I answered several questions related to the PowerShell cmdlet Get-WinEvent. For the first question, I had to identify the log names related to OpenSSH. After
running the command:

Get-WinEvent -ListLog *

I identified the following logs:

OpenSSH/Admin
OpenSSH/Operational
>
> <img width="871" height="246" alt="16" src="https://github.com/user-attachments/assets/fa7c79c7-5b1c-41d6-9e96-3b9233cba1c1" />

> I then identified the name of the third log provider as:

Microsoft-Windows-PowerShell-DesiredStateConfiguration-FileDownloadManager

This was accomplished using the command:

Get-WinEvent -ListProvider *PowerShell*
>
> <img width="1202" height="348" alt="18" src="https://github.com/user-attachments/assets/6f118b7d-60de-41b8-a8bd-2b2607fc8353" />
> <img width="883" height="472" alt="17" src="https://github.com/user-attachments/assets/d3b59979-9c1d-4501-9ca1-2b3c4447bfb9" />

> Moving on, I discovered that a total of 192 event IDs were displayed for the event provider:

Microsoft-Windows-PowerShell

This was determined using the command:

(Get-WinEvent -ListProvider Microsoft-Windows-PowerShell).Events | Format-Table Id, Description
>
> <img width="1175" height="368" alt="19" src="https://github.com/user-attachments/assets/4efe6a4b-6309-4bac-9224-90560782842c" />
> <img width="1133" height="268" alt="20" src="https://github.com/user-attachments/assets/bef8b4be-fa61-43b2-b40c-541c1545a469" />

> To specify the number of events returned, you use:

-MaxEvents

within your PowerShell command syntax.
>
> <img width="1119" height="401" alt="21" src="https://github.com/user-attachments/assets/51eb4166-b2ac-4042-8ed7-ab342e298033" />

> Finally, when using the FilterHashtable parameter and filtering by level, the value for Informational is:

4
>
> <img width="1097" height="428" alt="22" src="https://github.com/user-attachments/assets/a743b7ea-611a-4ea9-82fc-b499ee4cf94a" />
> <img width="1198" height="594" alt="23" src="https://github.com/user-attachments/assets/516bbe60-6c6b-4ca9-abce-85d7e47ca8d3" />

*** XPath Queries ***

> In this section, I used my knowledge of both Get-WinEvent and XPath to answer several questions. For the first question, I had to determine the full query required to find WLMS
events with a System Time of:

2020-12-15T01:09:08.940277500Z

After some trial and error, I determined the full query to be:

Get-WinEvent -LogName Application -FilterXPath '*/System/Provider[@Name="WLMS"] and */System/TimeCreated[@SystemTime="2020-12-15T01:09:08.940277500Z"]'
>
> <img width="1334" height="262" alt="24" src="https://github.com/user-attachments/assets/ffbe4df3-23a0-487f-a474-c49b39092e09" />

> I then used the query:

Get-WinEvent -LogName Security -FilterXPath '*/EventData/Data[@Name="TargetUserName"]="Sam" and */System/EventID=4720'

to locate a user named Sam with Event ID 4720. The query generated an error because the Event ID had been removed from the EVTX file provided in the VM.
>
> <img width="1195" height="230" alt="25" src="https://github.com/user-attachments/assets/8c102675-f8a3-40c2-8a2b-d8e92a6a4b5b" />

> Moving on, I identified the recorded time for Event ID 4724 associated with user Sam as:

12/17/2020 1:57:14 PM

The provider name was identified as:

Microsoft-Windows-Security-Auditing

Again, the Event ID was not displayed because it had been removed from the EVTX file included with the VM.
>
> <img width="1098" height="200" alt="26" src="https://github.com/user-attachments/assets/b0dc888f-d6fc-4c99-8153-8a9c30ad0d93" />

*** Putting theory into practice ***

> For the final practical exercise in this room, I answered a series of questions by investigating the external event log file titled merged.evtx.

For the first question, I had to determine which Event ID was used to detect a PowerShell downgrade attack. After conducting research, I identified the Event ID as:

400
>
> <img width="859" height="423" alt="27" src="https://github.com/user-attachments/assets/9c8bea39-7b34-4c8a-afeb-fa90f7b6fc5f" />
> <img width="512" height="375" alt="28" src="https://github.com/user-attachments/assets/655fdecc-a988-4e0b-997b-5ad79c3d7ed6" />

> Moving on, I discovered that the attack occurred at:

12/18/2020 7:50:33 AM

This was determined because the Host Version changed from 1.0 to 2.0.
>
> <img width="1205" height="801" alt="29" src="https://github.com/user-attachments/assets/6146f16e-5e83-4558-a3bf-03c24bded1bd" />

> I then observed that a log-clearing event had been recorded. The Event Record ID was identified as:

27736
>
> <img width="1172" height="845" alt="30" src="https://github.com/user-attachments/assets/c7a363ee-dd79-4d7b-8ac7-c0a5fb7c52f2" />

> The name of the computer was identified as:

PC01.example.corp
>
> <img width="872" height="373" alt="31" src="https://github.com/user-attachments/assets/3aaf1067-e66d-4848-b14f-59581cce45dc" />

> I then discovered that the name of the first variable within the PowerShell command was:

$Va5w3n8

The date and time the attack occurred was:

8/25/2020 10:09:28 PM
>
> <img width="1349" height="419" alt="32" src="https://github.com/user-attachments/assets/5809356d-b4e8-4e2c-acfb-5917767bd92f" />

> The execution Process ID identified was:

6620
>
> <img width="637" height="353" alt="33" src="https://github.com/user-attachments/assets/c47fb016-1ace-4d81-8590-51c96df3055b" />

> The security group that was enumerated was identified as:

S-1-5-32-544
>
> <img width="639" height="365" alt="34" src="https://github.com/user-attachments/assets/fb329630-e4ef-49d7-b9ae-e80b2acdbd1e" />

--- 

## Reflection

> This lab strengthened my ability to work with Windows Event Logs to investigate system activity and identify important security-related events. I developed a stronger
understanding of how Windows records information across different log categories and how those logs can be used to support monitoring, troubleshooting, and incident response
activities.

I also improved my skills in querying and filtering event data using tools such as Event Viewer and PowerShell. By working with event IDs, filter parameters, and XPath queries, I 
learned how to efficiently locate relevant events and reduce large volumes of log data into actionable information.

Additionally, I gained a better understanding of how event logs can reveal indicators of suspicious activity, such as failed logins, PowerShell execution, log clearing, and other 
system changes. This reinforced the importance of log analysis as a core skill for security analysts and incident responders.

Overall, this lab improved my confidence in navigating and analyzing Windows Event Logs, better preparing me for real-world SOC investigations where accurate log analysis is 
essential for detecting, investigating, and responding to security incidents.
