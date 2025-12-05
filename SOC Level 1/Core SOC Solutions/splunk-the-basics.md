# [Core SOC Solutions]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Splunk: The Basics]  
**Date Completed**: [12/05/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding

---

## 🎯 Objectives
- [ ] Understanding the components of Splunk
- [ ] Exploring some available options in Splunk
- [ ] Understanding log ingestion in Splunk
- [ ] Practically ingesting some Logs in Splunk and analyzing them

---

## 🧰 Tools Used
- THM Mozilla FireFox
- THM AttackBox
- THM Splunk
  
---

## 📊 Analysis & Screenshots

*** Connect with the Lab ***

> For this room, I had to upload the data attached to the task and create an index "VPN_Logs" within Splunk. To first do this i had to first connect with the lab by clicking "Start Machine," then wait for the
machine to load, then launch the "AttackBox." After both the target machine loaded for the Splunk program and the AttackBox i then navigated to Mozilla FireFox copied and pasted the Splunk target machine URL
into the input field and pressed "Enter."
> 
> <img width="635" height="203" alt="sp2" src="https://github.com/user-attachments/assets/68c8f8f9-9b29-43fb-baf2-d38c9d46c237" />
> <img width="885" height="365" alt="sp3" src="https://github.com/user-attachments/assets/7a01eca2-a2c9-483e-b824-1e8847d8b88e" />
> <img width="1223" height="369" alt="sp4" src="https://github.com/user-attachments/assets/18639adf-736a-4e9e-9ebe-6056af157a17" />
> <img width="808" height="494" alt="sp1" src="https://github.com/user-attachments/assets/6279d438-3c46-431d-ad51-ce714f7a1635" />
> <img width="1451" height="591" alt="sp5" src="https://github.com/user-attachments/assets/485fd748-85f0-47dc-bf97-a85d18d4fb5a" />

> After reviewing everything i then clicked "submit." After clicking submit i was presented with the total number of events present in the log file which was "2862" which was the answer to the first question.
>
> <img width="1390" height="456" alt="sp6" src="https://github.com/user-attachments/assets/fef55e8e-4eac-4839-a4fe-2faa56a4cade" />
> <img width="1301" height="600" alt="sp7" src="https://github.com/user-attachments/assets/bb665fae-1418-4f4d-a5f0-7f82902139b3" />
> <img width="791" height="450" alt="sp8" src="https://github.com/user-attachments/assets/13fc1bb1-990c-4444-8398-aa9281a88e24" />

> For my next question i had to figure out how many log events are captured by the user Maleena. To figure this out i just went to the top up the Splunk application and inputted the following into the
input field "source="VPNlogs.json" host="ip-10-10-40-195" index="vpn_logs" sourcetype="_json" UserName=Maleena" and saw that following log events were "60."
>
> <img width="776" height="310" alt="sp9" src="https://github.com/user-attachments/assets/674b6a16-e153-414a-aa48-32a227310c7c" />

> For the next question i had to figure out the username associated with the IP address "107.14.182.38." To figure this out i inputted the following into the input field
"source="VPNlogs.json" host="ip-10-10-40-195" index="vpn_logs" sourcetype="-json" Source_ip="107.14.182.38" which returned the username "Smith."
>
> <img width="997" height="600" alt="sp10" src="https://github.com/user-attachments/assets/0e6d512c-61e0-49e2-8934-419bd7aed57a" />

> For the next question i had to figure out the number of events that originated from all countries except France. To do this i enterted the following into the input field
"source="VPNlogs.json" host="ip-10-10-40-195" index="vpn_logs" sourcetype="_json" Source_Country!="France" which resulted in the total number of events to be 2814.
>
> <img width="1008" height="395" alt="sp11" src="https://github.com/user-attachments/assets/22a77d97-ece2-4a06-b5e9-889e2fe96e2a" />

> For the final question i had to figure out how many VPN events were associated with the IP 107.3.206.58. To figure this out i entered the following into the above input field
"source="VPNlogs.json" host="ip-10-10-40-195" index="vpn_logs" sourcetype="j_son" Source_ip"107.3.206.58"
>
> <img width="905" height="401" alt="sp12" src="https://github.com/user-attachments/assets/987a1763-67f0-419b-922d-df251cd93282" />
---

## Reflection

> This lab provided me with knowledge about how SOC analysts use Splunk for log investigations.
