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

> Moving on to the next question i had to figure out the number of generated alerts 

























--- 

## Reflection

> This lab provided me with knowledge 
