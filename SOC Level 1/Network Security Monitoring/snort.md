# [Network Security Monitoring]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Snort]  
**Date Completed**: [02//2026]

---

## 🧠 Summary

> In this lab, I learned how

---

## 🎯 Objectives
- [ ] 

---

## 🧰 Tools Used
- THM 

---

## 📊 Analysis & Screenshots

*** Interactive Material and VM ***

> For this room, I had to answer one question related to the section "Interactive Material and VM." I had to navigate to the "Task-Exercise" folder, run the command "./.easy.sh"
and write the output. After doing so, i managed to retrieve the output "Too Easy!"
>
> <img width="703" height="185" alt="1" src="https://github.com/user-attachments/assets/903e9a61-f355-4b36-b020-1196e6467245" />

*** First Interaction with Snort ***

> Moving on to the next section, I had to answer a few questions related to "First Interaction with Snort." For the first question i had to run the Snort instance and figure out
the build number. To go about this i launched the "Terminal" application, then inputted the command "snort -V," then "enter" which gave me the build number of "Build 149."
>
> <img width="793" height="201" alt="2" src="https://github.com/user-attachments/assets/028b71dd-136e-42fb-bde4-411972b607d2" />

> For the next question i had to check how many rules were loaded with the current build by testing the instance. To figure this out i entered the command
"sudo snort -c /etc/snort/snort.conf -T," then "enter" which gave me back the total number of rules to be "4151."
>
> <img width="751" height="162" alt="3" src="https://github.com/user-attachments/assets/06386333-ad1e-4576-808c-a55539f71838" />
> <img width="643" height="198" alt="4" src="https://github.com/user-attachments/assets/38138532-ac6c-41db-860b-e7bf1240e389" />

> Moving on to the last question of this section i had to check how many rules were loaded with the current build by testing the instance. To figure this out i entered the
command "sudo snort -c /etc/snort/snortv2.conf -T," then "enter" which gave me back the total number of rules to be "1."
>
> <img width="854" height="161" alt="5" src="https://github.com/user-attachments/assets/a74401e1-3093-4953-b760-c95a4f6e0325" />
> <img width="487" height="166" alt="6" src="https://github.com/user-attachments/assets/7b84ebd8-eefe-42c9-a9a4-5b0f14cb95b4" />

*** Operation Mode 2: Packet Logger Mode ***

> Moving on to this section i had to answer a set of questions related to "Packet Logger Mode." For the first question i had to figure out the source port used to connect port 53.
To go about this i had to first execute the traffic generator script "sudo snort -dev -K ASCII -l .," then choose "TASK-6 Exercise." After waiting until the traffic ended i
stopped the Snort instance, analyzed the output summary, then inputted "sudo ./traffic-generator.sh," then "enter" to save the logs within the current directory. I then
navigated to the folder "145.254.160.237" by inputting "sudo ls 145.254.160.237," then "enter" which then retrieved the source port of 3009 used to connect to port 53.
>
> <img width="626" height="188" alt="7" src="https://github.com/user-attachments/assets/269b5cf5-2177-4e48-8517-22e63aa06e0a" />
> <img width="800" height="59" alt="8" src="https://github.com/user-attachments/assets/4a3772f6-cfd3-43b3-8987-9cf9667b2b1a" />
> <img width="500" height="42" alt="9" src="https://github.com/user-attachments/assets/f2de8f38-41fb-4e7f-a264-1b6a620a398c" />

> For the next question i then had to figure out the IP ID of the 10th packet of the snort.log file "snort.log.1640048004." To figure this out i inputted the command synthax of
"snort -r snort.log.1640048004 -X," then "enter." After running this command and scrolling through the output i retrieved the IP ID of "49313" for the 10th packet.
>
> <img width="1110" height="132" alt="10" src="https://github.com/user-attachments/assets/217346d9-1645-4e40-bb28-fb4e97cf3b8f" />
> <img width="778" height="265" alt="11" src="https://github.com/user-attachments/assets/5e272b35-fdef-44a4-a923-5ab4e7813a18" />

> For the next question i then had to figure out the referer of the 4th packet. After scrolling through the output i found the referer to be
"http://www.ethereal.com/development.html."
>
> <img width="862" height="188" alt="12" src="https://github.com/user-attachments/assets/992c63ca-9e81-4ad9-84d9-2fd8f9424398" />

> For the next question i had to figure out the Ack number of the 8th packet. After scrolling thorugh the output i found the Ack number of the 8th packet to be "0x38AFFFF3."
>
> <img width="759" height="226" alt="13" src="https://github.com/user-attachments/assets/482658cc-b73b-41b2-a3fe-adf1092601bb" />

> For the last question i had to figure out the number of the "TCP port 80" packets. To figure this out i inputted the command synthax of
"sudo snort -r snort.log.1640048004 'tcp and port 80'", then "enter" which then gave me back the total number of "TCP port 80" packets to be 41.
>
> <img width="1286" height="155" alt="14" src="https://github.com/user-attachments/assets/9b643ee6-1caf-438e-90f6-090c4bebb381" />
> <img width="750" height="173" alt="15" src="https://github.com/user-attachments/assets/6e5df686-cfac-4d28-b870-8d6703270dd9" />

*** Operation Mode 3: IDS/IPS ***

> Moving on to this section i had to answer a set of questions related to "IDS/IPS." For the first question i had to figure out the number of the detected HTTP GET methods.
I first had to investigate the traffic with the default configuration file by using the generator script "sudo snort -c /etc/snort/snort.conf -A full -l .", then choosing
"TASK-7 Exercise." After the traffic stopped i inputted the command sythax "sudo ./traffic-generator.sh," then "enter" which then showed me the total number of HTTP GET methods
to be "2."
>
> <img width="757" height="115" alt="16" src="https://github.com/user-attachments/assets/ebd8bd32-904b-4591-9d4c-d8972221b749" />
> <img width="1088" height="126" alt="17" src="https://github.com/user-attachments/assets/4db75055-20f5-4777-ac1c-fb17ce666e5d" />
> <img width="577" height="572" alt="18" src="https://github.com/user-attachments/assets/79357aab-1513-4e46-b475-c21ee60b8d7b" />
> <img width="876" height="74" alt="19" src="https://github.com/user-attachments/assets/069969a4-fd3d-4bac-ac0c-6f0085ec632a" />

*** Operation Mode 4: PCAP Investigation ***

> Moving on to this section i had to answer a set of questions related to "PCAP Investigation." For the first question i had to figure out the total number of generated alerts
by investigating the mx-1.pcap file with the default configuration file using the command synthax "sudo snort -c /etc/snort/snort.conf -A full -l . -r mx-1.pcap." To go about
this i navigated to the directory named "TASK-8" within the "Exercise-Files" directory, then inputted the command sythax
"sudo snort -c /etc/snort/snort.conf -A full -l . -r mx-1.pcap," then "enter." After going through the retrieved output i saw the total number of alerts to be "170."
>
> <img width="1324" height="318" alt="20" src="https://github.com/user-attachments/assets/ead105ae-2373-4691-9e72-e6b6929ae03c" />
> <img width="509" height="131" alt="21" src="https://github.com/user-attachments/assets/7a4ddb46-f342-4b7c-8370-e12db349282c" />

> For the next question i had to figure out how many TCP Segments are Queued. To get this i simply scrolled down throughout the output and saw a total of 18 TCP Segments Queued.
>
> <img width="424" height="317" alt="22" src="https://github.com/user-attachments/assets/da29d966-8148-4fa2-aa04-111bd755e2cd">

> For the next question i had to figure out how many "HTTP response headers" were extracted. To get this i scrolled down throughout the output and saw a total of 3 HTTP response
headers extracted.
>
> <img width="768" height="208" alt="23" src="https://github.com/user-attachments/assets/539efc9b-388b-4cb0-a41a-88ad702b24ec" />

> Moving on to the next question i had to figure out the number of generated alerts by investigating the mx-1.pcap file with the second configuaration file using the command
synthax "sudo snort -c /etc/snort/snortv2.conf -A full -l . -r mx-1.pcap." To go about this, since i was already within the directory "Exercise-Files/TASK-8," i inputted the
command synthax "sudo snort -c /etc/snort/snortv2.conf -A full -l . -r mx-1.pcap," then "enter," then scrolled through the retrieved output and saw a total number of 68 alerts.
>
> <img width="1364" height="151" alt="24" src="https://github.com/user-attachments/assets/e13fc44e-668f-418f-a74f-51026d045035" />
> <img width="709" height="165" alt="25" src="https://github.com/user-attachments/assets/0746448a-3fed-4cfa-a03a-aa552358bdeb" />

> Moving on to the next question i had to figure out the number of generated alerts by investigating the mx-2.pcap file with the default configuration file using the command
synthax "sudo snort -c /etc/snort/snort.conf -A full -l . -r mx-2.pcap." To go about this, i inputted the command synthax
"sudo snort -c /etc/snort/snort.conf -A full -l . -r mx-2.pcap," then "enter" which retrieved a total of "340" alerts.
>
> <img width="1398" height="151" alt="26" src="https://github.com/user-attachments/assets/046bb0c2-91fc-4075-b899-33349c15ac4e" />
> <img width="753" height="132" alt="27" src="https://github.com/user-attachments/assets/e10ebed1-dc8e-421c-9aaf-08f6f2d7bbbc" />

> For the next question i had to figure out the number of detected TCP packets. To figure this out i simply scrolled through the output and saw a total of 82 TCP packets.
>
> <img width="454" height="598" alt="28" src="https://github.com/user-attachments/assets/5ebbaa6c-9b62-4706-b4ce-8c6143f498b8" />

> For the last question i had to figure out the number of generated alerts by investigating the mx-2.pcap and mx-3.pcap files with the default configuration file by using the
command synthax "sudo snort -c /etc/snort/snort.conf -A full -l . --pcap-list='mx-2.pcap mx-3.pcap.'" After inputting the command sythax, then pressing "enter," i went through
the output, and saw a total of 1020 generated alerts.
>
> <img width="1433" height="152" alt="29" src="https://github.com/user-attachments/assets/48dd1009-be01-4afb-8c45-2c9ed2b7b349" />
> <img width="812" height="140" alt="30" src="https://github.com/user-attachments/assets/1757acd0-5de5-46fb-b0ab-dfa609269704" />

*** Snort Rule Structure ***

> Moving on to this section i had to answer a set of questions related to "Snort Rule Structure." For the first question i had to figure out the request name of the detected
packet by using the "task9.pcap" file, writing a rule to filter IP ID "35369," and run it against the given pcap file. To go about this i first inputted the command synthax
"sudo gedit local.rules," then "enter." On line 8, i entered "alert icmp any any <> (msg: "Sus IP ID found"; id:35369; sid:1000001; rev:1;)", clicked "Save," then entered the
command sythax "snort -c local.rules -A full -l . -r task9.pcap," navigated to the directory "TASK-9" within the "Exercise-Files," inputted the command sythax of
"sudo snort -r snort.log.1770146213," then "enter." After scrolling through the retrieved output i saw the request name of the detected packet to be "TIMESTAMP REQUEST."
>
> <img width="1048" height="44" alt="31" src="https://github.com/user-attachments/assets/65e2cc54-2d35-45f5-be19-ac4517277904" />
> <img width="933" height="336" alt="32" src="https://github.com/user-attachments/assets/84f7c58a-e91a-4006-8144-733831c93a8d" />
> <img width="1235" height="102" alt="33" src="https://github.com/user-attachments/assets/d1f0d50c-ea16-4ebe-9dac-ffad8051d063" />
> <img width="1136" height="175" alt="34" src="https://github.com/user-attachments/assets/9319f381-3fb4-4738-ad77-19fbc00cdb13" />
> <img width="713" height="265" alt="35" src="https://github.com/user-attachments/assets/920d3148-a026-45d4-8548-c465505093c5" />

> Moving on to the next question i had to figure out the number of detected packets by creating a rule to filter packets with Syn flag and run it against the same pcap file.
To go about this i inputted the command synthax "sudo gedit local.rules," then "enter." On line 10, i entered
"alert tcp any any <> any any(msg: "FLAG TEST"; flags:S;sid: 1000002; rev:1;)", clicked "Save," then entered the command syntax "snort -c local.rules -A full -l . -r task9.pcap,"
navigated to the directory "TASK-9" within the "Exercise-Files," inputted the command syntax of "sudo snort -r snort.log.1770146213," then "enter." After scrolling through the
retrieved output i saw the number of the detected packets to be 1.
>
> <img width="945" height="34" alt="36" src="https://github.com/user-attachments/assets/83754711-618e-40cd-a914-176d3df5d5be" />
> <img width="927" height="303" alt="37" src="https://github.com/user-attachments/assets/1db55d35-a70b-4a67-8a5d-23859b5381b3" />
> <img width="1498" height="106" alt="38" src="https://github.com/user-attachments/assets/4069f667-e250-4418-b2fe-d4528ef7032a" />
> <img width="839" height="184" alt="39" src="https://github.com/user-attachments/assets/f5e8bbb3-beaa-41bf-97bb-a88b2f8f757a" />

> Moving on to the next question i had to figure out the number of detected packets by writing a rule to filter packets with Push-Ack flags and run it against the same pcap file.
To go about this i inputted the command synthax "sudo gedit local.rules," then "enter." On line 9, i entered
"alert tcp any any <> any any (msg: "FLAG TEST"; flags:P,A;sid: 1000003; rev:1;)", clicked "Save," then entered the command syntax
"snort -c local.rules -A full -l . -r task9.pcap," navigated to the directory "TASK-9" within the "Exercise-Files," inputted the command syntax of
"sudo snort -r snort.log.1770148526," then "enter." After scrolling through the retrieved output i saw the number of detected packets to be 218.
>
> <img width="1012" height="51" alt="40" src="https://github.com/user-attachments/assets/f7c6d22b-ec53-446b-9fba-5e76012b38b5" />
> <img width="921" height="879" alt="41" src="https://github.com/user-attachments/assets/0c2e4568-4b63-4d5c-822b-af8a0abd44ab" />
> <img width="1495" height="174" alt="42" src="https://github.com/user-attachments/assets/55bccc6d-df2b-454e-a2b5-d794b2297cad" />
> <img width="1167" height="177" alt="43" src="https://github.com/user-attachments/assets/5d7c6007-4ea2-4e22-9739-5b6d7e8323dc" />
> <img width="853" height="241" alt="44" src="https://github.com/user-attachments/assets/bdb25bb6-7f6b-4213-a6da-9c6bbc3bfead" />

> Moving on to the next question i had to figure out the number of packets that show the same source and destination address by creating a rule to filter UDP packets with the
same source and destination IP and run it against the same pcap file. To go about this i inputted the command syntax "sudo gedit local.rules," then "enter." On line 10, i entered
"alert udp any any <> any any (msg:"UDP Same IP"; sameip; sid:1000004; rev:1;)", clicked "Save," then entered the command syntax
"snort -c local.rules -A full -l . -r task9.pcap," navigated to the directory "TASK-9" within the "Exercise-Files," inputted the command syntax
"sudo snort -r snort.log.1770151832," then "enter." After scrolling through the retrieved output i saw the number of packets that show the same source and destination address
to be 7.
>
> <img width="896" height="25" alt="48" src="https://github.com/user-attachments/assets/c9992e47-6764-453f-9af6-3485321346d4" />
> <img width="918" height="368" alt="49" src="https://github.com/user-attachments/assets/1b3e09ac-d82e-49ae-a4eb-77a5975ba95c" />
> <img width="1508" height="100" alt="50" src="https://github.com/user-attachments/assets/37cac292-7a97-48d0-a340-69d47d52fbab" />
> <img width="1161" height="140" alt="51" src="https://github.com/user-attachments/assets/630787e8-eb64-4fcd-9c88-c7476a0b87a1" />
> <img width="1119" height="149" alt="52" src="https://github.com/user-attachments/assets/9ff6778a-4f12-4c92-803f-eb87016e6716" />
> <img width="522" height="272" alt="53" src="https://github.com/user-attachments/assets/a4dc5282-90c6-4efe-844d-5402642f689e" />
--- 

## Reflection

> This lab provided me with knowledge 
