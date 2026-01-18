# [Network Traffic Analysis]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Wireshark: Traffic Analysis]  
**Date Completed**: [01//2026]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding

---

## 🎯 Objectives
- [ ] 

---

## 🧰 Tools Used
- THM AttackBox
- THM Wireshark
  
---

## 📊 Analysis & Screenshots

*** Nmap Scans ***

> For this room, I had to investigate packet-level details by synthesizing the analyst knowledge and Wireshark functionality for detecting anomalies and odd situations for a given
case. For the first section of the room i had to answer a few questions within the "Nmap Scans" section by investigating a "Exercise.pcapng" file.
>
> <img width="365" height="249" alt="1" src="https://github.com/user-attachments/assets/35987c37-e975-44ab-bc41-1ca0f5103e2f" />
> <img width="443" height="279" alt="2" src="https://github.com/user-attachments/assets/bcedc07b-c10d-4f8e-ad20-59ebc280f4e1" />

> For the first question i had to find the total number of the "TCP Connect" scans. To figure this out after launching the "Exercise.pcapng" file with Wireshark i navigated to the
top of the web application, inputted "tcp.flags.syn==1" into the input field, pressed the enter button, then navigated to the drop-down menu at the bottom titled
"Transmission Control Protocol," selected "Window size value: 62727" under the "Flags" sub drop-down menu and dragged it into the input field selected "and selected" to add it to
the existing "tcp.flag.syn==1" filter. After doing that i then navigated back to the input field, adding another filter alongside the other two filters by inputting
"and tcp.flags.ack==0," which led me to have the filter expression of "(tcp.flags.syn==1) && (tcp.window_size_value == 62727) and tcp.flags.ack==0." After correlating this filter
i pressed "Enter" which then gave me the total number of "TCP Connect" scans to be "1000."
>
> <img width="388" height="199" alt="3" src="https://github.com/user-attachments/assets/719ede97-7760-4a5e-a8da-2e1451978e79" />
> <img width="472" height="151" alt="4" src="https://github.com/user-attachments/assets/0cb45ce4-e596-449d-b17d-e316d6b0646e" />
> <img width="664" height="310" alt="5" src="https://github.com/user-attachments/assets/5544fa5e-d802-44ca-b86e-78196c70b365" />
> <img width="733" height="174" alt="6" src="https://github.com/user-attachments/assets/7f80f84c-d179-4762-9f35-f0ff71be82f8" />
> <img width="494" height="173" alt="7" src="https://github.com/user-attachments/assets/4cdc5222-efd5-4258-9f05-7a9166503694" />

> For the next question, i had to figure out which scan type was used to scan the TCP port 80. To figure this out i simply navigated back to the top of the Wireshark web
application, inputted "tcp.port==80," then "enter" to retrieve the first packet that was scan type "TCP Connect."
>
> <img width="962" height="146" alt="8" src="https://github.com/user-attachments/assets/33f00498-15ac-4a25-bc38-a511d28699d5" />

> Moving onto the next question for this section, i had to figure out how many "UDP close port" messages were there. To figure this out i navigated back to the top of the
Wireshark web application's input field, inputted "udp," then "enter" to filter out all udp packets. I then selected the 4 close packet, then navigated to the bottom left,
expanded the "ICMP" drop-down menu, selected "Code 3: Port unreachable," dragged it to the input field above, and chose "Selected," then pressed "enter" which returned a total
of "1083" UDP close port messages.
>
> <img width="1129" height="171" alt="9" src="https://github.com/user-attachments/assets/56c9126d-9bc2-4618-9f34-9c5d11c5475b" />
> <img width="584" height="322" alt="10" src="https://github.com/user-attachments/assets/b95a336b-5c5a-4d30-b714-de2ceba5534c" />
> <img width="549" height="335" alt="11" src="https://github.com/user-attachments/assets/7b251251-3482-4ad5-a57b-a67b9bffd896" />
> <img width="501" height="193" alt="12" src="https://github.com/user-attachments/assets/3b66aae7-5d3f-4522-a7c6-34bad3a3d44e" />

> Moving onto the last question for this section, i had to figure out which UDP port in the 55-70 port range was open. To figure this out i navigated back to the top of the
Wireshark input field, inputted "udp.port in {55..70}," pressed "enter," and saw that port "68" was open because it did not return "Destination unreachable."
>
> <img width="948" height="206" alt="13" src="https://github.com/user-attachments/assets/4933f644-3aa0-4c7b-afa1-196288908d44" />

*** ARP Poisoning & Man In The Middle! ***

> For this section i had to investigate the "Exercise.pcapng" file located in the directory "Desktop/exercise-pcaps/arp/." For the first question i had to figure out the number
of ARP requests crafted by the attacker. To figure this out I had to first launch the "Exercise.pcapng" file, then select the first ARP packet, then navigate to the bottom-left
under the ARP dropdown menu, select the "Opcode: request (1)," drag it to the input field above. This then filtered out all the ARP packets within the "Exercise.pcapng" file.
I then navigated back to the bottom-left, selected "Source:..." under the "Ethernet II" drop-down menu, dragged it to the top input field, and selected "...and Selected" which
will then give me a full filter expression of "(arp.opcode == 1) && (eth.src == 00:0c:29:e2:18:b4)." After doing all of this and pressing "enter" i retrieved a total number of
"284" ARP requests crafted by the attacker.
>
> <img width="410" height="339" alt="14" src="https://github.com/user-attachments/assets/819dbdeb-7a6c-4672-a816-04248471d411" />
> <img width="432" height="293" alt="15" src="https://github.com/user-attachments/assets/55256a2d-c85d-4d2a-b722-35388a8a81ec" />
> <img width="630" height="643" alt="16" src="https://github.com/user-attachments/assets/6843a309-a304-49e4-8d38-ddbecb2b3ad6" />
> <img width="632" height="260" alt="17" src="https://github.com/user-attachments/assets/a62183b2-ac9c-437b-82a5-f30f61620b60" />
> <img width="600" height="300" alt="18" src="https://github.com/user-attachments/assets/6b4196f1-6ba5-40be-bbf6-959b74d58063" />
> <img width="596" height="250" alt="19" src="https://github.com/user-attachments/assets/9c3016b9-f5ab-44c1-8ded-dc5d5ab36e0e" />
> <img width="460" height="160" alt="20" src="https://github.com/user-attachments/assets/27a84d98-5972-4093-a8d2-8fa2a20aecca" />


> Moving on to the next question, i had to figure out the number of HTTP packets received by the attacker. To figure this out i navigated back to the top of the input field,
inputted the filter expression "http && (eth.dst== 00:0c:29:e2:18:b4)," then pressed "enter" which retrieved a total of 90 packets received by the attacker.
>
> <img width="431" height="224" alt="21" src="https://github.com/user-attachments/assets/2c257816-d701-45e0-9839-248da30fd57e" />
> <img width="360" height="172" alt="22" src="https://github.com/user-attachments/assets/c74d4f5f-7d4f-4793-af15-5472b3ef6ad4" />

> For the next question, i had to figure out the total number of sniffed username&password entries. To figure this out i navigated to the top of the input field, inputted
"http contains 'uname'" then pressed "enter," which then retrieved a total of 7 packets but due to one of the packets containing the same username&password it was sought that
they were a total of 6 sniffed username&password entries.
>
> <img width="505" height="279" alt="23" src="https://github.com/user-attachments/assets/858446eb-ed87-4fa7-bdbd-2cfbd719e838" />
> <img width="514" height="185" alt="24" src="https://github.com/user-attachments/assets/2a477836-0e55-498d-b6ae-c64cd7c530ef" />

> For the next question, i had to figure out the password of the "Client986." To figure this out i simply navigated back up to the middle of the Wireshark application that
contained the packets i filtered out, selected the 6th packet, then navigated back to the bottom-left, clicked on the drop-down menu "HTML Form URL Encoded," and saw the password
to be "clientnothere!"
>
> <img width="671" height="556" alt="25" src="https://github.com/user-attachments/assets/bb08e5f7-29d6-4f86-b48c-9484177ed47a" />

> Moving on to the last question, i had to figure out the comment provided by the "Client354." To figure this out i navigated to the top of the input field, inputted the filter
expression "htpp contains 'client354'" then "enter" which retrieved the packet. After retrieving the packet i then navigated to the bottom-left, clicked the drop-down
menu "HTML Form Encoded:..." and saw that the comment was "Nice Work!"
>
> <img width="677" height="744" alt="26" src="https://github.com/user-attachments/assets/1922afb7-74a4-41bf-92fd-603dff54d70b" />

*** Identifying Hosts: DHCP, NetBIOS and Kerberos *** 

> For this section, i had to investigate the "dhcp-netbios.pcap" file within the directory "/Desktop/exercise-pcaps/dhcp-netbios-kerberos/" for suspicious activities. For the first
question i had to figure out the MAC Address of the host "Galaxy A30." To figure this out i had to first launch the "dhcp-netbios.pcap" using Wireshark, then navigating to the
top of the Wireshark app, inputting "frame matches Galaxy," then selecting the 3rd packet within the filtered results, then navigating to the bottom-left of the Wireshark app
expanding the DHCP drop-down menu to find the MAC address of "9a:81:41:cb:96:6c" under the "Bootp flag:..." sub drop-down menu.
>
> <img width="510" height="345" alt="27" src="https://github.com/user-attachments/assets/97aa238b-98a9-4cd8-b437-eebcaf01d1be" />
> <img width="411" height="305" alt="28" src="https://github.com/user-attachments/assets/2f56bbe4-fc35-4ebf-9474-e2748ce79157" />
> <img width="471" height="212" alt="29" src="https://github.com/user-attachments/assets/d2f4128e-0f89-4887-8f27-801e26c773fb" />
> <img width="1354" height="515" alt="30" src="https://github.com/user-attachments/assets/18e49c4c-a38a-4308-9c0d-18e7d55e26a1" />

> For the next question i had to figure out how many NETBIOS registration requests does the "LIVALJM" workstation have. To figure this out i navigated to the top of the Wireshark
app, inputted the filter expression "nbns.name contains 'LIVALJM'" then "enter," after generating the filtered results i selected a packet then navigated to the bottom-left of the
app, then expanded the drop-down menu titled "NetBIOS Name Service," then selected "Opcode: Registration (5)" which was under "Flags" sub drop-down header, then dragged it to the
input field above, then selected "..and Selected" to generate the full filter expression of "(nbns.name contains "LIVALJM") && (nbns.flags.opcode == 5)." After pressing "enter"
i retrieved a total of 16 registration requests.
>
> <img width="528" height="203" alt="31" src="https://github.com/user-attachments/assets/05d2f58e-cde8-4147-b240-2226eba836e1" />
> <img width="670" height="300" alt="32" src="https://github.com/user-attachments/assets/a4c29df6-617c-4749-b248-b3cea95bfaf2" />
> <img width="683" height="342" alt="33" src="https://github.com/user-attachments/assets/fe8acb83-3424-47a0-84b8-475ad1bf394a" />
> <img width="551" height="214" alt="34" src="https://github.com/user-attachments/assets/a58997ba-37e9-490c-a183-335dc7228ad4" />
> <img width="431" height="189" alt="35" src="https://github.com/user-attachments/assets/c820df13-672a-45ca-939c-31f5c87d9998" />

> Moving onto the next question, i had to figure out which host requested the IP address "172.16.13.85." To figure this out i navigated to the top of the Wireshark application,
inputted "dhcp," then pressed "enter." After all dhcp packets loaded i navigated to packet number 18413 which was a request type dhcp packet. After selecting the specific packet
i navigated to the bottom left, selected "Option: 50" drop-down header under the "DHCP (Request)" header, selected the requested IP, dragged it into the input field above, and
selected "...and Selected." After adding the filter in addition to the filter i already had the entire filter expression became
"(dhcp ) && (dhcp.option.requested_ip_address == 192.168.0.53." I then replaced the IP address from within the filter expression to "172.16.13.85" so the filter expression became
"(dhcp ) && (dhcp.option.requested_ip_address == 172.16.13.85)." I then pressed "enter," which retrieved packet number 72529. I then selected the packet, then navigated to the
bottom left, clicked on the drop-down menu "Option: 12" to retrieve the host name "Galaxy-A12."
>
> <img width="298" height="200" alt="36" src="https://github.com/user-attachments/assets/1f80d1f9-6895-4b02-a9fc-7e045e759edf" />
> <img width="1200" height="125" alt="37" src="https://github.com/user-attachments/assets/68a9ae2d-abdb-413c-b1b6-c7392247d3a4" />
> <img width="633" height="207" alt="38" src="https://github.com/user-attachments/assets/53778328-d79a-4594-8974-5193663df1e3" />
> <img width="578" height="265" alt="39" src="https://github.com/user-attachments/assets/777ece2a-8634-4c6d-ab5a-db0fa98f58be" />
> <img width="543" height="109" alt="40" src="https://github.com/user-attachments/assets/d39e03ef-ab0d-4b2b-af95-d4ba6ec984bb" />
> <img width="588" height="205" alt="41" src="https://github.com/user-attachments/assets/ffef9ce3-a2a2-40aa-b9dc-54295a86255c" />

> For the next question i had to investigate the pcap file titled "kerberos.pcap" which was in the "~/Desktop/exercise-pcaps/dhcp-netbios-kerberos/**kerberos.pcap" directory.
I had to figure out the IP address of the user "u5" and enter it in defanged format. To figure this out i first selected a packet within the "pcap" file then navigated to the
bottom left, selected "CNameString: des," right clicked it, then selected "Apply as Column," then selected "Kerberos," then dragged it to the input field "Apply a display filter,"
which then retrieved the user "u5." I then selected a packet that contained the user "u5," navigated back to the bottom left, selected Internet Protocol Version 4 drop-down menu
which also had the IP address of the "u5" user. I was asked to enter it in defanged format so the defanged IP address turned out to be "10[.]1[.]12[.]2"
>
> <img width="309" height="242" alt="42" src="https://github.com/user-attachments/assets/b8355f49-143e-442b-a08c-7be04abc93f2" />
> <img width="568" height="216" alt="43" src="https://github.com/user-attachments/assets/6481263b-ce69-4420-8890-41779c97d219" />
> <img width="592" height="224" alt="44" src="https://github.com/user-attachments/assets/01e34f86-5bf8-48a8-bf3b-e9edb6434be1" />
> <img width="674" height="257" alt="45" src="https://github.com/user-attachments/assets/907fcac0-6044-4291-907d-be313cbd2639" />
> <img width="646" height="523" alt="46" src="https://github.com/user-attachments/assets/b3f34431-0733-4d49-834a-2d6ade5e25b0" />
> <img width="1170" height="540" alt="47" src="https://github.com/user-attachments/assets/7a214ba9-c322-4de9-aea4-1958ec55690c" />

> Moving onto the last question for this section in had to figure out the hostname of the available host in the Kerberos packets. To figure this out i simply scrolled down to
packet number 8 within the pcap file and saw that the available host name was "xp1$"
>
> <img width="994" height="594" alt="48" src="https://github.com/user-attachments/assets/5aa8a358-835f-4377-9794-494d3cc9095d" />

*** Tunneling Traffic: DNS and ICMP ***

> For this section, i had to investigate the anomalous packets within the pcap file "icmp-tunnel.pcap" which was located within the directory "Desktop/exercise-pcaps/dns-icmp/."
For the first question i had to figure out which protocol is used in ICMP tunneling. To figure this out i simply just scrolled to packet number 42, selected it, then navigated to
the bottom-right and saw the protocol was SSH.
>
> <img width="323" height="204" alt="49" src="https://github.com/user-attachments/assets/cdc0bdf8-d782-45c2-8fd8-2cedae49e18c" />
> <img width="565" height="299" alt="50" src="https://github.com/user-attachments/assets/f0013b6e-494e-484d-8197-4652415c2514" />
> <img width="1435" height="127" alt="51" src="https://github.com/user-attachments/assets/c64b72ce-44a3-4b45-a5b4-397b2075e086" />
> <img width="595" height="344" alt="52" src="https://github.com/user-attachments/assets/b9f55c30-0231-4714-a6ca-d22329d3ca80" />

> Moving on to the next question i had to investigate the anomalous packets with the pcap file "dns.pcap" which was located within the directory "Desktop/exercise-pcaps/dns-icmp/."
I had to figure out the suspicious domain address that receives anomalous DNS queries. To figure this out i first inputted "dns" in the input field above, pressed "enter," then
selected packet 49 within the pcap file, navigated to the bottom-left, selected "v10.events.data.microsoft.com," right clicked it then selected "Apply as column," then scrolled to
packet number 2621, then navigated to the bottom left, and saw the suspicious domain address defanged to be "dataexfil[.]com."
>
> <img width="339" height="310" alt="53" src="https://github.com/user-attachments/assets/6a677310-216e-4bb5-b83c-fc7ecbbb414f" />
> <img width="834" height="677" alt="54" src="https://github.com/user-attachments/assets/1aebf59b-87ea-4a03-9de5-2efdbf0a0039" />
> <img width="614" height="691" alt="55" src="https://github.com/user-attachments/assets/c9ac5e61-8cae-4a95-8470-f780b04fc55b" />
> <img width="820" height="424" alt="56" src="https://github.com/user-attachments/assets/bb14d8ab-61b0-4ab2-86c5-adb884991958" />

*** Cleartext Protocol Analysis: FTP ***

> For this section, i had to investigate the "~/Desktop/exercise-pcaps/ftp/ftp.pcap" file, for the first question i had to figure out how many incorrect login attempts there were.
To figure this out, i first launched the file from the Desktop, then i selected the 4th packet within the file, navigated to the bottom left, selected the drop-down menu "FTP,"
then selected the drop-down menu "530 Login incorrect," then selected "Response arg: Login incorrect," dragged it to the top of the Wireshark input filter, and retrieved the
total number of incorrect login attempts to be 737.
>
> <img width="385" height="227" alt="57" src="https://github.com/user-attachments/assets/95c78941-9871-41db-859c-7fb02c24121d" />
> <img width="430" height="256" alt="58" src="https://github.com/user-attachments/assets/7310afe4-0a79-4f05-902c-58c4a2b098a5" />
> <img width="932" height="647" alt="59" src="https://github.com/user-attachments/assets/2bf91ccb-22c8-4db0-9249-06ba886962f7" />
> <img width="491" height="210" alt="60" src="https://github.com/user-attachments/assets/c526e63a-5375-4a46-b093-063bb42af07a" />
> <img width="435" height="199" alt="61" src="https://github.com/user-attachments/assets/9d4d6b79-3958-4514-8ec4-c475baf592cb" />

> Moving on to the next question, i had to figure out the size of the file accessed by the "ftp" account. To figure this out, i navigated to the top of the input field, inputted
"ftp contains 'ftp'", then clicked "enter," selected packet number "19736," right-clicked, then selected the option "Conversation Filter," then "TCP," then scrolled down to packet
19770 and saw the size of the resume.doc to be 39424.
>
> <img width="448" height="213" alt="62" src="https://github.com/user-attachments/assets/acc451b4-2a1d-4b1f-ba9f-d6849f48a6fa" />
> <img width="836" height="585" alt="63" src="https://github.com/user-attachments/assets/2a36da43-e23b-4fa2-a1ea-cdf671d7b107" />
> <img width="1056" height="387" alt="64" src="https://github.com/user-attachments/assets/730d1202-b370-4483-8528-6530b0b7858e" />

> Moving on to the next question, i had to figure out the filename of the document the adversary uploaded to the FTP server. To figure this out, i just went back to the previous
question and saw that the file name was "resume.doc."

> For the last question within this section i had to figure out the command used by the adversary when they tried to assign special flags to change the executing permissions of the
uploaded file. To fiugre this out, 








---

## Reflection

> This lab provided me with knowledge about 
