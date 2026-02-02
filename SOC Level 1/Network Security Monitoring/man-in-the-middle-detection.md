# [Network Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Man-in-the-Middle Detection]  
**Date Completed**: [02/01/2026]

---

## 🧠 Summary

> In this lab, I learned how Man-in-the-Middle (MITM) attacks compromise the trust of network communications by intercepting or manipulating data in transit rather than
exploiting systems directly. I analyzed network traffic to identify MITM indicators such as ARP spoofing, TLS certificate mismatches, HTTPS downgrades, abnormal DNS responses,
and unusual traffic behavior. This lab reinforced the importance of detecting subtle network-level anomalies to identify stealthy attacks and support effective SOC investigations.

---

## 🎯 Objectives
- [ ] Understand common MITM attack vectors and techniques
- [ ] Learn to identify indicators of compromise related to MITM attacks
- [ ] Master network monitoring tools for detecting suspicious traffic patterns
- [ ] Practice incident response procedures for MITM scenarios

---

## 🧰 Tools Used
- THM AttackBox
- THM WIreShark

---

## 📊 Analysis & Screenshots

*** Detecting ARP Spoofing ***

> For this room, I had to answer several questions within this section. For the first question, I needed to determine how many ARP packets from the gateway MAC address were
observed. To do this, I opened the network_traffic.pcap file located on the Desktop. I then navigated to the filter input field, entered the following display filter:

arp && arp.src.proto_ipv4 == 192.168.10.1 && eth.src == 02:aa:bb:cc:00:01

and pressed Enter.
>
> <img width="535" height="208" alt="1" src="https://github.com/user-attachments/assets/ea8d71ee-eb75-4111-9513-3de949050ebe" />
> <img width="696" height="344" alt="2" src="https://github.com/user-attachments/assets/8511fe9c-3f0a-4c28-851e-6537d39d8fc7" />
> <img width="666" height="286" alt="3" src="https://github.com/user-attachments/assets/ba3b51b6-f151-42ec-86b3-2875761d2343" />

> Moving on to the next question, I needed to identify the MAC address used by the attacker to impersonate the gateway. To determine this, I navigated to the filter input field
in Wireshark and entered the following display filter:

(arp) && (arp.proto.type == 0x0800)

After pressing Enter, the results revealed the attacker’s MAC address as 02:fe:fe:fe:55:55.
>
> <img width="613" height="773" alt="4" src="https://github.com/user-attachments/assets/59e0790d-8d25-4fbd-ad5d-0912977b014e" />

> Moving on to the next question, I needed to determine how many gratuitous ARP replies were observed for 192.168.10.1. To do this, I navigated to the filter input field and
entered the following display filter:

(arp.isgratuitous) && (arp.src.proto_ipv4 == 192.168.10.1)

After pressing Enter, the results showed that two gratuitous ARP replies were observed.
>
> <img width="573" height="134" alt="5" src="https://github.com/user-attachments/assets/a951492e-bf7f-47eb-b5f1-903ea0a66c55" />

> Moving on to the next question, I needed to determine how many unique MAC addresses claimed the same IP address (192.168.10.1). To do this, I entered the following display
filter in the input field:

arp.duplicate-address-detected || arp.duplicate-address-frame

After pressing Enter, the results showed that two unique MAC addresses were claiming the same IP address (192.168.10.1).
>
> <img width="1180" height="758" alt="6" src="https://github.com/user-attachments/assets/c8a285d5-aad2-4312-80ce-67917e760607" />

> For the final question in this section, I needed to determine how many ARP spoofing packets were observed in total from the attacker. To do this, I navigated to the filter
input field and entered the following display filter:

arp.duplicate-address-detected || arp.duplicate-address-frame

After pressing Enter, the results showed a total of 14 ARP spoofing packets.
>
> <img width="612" height="227" alt="7" src="https://github.com/user-attachments/assets/2be85ded-b1b6-46dd-805d-c694c620e9ff" />

*** Unmasking DNS Spoofing ***

> Moving on to this section, I had to answer several questions. For the first question, I needed to determine how many DNS responses were observed for the domain corp-login.acme-
corp.local. To do this, I entered the following display filter:

dns.flags.response == 1 && dns.qry.name == "corp-login.acme-corp.local"

After pressing Enter, the results showed a total of 211 DNS responses.
>
> <img width="660" height="176" alt="8" src="https://github.com/user-attachments/assets/c72ac209-1f22-4427-9c1b-d1e8e231ec86" />
> <img width="482" height="165" alt="9" src="https://github.com/user-attachments/assets/b89363a4-c0a4-4c38-8cf6-b9c24acf36ac" />


> For the next question, I needed to determine how many DNS requests were observed from IP addresses other than 8.8.8.8. To do this, I navigated to the filter input field and
entered the following display filter:

dns.flags.response == 1 && ip.src != 8.8.8.8 && dns.qry.name == "corp-login.acme-corp.local"

After pressing Enter, the results showed a total of two DNS requests.
>
> <img width="709" height="191" alt="10" src="https://github.com/user-attachments/assets/274a48aa-19c6-4051-a502-e1225173e76d" />
> <img width="371" height="121" alt="11" src="https://github.com/user-attachments/assets/e258f845-075b-4052-aee7-e1bfd870e097" />

> For the next question, I needed to determine which IP address the attacker’s forged DNS response returned for the domain. To identify this, I referred back to the previous
question, navigated through the two DNS requests, and observed that the forged response resolved to the IP address 192.168.10.55.
>
> <img width="709" height="191" alt="10" src="https://github.com/user-attachments/assets/d4a5de45-d5fa-4a76-be4e-7cd5fc55a009" />

*** Spotting SSL Stripping in Action ***

> Moving on to this section, I had to answer several questions. For the first question, I needed to determine how many HTTP POST requests were observed for the domain corp-
login.acme-corp.local. To do this, I navigated to the filter input field and entered the following display filter:

http && ip.src == 192.168.10.10 && ip.dst == 192.168.10.55

After pressing Enter, the results showed that one POST request was observed for the domain corp-login.acme-corp.local.
>
> <img width="960" height="159" alt="12" src="https://github.com/user-attachments/assets/ab8a877f-e94c-47c5-8465-921e05e2d292" />

> For the final question in the room, I needed to identify the victim’s password found in plaintext after a successful SSL stripping attack. To determine this, I selected the
POST request and navigated to the bottom-right pane, where I observed the victim’s password as Secret123!.
>
> <img width="488" height="399" alt="13" src="https://github.com/user-attachments/assets/20772587-0293-4f59-98ef-5d398f371602" />

--- 

## Reflection

> This lab provided me with knowledge of what a Man-in-the-Middle (MITM) attack is and how to identify its footprints in network traffic.
