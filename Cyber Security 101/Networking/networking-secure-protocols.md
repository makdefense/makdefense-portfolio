# [Networking]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Networking Secure Protocols]  
**Date Completed**: [08/10/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of knowing about SFTP, which is one of the safest and most common ways to transfer files over a network - and in cybersecurity, it's both a critical secure tool and something
attackers also use to move stolen data. Next, I learned the importance of knowing about VPN, which is that it is one of the most common tools for secure remote access, and in cybersecurity, it can be both a defensive shield
and a cover for malicious activity. Lastly, I learned the importance of knowing about TLS, which is that it's the protocol that keeps most of the internet's communication private and secure - and in cybersecurity, understanding
it is critical for both protecting data and spotting threats hidden inside encryption.

---

## 🎯 Objectives
- [ ] Launch THM AttackBox
- [ ] Learn about TLS
- [ ] Learn about HTTPS
- [ ] Learn about SMTPS, POP3S, and IMAPS
- [ ] Learn about SSH
- [ ] Learn about SFTP and FTPS
- [ ] Learn about VPN
- [ ] Challenge: Decrypt TLS traffic using Wireshark

---

## 🧰 Tools Used
- THM AttackBox
- THM Wireshark
  
---

## 📸 Screenshots

> [Launching Wireshark Application] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20launch.png"
> [Wireshark opening randy-chromium pcapng file and opening its TLS preferences] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/opening%20%20pcapng%20file.png"
> [Wireshark broswing for specific file] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20browsing%20files.png"
> [Wireshark selecting documents tab] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20selecting%20documents%20tab.png"
> [Wireshare selecting specifc log file ssl-key.log to decrypt] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20selecting%20specific%20log%20file.png"
> [Wireshark locating hidden flag in decrypted ssl-key.log file] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20locating%20flag%20in%20decrypted%20log%20file.png"

 
---

## 📊 Analysis

> After launching AttackBox, I had to look for a password submitted by a user within a packet. I launched the "Wireshark" application, then opened "/home/ubuntu/Documents/randy-chromium.pcapng," following which I scrolled to packet
"366," then right-clicked on it, then selected "protocol preferences," then "TLS," then "Open Transport Layer Security preferences.." After opening TLS preferences, I then clicked on the second "Browse" button within the pop-up,
then selected the "Documents" tab, then within the "Documents" tab, I selected the "ssl-key.log," then pressed the "open" button. After the second pop-up closed, I returned to the first pop-up and then pressed the "ok" button.
Next, I double-clicked on packet 366, then selected the "Decrypted TLS (141 bytes)" tab and clicked on the lines of "0040 & 0050" to retrieve the hidden flag "THM{B8WM6P}."

---

## Reflection

> This lab provided me with knowledge about TLS, HTTPS, SMTPS, POP3S, IMAPS, SSH, SFTP, FTPS, VPN, and how to go about decrypting log files using the Wireshark application.



