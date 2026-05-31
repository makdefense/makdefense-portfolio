# [Advanced Splunk]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Splunk: Setting up a SOC Lab]  
**Date Completed**: [05//2026]

---

## 🧠 Summary

> In this lab,

---

## 🎯 Objectives
- [ ] 

---

## 🧰 Tools Used
- THM AttackBox
- Splunk

---

## 📊 Analysis & Screenshots

*** Linux Deployment ***

> In this section, I was given specific instructions to set up my first SOC Lab. After following the instructions, i was able to access my Splunk SOC Lab using the link:
http://coffely:8000
>
> <img width="1111" height="558" alt="1" src="https://github.com/user-attachments/assets/82fe5df3-e65b-479c-b4d2-3356a2e1f60b" />
> <img width="929" height="324" alt="2" src="https://github.com/user-attachments/assets/aaac8080-fdb5-492a-9ee3-f1756effe670" />

*** Splunk Universal Forwarder ***

> In this section, i then had to set up a forwarder for my SOC Lab. To do this i navigated to the "/home/ubuntu/Downloads/splunk" directory, then entered the command syntax:
tar xvzf splunkforwarder.tgz -C /opt
>
> <img width="1364" height="313" alt="3" src="https://github.com/user-attachments/assets/8b57d9cc-3362-46f9-aba6-c98e0456e48a" />

> After using that command syntax to setup the forwarder, i then used the command syntax:
./splunk start --accept-license
to start the forwarder.
>
> <img width="877" height="132" alt="4" src="https://github.com/user-attachments/assets/0132f52b-d743-476c-9e11-da7702249599" />

> I then had to switch the default port of 8089 to port 8090 so the SOC Lab and forwarder can run simultaneously.
>
> <img width="1024" height="604" alt="5" src="https://github.com/user-attachments/assets/42b10157-bc50-4efd-beb7-4dee1774fc02" />

*** COnfiguring the Forwarder ***

> Moving on to this section, i then had to first set up Splunk configuration by configuring the recieving port to port 9997.
>
> <img width="747" height="395" alt="6" src="https://github.com/user-attachments/assets/ceed98ea-5c6c-4f04-81df-321335cb8dce" />
> <img width="1402" height="531" alt="7" src="https://github.com/user-attachments/assets/32a8d92c-f511-46b7-9d46-e0145d5a655e" />

> I then created an index called "linux_host"
>
> <img width="741" height="608" alt="8" src="https://github.com/user-attachments/assets/e7ee70c5-4f4a-402c-9249-c77a005db069" />
> <img width="436" height="275" alt="9" src="https://github.com/user-attachments/assets/6ae15e9f-539b-42e2-b9c5-5446a8a75c00" />
> <img width="1121" height="993" alt="10" src="https://github.com/user-attachments/assets/a6805a38-0001-4029-b6d0-a874f5bb381c" />

> Moving on i then had to configure the forwarder to make sure data was being sent to the right destination. To do so i used the command syntax:
./splunk add forward-server 10.67.188.176:9997
which basically directed the forwarding to that specific ip address and port.
>
> <img width="1005" height="188" alt="11" src="https://github.com/user-attachments/assets/c2e712a5-e61c-4827-966e-0be61a57bad2" />

> Moving on i then ingested the "syslog" file into Splunk by using the command syntax:
./splunk add monitor /var/log/syslog -index linux_host
I then used the logger utility to rename the log to
"coffely-has-the-best-coffee-in-town"
Then finally to confirm that my log was added to my Splunk SOC lab, i searched using the query:
index = linux_host "coffely-has-the-best-coffee-in-town"
>
> <img width="1119" height="176" alt="12" src="https://github.com/user-attachments/assets/19decc16-1419-465a-ba7b-78d283737ae8" />
> <img width="1205" height="619" alt="13" src="https://github.com/user-attachments/assets/ecf3e567-4069-43a3-a70d-03f9a2449ba2" />

> I then was given a few questions to answer within this section, my first question was to repeat the same steps i did to ingest the "syslog" file into the index, but this time
ingest the "/var/log/auth.log" file into the "linux_host," then figure out the "sourcetype" field. After repeating the steps i did earlier i was able to identify the value in the
"sourcetype" field to be:
auth
>
> <img width="1242" height="407" alt="14" src="https://github.com/user-attachments/assets/96f4e87b-60e9-464c-8e00-4f0e08ec57ff" />
> <img width="1067" height="760" alt="15" src="https://github.com/user-attachments/assets/c79f8e3e-ba60-4796-ba6c-05e08728b169" />

> For the last question of this section, i had to create a new user named analyst using the command adduser analyst, then look at the syslog events generated in Splunk related to
the user creation activity, then figure out the value of the process field when the new user is added. After completing these steps, i was able to identify the value of the
process field when the new user is added to be:
adduser
>
> <img width="726" height="815" alt="16" src="https://github.com/user-attachments/assets/0ad1cc10-c684-42b7-9e3e-e60718cd2e9d" />
> <img width="1061" height="513" alt="17" src="https://github.com/user-attachments/assets/b370b5a6-69de-465a-9528-a0c70d04a516" />
> <img width="1210" height="786" alt="18" src="https://github.com/user-attachments/assets/07a9f09a-dcae-4679-9512-41f62c82dcdb" />

***  ***





















--- 

## Reflection

> This lab strengthened my ability to 
