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













--- 

## Reflection

> This lab strengthened my ability to 
I also improved my ability to work with structured data and identify patterns that may be useful for security analysis, threat hunting, and incident response. This lab reinforced 
the importance of writing precise queries when working with large amounts of log data, especially in a SOC environment where speed and accuracy are important.
