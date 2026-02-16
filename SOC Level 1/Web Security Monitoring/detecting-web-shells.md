# [Web Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Detecting Web Shells]  
**Date Completed**: [02/15/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding

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

> For this room, I had to start off answering questions under this section. For the first question i had to access the provided shell by THM then determine which account i had to
access by running the command "whoami." To go about this i first launched the machine, then launched Mozilla FireFox, then copied + pasted the web shell link
"http://MACHINE_IP:8080/files/awebshell.php" into the input field, and clicked enter. After landing on the web shell's web page i entered the command "whoami," then pressed the
"run" button. This then returned the output "www-data" which was the account i had to access.
>
> <img width="631" height="324" alt="1" src="https://github.com/user-attachments/assets/3f629b2f-0773-40cb-ab52-84c74e944e0b" />
> <img width="626" height="478" alt="2" src="https://github.com/user-attachments/assets/d807e8f0-7163-4d1c-ad5f-09feeedc3b33" />

> Moving on to the last question for this section, i had to find a flag within the directory. To go about this i entered "ls" within the input field of the Web Shell, pressed
"return," then "cat flag.txt," then return. This then retrieved the flag of "THM{W3b_Sh3ll_Usag3}."
>
> <img width="548" height="410" alt="3" src="https://github.com/user-attachments/assets/3b93eff4-6190-4aec-9287-d6fe5ad06972" />
> <img width="663" height="377" alt="4" src="https://github.com/user-attachments/assets/3f866315-8683-430f-8cb1-0484b2753b0f" />
> <img width="597" height="381" alt="5" src="https://github.com/user-attachments/assets/5ca4f919-4aba-4d5c-931b-05df79406895" />

*** Investigation ***

> Moving on to the investigation part of the room, I had to answer a set of questions based on investigating the provided Apache access logs. For the first question i had to
figure the IP address that belongs to the attacker. To figure this out i first launched the Terminal application, then "cd" to the directory "var/log/apache2," then
"cat access.log." After concatenating the access log i searched through to find repeated GET requests in quick succession to the determine the attacker's IP address. Upon
investigation i determined that the attacker's IP address was "203.0.113.66."
>
> <img width="669" height="205" alt="6" src="https://github.com/user-attachments/assets/daba87fa-4ae0-462f-adb9-d4c595119ad2" />
> <img width="405" height="130" alt="7" src="https://github.com/user-attachments/assets/8816ed22-41d3-46d4-9d89-1dcc61b0a667" />

> For the next question i had to figure out the first directory that the attacker successfully identifies. To figure this out i just navigated to the top of the access.log file
results and saw the first "GET" request to the directory "/wordpress."
>
> <img width="856" height="144" alt="8" src="https://github.com/user-attachments/assets/58237bf3-3606-485e-8949-e15a21446a58" />

> Moving on to the next question i had to figure out the name of the .php file that the attacker uses to upload the web shell. To figure this out i navigated through the
access.log results, and looked for the first "POST" request. Upon investigation i determined the name of the .php file to be "upload_form.php"
>
> <img width="1390" height="242" alt="9" src="https://github.com/user-attachments/assets/ff9a9d61-f1bb-4704-a202-d683085bfc59" />

> For the next question i had to figure out the first command ran by the attacker using the newly uploaded web shell. To figure this out i navigated through the access.log
results, and looked for the first "cmd" search query. Upon investigation i determined that the first command ran by the attacker was "whoami."
>
> <img width="652" height="234" alt="10" src="https://github.com/user-attachments/assets/f40b5127-fe6e-4a86-9206-8b347990bdbd" />

> Moving on to the second to last question i had to figure out the name of the second file the attacker downloaded onto the server after gaining access to the Web Shell by using
a command. To figure this out i simply navigated through the results, and looked for a "wget" command which basically means downloading a file from the web. Upon further
investigation i determined the name of the second file to be "linpeas.sh"
>
> <img width="642" height="180" alt="11" src="https://github.com/user-attachments/assets/aef3c49c-d867-4bd6-81cb-3183bbaf3983" />

> For the last question i had to figure out the hidden secret within the web shell, and use cat to further investigate and find a flag. To go about this i navigated to the
directory "/var/www/html/wordpress/wp-content/uploads," then inputted "cat shadyshell.php." Doing this retrieved the hidden flag "THM{W3b_Sh3ll_Int3rnals}."
>
> <img width="1057" height="547" alt="12" src="https://github.com/user-attachments/assets/bb2bc83e-04fa-46a4-b71f-9cf0f7159283" />

--- 

## Reflection

> This lab provided me with knowledge on how to 
