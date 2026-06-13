# [Advanced ELK]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Elastic: Using Logstash]  
**Date Completed**: [06/13/2026]

**Lab Link**: [https://tryhackme.com/room/logstash]

---

## 🧠 Summary

> In this lab, I learned how to collect, process, and transform data using Logstash within the ELK stack. I gained hands-on experience configuring Logstash pipelines to ingest
data from various sources, apply filters to parse and structure the data, and output it to destinations such as Elasticsearch for further analysis.

Throughout the lab, I worked with key components such as input, filter, and output plugins, allowing me to manipulate raw data into a standardized and searchable format. I also 
explored how to use Grok patterns and other filtering techniques to extract meaningful fields from unstructured logs.

This lab reinforced the importance of data transformation in the log pipeline, improving my ability to prepare high-quality data for analysis and strengthening my understanding of 
how Logstash supports efficient log management in real-world security operations.

---

## 🎯 Objectives
- [ ] Install and configure Logstash
- [ ] Explore various input, filter, and output plugins for Logstash
- [ ] Use Grok plugins to parse and normalize unstructured data
- [ ] Use Logstash to ingest, filter, and send Linux authentication logs to Elasticsearch
      
---

## 🧰 Tools Used
- THM AttackBox
- ELK
- Logstash

---

## 📊 Analysis & Screenshots

*** Installing Logstash ***

> In this section, I installed Logstash on the THM AttackBox in preparation for applying what I learned in the upcoming tasks. The version installed on the machine was:
9.2.4
>
> <img width="904" height="432" alt="1" src="https://github.com/user-attachments/assets/97c39af8-a12c-49c9-a7bc-a1ab2473c365" />

***  Filter Configurations ***

> In this section, I learned about filter configurations and modified a mutate filter in an example by renaming the field src_ip to source_ip. I achieved this using the following
configuration:

rename => { "src_ip" => "source_ip" }
>
> <img width="960" height="342" alt="2" src="https://github.com/user-attachments/assets/2600fac1-17dc-493f-ab90-939759314f27" />

*** Putting Pipelines Into Practice ***

> In this section, I configured an auth.conf file by using the nano command and entering the following configuration:
input {
 file {
   path => "/var/log/auth.log"
   start_position => "beginning"
   sincedb_path => "/dev/null"
 }
}

filter {
 grok {
   match => {
     "message" => "^%{TIMESTAMP_ISO8601:timestamp} %{NOTSPACE:[host][name]} %{WORD:program}(?:\[%{NUMBER:pid}\])?: %{GREEDYDATA:msg}"
   }
 }
 date {
   match => ["timestamp", "ISO8601"]
   target => "@timestamp"
 }
}

output {
 elasticsearch {
   hosts => ["https://localhost:9200"]
   user => "elastic"
   password => "pn00IuML9u43_yKb688y"
   index => "auth-logs-%{+YYYY.MM.dd}"
   ssl_verification_mode => "none"
   ssl_enabled => true
 }
}
After saving the configuration, I renamed the file to:
auth.conf
>
> <img width="782" height="174" alt="3" src="https://github.com/user-attachments/assets/c735a9c1-1343-4241-909a-a6d2b8d47144" />
> <img width="678" height="480" alt="4" src="https://github.com/user-attachments/assets/3f289f96-3632-4b51-9f92-3aaaf0a8fb92" />
> <img width="477" height="220" alt="5" src="https://github.com/user-attachments/assets/87f65076-3dc8-41e3-aef8-b7189167516f" />
> <img width="659" height="148" alt="6" src="https://github.com/user-attachments/assets/ac7ab29f-eda8-4af3-925f-67b3185cc152" />
> <img width="1425" height="320" alt="7" src="https://github.com/user-attachments/assets/af3536c8-a88c-47f4-9d26-122c4a6d4731" />
> <img width="738" height="366" alt="8" src="https://github.com/user-attachments/assets/5a5177e4-cb60-4d71-8c15-bc7cbc92bf15" />
> <img width="1471" height="848" alt="9" src="https://github.com/user-attachments/assets/0fd79f09-d1ff-4794-b1a1-122a1b1c5648" />
> <img width="813" height="128" alt="10" src="https://github.com/user-attachments/assets/7fa5ba52-7f1e-4cba-9017-78c44d52356f" />


> The two filters used in this configuration were:

Grok
Date
>
> <img width="480" height="375" alt="17" src="https://github.com/user-attachments/assets/465eab8b-69c8-47f7-bb97-eebce1aa95a2" />

> To visualize the log data in Kibana, I created a Data View within Stack Management and set the index pattern to:
auth-logs-*
>
> <img width="589" height="358" alt="11" src="https://github.com/user-attachments/assets/854809ac-86d1-470b-887b-119768da14c8" />
> <img width="846" height="464" alt="12" src="https://github.com/user-attachments/assets/8136fd6e-31b8-4f59-897d-9762445dd930" />
> <img width="816" height="998" alt="13" src="https://github.com/user-attachments/assets/c9d0f054-f2c2-402d-9c6c-d2135ddd9e22" />
> <img width="490" height="337" alt="14" src="https://github.com/user-attachments/assets/18af90c3-86b3-4f67-a1b3-2751c0b5777f" />
> <img width="614" height="720" alt="15" src="https://github.com/user-attachments/assets/58eb86db-6fc8-4694-9618-d3765863f04f" />
> <img width="1503" height="971" alt="16" src="https://github.com/user-attachments/assets/328f934f-eab1-4f65-a40e-95c008005f38" />

> After configuring Kibana to display auth_logs, I executed the following command in the terminal:
useradd -m detective_elastic
I then returned to Kibana to identify the field value for the latest event, which was:
useradd
>
> <img width="1013" height="267" alt="21" src="https://github.com/user-attachments/assets/7d980261-89b2-47a4-bed6-e9eba41230de" />
> <img width="496" height="516" alt="18" src="https://github.com/user-attachments/assets/f5ed9f75-a1d9-47d1-994a-0d512477887c" />
> <img width="1064" height="760" alt="19" src="https://github.com/user-attachments/assets/d1e48931-7a9a-4631-b45c-302233908dd6" />
> <img width="871" height="933" alt="20" src="https://github.com/user-attachments/assets/810ee680-302d-427d-9e60-fd06dbf1514a" />

> Next, I set a password for the user using:

passwd detective_elastic

After analyzing the password change event in Kibana, I identified the full msg field value as:
pam_unix(passwd:chauthtok): password changed for detective_elastic
>
> <img width="789" height="264" alt="22" src="https://github.com/user-attachments/assets/2f3afd43-3222-4a99-8215-066c3431d07a" />
> <img width="1494" height="744" alt="23" src="https://github.com/user-attachments/assets/8c397f4e-ce56-486c-abbf-370f4a80057f" />

--- 

## Reflection

> This lab strengthened my ability to work with Logstash to efficiently collect, process, and transform log data within a centralized pipeline. I developed a deeper understanding
of how to configure input, filter, and output stages to ensure data is properly ingested and structured for analysis.

I also improved my skills in parsing unstructured data using techniques such as grok patterns, which allowed me to extract meaningful fields and normalize logs into a consistent 
format. This enhanced my ability to prepare data for downstream analysis tools like Elasticsearch.

Additionally, I gained insight into how data transformation impacts the overall quality and usability of logs in a security environment. This reinforced the importance of clean, 
structured data for accurate detection and investigation.

Overall, this lab improved my confidence in building and managing log pipelines, better preparing me for real-world scenarios where efficient data processing is critical for 
effective monitoring and threat detection.
