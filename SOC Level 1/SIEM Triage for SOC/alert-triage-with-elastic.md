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













--- 

## Reflection

> This lab strengthened my ability to 
