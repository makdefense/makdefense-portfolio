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

> 
 











---

## Reflection

> This lab strengthened my ability to 
