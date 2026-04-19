# [SIEM Triage for SOC]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Benign]  
**Date Completed**: [04/19/2026]

---

## 🧠 Summary

> In this lab, I learned how to investigate a compromised host using Splunk.

---

## 🎯 Objectives
- [ ] Complete Challenge Room
      
---

## 🧰 Tools Used
- THM AttackBox
- Splunk

---

## 📊 Analysis & Screenshots

*** Scenario: Identify and Investigate an Infected Host ***

> In this room, I used the logs ingested into the index "win_eventlogs" to conduct an investigation on a compromised host from the HR department. For the first question, I had to determine how many logs were ingested during the month of March 2022. To do this, I launched the Splunk application using the given IP address, then entered the query:
>  
> "index=win_eventlogs"
>  
> which returned "13959."
>
> <img width="722" height="395" alt="1" src="https://github.com/user-attachments/assets/9ce3191b-c3f5-4300-a4ce-8e1a57668fc6" />
> <img width="643" height="416" alt="2" src="https://github.com/user-attachments/assets/cbb22c76-ed86-43be-84b6-1ed4d3ec1d9c" />

> I then identified an imposter account in the logs as "Amel1a."
>
> <img width="1035" height="566" alt="3" src="https://github.com/user-attachments/assets/a735cc8a-54f8-4e62-b551-32fe20f19771" />
> <img width="1022" height="311" alt="4" src="https://github.com/user-attachments/assets/199f86b5-d22a-48fa-a19e-cadf31c8f6f6" />
> <img width="1458" height="795" alt="5" src="https://github.com/user-attachments/assets/192e52a1-5c28-4d5f-9235-1c3e67ac76b6" />

> Moving on to the next question, I observed that "Chris.fort" from the HR department was running scheduled tasks.
>
> <img width="1344" height="809" alt="6" src="https://github.com/user-attachments/assets/34e7c9be-42f9-4257-842c-76a62c992507" />

> I then identified the user "haroon" from the HR department as having executed a system process (LOLBIN) to download a payload from a file-sharing host. The system process used to
download the payload from the internet in order to bypass security controls was "certutil.exe."
>
> <img width="1203" height="799" alt="7" src="https://github.com/user-attachments/assets/c3cde2a8-40bc-4fc8-b324-bd3bb6779c6e" />
> <img width="1080" height="688" alt="11" src="https://github.com/user-attachments/assets/9d47b027-645c-46a2-9d78-8c11cbea06a6" />

> I then identified the date this binary was executed on the infected host as "2022-03-04."
>
> <img width="939" height="539" alt="8" src="https://github.com/user-attachments/assets/40693ad8-a523-417e-855f-5b67d79a236b" />

> The third-party site accessed to download the malicious payload was identified as "controlc.com."
>
> <img width="338" height="179" alt="9" src="https://github.com/user-attachments/assets/ab4fd842-cbcd-4796-913d-1b86bc6d460a" />

> The file saved on the host machine from the C2 server during the post-exploitation phase was "benign.exe."
>
> <img width="590" height="306" alt="10" src="https://github.com/user-attachments/assets/fe8f75d9-5518-486c-8927-980a37774518" />

> The suspicious file downloaded from the C2 server contained malicious content with the pattern THM{......}; the pattern identified was "THM{KJ&*H^B0}." Finally, the URL that the
infected host connected to was "https://controlc.com/e4d11035."
>
> <img width="399" height="353" alt="12" src="https://github.com/user-attachments/assets/78e1dc0c-e308-4836-941f-33ab629861b0" />

--- 

## Reflection

> This lab strengthened my ability to use Splunk to investigate compromised hosts.
