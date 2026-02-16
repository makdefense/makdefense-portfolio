# [Web Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Detecting Web Shells]  
**Date Completed**: [02/15/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding web shell detection using logs, file systems, and network traffic. Web shells allow attackers to control compromised
servers after they break in. By analyzing these data sources, defenders can reconstruct what the attacker did, find hidden malicious files, detect ongoing activity, and remove
access before more damage occurs. This skill builds real incident-response capability, which is essential for SOC analysts and highly valued by cybersecurity employers.

---

## 🎯 Objectives
- [ ] Understand what web shells are and how attackers use them
- [ ] Detect web shell activity through log, file system, and network analysis
- [ ] Understand common tooling in web shell detection

---

## 🧰 Tools Used
- THM Attackbox
- THM Command Line
- Mozilla FireFox

---

## 📊 Analysis & Screenshots

*** Anatomy of a Web Shell ***

> For this room, I began by answering questions under this section. For the first question, I had to access the provided shell from THM and determine which account I was accessing
by running the command "whoami." To do this, I first launched the machine, then opened Mozilla Firefox, then copied and pasted the web shell link
"http://MACHINE_IP:8080/files/awebshell.php" into the address bar and pressed Enter. After landing on the web shell page, I entered the command "whoami" and pressed the Run
button. This returned the output "www-data," which was the account I had accessed.
>
> <img width="631" height="324" alt="1" src="https://github.com/user-attachments/assets/3f629b2f-0773-40cb-ab52-84c74e944e0b" />
> <img width="626" height="478" alt="2" src="https://github.com/user-attachments/assets/d807e8f0-7163-4d1c-ad5f-09feeedc3b33" />

> Moving on to the last question for this section, I had to find a flag within the directory. To do this, I entered "ls" into the web shell input field and pressed Enter, then
entered "cat flag.txt" and pressed Enter again. This retrieved the flag: "THM{W3b_Sh3ll_Usag3}."
>
> <img width="548" height="410" alt="3" src="https://github.com/user-attachments/assets/3b93eff4-6190-4aec-9287-d6fe5ad06972" />
> <img width="663" height="377" alt="4" src="https://github.com/user-attachments/assets/3f866315-8683-430f-8cb1-0484b2753b0f" />
> <img width="597" height="381" alt="5" src="https://github.com/user-attachments/assets/5ca4f919-4aba-4d5c-931b-05df79406895" />

*** Investigation ***

> Moving on to the investigation portion of the room, I had to answer a set of questions based on analyzing the provided Apache access logs. For the first question, I had to
determine the IP address that belonged to the attacker. To do this, I first launched the Terminal application, then navigated to the directory "/var/log/apache2" and ran "cat
access.log." After viewing the access log, I searched through it to find repeated GET requests occurring in quick succession to determine the attacker’s IP address. Upon
investigation, I determined that the attacker’s IP address was "203.0.113.66."
>
> <img width="669" height="205" alt="6" src="https://github.com/user-attachments/assets/daba87fa-4ae0-462f-adb9-d4c595119ad2" />
> <img width="405" height="130" alt="7" src="https://github.com/user-attachments/assets/8816ed22-41d3-46d4-9d89-1dcc61b0a667" />

> For the next question, I had to determine the first directory that the attacker successfully identified. I navigated to the top of the access.log results and observed the first
GET request to the directory "/wordpress."
>
> <img width="856" height="144" alt="8" src="https://github.com/user-attachments/assets/58237bf3-3606-485e-8949-e15a21446a58" />

> Moving on, I had to determine the name of the .php file that the attacker used to upload the web shell. I navigated through the access.log results and looked for the first POST
request. Upon investigation, I determined that the file name was "upload_form.php."
>
> <img width="1390" height="242" alt="9" src="https://github.com/user-attachments/assets/ff9a9d61-f1bb-4704-a202-d683085bfc59" />

> For the next question, I had to determine the first command run by the attacker using the newly uploaded web shell. I navigated through the access.log results and searched for
the first "cmd" query. Upon investigation, I determined that the first command executed by the attacker was "whoami."
>
> <img width="652" height="234" alt="10" src="https://github.com/user-attachments/assets/f40b5127-fe6e-4a86-9206-8b347990bdbd" />

> Moving on to the second-to-last question, I had to determine the name of the second file the attacker downloaded onto the server after gaining access to the web shell using a
command. To do this, I navigated through the log results and searched for a "wget" command, which indicates downloading a file from the web. Upon further investigation, I
determined that the name of the second file was "linpeas.sh."
>
> <img width="642" height="180" alt="11" src="https://github.com/user-attachments/assets/aef3c49c-d867-4bd6-81cb-3183bbaf3983" />

> For the last question, I had to determine the hidden secret within the web shell and use cat to investigate further and find a flag. To do this, I navigated to the directory
"/var/www/html/wordpress/wp-content/uploads" and entered the command "cat shadyshell.php." This retrieved the hidden flag: "THM{W3b_Sh3ll_Int3rnals}."
>
> <img width="1057" height="547" alt="12" src="https://github.com/user-attachments/assets/bb2bc83e-04fa-46a4-b71f-9cf0f7159283" />

--- 

## Reflection

> This lab strengthened my ability to detect post-exploitation activity by analyzing logs, filesystem artifacts, and attacker command execution patterns.
