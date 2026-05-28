# [Log Analysis]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Intro to Log Analysis]  
**Date Completed**: [05/27/2026]

---

## 🧠 Summary

> In this lab, I learned log analysis best practices, explored essential tools used for analyzing logs, and gained hands-on experience investigating and interpreting log data
using multiple technologies to detect and understand potential security threats.

---

## 🎯 Objectives
- [ ] Learn log analysis best practices.
- [ ] Discover the essential tools for log analysis.
- [ ] Gain hands-on experience in analyzing logs by using multiple tools and technologies.
      
---

## 🧰 Tools Used
- THM AttackBox
- Terminal
- CyberChef

---

## 📊 Analysis & Screenshots

*** Log Analysis Tools: Command Line ***

> In this section, I conducted command-line analysis on the "apache.log" file located on the machine and answered several related questions. For the first question, I had to
identify a hidden flag by using the cut command to extract only URLs from the log file. After running the command, I discovered the hidden flag:
c701d43cc5a3acb9b5b04db7f1be94f6
>
> <img width="731" height="402" alt="1" src="https://github.com/user-attachments/assets/871c2699-a1ed-4b35-acfb-51114fee735c" />
> <img width="949" height="138" alt="2" src="https://github.com/user-attachments/assets/6c756db5-3f0d-4acb-a6cd-7442f285b6f5" />
> <img width="695" height="209" alt="3" src="https://github.com/user-attachments/assets/dbcdd274-10ab-4e16-b93b-1221fa9299fe" />

> I then identified the total number of HTTP 200 responses logged as:
52
>
> <img width="811" height="81" alt="4" src="https://github.com/user-attachments/assets/2d01a11d-f7bf-48dd-bf94-d376af4927ff" />

> Next, I discovered that the IP address:
145.76.33.201
generated the most traffic within the apache.log file.
>
> <img width="1084" height="671" alt="5" src="https://github.com/user-attachments/assets/541900d7-24dd-4de7-bd0e-ba75623b7afb" />

> Finally, I identified the complete timestamp of the entry where 110.122.65.76 accessed /login.php:
31/Jul/2023:12:34:40 +0000
>
> <img width="1510" height="166" alt="6" src="https://github.com/user-attachments/assets/d79ce976-8204-418f-bd54-0f8ded7525ea" />

*** Log Analysis Tools: Cyber Chef ***

> In this section, I answered several questions related to analyzing the "access.log" file located in the directory:
/root/Rooms/introloganalysis/task8

After extracting the file, I identified the full IP address beginning with 212 by using regex to list all IP addresses:
212.14.17.145
>
> <img width="1392" height="1025" alt="7" src="https://github.com/user-attachments/assets/6f532f06-e468-475a-9e22-31bb8afc3985" />
> <img width="1083" height="418" alt="8" src="https://github.com/user-attachments/assets/002f5cca-7852-48bc-82cf-57f81fc23c91" />
> <img width="1336" height="1086" alt="9" src="https://github.com/user-attachments/assets/7e26f5c7-d8c3-465d-8437-6208bab25c97" />

> I then identified a request that was encoded in Base64 and decoded it using CyberChef. The decoded value was:
THM{CYBERCHEF_WIZARD}
>
> <img width="504" height="223" alt="10" src="https://github.com/user-attachments/assets/35bfadc1-4192-46b2-8163-b27f1116c35c" />
> <img width="1349" height="958" alt="11" src="https://github.com/user-attachments/assets/75ef07ae-3451-4358-a4a2-dac4891566ca" />

> Lastly, I identified the extracted value after decoding the file "encodedflag.txt" and using regex to extract a MAC address:
08-2E-9A-4B-7F-61
>
> <img width="1265" height="766" alt="12" src="https://github.com/user-attachments/assets/eeecd987-27a8-4c36-8cd6-5f9abe142d11" />
> <img width="1328" height="980" alt="13" src="https://github.com/user-attachments/assets/fe153d56-6ab0-4397-ae46-5e24d327dff8" />

--- 

## Reflection

> This lab strengthened my ability to adopt effective log analysis strategies. I explored the importance of log data collection, identified common attack patterns, and used
various tools to support investigation and incident response processes.
