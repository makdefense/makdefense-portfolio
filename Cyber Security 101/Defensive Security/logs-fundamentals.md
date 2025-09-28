# [Defensive Security]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Logs Fundamentals]  
**Date Completed**: [09/28/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding the different types of logs, which is that different logs reveal different parts of an incident, find root causes, and satisfy compliance
and retention rules. Correlating logs reveals stealthy threats that SOCs often miss. Next, I learned about the importance of understanding how to analyze logs, which is that logs show the
who/what/when/where ofincidents, so that you can detect and stop breaches. Forensics and audits rely on analyzed logs to build timelines and evidence. Good analysis distinguishes between real threats and
false positives. Hence, SOCs act faster, and patterns in logs reveal weak configs, recurring failures, and risky user behavior you can fix. I then learned about the importance of understanding the analysis
of Windows event logs, which is that they are the single best built-in record of what happened on Windows machines - knowing how to read them lets you detect intrusions, investigate incidents, stop
attacks, and prove what occurred. Lastly, I learned about the importance of understanding the analysis of web access logs, which is that it reveals web attacks, builds timelines for investigations, and
helps troubleshoot performance and user behavior. By inspecting IPs, URLs, status codes, user-agents, and timestamps, you spot malicious patterns and take action to block offenders, tune alerts, or improve
the app.

---

## 🎯 Objectives
- [ ] Learn about The different types of logs
- [ ] Learn How to analyze logs
- [ ] Learn about Analyzing Windows Event logs
- [ ] Learn about Analyzing Web Access logs

---

## 🧰 Tools Used
- THM Windows
- THM AttackBox Linux
  
---

## 📊 Analysis & Screenshots

*** Windows Event Logs Analysis ***

> After reading through all the Log Fundamentals sections, I was given a lab at the end where I had to do Windows event log analysis. For my first question, I had to figure out the name of the last user
account created on the THM machine. To do this, I first launched the THM Windows machine, clicked the "Start" button, then "Event Viewer."

> <img width="835" height="690" alt="lf1" src="https://github.com/user-attachments/assets/ead3dbfb-2c3a-4651-986a-60c063c5c1c0" />

> After launching the "Event Viewer" app, I then clicked "Security," which was located on the left side, then "filter current log," then input "4722," which is the event ID for "A user account was enabled,"
then the "OK" button.

> <img width="1049" height="874" alt="lf2" src="https://github.com/user-attachments/assets/d9ed8f77-8a59-4ab8-95e0-417c90744d16" />

> After clicking "OK," I was given the name "hacked" for the last user account created on the system.

> <img width="634" height="603" alt="lf3" src="https://github.com/user-attachments/assets/9ad8ec5a-653d-497a-8093-572594bed78f" />

> I then had to determine which user account had created the account. To do this, I just scrolled within the "Subject" box and saw it was created by "Administrator."

> <img width="626" height="432" alt="lf4" src="https://github.com/user-attachments/assets/5b85aa5e-7e6d-4620-900f-9bab17ba9be4" />

> For my next question, I had to determine the specific date the user account was enabled. To find this, I just looked within the details section and found it under "Logged," which showed me the date
of "6/7/2024."

> <img width="732" height="412" alt="lf5" src="https://github.com/user-attachments/assets/ad5171a1-aaed-4e19-b250-e2be08757a70" />

> For the last question, I had to determine if the account had undergone a password reset. To figure this out, I went back to the top of the "Security" section under "Number of Events," and saw that they
were 3 events with different times based on the "hacked" account.

> <img width="557" height="276" alt="lf6" src="https://github.com/user-attachments/assets/7c239b92-8a97-4d9b-9738-76ac49dcc96f" />

*** Web Server Access Logs Analysis ***

> For the next practical, I had to analyze web server access logs. For the first question, I had to determine which IP address made the last GET request to the URL "/contact". To figure this out, I
launched the AttackBox Linux Terminal and inputted the command "ls," then "enter" to see all the directories. The directory I had to specifically access was "/root/Rooms/logs".

> <img width="739" height="56" alt="lf7" src="https://github.com/user-attachments/assets/91e612da-4000-4d92-a453-8960e9a8c17e" />

> So to get to the "/root/Rooms/logs" directory, I input the command "cd /root/Rooms/logs," pressed "enter," then "ls," then "enter" to list all the files within that directory, and saw the
"access.log" file.

> <img width="451" height="60" alt="lf8" src="https://github.com/user-attachments/assets/6b2ed47d-e8f8-45b0-b610-64caba839ffa" />

> I then input the command "cat access.log," followed by "enter," and saw that the IP address "10.0.0.1" had made the last GET request to the URL "/contact".

> <img width="556" height="267" alt="lf9" src="https://github.com/user-attachments/assets/0d955ca8-9ccd-43b5-a5ec-9a3e5a7ad682" />

> I then had to determine the last POST request made by IP address "172.16.0.1". To figure this out, I scrolled through the concatenated information and saw the date/time of "06/Jun/2024:13:55:44". I also
had to figure out which URL the POST request made. I ended up discovering that it was made to "/contact" URL.

> <img width="707" height="202" alt="lf10" src="https://github.com/user-attachments/assets/ecad3a34-e57b-424c-9d1b-2df0ba23d483" />

---

## Reflection

> This lab provided me with knowledge about what logs are and how to analyze them for effective investigation.
