# [Networking]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Tcpdump: The Basics]  
**Date Completed**: [08//2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding 


---

## 🎯 Objectives
- [ ] 
      

---

## 🧰 Tools Used
- THM Virtual Machine
- THM Linux
  
---

## 📸 Screenshots

> [Tcpdump retrieving packets for traffic.pcap file using ICMP protocol] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/tcpdump%20figuring%20out%20packets%20in%20traffic%20file.png"
> [Tcpdump condensing displayed info for traffic.pcap file using "| wc"] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/tcpdump%20condensing%20using%20wc.png"
> [Tcpdump IP address of the host that asked for MAC address] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/tcpdump%20ip%20adress%20of%20host%20that%20asked%20for%20MAC%20addy.png"
> [Tcpdump hostname (subdomain) in first DNS query] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/tcpdump%20hostname%20in%20first%20DNS%20query.png"
> [] ""
> [] ""
> [] ""
> [] ""
> [] ""
> 
> 


---

## 📊 Analysis

> After launching THM's Virtual Machine, i read the introduction to Tcpdump: The basics and wen on to start the first exercise i was given. I had to find out how many packets were in the file "traffic.pcap"
using the ICMP protocol, to do this i entered the command "tcpdump -r traffic.pcap icmp," then pressed enter button. I was then given a long list of data so to condense it i entered "tcpdumb -r traffic.pcap
icmp | wc," then pressed the "enter" button. The reason why i added "| wc" was to pipe the data down into a single line of information and just get the total word count for the data. After doing this i got 
26 for the total number of packets. Next i had to figure out the IP address of the host that asked for the MAC address of "192.168.124.137," to do this i inputted "tcpdump -r traffic.pcap -nn arp," then pressed
enter. This then displayed the IP address of "192.168.124.148." Following i had to figure out the hostname (subdomain) that appears in the first DNS query, to do this i inputted "tcpdump -r traffic.pcap port 53,"
i added port 53 to the command because that's the port where DNS happens. 
---

## Reflection

> This lab provided me with knowledge about 


