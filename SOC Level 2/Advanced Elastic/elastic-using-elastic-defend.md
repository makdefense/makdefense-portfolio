# [Advanced Elastic]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Elastic: Using Elastic Defend]  
**Date Completed**: [09//2026]

**Lab Link**: [https://tryhackme.com/room/elasticdefend]

---

## 🧠 Summary

> In this lab, 

---

## 🎯 Objectives
- [ ] Configure the Elastic Defend integration
- [ ] Understand what Elastic Defend monitors and protects
- [ ] Explore endpoint telemetry data in Kibana Discover
- [ ] Analyze key fields and events within endpoint logs
- [ ] Investigate alerts in Elastic Security
      
---

## 🧰 Tools Used
- THM AttackBox
- 

---

## 📊 Analysis & Screenshots

*** Configuring Elastic Defend ***

> For this section, i had to go through the steps to configure Elastic Defend Integration on the VM. After configuring the Intergration i was given a few questions to answer. I first
identified the version of the Elastic Defend integration installed on my Linux host machine to be:
9.2.0
>
> <img width="635" height="517" alt="1" src="https://github.com/user-attachments/assets/9be307f0-6917-4766-8500-5f5f8195f37a" />
> <img width="530" height="1066" alt="2" src="https://github.com/user-attachments/assets/81a8aed9-094c-41ae-8797-6202d4ba9a39" />
> <img width="1497" height="772" alt="3" src="https://github.com/user-attachments/assets/be4b9f03-19f6-4a12-98dd-e11bc4b4d569" />
> <img width="1518" height="307" alt="4" src="https://github.com/user-attachments/assets/bf5d72b0-8d17-4e29-88e2-d6b4b753f9e1" />
> <img width="1411" height="667" alt="5" src="https://github.com/user-attachments/assets/9d27a81a-6804-47a5-bc70-315fb8ffa706" />
> <img width="532" height="408" alt="6" src="https://github.com/user-attachments/assets/209e0863-180b-4c2f-a07f-29920dec3e70" />

*** Logging With Elastic Defend ***

> Moving onto this section, i then had to build an elastic defend data view.
>
> <img width="956" height="1068" alt="7" src="https://github.com/user-attachments/assets/92df585c-f868-406a-b2f1-b58441a132b6" />
> <img width="539" height="1007" alt="8" src="https://github.com/user-attachments/assets/242960a0-e527-478c-a6a9-78e57faa2857" />
> <img width="659" height="308" alt="9" src="https://github.com/user-attachments/assets/b3bddfdb-8dcd-4e6e-8aae-24071a68fce5" />
> <img width="1275" height="1073" alt="10" src="https://github.com/user-attachments/assets/7bedcd0c-9692-443a-933f-6b156649cac2" />
> <img width="1498" height="1036" alt="11" src="https://github.com/user-attachments/assets/5a8a954f-b93a-4593-8382-adefcc5feea9" />

> After building the view i had to make sure it was active.
>
> <img width="597" height="605" alt="12" src="https://github.com/user-attachments/assets/6bb58422-2dd9-471b-af1b-eec05386b10d" />
> <img width="973" height="990" alt="13" src="https://github.com/user-attachments/assets/53ad57fc-d56a-4ae7-96c3-5759818723a5" />

> I then was tasked to answer a few questions. I had to identify the full "process.name" field value for the "Python" process. After highlighting the necessary fields, i identified the
"process.name" to be:
python3.12
>
> <img width="1403" height="834" alt="14" src="https://github.com/user-attachments/assets/bab04a65-c120-401b-8e67-7135b2c8f98e" />

> I then identified the top value for the "network.type" field to be:
ipv4
>
> <img width="1501" height="804" alt="15" src="https://github.com/user-attachments/assets/6d968542-23f1-4f8b-82bb-3f4ec2a61650" />

*** Exploring Elastic Defend Data ***

> Moving onto this section, after going through the readings i had to then carry out an investigation, and answer a few questions below. For the investigation i had to first run the
"discovery.sh" script.
>
> <img width="792" height="262" alt="16" src="https://github.com/user-attachments/assets/f66a8e21-5843-4ce9-a310-37736cb2f49d" />

> Then for the first question, i had to identify the "process.parent.executable" field value for the event i located with the query:
process.args: *discovery.sh*
upon further investigation i was able to identify the field value to be:
/usr/bin/bash
>
> <img width="1497" height="607" alt="17" src="https://github.com/user-attachments/assets/87316a94-b6ba-479c-bb73-c0c171bfa2c2" />

> I then had to figure out the first command executed by the script by locating the "process.entity_id" field value from the previous question, and using it against the
"process.parent.entity_id" field to track the process chain. After doing so i was able to identify the first command executed to be:
find /home -name *creds*
>
> <img width="1405" height="871" alt="18" src="https://github.com/user-attachments/assets/fe4a0a06-49e7-45ee-87c2-33046d6df742" />

> For the final question in this section, i had to continue looking through the commands that were executed, then figure out the name of the directory created in /tmp. The name of the
created directory was:
creds
>
> <img width="1466" height="691" alt="19" src="https://github.com/user-attachments/assets/0ac37e6b-4f68-4f51-ba6d-6242d5422b98" />

*** Elastic Security Alerts and Analysis ***

> For this section, i had to create then investigate a new alert. I navigated back to the command line, then created a new alert using the following commands:
sudo su
cat /etc/shadow > shadow_copy
>
> <img width="862" height="122" alt="20" src="https://github.com/user-attachments/assets/7557bf92-ebdb-4671-a5b3-b718000b2882" />

> I then had to answers a few questions related to the created alert. For the first question, i had to investigate the malware prevention alert created from the EICAR test file. I
identified the "event.risk_score" field value to be:
73
>
> <img width="1345" height="306" alt="21" src="https://github.com/user-attachments/assets/e3f5245a-48ee-4b08-90d4-500c2dff1876" />

> The "event.code" field value assigned to the above alert was discovered to be:
malicious_file
>
> <img width="1494" height="585" alt="22" src="https://github.com/user-attachments/assets/e4dbdff9-fbef-4e6c-b2f3-3f86207b5ec0" />

> I then identified the risk score assigned to the /etc/shadow file read alert to be:
47
>
> <img width="1485" height="799" alt="23" src="https://github.com/user-attachments/assets/549683c7-0101-4498-a635-6dca5f228510" />

> The first MITRE ATT&CK tactic name associated with the alert was discovered to be:
Privilege Escalation
>
> <img width="1438" height="769" alt="24" src="https://github.com/user-attachments/assets/50de2c7a-4833-4f99-b41a-526bf7475093" />

*** Detection Rules and Further Investigation ***

> For this last section, I had to complete my analysis using the provided alert, along with the Analyzer graph, and event flyout panels, then examining the parent and child processes to
gain insight into the potential attack and reconstruct the full sequence of events that occurred on the system. For the first question, i had to identify how many MITRE Tactics were
associated with the "Cron Job Created or Modified" alert. Upon further investigation i discovered that they were:
3
>
> <img width="728" height="913" alt="25" src="https://github.com/user-attachments/assets/dfb0942f-1583-4d12-bcda-c9b7aa205dbd" />
> <img width="644" height="679" alt="26" src="https://github.com/user-attachments/assets/0d9e7155-1913-4af7-8689-d4745aec8b95" />
> <img width="619" height="939" alt="27" src="https://github.com/user-attachments/assets/ac003482-dd1b-4733-aa67-22e9a96da94a" />

> For the next question i had to investigate the "printf" child process using the analyzer graph and flyout panel. I then identified the "process.executable" field value to be:
/usr/bin/printf
>
> <img width="1498" height="920" alt="28" src="https://github.com/user-attachments/assets/9a014dc0-8e88-4a16-81c6-b941ae5a2af8" />

> I then identified the IP address and port number that were used for the reverse shell attempt to be:
10.10.10.100 4444
>
> <img width="699" height="952" alt="29" src="https://github.com/user-attachments/assets/91861c6c-3e4b-430b-8a36-86e33b9769d7" />

> After checking out the remaining "chmod" child process. I identified the name of the cron job whose permissions were set to be:
system-update
>
> <img width="863" height="969" alt="30" src="https://github.com/user-attachments/assets/bb9f9a3e-e7dd-4adb-8041-6c5df6cd372e" />

---

## Reflection

> This lab strengthened my ability to 
