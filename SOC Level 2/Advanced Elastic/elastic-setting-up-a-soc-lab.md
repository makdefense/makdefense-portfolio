# [Advanced Elastic]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Elastic: Setting up a SOC Lab]  
**Date Completed**: [09/13/2026]

**Lab Link**: [https://tryhackme.com/room/elasticlab]

---

## 🧠 Summary

> In this lab, 

---

## 🎯 Objectives
- [ ] 
      
---

## 🧰 Tools Used
- THM AttackBox
- Terminal
- Elastic

---

## 📊 Analysis & Screenshots

*** Deploying Elasticsearch and Kibana ***

> For this section, I first installed Elasticsearch onto my machine by switching to the root user within Terminal using the command:
sudo su
then navigated to the:
/Downloads/elastic directory, and ran the command:
dpkg -i elasticsearch.deb
>
> <img width="871" height="511" alt="1" src="https://github.com/user-attachments/assets/6a97a253-fd32-49ae-83a1-201ab5269edf" />

> I then started elastic using the following commands:
systemctl start elasticsearch
systemctl enable elasticsearch
systemctl status elasticsearch
>
> <img width="1498" height="602" alt="2" src="https://github.com/user-attachments/assets/3e537ea1-63a8-4517-9987-955101d143a0" />

> I then moved on to installing Kibana onto my machine by maintaining my root user privileges then used the command:
dpkg -i kibana.deb
>
> <img width="1043" height="409" alt="3" src="https://github.com/user-attachments/assets/ddb3642e-71fc-4ad8-af8f-bc25ada37bfa" />

> I then made two small additions to the config file "/etc/kibana/kibana.yml" that would later help me with the Fleet server installation.
>
> <img width="1095" height="207" alt="4" src="https://github.com/user-attachments/assets/b1edb1c8-0167-467b-ac5d-daaeeed8c9fa" />
> <img width="1148" height="485" alt="5" src="https://github.com/user-attachments/assets/4f91aba7-e7b0-4d06-9b58-19d291756670" />

> I then started kibana using the following commands:
systemctl start kibana
systemctl enable kibana
systemctl status kibana
>
> <img width="1340" height="485" alt="6" src="https://github.com/user-attachments/assets/c2527e5e-b202-48b5-8a09-bc41e70820ab" />

> I then accessed the UI by navigating to the link:
http://localhost:5601/
>
> <img width="1114" height="395" alt="7" src="https://github.com/user-attachments/assets/a9d8ae57-3293-4d6b-9a64-7977bfa3bcb4" />

> I then created an enrollment token and verification code within Terminal that would be used to complete the setup of Elastic and Kibana.
>
> <img width="1505" height="385" alt="8" src="https://github.com/user-attachments/assets/b2448240-4629-4793-ae90-786af86dcd80" />
> <img width="913" height="661" alt="9" src="https://github.com/user-attachments/assets/b5785c59-c447-4129-a36f-e6a726daeb5f" />
> <img width="853" height="692" alt="10" src="https://github.com/user-attachments/assets/d5d2ce0f-95ab-4a32-ba04-cf5f5a429b20" />

> After getting my token, verification code, and following the prompts to complete setup, I then had to reset the password for the user to login to elastic. I did this by using the
command:
/usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic
>
> <img width="1210" height="388" alt="11" src="https://github.com/user-attachments/assets/748818b7-b3e9-46a8-89a6-3e798ee94d73" />
> <img width="725" height="547" alt="12" src="https://github.com/user-attachments/assets/47dab610-7fb6-4b9c-a97b-491224688998" />

> I was then able to access Kibana, which led me to discover the name of the first section listed within the menu to be:
Analytics
>
> <img width="510" height="395" alt="13" src="https://github.com/user-attachments/assets/4537f322-a7bc-4ab1-8ed9-2713bd7883ae" />

*** Deploying Fleet Server and Elastic Agent ***

> Moving on, i then began setting up the Fleet server.
>
> <img width="490" height="351" alt="14" src="https://github.com/user-attachments/assets/12476544-590f-40c1-a8dc-7a22b6df62e2" />
> <img width="867" height="587" alt="15" src="https://github.com/user-attachments/assets/b94298b9-bae3-40b1-850b-ac93c0d8a011" />
> <img width="801" height="773" alt="16" src="https://github.com/user-attachments/assets/31d29ff8-daba-4a2f-8220-7d522f6032ad" />
> <img width="831" height="576" alt="17" src="https://github.com/user-attachments/assets/31b25505-42e6-4cc6-b591-6f00638f4f00" />

> I then used a modified command to complete installation of Fleet server.
>
> <img width="881" height="777" alt="18" src="https://github.com/user-attachments/assets/5edf27f0-bad0-4a35-b23b-eb61e6340124" />
> <img width="1504" height="388" alt="19" src="https://github.com/user-attachments/assets/c816d77b-bc7a-40b0-9a83-ad1c885fae9a" />
> <img width="1513" height="682" alt="20" src="https://github.com/user-attachments/assets/58bc56c6-03cb-42f5-837c-c678c8704d32" />
<img width="713" height="306" alt="21" src="https://github.com/user-attachments/assets/71157798-c261-4374-b222-acf4bc43ede5" />

> I then confirmed log ingestion by navigating to the:
logs-*
>
> <img width="485" height="486" alt="22" src="https://github.com/user-attachments/assets/0d7020c1-8580-42e3-b524-2f10b20a1010" />
> <img width="286" height="249" alt="23" src="https://github.com/user-attachments/assets/5212d246-c76b-427c-b17b-64db42163489" />

> After doing this setup, i then had to answer a set of questions. For the first question i figured out that the name of the default configuration used to collect system metrics and
log data from your host is:
System
>
> <img width="1058" height="246" alt="23 1" src="https://github.com/user-attachments/assets/1521e481-2012-4677-ad60-40568a3b8485" />

> Next i then had to create a new user using:
useradd testuser
within the VM terminal, then navigate back to Discover within Kibana, enter the query:
process.name: "useradd"
then figure out the "event.dataset" field value associated log, which was validated to be:
system.auth
>
> <img width="1076" height="71" alt="23 2" src="https://github.com/user-attachments/assets/d85155ea-9890-48dd-96b2-3cbf0ffae02e" />
> <img width="1031" height="710" alt="23 3" src="https://github.com/user-attachments/assets/5a358cb8-a40a-4200-86c4-fe1854049bb2" />

> For the next question, i then had to create an event by first using the command:
gpasswd -a testuser sudo
within the VM terminal. This basically adds "testuser" to the sudoer group. I then navigated back to Discover, entered the query:
process.name: "gpasswd"
then selected the "message" field which then revealed the full value for the event i created to be:
user testuser added by root to group sudo
>
> <img width="1078" height="93" alt="23 4" src="https://github.com/user-attachments/assets/7fab06bd-9178-45e9-a2fc-4400e699f90b" />
> <img width="1314" height="603" alt="23 5" src="https://github.com/user-attachments/assets/d0e2a01d-869f-4536-8282-a3cac4c7f227" />




























--- 

## Reflection

> This lab strengthened my ability to 
I also improved my ability to work with structured data and identify patterns that may be useful for security analysis, threat hunting, and incident response. This lab reinforced 
the importance of writing precise queries when working with large amounts of log data, especially in a SOC environment where speed and accuracy are important.
