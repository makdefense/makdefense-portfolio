# [Networking]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Networking Essentials]  
**Date Completed**: [08//2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of

---

## 🎯 Objectives
- [ ] Launch THM AttackBox
- [ ]

---

## 🧰 Tools Used
- THM AttackBox
- THM Linux
  
---

## 📸 Screenshots

> [Linux retrieve hidden flag using "curl"] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/linux%20get%20flag%20using%20curl.png"
> [Linux retieve flag using GET HTTP method] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/linux%20get%20http%20flag.png"
> [Linux retrieving available downloadable file using FTP] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/linux%20ftp%20mode%20for%20file%20download.png"
> [Linux retrieving hidden flag after downloading file using FTP] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/linux%20ftp%20hidden%20flag.png"
> [Linux authenticating POP3's server to retrieve hidden flag] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/liniux%20POP3%20recieving%20emails.png"
> [Linux retrieving hidden flag from the fourth message] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/linux%20using%20POP3%20to%20display%20flag.png"
> []

 
---

## 📊 Analysis

> After launching AttackBox, I wanted to find a hidden flag within html file "flag.html." so i launch the "Terminal" application, then inputted "curl 10.201.124.210/flag.html," then "enter" which displayed the flag
"THM{TELNET-HTTP}." I then wanted to retrieve the hidden flag using the "telnet" command instead of "curl," so i inputted "telnet 10.201.124.210 80," pressed "enter" button, then inputted "GET /flag.html HTTP/1.1,"
pressed "enter," then inputted "Host: anything," then "enter" button which then display the hidden flag "THM{TELNET-HTTP}." Next i then used FTP to retrieve a file to display its hidden flag. First i inputted
"ftp 10.201.124.210," then pressed "enter," then inputted the name as "anonymous," then pressed "enter," then "enter" again because no password was required. I then inputted "ls" to display the list of files that
were available for download, then pressed "enter," thne inputted "tpye ascii," then "get flag.txt," to download that specific file to retrieve the hidden flag. Next i inputted "quit" to exit ftp mode, then inputted
the command "cat flag.txt" to display the flag of the txt file. The hidden flag was "THM{FAST-FTP}." Next, i was given a task to retrieve a hidden flag from a received email using "POP3." In order to do this i first
inputted "telnet 10.201.124.210 110," 110 is a the end because that is the default port number for receiving email from a POP3's server. Next i pressed "enter," then inputted "AUTH," then "enter," then inputted
login credentials to authenticate the POP3's server, the credentials used were "linda" for the username and "Pa$$123" for the password, i then pressed "enter" after inputting the credentials. I then inputted "STAT"
to request the total number of messages and total size, then pressed "enter," then inputted "LIST," to list all messages and their sizes, then pressed "enter," then "RETR 4," then pressed "enter" to retrieve the email and
show the hidden flag within the message. The flag shown was "THM{TELNET_RETR_EMAIL}." 

---

## Reflection

> This lab provided me with knowledge about 


