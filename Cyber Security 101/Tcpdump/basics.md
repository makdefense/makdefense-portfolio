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
> [Tcpdump total packets within the TCP Reset (RST) flag set] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/tcpdump%20total%20number%20of%20packets%20in%20rst%20flag%20set.png"
> [Tcpdump IP address of host sending packets larger than 15000 bytes] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/tcpdump%20IP%20address%20of%20host%20sending%20pk%20%3E%2015000%20bytes.png"
> [Tcpdump MAC address of the host that sent an ARP request] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/tcpdump%20MAC%20address%20of%20host%20that%20sent%20ARP%20request.png"


---

## 📊 Analysis

> After launching THM's Virtual Machine, I read the introduction to Tcpdump: The basics, and started the first exercise I was given. I had to find out how many packets were in the file "traffic.pcap"
To use the ICMP protocol, I entered the command "tcpdump -r traffic.pcap icmp" and then pressed the Enter button. I was then given a long list of data, so to condense it, I entered "tcpdumb -r traffic.pcap
icmp | wc," then pressed the "enter" button. I added "| wc" to pipe the data down into a single line of information and get the total word count for the data. After doing this, I got 
26 for the total number of packets. Next, I had to figure out the IP address of the host that asked for the MAC address of "192.168.124.137." To do this, I input "tcpdump -r traffic.pcap -nn arp," then pressed
enter. This then displayed the IP address of "192.168.124.148." Following, I had to figure out the hostname (subdomain) that appears in the first DNS query, to do this, I inputted "tcpdump -r traffic.pcap port 53,"
I added port 53 to the command because that's the port where DNS happens.
> I then had to figure out how many packets were in the TCP Reset (RST) flag set. I did this by inputting the command "tcpdump -r traffic.pcap 'tcp[tcpflags] == tcp-rst' | wc," then pressing "enter." I add the "| wc"
to condense the data because there was too much data given without using the "| wc" command. The total number of packets given was 57. Next, I had to figure out the IP address of the host that sent packets larger
than Fifteen thousand bytes. I did this by inputting "tcpdump -r traffic.pcap greater 15000 -n," then pressing the "enter" button. What was displayed was the IP address "185.117.80.53"
> Finally, I had to figure out the MAC address of the host that sent an ARP request with the traffic.pcap file, to do this I inputted "tcpdump -r traffic.pcap arp -e," then pressed "enter."
The MAC address displayed is "52:54:00:7c:d3:5b." I added the command "-e" at the end of the script because this command is used to include the MAC address when displaying packets.

---

## Reflection

> This lab provided me with knowledge about 


