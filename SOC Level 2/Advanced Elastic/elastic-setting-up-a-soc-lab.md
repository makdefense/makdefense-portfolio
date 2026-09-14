# [Advanced Elastic]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Elastic: Setting up a SOC Lab]  
**Date Completed**: [09/13/2026]

**Lab Link**: [https://tryhackme.com/room/elasticlab]

---

## 🧠 Summary

> In this lab, I set up a Security Operations Center (SOC) environment using Elasticsearch, Kibana, and Fleet Server. I configured Elasticsearch to store and process security data, used
Kibana to provide a centralized interface for monitoring and analyzing information, and deployed Fleet Server to manage Elastic Agents from a central location. This lab helped me
understand how the different components of the Elastic Stack work together to support security monitoring, log collection, endpoint management, and SOC operations. It also gave me hands-
on experience building the foundation of a centralized environment that can be used for threat detection, investigation, and security analysis.


---

## 🎯 Objectives
- [ ] Understand the core components of the Elastic Stack
- [ ] Install and configure an Elastic Stack deployment
- [ ] Ingest, parse, and search log data from multiple sources
- [ ] Build dashboards and visualizations to analyze log data
      
---

## 🧰 Tools Used
- THM AttackBox
- Terminal
- Elastic
- Kibana

---

## 📊 Analysis & Screenshots

*** Deploying Elasticsearch and Kibana ***

> For this section, I first installed Elasticsearch on my machine by switching to the root user within the Terminal using the following command:

sudo su

I then navigated to the /Downloads/elastic directory and ran the following command:

dpkg -i elasticsearch.deb
>
> <img width="871" height="511" alt="1" src="https://github.com/user-attachments/assets/6a97a253-fd32-49ae-83a1-201ab5269edf" />

> I then started elastic using the following commands:
systemctl start elasticsearch
systemctl enable elasticsearch
systemctl status elasticsearch
>
> <img width="1498" height="602" alt="2" src="https://github.com/user-attachments/assets/3e537ea1-63a8-4517-9987-955101d143a0" />

> I then moved on to installing Kibana on my machine. While maintaining root user privileges, I used the following command:
dpkg -i kibana.deb
>
> <img width="1043" height="409" alt="3" src="https://github.com/user-attachments/assets/ddb3642e-71fc-4ad8-af8f-bc25ada37bfa" />

> I then made two small additions to the /etc/kibana/kibana.yml configuration file, which would later help with the Fleet Server installation.
>
> <img width="1095" height="207" alt="4" src="https://github.com/user-attachments/assets/b1edb1c8-0167-467b-ac5d-daaeeed8c9fa" />
> <img width="1148" height="485" alt="5" src="https://github.com/user-attachments/assets/4f91aba7-e7b0-4d06-9b58-19d291756670" />

> I then started kibana using the following commands:
systemctl start kibana
systemctl enable kibana
systemctl status kibana
>
> <img width="1340" height="485" alt="6" src="https://github.com/user-attachments/assets/c2527e5e-b202-48b5-8a09-bc41e70820ab" />

> I then accessed the Kibana user interface by navigating to the following link:
http://localhost:5601/
>
> <img width="1114" height="395" alt="7" src="https://github.com/user-attachments/assets/a9d8ae57-3293-4d6b-9a64-7977bfa3bcb4" />

> I then created an enrollment token and verification code within the Terminal, which were used to complete the setup of Elasticsearch and Kibana.
>
> <img width="1505" height="385" alt="8" src="https://github.com/user-attachments/assets/b2448240-4629-4793-ae90-786af86dcd80" />
> <img width="913" height="661" alt="9" src="https://github.com/user-attachments/assets/b5785c59-c447-4129-a36f-e6a726daeb5f" />
> <img width="853" height="692" alt="10" src="https://github.com/user-attachments/assets/d5d2ce0f-95ab-4a32-ba04-cf5f5a429b20" />

> After obtaining my enrollment token and verification code and following the prompts to complete the setup, I then had to reset the password for the user account used to log in to
Elastic. I did this by using the following command:
/usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic
>
> <img width="1210" height="388" alt="11" src="https://github.com/user-attachments/assets/748818b7-b3e9-46a8-89a6-3e798ee94d73" />
> <img width="725" height="547" alt="12" src="https://github.com/user-attachments/assets/47dab610-7fb6-4b9c-a97b-491224688998" />

> I was then able to access Kibana, where I discovered that the name of the first section listed within the menu was Analytics.
>
> <img width="510" height="395" alt="13" src="https://github.com/user-attachments/assets/4537f322-a7bc-4ab1-8ed9-2713bd7883ae" />

*** Deploying Fleet Server and Elastic Agent ***

> Moving on, I then began setting up the Fleet Server.
>
> <img width="490" height="351" alt="14" src="https://github.com/user-attachments/assets/12476544-590f-40c1-a8dc-7a22b6df62e2" />
> <img width="867" height="587" alt="15" src="https://github.com/user-attachments/assets/b94298b9-bae3-40b1-850b-ac93c0d8a011" />
> <img width="801" height="773" alt="16" src="https://github.com/user-attachments/assets/31d29ff8-daba-4a2f-8220-7d522f6032ad" />
> <img width="831" height="576" alt="17" src="https://github.com/user-attachments/assets/31b25505-42e6-4cc6-b591-6f00638f4f00" />

> I then used a modified command to complete the installation of Fleet Server.
>
> <img width="881" height="777" alt="18" src="https://github.com/user-attachments/assets/5edf27f0-bad0-4a35-b23b-eb61e6340124" />
> <img width="1504" height="388" alt="19" src="https://github.com/user-attachments/assets/c816d77b-bc7a-40b0-9a83-ad1c885fae9a" />
> <img width="1513" height="682" alt="20" src="https://github.com/user-attachments/assets/58bc56c6-03cb-42f5-837c-c678c8704d32" />
<img width="713" height="306" alt="21" src="https://github.com/user-attachments/assets/71157798-c261-4374-b222-acf4bc43ede5" />

> I then confirmed that logs were being ingested by navigating to the logs-* data view.
>
> <img width="485" height="486" alt="22" src="https://github.com/user-attachments/assets/0d7020c1-8580-42e3-b524-2f10b20a1010" />
> <img width="286" height="249" alt="23" src="https://github.com/user-attachments/assets/5212d246-c76b-427c-b17b-64db42163489" />

> After completing the setup, I then had to answer a set of questions. For the first question, I determined that the name of the default configuration used to collect system metrics and
log data from the host is System.
>
> <img width="1058" height="246" alt="23 1" src="https://github.com/user-attachments/assets/1521e481-2012-4677-ad60-40568a3b8485" />

> Next, I had to create a new user within the VM Terminal using the following command:

useradd testuser

I then navigated back to Discover within Kibana and entered the following query:

process.name: "useradd"

From there, I identified the event.dataset field value associated with the log, which was validated as:

system.auth
>
> <img width="1076" height="71" alt="23 2" src="https://github.com/user-attachments/assets/d85155ea-9890-48dd-96b2-3cbf0ffae02e" />
> <img width="1031" height="710" alt="23 3" src="https://github.com/user-attachments/assets/5a358cb8-a40a-4200-86c4-fe1854049bb2" />

> For the next question, I had to create an event by first using the following command within the VM Terminal:

gpasswd -a testuser sudo

This command adds testuser to the sudo group. I then navigated back to Discover in Kibana and entered the following query:

process.name: "gpasswd"

I then selected the message field, which revealed the full value of the event I created:

user testuser added by root to group sudo
>
> <img width="1078" height="93" alt="23 4" src="https://github.com/user-attachments/assets/7fab06bd-9178-45e9-a2fc-4400e699f90b" />
> <img width="1314" height="603" alt="23 5" src="https://github.com/user-attachments/assets/d0e2a01d-869f-4536-8282-a3cac4c7f227" />

*** Integrating Apache Web Logs ***

> Moving on to this section, I then had to ingest Apache web logs. First, I navigated to a specific website and browsed it for a short period of time. I then returned to the VM Terminal
and entered the following command:

tail /var/log/apache2/access.log

After running this command, I was able to view the web activity generated from my earlier browsing session.
>
> <img width="629" height="206" alt="24" src="https://github.com/user-attachments/assets/b16a432f-1955-4fb5-9f23-66773cf8d114" />
> <img width="750" height="753" alt="25" src="https://github.com/user-attachments/assets/9f1117a0-937c-41d1-bb0f-7a8b8ff843a9" />
> <img width="1511" height="296" alt="26" src="https://github.com/user-attachments/assets/ff2702ec-5ab9-491d-a199-73bc7d7be8f8" />

> I then moved on to Elastic Integrations to begin ingesting Apache web logs.
>
> <img width="550" height="395" alt="27" src="https://github.com/user-attachments/assets/996efbe7-b85b-424f-9b6d-abcfab37e9bc" />
> <img width="1380" height="419" alt="28" src="https://github.com/user-attachments/assets/d43d0a42-887f-4560-9460-2d2b6e86921d" />
> <img width="1306" height="798" alt="29" src="https://github.com/user-attachments/assets/5ba0b068-83ca-4e7e-8684-2754bc51c37b" />
> <img width="1012" height="505" alt="30" src="https://github.com/user-attachments/assets/fd0ea5c4-40c8-4562-ae0d-2cac75e9e147" />
> <img width="1497" height="478" alt="31" src="https://github.com/user-attachments/assets/9be4edc1-8ac7-4516-8000-7aa0f8d4ebcd" />

> After completing the steps to ingest the Apache web logs into Elastic, I confirmed that the logs were being ingested by using the following query within the logs-* data view:

event.module: "apache"
>
> <img width="836" height="411" alt="32" src="https://github.com/user-attachments/assets/4bd6b57c-b47c-42cc-a79d-1760bc3405af" />

> I then had to answer a few questions. For the first question, I identified the event.dataset value associated with the Apache access logs as:

apache.access
>
> <img width="1208" height="654" alt="33" src="https://github.com/user-attachments/assets/b781fad3-720c-4412-bbb0-69feff4f1422" />

> For the final question, I navigated back to the website I had been browsing earlier and added /secret.html to the end of the URL in the input field. I then returned to Kibana and
analyzed the corresponding log entry, where I discovered the hidden flag value under the user_agent.original field:

THM{access_log_secrets!}
>
> <img width="1179" height="761" alt="34" src="https://github.com/user-attachments/assets/8dbb696f-b307-46eb-8313-ca6cd53cab20" />
> <img width="1280" height="589" alt="35" src="https://github.com/user-attachments/assets/1ee43988-66b3-40f5-814a-7cd01c33c7df" />

*** Managing Custom Log Types ***

> Moving on to this section, I was tasked with ingesting custom VPN logs into Elastic. To begin the setup, I first navigated to the /scripts directory using the VM Terminal and then ran
the following Python script:

python3 /home/ubuntu/Downloads/scripts/vpnlog.py

I then used the following command to view the generated VPN logs:

tail /var/log/vpnlog
>
> <img width="1109" height="197" alt="36" src="https://github.com/user-attachments/assets/5d4f1d91-8198-445e-80c1-caa37f18fc9c" />
> <img width="889" height="302" alt="37" src="https://github.com/user-attachments/assets/b701ab8e-59ba-4fd4-80f0-cc2134dbcb04" />
this basically created a file containing 500 VPN log entries.

> I then built an ingest pipeline within Elastic and added two processors to it.
>
> <img width="504" height="993" alt="38" src="https://github.com/user-attachments/assets/65057e37-8e17-4078-ba8b-798f63245009" />
> <img width="403" height="370" alt="39" src="https://github.com/user-attachments/assets/d0d9e7b1-5c20-48dd-8479-5467ddf98d41" />
> <img width="635" height="307" alt="40" src="https://github.com/user-attachments/assets/fe00e554-04c1-4563-9e85-0a096ac24470" />
> <img width="1498" height="922" alt="41" src="https://github.com/user-attachments/assets/dd794b45-6669-47b8-b019-0a36961e2947" />
> <img width="786" height="900" alt="42" src="https://github.com/user-attachments/assets/15bf8215-03fb-4a95-81e0-dbbd4f0667f7" />
> <img width="732" height="930" alt="43" src="https://github.com/user-attachments/assets/15285fa3-0c9f-4b34-9cfc-ccaadd65c457" />
> <img width="787" height="954" alt="44" src="https://github.com/user-attachments/assets/4d3c1248-5676-48e3-b0aa-41c26ae90cfd" />
> <img width="735" height="936" alt="45" src="https://github.com/user-attachments/assets/0367d5ce-6785-434e-98d6-8c786173372a" />
> <img width="1034" height="685" alt="46" src="https://github.com/user-attachments/assets/b8cd0b3e-c914-459b-87db-c4f0ef8033db" />
> <img width="862" height="1029" alt="47" src="https://github.com/user-attachments/assets/770a82df-ad0f-4f25-ab42-27dc96f96035" />

> After building the ingest pipeline, I configured the Filestream integration and applied it to my created vpnlog file.
>
> <img width="358" height="808" alt="48" src="https://github.com/user-attachments/assets/01bfcf8e-4903-41c0-b425-245715900939" />
> <img width="984" height="650" alt="49" src="https://github.com/user-attachments/assets/5d9d5ade-5083-49f4-87c5-76e12b7ecfbb" />
> <img width="1499" height="391" alt="50" src="https://github.com/user-attachments/assets/486a32f8-fafa-457f-a6b4-ea6551453473" />
> <img width="1453" height="865" alt="51" src="https://github.com/user-attachments/assets/843db7e3-f632-4704-8675-ad946510d005" />
> <img width="1268" height="360" alt="52" src="https://github.com/user-attachments/assets/780ed2fa-0f0b-4985-8e65-1064e3c38dd2" />
> <img width="1496" height="518" alt="53" src="https://github.com/user-attachments/assets/1366fc4a-34d0-494c-9d55-76bdd1f59737" />

> I then validated the Filestream integration and my ingest pipeline by navigating back to Discover and entering the following query:

event.module: "filestream"

I also set the time range to Last 24 hours, built a table using several relevant fields, and saved the Discover session.
>
> <img width="1496" height="992" alt="54" src="https://github.com/user-attachments/assets/8bfd50f9-79be-4bb7-8477-1d3bea216242" />
> <img width="730" height="745" alt="55" src="https://github.com/user-attachments/assets/f9fc5dbf-afc3-42a0-9bc3-b5f08b14ff6a" />

> I then had to answer a few questions. For the first question, I investigated the newly ingested VPN log data to determine the most active user on the network. After analyzing the
data, I identified the most active user as:

s.summer
>
> <img width="953" height="972" alt="56" src="https://github.com/user-attachments/assets/8c44866b-c18e-426b-ab06-0a3301380766" />

> I then identified the source.ip value associated with the previously identified user as:

72.14.24.1
>
> <img width="724" height="852" alt="57" src="https://github.com/user-attachments/assets/bad85371-9309-474c-acad-e7ffd6aa7af5" />

*** Creating Dashboards and Visualizations ***

> For this final section, I was first tasked with creating a dashboard within Kibana. After creating the dashboard, I added data by incorporating the VPN logs into it.
>
> <img width="1505" height="438" alt="58" src="https://github.com/user-attachments/assets/674b8fea-5357-49bc-ab21-2497213494c1" />
> <img width="1499" height="649" alt="59" src="https://github.com/user-attachments/assets/85b60f96-0b7f-468b-ad46-bafd9a2779e2" />

> I then added visualizations to the dashboard I created.
>
> <img width="1495" height="407" alt="60" src="https://github.com/user-attachments/assets/5755a746-4e1b-46ad-981b-4aed68e03296" />
> <img width="1500" height="956" alt="61" src="https://github.com/user-attachments/assets/1ab56d68-a621-4ab2-a530-8c39e5017744" />
> <img width="1492" height="963" alt="62" src="https://github.com/user-attachments/assets/b43e0552-5265-45c1-b0c3-513b9d351ca7" />
> <img width="1099" height="990" alt="63" src="https://github.com/user-attachments/assets/72ebd50e-864b-4c05-858e-85400a9dad5f" />

> Moving on, I then had to answer a few questions. For the first question, I created a new pie chart visualization using the following search:

event.action: "auth_fail"

I then added the user.name field and set the metric to Count under Slice by. After configuring the visualization, I discovered that the user p.mallow accounted for 62.5% of all 
auth_fail events.
>
> <img width="1375" height="978" alt="64" src="https://github.com/user-attachments/assets/ce0770a0-9f2c-4b22-8f1e-ef8dca101e9e" />

> Next, I created a visualization for the vpn.server.region field. After analyzing the visualization, I discovered that the least accessed VPN server region was:

us-west-1
>
> <img width="1498" height="989" alt="65" src="https://github.com/user-attachments/assets/20695097-528b-4880-8f72-214b5a594408" />

> For the final question, I investigated the vpn.client.ip field and discovered that the VPN client IP address logged 26 times was:

10.10.10.116
>
> <img width="1499" height="979" alt="66" src="https://github.com/user-attachments/assets/edd3d1dc-4c3d-41a7-8662-ee2ab4e41d95" />

---

## Reflection

> This lab strengthened my ability to build and configure a foundational SOC environment using Elasticsearch, Kibana, and Fleet Server. By working through the setup process, I gained a
better understanding of how security data is collected, managed, and analyzed within the Elastic Stack. I also improved my familiarity with centralized agent management and how SOC
tools work together to support monitoring and threat detection. Overall, this lab gave me more confidence working with technologies commonly used in real-world security operations
environments.
