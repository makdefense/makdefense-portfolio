# [Network Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Data Exfiltration Detection]  
**Date Completed**: [01/31/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of understanding

---

## 🎯 Objectives
- [ ] Understand the common methods used for data exfiltration.
- [ ] Learn how to detect exfiltration attempts using network traffic analysis.
- [ ] Identify signs of exfiltration on endpoint devices.
- [ ] Correlate logs in a SIEM to uncover hidden exfiltration channels.

---

## 🧰 Tools Used
- THM AttackBox
- THM Wireshark
- THM CyberChef

---

## 📊 Analysis & Screenshots

*** Detection: Data Exfil through DNS Tunneling ***

> For this room, i had to answer a few questions in this section about data exfiltration through DNS Tunneling. For the first question i had to figure out the suspicious domain
receiving the DNS traffic. To figure this out i launched the "dns_exfil.pcap" file, navigated to the top of the input field, inputted the filter expression of
"dns && frame.len > 70" and pressed "enter." This then retrieved the suspicious domain of "tunnelcorp.net."
>
> <img width="448" height="302" alt="1 1 29 40 PM" src="https://github.com/user-attachments/assets/38479e92-d9f1-464d-9535-39716b84f921" />
> <img width="477" height="375" alt="2 1 29 40 PM" src="https://github.com/user-attachments/assets/02cc6b11-a262-4be4-b06b-3e71e93c704f" />
> <img width="409" height="299" alt="3 1 29 40 PM" src="https://github.com/user-attachments/assets/60709fcc-6921-409b-ace8-9bab996a0d97" />
> <img width="1325" height="766" alt="4 1 29 40 PM" src="https://github.com/user-attachments/assets/22029e82-5a61-44e5-93b4-63de6ed2fece" />

> Moving on to the next question i had to figure out how many suspicious traffic/logs related to DNS Tunneling were observed. To figure this out i navigated to the bottom of the
WireShark application and saw that there were 5 packets.
>
> <img width="465" height="239" alt="5 1 29 41 PM" src="https://github.com/user-attachments/assets/40a7fb06-a23e-4918-ae9b-8140e8806507" />

> For the last question in this section i had to figure out the local IP sent the maximum number of suspicious requests. To figure this out i navigated to the top of the
WireSHark application, inputted "dns.qry.name == '4f2k1a4f01m894n7w9ys.tunnelcorp.net'" and pressed "enter." After doing this i retrieved the local IP of "192.168.1.103."
>
> <img width="450" height="164" alt="6 1 49 39 PM" src="https://github.com/user-attachments/assets/e8423134-ffb2-4577-8177-1e14f5eed3b2" />

*** Detection: Data Exfil through FTP ***

> Moving on to this section, i had to answer a few questions related to data exfiltration through FTP. For the first question i had to figure out how many connections were
observed from the guest account. To figure this out i first launched the "ftp_lab.pcap" file from the Desktop, then navigated to the filter search field above, then entered
"ftp.request.arg == 'guest'" and pressed enter. After doing this i was able to retrieve 5 connections.
>
> <img width="559" height="327" alt="7 1 49 40 PM" src="https://github.com/user-attachments/assets/f6b48470-fc8a-432c-b2b2-70b9a4abf94a" />
> <img width="750" height="305" alt="8 1 49 40 PM" src="https://github.com/user-attachments/assets/58af7a9c-8b85-4cb3-884d-77cddec5fa02" />
> <img width="398" height="103" alt="9 1 49 40 PM" src="https://github.com/user-attachments/assets/91eb8506-b489-48f3-a653-bc376d0e1e8a" />
> <img width="390" height="161" alt="10" src="https://github.com/user-attachments/assets/ffe2b6c1-0813-4ab2-922f-1ba14d2043c3" />

> For the next question i had to figure out the name of the customer-related file exfiltrated from the root account. To figure this out i navigated to the filter search field
above, inputted the filter expression "ftp.request.arg == 'root'" then pressed "enter." I then selected a packet then right-clicked on it, selected "Follow," then "TCP Stream,"
which then retrieved the customer-related file "customer_data.xlsx."
>
> <img width="353" height="72" alt="11" src="https://github.com/user-attachments/assets/9cbf6717-4a75-4278-a462-bf4eed4b00f6" />
> <img width="916" height="239" alt="12" src="https://github.com/user-attachments/assets/1e418867-b073-4d19-a0cf-f13856b73714" />
> <img width="493" height="233" alt="13" src="https://github.com/user-attachments/assets/2126506e-3c56-4ce3-a9ae-c3f41ec4114b" />

< For the next qeustion i had to figure out which internal IP address was found to be sending the largest payload to an external IP. To figure this out i simply navigated to the 
filter expression search bar above, inputted "ftp && frame.len > 90" and pressed "enter," which then gave me the internal IP of "192.168.1.105."
>
> <img width="1030" height="271" alt="14" src="https://github.com/user-attachments/assets/7a573249-652d-4aef-ac59-d9f3793d50eb" />

> For the last question of this section i had to figure out the hidden flag inside the ftp stream transferring the CSV file to the suspicious IP. To figure this out i just
selected the same packet i filtered out for the previous question, right-clicked it, selected "Follow," then "TCP Stream," which then retrieved the hidden flag of
"THM{ftp_exfil_hidden_flag}."
>
> <img width="968" height="485" alt="15" src="https://github.com/user-attachments/assets/bb47ce1b-96a1-48c3-b972-851420a7bf61" />
> <img width="465" height="268" alt="16" src="https://github.com/user-attachments/assets/fa19e320-ef0f-4fba-8339-c66c7b78336b" />

*** Detection: Data Exfil via HTTP ***

> Moving on to this section, i had to answer a few questions related to data exfiltration via HTTP. For the first question i had to figure out which internal compromised host
was used to exfiltrate this sensitive data. To figure this out i first launched the "http_lab.pcap" file from the Desktop, navigated to the top of the WireShark application,
inputted the filter expression of "http.reqeust.method == 'POST' and frame.len > 750" and pressed "enter." After doing this i was able to retrieve internal compromised host of
"192.168.1.103."
>
> <img width="488" height="293" alt="17" src="https://github.com/user-attachments/assets/dd2597f4-8291-4971-9fc0-16477e8bd8eb" />
> <img width="421" height="248" alt="18" src="https://github.com/user-attachments/assets/a6fb5567-d3fa-4e41-8f33-ec40dd269295" />
> <img width="805" height="177" alt="19" src="https://github.com/user-attachments/assets/893adf3e-ae3b-4303-b4e6-6d996e2ee6b1" />

> For the last question i had to figure out the hidden flag inside the exfiltrated data. To figure this out i selected the same packet i filtered for the previous question,
right-clicked it, selected "Follow," then "HTTP Stream," which then retrieved the hidden flag of "THM{http_raw_3xf1ltr4t10n_succ3ss}."
>
> <img width="1017" height="578" alt="20" src="https://github.com/user-attachments/assets/ea9c1ff6-761a-4263-95e2-953df69f2869" />
> <img width="827" height="425" alt="21" src="https://github.com/user-attachments/assets/478e0d35-6c1a-48af-94dd-3236065467f2" />

*** Detection: Data Exfiltration via ICMP ***

> Moving onto the last section of the room, i had to answer a question related to data exfiltration via ICMP. I had to figure out flag within the exfiltrated data through ICMP.
To figure this out i first launched the "icmp_lab.pcap" file from the Desktop with WireShark, then inputted the filter expression "icmp.type == 8 and frame.len > 100," clicked
the last packet that was generated by the filter expression, navigated to the bottom of the text based on the packet, right-clicked the highlighted text, copied it as
"Base64 String," then pasted it into CyberChef, used the recipe "From Base64" to generate the hidden flag "THM{1cmp_3ch0_3xf1ltr4t10n_succ3ss}."
>
> <img width="461" height="228" alt="22" src="https://github.com/user-attachments/assets/9a2de40c-1e8d-4a92-a81f-98c9c70b4a69" />
> <img width="643" height="313" alt="23" src="https://github.com/user-attachments/assets/f6098523-d15c-450a-96c2-f1de5ea550d0" />
> <img width="644" height="190" alt="24" src="https://github.com/user-attachments/assets/107d789b-2c3b-4f5e-9ed8-57c9f8598ec4" />
> <img width="914" height="574" alt="25" src="https://github.com/user-attachments/assets/0c62a930-a2b5-4fae-aa7b-c90b8ea91b31" />
> <img width="1644" height="752" alt="26" src="https://github.com/user-attachments/assets/71c207e3-8ad4-4fa4-8a8f-4d8818cf1e99" />

--- 

## Reflection

> This lab 
