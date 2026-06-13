# [THM Walkthrough]

**TryHackMe Path**: [Walkthrough]  
**Lab Topic**: [Nmap]  
**Date Completed**: [06/13/2026]

**Lab Link**: [https://tryhackme.com/room/furthernmap]

---

## 🧠 Summary

> In this lab, I explored advanced scanning techniques using Nmap, gaining a deeper understanding of how to identify hosts, open ports, and running services within a network. I
practiced performing various scan types, including TCP connect scans, SYN scans, and stealth scans such as NULL, FIN, and Xmas scans, to understand how different techniques
interact with target systems.

Throughout the lab, I learned how to customize scans using specific flags to control port ranges, increase verbosity, and optimize scan performance. I also explored the use of 
Nmap scripting (NSE) to automate service enumeration and vulnerability detection, enhancing the effectiveness of network reconnaissance.

This lab reinforced the importance of network scanning in both offensive and defensive security, improving my ability to identify exposed services and understand how attackers 
gather information during the reconnaissance phase of an attack.

---

## 🎯 Objectives
- [ ] Complete Nmap Walkthrough
      
---

## 🧰 Tools Used
- THM AttackBox
- Nmap
- Wireshark

---

## 📊 Analysis & Screenshots

*** Introduction ***

> In this section, I conducted research to determine how many ports are available on a network-enabled computer. After researching, I identified a total of 65,535 ports.
>
> <img width="512" height="451" alt="1" src="https://github.com/user-attachments/assets/ea8b3f4b-f8ac-474b-8f69-57d63f089d0b" />

> Out of these 65,535 ports, a total of 1,024 are considered well-known ports.

*** Nmap Switches ***

> In this section, I explored various Nmap switches. I identified the switch for a SYN scan as:
-sS
>
> <img width="604" height="301" alt="2" src="https://github.com/user-attachments/assets/da3eb0d4-adcd-46f5-8fd9-205401786d1a" />

> For a UDP scan, the switch identified was:
-sU
>
> <img width="837" height="252" alt="3" src="https://github.com/user-attachments/assets/201757a6-908c-4b2b-9884-00e832e7b05b" />

> To detect the operating system of the target, the switch used is:
-O
>
> <img width="675" height="280" alt="4" src="https://github.com/user-attachments/assets/202dac5d-3b81-4b37-91f6-7cab20592e40" />

> The switch used to detect the version of services running on the target is:
-sV
>
> <img width="1063" height="304" alt="5" src="https://github.com/user-attachments/assets/7b4ed173-e4bb-4f60-884d-59f012e381c1" />

> To increase verbosity, the following switches are used:

-v (verbose)
-vv (more verbose)
> 
> <img width="944" height="205" alt="6" src="https://github.com/user-attachments/assets/c6127345-4638-4840-bca8-c1f37f154536" />

> The switch used to save results in all major formats is:
-oA
>
> <img width="1072" height="243" alt="7" src="https://github.com/user-attachments/assets/536f816b-2b2e-4eb5-a338-4df391bf97d0" />

> To save results in normal and grepable formats, the switches used are:

-oN (normal)
-oG (grepable)
>
> <img width="999" height="289" alt="8" src="https://github.com/user-attachments/assets/ec0af977-40aa-46a3-9db3-f6d6d5efb361" />

> To activate aggressive mode, the switch used is:
-A
>
> <img width="984" height="247" alt="9" src="https://github.com/user-attachments/assets/1fe62b4b-c379-4a33-b8e3-35429c739397" />

> To set the timing template to level 5, the command used is:
-T5
>
> <img width="899" height="369" alt="10" src="https://github.com/user-attachments/assets/55902f5b-2db3-47f6-8d8e-71f950867a13" />

> To scan specific ports:

Port 80:
-p 80
Ports 1000–1500:
-p 1000-1500
All ports:
-p-

> To activate an NSE script, the switch used is:
--script
>
> <img width="795" height="259" alt="11" src="https://github.com/user-attachments/assets/64312ecb-27e4-4577-aff2-465c49761d53" />

> To run all scripts in the vulnerability category:

--script=vuln

*** Searching for Scripts ***

> In this section, I searched for SMB-related scripts in /usr/share/nmap/scripts/ and identified the script used to determine the underlying OS of an SMB server as:
smb-os-discovery.nse
>
> <img width="805" height="321" alt="12" src="https://github.com/user-attachments/assets/029cfbb9-a4f4-4efb-9334-5fd38e5ce5ec" />
> <img width="721" height="620" alt="13" src="https://github.com/user-attachments/assets/91dfaec6-87b2-44e1-8c02-73a918af927b" />

> After reviewing the script, I discovered that it depends on:
smb-brute
>
> <img width="885" height="204" alt="14" src="https://github.com/user-attachments/assets/bac6d37a-3b8a-4184-9395-7737a9a17998" />
> <img width="609" height="384" alt="15" src="https://github.com/user-attachments/assets/cbefbe6c-4951-4d9f-a79d-2eea45cec1c1" />

*** Firewall Evasion ***

> In this section, I researched which switch allows appending arbitrary-length random data to packets. The switch identified was:
--data-length
>
> <img width="541" height="388" alt="16" src="https://github.com/user-attachments/assets/e71ec3d6-d5f8-4e7d-b3da-206a84204ffe" />

*** Practical ***

> In this section, I completed a practical lab by scanning the target machine.
After performing an ICMP echo request, I confirmed that the target IP responds to ping requests.
>
> <img width="1005" height="114" alt="17" src="https://github.com/user-attachments/assets/b5e29b02-9d96-4173-add8-d7c80fec3e22" />

> I then performed an Xmas scan on the first 999 ports of the target IP and observed that all 999 ports were either open or filtered.
>
> <img width="907" height="273" alt="18" src="https://github.com/user-attachments/assets/9ad0092c-ec6d-474e-8b48-3ef5874f0987" />

> The reason for these results was identified as:
No response
>
> <img width="1011" height="383" alt="19" src="https://github.com/user-attachments/assets/e4eb0a56-3d68-45f1-8195-49e1cf07403f" />

> Next, I performed a TCP SYN scan on the first 5,000 ports of the target and identified a total of:
5 open ports
>
> <img width="839" height="612" alt="20" src="https://github.com/user-attachments/assets/6e96f85b-d18a-49a4-825e-4096e7932985" />

> I then launched Wireshark and performed a TCP connect scan on port 80. During this analysis, I observed a full TCP three-way handshake in the captured packets.

Additionally, I determined that Nmap could successfully access the FTP server on port 21 when the ftp-anon script was used.
>
> <img width="874" height="362" alt="21" src="https://github.com/user-attachments/assets/1b057bf5-a04c-4ad9-a553-0de70da8bb0c" />
> <img width="1357" height="176" alt="22" src="https://github.com/user-attachments/assets/6b166efd-143c-4542-a3d1-786759ff08dc" />
> <img width="1516" height="167" alt="23" src="https://github.com/user-attachments/assets/9eaac027-429f-44e1-b3d5-16aeaeec82c5" />
> <img width="855" height="485" alt="24" src="https://github.com/user-attachments/assets/4ab9a2f9-23fa-4e0b-a9f7-b8f76021d9b2" />

--- 

## Reflection

> This lab strengthened my ability to use Nmap to perform detailed network reconnaissance and identify potential attack surfaces. I developed a stronger understanding of different
scanning techniques, including TCP connect, SYN, and stealth scans, and how each method interacts with target systems under various conditions.

I also improved my ability to interpret scan results, allowing me to better distinguish between open, closed, and filtered ports. This enhanced my understanding of how network 
services are exposed and how misconfigurations can introduce security risks.

Additionally, I gained hands-on experience customizing scans using specific flags to control port ranges, adjust scan intensity, and increase verbosity. This helped me understand 
how to balance speed, accuracy, and stealth when performing network scans.

Overall, this lab improved my confidence in conducting network enumeration and better prepared me for real-world scenarios where identifying and assessing exposed services is a 
critical part of both offensive and defensive security operations.
