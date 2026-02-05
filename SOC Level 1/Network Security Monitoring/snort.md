# [Network Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Snort]  
**Date Completed**: [02/05/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of learning Snort, as it teaches real, hands-on defensive cybersecurity skills. It helps detect attacks as they happen, analyze past
incidents using traffic captures (PCAPs), and identify abnormal behavior that automated tools might miss. These skills are core to SOC and incident response roles, help build a
strong threat-hunting mindset, and make advanced security tools easier to understand. Overall, Snort bridges the gap between theory and real-world cyber defense, making me more
credible and job-ready as a security analyst.
---

## 🎯 Objectives
- [ ] Overview of IDS / IPS
- [ ] Snort Overview
- [ ] Writing IDS rules
- [ ] Detecting Intrusion with Snort

---

## 🧰 Tools Used
- THM AttackBox
- THM Snort
- THM Terminal

---

## 📊 Analysis & Screenshots

*** Interactive Material and VM ***

> For this room, I answered a question related to the “Interactive Material and VM” section. I navigated to the “Task-Exercise” folder, executed the command ./easy.sh, and
recorded the output. After running the script, I successfully retrieved the output: “Too Easy!”
>
> <img width="703" height="185" alt="1" src="https://github.com/user-attachments/assets/903e9a61-f355-4b36-b020-1196e6467245" />

*** First Interaction with Snort ***

> Moving on to the next section, I answered several questions related to “First Interaction with Snort.” For the first question, I had to run the Snort instance and identify the
build number. To do this, I launched the Terminal application, executed the command snort -V, and pressed Enter. This returned the build number: Build 149.
>
> <img width="793" height="201" alt="2" src="https://github.com/user-attachments/assets/028b71dd-136e-42fb-bde4-411972b607d2" />

> For the next question, I needed to determine how many rules were loaded with the current build by testing the Snort instance. To do this, I executed the command
sudo snort -c /etc/snort/snort.conf -T and pressed Enter. The output showed that a total of 4,151 rules were loaded.
>
> <img width="751" height="162" alt="3" src="https://github.com/user-attachments/assets/06386333-ad1e-4576-808c-a55539f71838" />
> <img width="643" height="198" alt="4" src="https://github.com/user-attachments/assets/38138532-ac6c-41db-860b-e7bf1240e389" />

> Moving on to the last question of this section, I checked how many rules were loaded with the current build by testing the Snort instance. To do this, I executed the command
sudo snort -c /etc/snort/snortv2.conf -T and pressed Enter. The output indicated that a total of 1 rule was loaded.
>
> <img width="854" height="161" alt="5" src="https://github.com/user-attachments/assets/a74401e1-3093-4953-b760-c95a4f6e0325" />
> <img width="487" height="166" alt="6" src="https://github.com/user-attachments/assets/7b84ebd8-eefe-42c9-a9a4-5b0f14cb95b4" />

*** Operation Mode 2: Packet Logger Mode ***

> Moving on to the next section, I answered a set of questions related to “Packet Logger Mode.” For the first question, I needed to determine the source port used to connect to
port 53. To do this, I first executed the traffic capture command sudo snort -dev -K ASCII -l . and selected the “TASK-6 Exercise.” After the traffic generation completed, I
stopped the Snort instance and reviewed the output summary. I then ran sudo ./traffic-generator.sh and pressed Enter to save the logs to the current directory. Next, I navigated
to the folder 145.254.160.237 by running sudo ls 145.254.160.237. This revealed that the source port used to connect to port 53 was 3009.
>
> <img width="626" height="188" alt="7" src="https://github.com/user-attachments/assets/269b5cf5-2177-4e48-8517-22e63aa06e0a" />
> <img width="800" height="59" alt="8" src="https://github.com/user-attachments/assets/4a3772f6-cfd3-43b3-8987-9cf9667b2b1a" />
> <img width="500" height="42" alt="9" src="https://github.com/user-attachments/assets/f2de8f38-41fb-4e7f-a264-1b6a620a398c" />

> For the next question, I needed to identify the IP ID of the 10th packet in the snort.log.1640048004 file. To do this, I executed the command snort -r snort.log.1640048004 -X
and pressed Enter. After reviewing and scrolling through the output, I determined that the IP ID of the 10th packet was 49313.
>
> <img width="1110" height="132" alt="10" src="https://github.com/user-attachments/assets/217346d9-1645-4e40-bb28-fb4e97cf3b8f" />
> <img width="778" height="265" alt="11" src="https://github.com/user-attachments/assets/5e272b35-fdef-44a4-a923-5ab4e7813a18" />

> For the next question, I needed to identify the referrer of the 4th packet. After reviewing and scrolling through the output, I determined that the referrer was
http://www.ethereal.com/development.html.
>
> <img width="862" height="188" alt="12" src="https://github.com/user-attachments/assets/992c63ca-9e81-4ad9-84d9-2fd8f9424398" />

> For the next question, I needed to determine the ACK number of the 8th packet. After reviewing and scrolling through the output, I identified the ACK number as 0x38AFFFF3.
>
> <img width="759" height="226" alt="13" src="https://github.com/user-attachments/assets/482658cc-b73b-41b2-a3fe-adf1092601bb" />

> For the final question, I needed to determine the number of TCP port 80 packets. To do this, I executed the command sudo snort -r snort.log.1640048004 'tcp and port 80' and
pressed Enter. The output indicated that there were a total of 41 TCP port 80 packets.
>
> <img width="1286" height="155" alt="14" src="https://github.com/user-attachments/assets/9b643ee6-1caf-438e-90f6-090c4bebb381" />
> <img width="750" height="173" alt="15" src="https://github.com/user-attachments/assets/6e5df686-cfac-4d28-b870-8d6703270dd9" />

*** Operation Mode 3: IDS/IPS ***

> Moving on to the next section, I answered a set of questions related to “IDS/IPS.” For the first question, I needed to determine the number of detected HTTP GET methods. To do
this, I first investigated the traffic using the default configuration file by running the command sudo snort -c /etc/snort/snort.conf -A full -l . and selecting the “TASK-7
Exercise.” After the traffic generation completed, I executed sudo ./traffic-generator.sh and pressed Enter. The output indicated that a total of 2 HTTP GET methods were detected.
>
> <img width="757" height="115" alt="16" src="https://github.com/user-attachments/assets/ebd8bd32-904b-4591-9d4c-d8972221b749" />
> <img width="1088" height="126" alt="17" src="https://github.com/user-attachments/assets/4db75055-20f5-4777-ac1c-fb17ce666e5d" />
> <img width="577" height="572" alt="18" src="https://github.com/user-attachments/assets/79357aab-1513-4e46-b475-c21ee60b8d7b" />
> <img width="876" height="74" alt="19" src="https://github.com/user-attachments/assets/069969a4-fd3d-4bac-ac0c-6f0085ec632a" />

*** Operation Mode 4: PCAP Investigation ***

> Moving on to the next section, I answered a set of questions related to “PCAP Investigation.” For the first question, I needed to determine the total number of generated alerts
by analyzing the mx-1.pcap file using the default configuration file. To do this, I navigated to the TASK-8 directory within the Exercise-Files directory and executed the command
sudo snort -c /etc/snort/snort.conf -A full -l . -r mx-1.pcap, then pressed Enter. After reviewing the output, I identified that a total of 170 alerts were generated.
>
> <img width="1324" height="318" alt="20" src="https://github.com/user-attachments/assets/ead105ae-2373-4691-9e72-e6b6929ae03c" />
> <img width="509" height="131" alt="21" src="https://github.com/user-attachments/assets/7a4ddb46-f342-4b7c-8370-e12db349282c" />

> For the next question, I needed to determine how many TCP segments were queued. By scrolling through the output, I identified that a total of 18 TCP segments were queued.
>
> <img width="424" height="317" alt="22" src="https://github.com/user-attachments/assets/da29d966-8148-4fa2-aa04-111bd755e2cd">

> For the next question, I needed to determine how many HTTP response headers were extracted. By reviewing and scrolling through the output, I identified that a total of 3 HTTP
response headers were extracted.
>
> <img width="768" height="208" alt="23" src="https://github.com/user-attachments/assets/539efc9b-388b-4cb0-a41a-88ad702b24ec" />

> Moving on to the next question, I needed to determine the number of generated alerts by analyzing the mx-1.pcap file using the second configuration file. Since I was already in
the Exercise-Files/TASK-8 directory, I executed the command sudo snort -c /etc/snort/snortv2.conf -A full -l . -r mx-1.pcap and pressed Enter. After reviewing and scrolling
through the output, I identified that a total of 68 alerts were generated.
>
> <img width="1364" height="151" alt="24" src="https://github.com/user-attachments/assets/e13fc44e-668f-418f-a74f-51026d045035" />
> <img width="709" height="165" alt="25" src="https://github.com/user-attachments/assets/0746448a-3fed-4cfa-a03a-aa552358bdeb" />

> Moving on to the next question, I needed to determine the number of generated alerts by analyzing the mx-2.pcap file using the default configuration file. To do this, I
executed the command sudo snort -c /etc/snort/snort.conf -A full -l . -r mx-2.pcap and pressed Enter. The output showed that a total of 340 alerts were generated.
>
> <img width="1398" height="151" alt="26" src="https://github.com/user-attachments/assets/046bb0c2-91fc-4075-b899-33349c15ac4e" />
> <img width="753" height="132" alt="27" src="https://github.com/user-attachments/assets/e10ebed1-dc8e-421c-9aaf-08f6f2d7bbbc" />

> For the next question, I needed to determine the number of detected TCP packets. By reviewing and scrolling through the output, I identified that a total of 82 TCP packets were
detected.
>
> <img width="454" height="598" alt="28" src="https://github.com/user-attachments/assets/5ebbaa6c-9b62-4706-b4ce-8c6143f498b8" />

> For the final question, I needed to determine the number of generated alerts by analyzing the mx-2.pcap and mx-3.pcap files using the default configuration file. To do this, I
executed the command sudo snort -c /etc/snort/snort.conf -A full -l . --pcap-list='mx-2.pcap mx-3.pcap' and pressed Enter. After reviewing the output, I identified that a total
of 1,020 alerts were generated.
>
> <img width="1433" height="152" alt="29" src="https://github.com/user-attachments/assets/48dd1009-be01-4afb-8c45-2c9ed2b7b349" />
> <img width="812" height="140" alt="30" src="https://github.com/user-attachments/assets/1757acd0-5de5-46fb-b0ab-dfa609269704" />

*** Snort Rule Structure ***

> Moving on to the next section, I answered a set of questions related to “Snort Rule Structure.” For the first question, I needed to identify the request name of the detected
packet by analyzing the task9.pcap file. This required writing a custom rule to filter packets with the IP ID 35369 and running it against the provided PCAP file. To begin, I
opened the local rules file by executing sudo gedit local.rules and pressed Enter. On line 8, I added the following rule: alert icmp any any <> (msg:"Sus IP ID found"; id:35369;
sid:1000001; rev:1;), then saved the file. Next, I ran the rule against the PCAP file using the command snort -c local.rules -A full -l . -r task9.pcap. I then navigated to the
TASK-9 directory within the Exercise-Files directory and analyzed the generated log file by executing sudo snort -r snort.log.1770146213. After reviewing the output, I identified
the request name of the detected packet as “TIMESTAMP REQUEST.”
>
> <img width="1048" height="44" alt="31" src="https://github.com/user-attachments/assets/65e2cc54-2d35-45f5-be19-ac4517277904" />
> <img width="933" height="336" alt="32" src="https://github.com/user-attachments/assets/84f7c58a-e91a-4006-8144-733831c93a8d" />
> <img width="1235" height="102" alt="33" src="https://github.com/user-attachments/assets/d1f0d50c-ea16-4ebe-9dac-ffad8051d063" />
> <img width="1136" height="175" alt="34" src="https://github.com/user-attachments/assets/9319f381-3fb4-4738-ad77-19fbc00cdb13" />
> <img width="713" height="265" alt="35" src="https://github.com/user-attachments/assets/920d3148-a026-45d4-8548-c465505093c5" />

> Moving on to the next question, I needed to determine the number of detected packets by creating a rule to filter packets with the SYN flag and running it against the same PCAP
file. To do this, I opened the local rules file by executing sudo gedit local.rules and pressed Enter. On line 10, I added the following rule: alert tcp any any <> any any
(msg:"FLAG TEST"; flags:S; sid:1000002; rev:1;), then saved the file. Next, I ran the rule against the PCAP file using the command snort -c local.rules -A full -l . -r
task9.pcap. I then navigated to the TASK-9 directory within the Exercise-Files directory and analyzed the generated log file by executing sudo snort -r snort.log.1770146213.
After reviewing the output, I determined that 1 packet was detected.
>
> <img width="945" height="34" alt="36" src="https://github.com/user-attachments/assets/83754711-618e-40cd-a914-176d3df5d5be" />
> <img width="927" height="303" alt="37" src="https://github.com/user-attachments/assets/1db55d35-a70b-4a67-8a5d-23859b5381b3" />
> <img width="1498" height="106" alt="38" src="https://github.com/user-attachments/assets/4069f667-e250-4418-b2fe-d4528ef7032a" />
> <img width="839" height="184" alt="39" src="https://github.com/user-attachments/assets/f5e8bbb3-beaa-41bf-97bb-a88b2f8f757a" />

> Moving on to the next question, I needed to determine the number of detected packets by writing a rule to filter packets with the PSH-ACK flags and running it against the same
PCAP file. To do this, I opened the local rules file by executing sudo gedit local.rules and pressed Enter. On line 9, I added the following rule: alert tcp any any <> any any
(msg:"FLAG TEST"; flags:P,A; sid:1000003; rev:1;), then saved the file. Next, I ran the rule against the PCAP file using the command snort -c local.rules -A full -l . -r
task9.pcap. I then navigated to the TASK-9 directory within the Exercise-Files directory and analyzed the generated log file by executing sudo snort -r snort.log.1770148526.
After reviewing the output, I determined that a total of 218 packets were detected.
>
> <img width="1012" height="51" alt="40" src="https://github.com/user-attachments/assets/f7c6d22b-ec53-446b-9fba-5e76012b38b5" />
> <img width="921" height="879" alt="41" src="https://github.com/user-attachments/assets/0c2e4568-4b63-4d5c-822b-af8a0abd44ab" />
> <img width="1495" height="174" alt="42" src="https://github.com/user-attachments/assets/55bccc6d-df2b-454e-a2b5-d794b2297cad" />
> <img width="1167" height="177" alt="43" src="https://github.com/user-attachments/assets/5d7c6007-4ea2-4e22-9739-5b6d7e8323dc" />
> <img width="853" height="241" alt="44" src="https://github.com/user-attachments/assets/bdb25bb6-7f6b-4213-a6da-9c6bbc3bfead" />

> Moving on to the next question, I needed to determine the number of packets that had the same source and destination IP address. This was done by creating a rule to filter UDP
packets with identical source and destination IPs and running it against the same PCAP file. To begin, I opened the local rules file by executing sudo gedit local.rules and
pressed Enter. On line 10, I added the following rule: alert udp any any <> any any (msg:"UDP Same IP"; sameip; sid:1000004; rev:1;), then saved the file. Next, I ran the rule
against the PCAP file using the command snort -c local.rules -A full -l . -r task9.pcap. I then navigated to the TASK-9 directory within the Exercise-Files directory and analyzed
the generated log file by executing sudo snort -r snort.log.1770151832. After reviewing the output, I determined that 7 packets showed the same source and destination address.
>
> <img width="896" height="25" alt="48" src="https://github.com/user-attachments/assets/c9992e47-6764-453f-9af6-3485321346d4" />
> <img width="918" height="368" alt="49" src="https://github.com/user-attachments/assets/1b3e09ac-d82e-49ae-a4eb-77a5975ba95c" />
> <img width="1508" height="100" alt="50" src="https://github.com/user-attachments/assets/37cac292-7a97-48d0-a340-69d47d52fbab" />
> <img width="1161" height="140" alt="51" src="https://github.com/user-attachments/assets/630787e8-eb64-4fcd-9c88-c7476a0b87a1" />
> <img width="1119" height="149" alt="52" src="https://github.com/user-attachments/assets/9ff6778a-4f12-4c92-803f-eb87016e6716" />
> <img width="522" height="272" alt="53" src="https://github.com/user-attachments/assets/a4dc5282-90c6-4efe-844d-5402642f689e" />
--- 

## Reflection

> This lab provided me with hands-on experience using Snort to detect real-time threats, analyze recorded traffic files, and identify anomalous behavior.
