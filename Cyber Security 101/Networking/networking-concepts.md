# [Networking]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Networking Concepts]  
**Date Completed**: [08/06/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of revising the OSI Model, which provides a structured framework for understanding how data travels through a network and helps with troubleshooting, design,
communication, and security. I then learned the importance of knowing about the TCP/IP Model, which is that it enables you to understand how the internet works, how to troubleshoot network problems, recognize cyberattacks, and
communicate clearly in tech environments. Next, knowing the importance of IP addresses and Subnets is that IP addressing identifies devices on a network, and Subnetting organizes networks for speed, security, and control.
The importance of UDP and TCP lies in the fact that TCP is connection-based and reliable for web browsing, email, and file transfers. On the other hand, UDP isn't connection-based and not reliable, but it is good for
Video streaming, VoIP, gaming, and DNS. Knowing the importance of Encapsulation is that it explains how data moves through a network, how it's protected, and how it gets to the correct destination, step by step, layer by layer.
Finally, I learned about the importance of knowing about Telnet, which is that it helps you to understand how remote terminals work, why it is a common security risk, and helps explain why SSH is needed and used in today's tech
world, and just a quick way to check open ports or services.

---

## 🎯 Objectives
- [ ] Launch THM AttackBox
- [ ] Revise the OSI Model
- [ ] Learn about the TCP/IP Model
- [ ] Learn about IP addresses and Subnets
- [ ] Learn about UDP and TCP
- [ ] Learn about Encapsulation
- [ ] Learn about Telnet and complete given exercise

---

## 🧰 Tools Used
- THM AttackBox
- THM Linux
  
---

## 📸 Screenshots

> [Linux Telnet grab fail] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/linux%20telnet%20fail.png"
> [Linux Telnet grab success] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/linux%20telnet%20grab%20success.png"
 
---

## 📊 Analysis

> After launching AttackBox, I then launched the Terminal application and used "telnet" to connect to the web server on IP address "10.201.4.6," inputted "telnet 10.201.4.6 80," then pressed the "enter" button. The reason why I
added "80" at the end of the command is that I needed to connect to port 80, and after pressing the "enter" button, I would have input "GET / HTTP/1.1" to request a webpage from that specific port. SO after pressing enter, I
inputted "GET / HTTP/1.1," then pressed "enter," then inputted "Host: telnet.thm," then pressed "enter" again. What was displayed was the exchange and the hidden flag "THM{TELNET_MASTER}." Then the connection was later closed by
the host. 

---

## Reflection

> This lab provided me with knowledge about the OSI Model, the TCP/IP Model, IP addresses and Subnets, UDP and TCP, Encapsulation, Telnet, and how to use it. I also completed a Telnet lab, where I had to connect to a web server
using Telnet. When I first tried to connect to the web server, it failed because I didn't put the "HTTP" in the correct place in time. A screenshot is attached showing my failure.


