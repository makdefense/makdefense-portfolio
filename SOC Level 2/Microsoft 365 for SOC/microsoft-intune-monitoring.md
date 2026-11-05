# [Microsoft 365 for SOC]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Microsoft Intune Monitoring]  
**Date Completed**: [11/04/2026]

**Lab Link**: [https://tryhackme.com/room/msintunemonitoring]

---

## 🧠 Summary

> In this lab, I learned how to monitor Microsoft Intune environments and detect potential security threats involving unauthorized device management activities and mass device-wiping
attacks. I explored how attackers can exploit compromised administrative accounts, excessive permissions, and device management capabilities to remotely wipe multiple devices within an
organization. I also gained a deeper understanding of how Security Operations Center (SOC) analysts investigate suspicious Intune activities by analyzing audit logs, monitoring
administrative actions, and identifying unusual device management operations. Additionally, I learned about detection strategies for identifying unauthorized wipe commands, monitoring
changes to administrative privileges, and recognizing indicators of compromise (IOCs) associated with destructive attacks.

---

## 🎯 Objectives

- [ ] Learn Microsoft Intune features and applications
- [ ] Discover the use of Intune by SOC and security teams
- [ ] Explore how Intune is exploited based on a Stryker incident
- [ ] Practice monitoring Intune from Splunk and the host perspective

---


## 🧰 Tools Used
- THM AttackBox
- Splunk

---

## 📊 Analysis & Screenshots

*** Intune Risks: Remote Wipe ***

> For this section, I was tasked with investigating a remote wipe operation performed on a Windows device by analyzing Microsoft Intune logs within Splunk. To begin the investigation, I
set the search time range to All Time and executed the index=intune SPL query to retrieve relevant events. For the first question, I had to identify the unique device ID associated with
the wiped Windows device. Upon further investigation and analysis of the Splunk logs, I was able to determine that the device ID was:

d66b71f3-a644-4392-89b2-d97ba5612356

This finding helped identify the affected device and provided valuable information for tracing the remote wipe activity and investigating potential unauthorized administrative actions 
within the Microsoft Intune environment.
>
> <img width="539" height="423" alt="1" src="https://github.com/user-attachments/assets/0eced9ff-d1ef-4a3d-9e31-8317a1ca557d" />
> <img width="1074" height="1134" alt="14" src="https://github.com/user-attachments/assets/12d07b79-2efc-48e5-b9fb-7438b454af8a" />

> For the next question, I had to identify the hostname of the Windows device that was remotely wiped through Microsoft Intune. Upon further investigation and analysis of the Intune logs
within Splunk, I was able to determine that the hostname of the affected device was LPT-08312. This finding helped establish the identity of the compromised device and provided valuable
information for correlating the remote wipe activity with other security events, allowing for further investigation into potential unauthorized device management operations within the
organization's Microsoft Intune environment.
>
> <img width="1390" height="874" alt="16" src="https://github.com/user-attachments/assets/e505a294-b0bc-4b24-a658-0ead1f143acb" />

> For the next question, I had to identify the IP address from which the administrator initiated the remote wipe operation on the Windows device through Microsoft Intune. Upon further
investigation and analysis of the Intune logs within Splunk, I was able to determine that the source IP address associated with the remote wipe operation was 149.40.62.43. This finding
provided valuable information for tracing the origin of the administrative action, correlating related security events, and investigating whether the remote wipe operation was authorized
or potentially malicious.
>
> <img width="1200" height="674" alt="15" src="https://github.com/user-attachments/assets/4c73a45b-b950-42c5-bc95-a8c7f851c54e" />

*** Intune Risks: Apps & Scripts ***

> Moving on to this section, I was tasked with investigating a script deployment on the device PC-096 by analyzing Microsoft Intune logs within Splunk. Following the investigation, I had
to answer a series of questions related to the suspicious script deployment activity. For the first question, I had to identify the resource ID associated with the deleted Intune script.
Upon further investigation and analysis of the Splunk logs, I was able to determine that the resource ID of the deleted script was:

c0709410-f1e0-4619-ac73-eca347ca1b8b

This finding helped identify the deleted script and provided valuable information for tracing its deployment history, correlating related administrative activities, and investigating 
potential unauthorized script execution within the Microsoft Intune environment.
>
> <img width="1045" height="404" alt="17" src="https://github.com/user-attachments/assets/88f15c93-10ef-40af-8ec9-380bad2541ae" />
> <img width="1105" height="444" alt="18" src="https://github.com/user-attachments/assets/329f6263-5224-4f7c-90ae-b8e2216d09c7" />

> For the next question, I had to determine the approximate date and time when the additional scripts were deployed to the targeted devices within the Microsoft Intune environment. Upon
further investigation and analysis of the Intune logs within Splunk, I was able to identify that the scripts were deployed on March 17, 2026, at approximately 18:57:57. This finding
helped establish a timeline of the suspicious script deployment activity and provided valuable information for correlating related security events, identifying potentially affected
devices, and investigating possible unauthorized administrative actions within the organization's Microsoft Intune environment.
>
> <img width="1268" height="902" alt="19" src="https://github.com/user-attachments/assets/2204bb46-561f-403e-b8a6-ea4f71635836" />

> For the next question, I had to identify the output generated by the script deployed to the targeted devices through Microsoft Intune. Upon further investigation and analysis of the
Intune logs within Splunk, I was able to determine that the script produced the following output:

THM{hello_world_from_intune!}

This finding helped confirm that the deployed script had successfully executed and generated the expected output. Additionally, it provided valuable information for verifying script 
execution, correlating related security events, and investigating potential unauthorized script deployment activities within the organization's Microsoft Intune environment.
>
> <img width="1263" height="607" alt="20" src="https://github.com/user-attachments/assets/4837df4c-4e72-4be9-b5f4-aceaf53ea857" />

---

## Reflection

> This lab strengthened my understanding of endpoint security, Microsoft Intune monitoring, incident response, and the importance of implementing effective security controls to prevent
large-scale device-wiping attacks and protect organizational assets.
