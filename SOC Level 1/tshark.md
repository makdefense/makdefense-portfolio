# [SIEM Triage for SOC]

**TryHackMe Path**: [Walkthrough]  
**Lab Topic**: [TShark: The Basics]  
**Date Completed**: [05/11/2026]

---

## 🧠 Summary

> In this lab, I learned how to apply Wireshark filters in TShark and automate packet analysis to quickly extract relevant network traffic during investigations.

---

## 🎯 Objectives
- [ ] Filtering the traffic with TShark
- [ ] Implementing Wireshark filters in TShark
- [ ] Expanding and automating packet filtering with TShark
      
---

## 🧰 Tools Used
- THM AttackBox
- TShark

## 📊 Analysis & Screenshots

*** Command-Line Packet Analysis Hints | TShark and Suppplemental CLI Tools ***

> In this section, I answered several questions related to investigating stored files on the VM using TShark. For the first question, I had to determine the RIPEMD160 value of the
demo.pcapng file using the capinfos command. After launching the terminal and running the necessary commands, I was able to retrieve the RIPEMD160 hash:

6ef5f0c165a1db4a3cad3116b0c5bcc0cf6b9ab7
>
> <img width="1043" height="704" alt="1" src="https://github.com/user-attachments/assets/b0f4c590-0f06-4fff-8d5c-a59d3aa2c95d" />

*** TShark Fundamentals I | Main Parameters I ***

> I then verified that the installed TShark version in the VM was 3.2.3.
>
> <img width="842" height="367" alt="2" src="https://github.com/user-attachments/assets/302c3f95-3390-49e1-8b3e-cdee7147ca0a" />

> I also retrieved a total of 12 interfaces in the VM using the following command:

sudo tshark -D

*** TShark Fundamentals I | Main Parameters II ***

> In this section, I determined the TCP flags assigned to the 29th packet in the demo.pcapng file. Using the following command:

tshark -r demo.pcapng -c 29

I identified the TCP flags as PSH and ACK.
>
> <img width="1283" height="604" alt="3" src="https://github.com/user-attachments/assets/5975b17f-6857-4ea5-88b8-e1695b1b6640" />

> I then discovered that the ACK value of the 25th packet was:
12421
>
> <img width="646" height="245" alt="4" src="https://github.com/user-attachments/assets/c7bd7801-1839-487d-bc6f-0be44c99c77d" />

> Next, I identified the window size value of the 9th packet as:
9660
>
> <img width="622" height="370" alt="5" src="https://github.com/user-attachments/assets/517a0085-0be3-4cef-b892-76d5d6b118be" />

*** TShark Fundamentals IV | Packet Filtering Options: Capture Filters ***

> In this section, I executed a set of commands provided in the Terminator terminal to answer several questions.

I discovered a total of 2 SYN bytes after running the provided commands on the target machine.
>
> <img width="731" height="181" alt="6" src="https://github.com/user-attachments/assets/37c5334f-afe5-44dc-b971-322b9f4e3305" />
> <img width="1435" height="715" alt="7" src="https://github.com/user-attachments/assets/9cb223a2-0bdd-491d-adfe-fa54e3b9081e" />

> I then determined that the number of packets sent to the IP address 10.10.10.10 was 7.

> Finally, I identified that the number of packets with ACK bytes was 8.

*** TShark Fundamentals V | Packet Filtering Options: Display Filters ***

> In this section, I used display filters on the demo.pcapng file to answer several questions.

First, I determined the number of packets with the destination IP address 65.208.228.223 by running:

tshark -r demo.pcapng -Y 'ip.dst == 65.208.228.223'

This returned a total of 34 packets.
>
> <img width="1379" height="686" alt="8" src="https://github.com/user-attachments/assets/6e2c335f-4439-420f-8f47-dfa4f449bcb8" />

> I then identified the number of packets using TCP port 3371 with the following command:

tshark -r demo.pcapng -Y 'tcp.port == 3371'
>
> <img width="1374" height="173" alt="9" src="https://github.com/user-attachments/assets/47064bcf-a09e-45d3-80f3-5bac8a7d67fb" />

> Next, I discovered that the number of packets with the source IP address 145.254.160.237 was 20, using:

tshark -r demo.pcapng -Y 'ip.src == 145.254.160.237'
>
> <img width="1341" height="442" alt="10" src="https://github.com/user-attachments/assets/d4ef6e23-332f-42a8-9022-e1346b585ff4" />

> Finally, I identified packet number 37 as a duplicate packet.
>
> <img width="1398" height="170" alt="11" src="https://github.com/user-attachments/assets/9fc2e08d-dc2c-4b20-ae6d-d8a977b28cd1" />

--- 

## Reflection

> Overall, this lab strengthened my ability to use TShark to enhance my PCAP analysis and efficiently filter and extract relevant network traffic.
