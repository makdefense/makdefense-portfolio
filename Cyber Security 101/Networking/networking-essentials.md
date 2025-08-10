# [Networking]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Networking Essentials]  
**Date Completed**: [08/10/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding DNS, which is the "phonebook" of the internet, and knowing how it works is like knowing how locks and keys work in physical security. Next, I learned about
the importance of knowing about WHOIS, which is that it is the internet's "who owns this and since when?" tool. Learned about the importance of HTTP & HTTPS, which is that they are the main ways data moves between web browsers
and servers - and in networking or cybersecurity, understanding them is like knowing how mail is packaged, delivered, and protected. Next, I learned about the importance of knowing about FTP, which is basically like an old postal
service that still provides packages - but the boxes aren't sealed, anyone can peek inside, and sometimes the warehouse doors are left wide open. I then learned the importance of SMTP, which is the backbone of how email is
sent - and in cybersecurity, email is one of the biggest attack vectors. Then I learned the importance of POP3S, which is that it is one of the main ways email is retrieved securely from a mail server - and while newer protocols
 are more common today, POP3S still shows up in corporate networks, legacy systems, and investigations. Finally, I learned the importance of IMAP, which is because it is one of the most widely used protocols for retrieving and
managing email, and in cybersecurity, it's both a standard tool and a common attack target.


---

## 🎯 Objectives
- [ ] Launch THM AttackBox
- [ ] Learn about DNS
- [ ] Learn about WHOIS
- [ ] Learn about HTTP(S):
- [ ] Learn about FTP: Transferring Files
- [ ] Learn about SMTP: Sending Email
- [ ] Learn about POP3S: Receiving Email
- [ ] Learn about IMAP: Synchronizing Email
      

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

 
---

## 📊 Analysis

> After launching AttackBox, I wanted to find a hidden flag within the HTML file "flag.html." So I launched the "Terminal" application, then input "curl 10.201.124.210/flag.html," then "enter," which displayed the flag
"THM{TELNET-HTTP}." I then wanted to retrieve the hidden flag using the "telnet" command instead of "curl," so I inputted "telnet 10.201.124.210 80," pressed the "enter" button, then inputted "GET /flag.html HTTP/1.1,"
pressed "enter," then inputted "Host: anything," then the "enter" button, which then displayed the hidden flag "THM{TELNET-HTTP}." Next, I then used FTP to retrieve a file to display its hidden flag. First, I input
"ftp 10.201.124.210," then pressed "enter," then inputted the name as "anonymous," then pressed "enter," then "enter" again because no password was required. I then input "ls" to display the list of files that
were available for download, then pressed "enter," then input "type ascii," then "get flag.txt," to download that specific file to retrieve the hidden flag. Next, I input "quit" to exit ftp mode, then input
the command "cat flag.txt" to display the flag of the txt file. The hidden flag was "THM{FAST-FTP}." Next, I was given a task to retrieve a hidden flag from a received email using "POP3." To do this, I first
input "telnet 10.201.124.210 110," 110 is at the end because that is the default port number for receiving email from a POP3 server. Next, I pressed "enter," then inputted "AUTH," then "enter," then inputted
login credentials to authenticate the POP3 server. The credentials used were "linda" for the username and "Pa$$123" for the password, I then pressed "enter" after inputting the credentials. I then input "STAT"
to request the total number of messages and total size, then pressed "enter," then inputted "LIST," to list all messages and their sizes, then pressed "enter," then "RETR 4," then pressed "enter" to retrieve the email and
show the hidden flag within the message. The flag shown was "THM{TELNET_RETR_EMAIL}."

---

## Reflection

> This lab provided me with knowledge about DNS, WHOIS, HTTP/S, FTP, SMTP, POP3S, and IMAP.


