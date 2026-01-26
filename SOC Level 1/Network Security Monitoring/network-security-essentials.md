# [Network Traffic Analysis]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Network Security Essentials]  
**Date Completed**: [01/25/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of the key aspects of network security essentials and how to monitor and protect against adversaries, as these skills form the foundation
of effective cybersecurity defense. Understanding network security helps prevent unauthorized access, data breaches, and system compromise by identifying vulnerabilities before
they can be exploited. Monitoring network activity enables early detection of suspicious behavior, such as malware communications or unauthorized connections, allowing threats to
be contained before they cause significant damage. Additionally, knowing how adversaries operate on a network prepares security professionals to respond quickly and effectively
during incidents, reducing downtime and protecting sensitive data.

---

## 🎯 Objectives
- [ ] Understand what a network is and identify its key components.
- [ ] Explore the concept of the network perimeter and its importance.
- [ ] Identify the key perimeter threats.
- [ ] Examine the firewall logs to monitor normal and suspicious logs.

---

## 🧰 Tools Used
- THM Splunk
- THM Mozilla Firefox
- THM Terminal

---

## 📊 Analysis & Screenshots

*** Network Perimeters: Monitoring and Protecting ***

> For this room, I first answered a few questions within the Network Perimeters: Monitoring and Protecting section. For the first question, I examined the firewall_log.txt file
located in the Perimeter_logs folder to determine which IP address was performing the port scan. To do this, I navigated to the desktop and opened the firewall_log.txt file, then
reviewed the log entries to identify the IP address conducting the scan. After analyzing the logs, I determined that the IP address used for port scanning was 203.0.113.10.
>
> <img width="371" height="193" alt="1" src="https://github.com/user-attachments/assets/cff5f7cb-d197-45a7-8f10-8c84d0aad49b" />
> <img width="468" height="337" alt="2" src="https://github.com/user-attachments/assets/13b8c4a2-72b4-43c8-ab3e-1880aa74ad23" />
> <img width="463" height="249" alt="3" src="https://github.com/user-attachments/assets/c063b518-60b3-45b6-a6ca-34b4abb06311" />
> <img width="653" height="276" alt="4" src="https://github.com/user-attachments/assets/a2c966ea-ec6c-4ef8-a9c5-f7b2a1a0d667" />

> Moving on to the next question, I investigated the waf_logs.txt file to determine which single source IP address was responsible for all blocked web attacks. To do this, I
navigated back to the desktop and opened the waf_logs.txt file, then scrolled through the log entries. On line 102, I observed that the IP address 198.51.100.12 was blocked for
all web attacks.
>
> <img width="534" height="245" alt="5" src="https://github.com/user-attachments/assets/c9420a9d-fab1-4a68-b0d2-71ac7581a9c9" />
> <img width="800" height="354" alt="6" src="https://github.com/user-attachments/assets/7c3a5ea8-2abf-4d01-a20f-99ad9ab4d92a" />

> For the second-to-last question in this section, I investigated the vpn_logs.txt file to determine how many brute-force attempts had failed. To do this, I navigated back to the
Perimeter_logs folder and opened the vpn_logs.txt file. After reviewing the log entries, I counted a total of 90 failed attempts out of 135 total attempts.
>
> <img width="590" height="311" alt="7" src="https://github.com/user-attachments/assets/fbf8db8d-bf9a-4a12-b762-2ed45e492f7e" />
> <img width="867" height="207" alt="8" src="https://github.com/user-attachments/assets/355192ce-4338-42b0-b6d6-758976cc7bfc" />

> Moving on to the final question of this section, I had to identify the suspicious IP address that was attempting a brute-force attack against the VPN gateway. To do this, I
reviewed the 135 logged attempts, examined a blocked attempt on line 134, and identified the suspicious IP address as 45.137.22.13.
>
> <img width="672" height="447" alt="9" src="https://github.com/user-attachments/assets/4a4055d9-0ecd-4ff1-b6d6-1ba1d22f2efd" />

*** Perimeter Logs: Investigating the Breach ***

> Moving on to this section, I answered several questions within the Perimeter Logs: Investigating the Breach section. For the first question, I examined the firewall logs to
determine which external IP address performed the most reconnaissance. To do this, I launched Mozilla Firefox and navigated to http://10.82.172.247:8000 to access Splunk. I then
selected Search & Reporting, entered index="network_logs" into the search bar, and filtered by sourcetype, firewall_logs, and src_ip. This analysis revealed that the IP address
203.0.113.45 conducted the most reconnaissance activity.
>
> <img width="722" height="143" alt="10" src="https://github.com/user-attachments/assets/aa60a373-bc66-41d5-a485-1029c9be44f3" />
> <img width="481" height="175" alt="11" src="https://github.com/user-attachments/assets/294abee7-4553-4a02-9aac-fa441b35cdee" />
> <img width="443" height="177" alt="12" src="https://github.com/user-attachments/assets/97a71993-e86a-4497-b4b4-6064785d98a8" />
> <img width="314" height="139" alt="13" src="https://github.com/user-attachments/assets/68c48c19-9b84-48bd-977b-ddc248246dd4" />
> <img width="421" height="174" alt="14" src="https://github.com/user-attachments/assets/5bb911ff-91fd-46d7-96c0-5c55c0accc1f" />
> <img width="911" height="353" alt="15" src="https://github.com/user-attachments/assets/427f7fde-f215-423d-ae66-050688e4a9c1" />

> Moving on to the next question, I had to determine which internal host was targeted by scans within the same firewall log file. To do this, I navigated to the left panel in
Splunk and selected dst_ip, then clicked on the IP address 10.0.0.20. I then navigated to the center of Splunk, selected an event associated with the same IP address, and observed
that it was the host targeted by scans, as it showed ALLOW for the TCP protocol.
>
> <img width="932" height="500" alt="16" src="https://github.com/user-attachments/assets/2f3362fd-045d-4175-bedc-21db6133e496" />
> <img width="726" height="369" alt="17" src="https://github.com/user-attachments/assets/ebb10923-9bad-4511-bce6-1a4c519aed9e" />

> Moving on to the next question, I investigated the VPN logs using the Splunk application to determine which username was targeted. To do this, I entered index="network_logs"
into the search field, navigated to the left panel, selected sourcetype, then vpn_logs, and finally applied the username filter. This analysis revealed that the targeted username
was svc_backup.
>
> <img width="948" height="599" alt="18" src="https://github.com/user-attachments/assets/046e75b2-2c76-4126-aa65-7993bb945c70" />
> <img width="948" height="374" alt="19" src="https://github.com/user-attachments/assets/5c0d54e1-784d-4aa3-9565-71a2a96b1268" />

> For the next question, I had to determine the internal IP address that was assigned after a successful VPN login. To do this, I navigated to the left panel in Splunk, selected
the result filter, chose SUCCESS, and then selected the IP address 10.8.0.23. I then navigated to the center panel, opened the event associated with the same IP address, and
confirmed that it was the internal IP assigned after a successful VPN login.
>
> <img width="964" height="361" alt="20" src="https://github.com/user-attachments/assets/92da93cb-ee9c-4b9a-9ef4-e4941fc4d911" />
> <img width="647" height="386" alt="21" src="https://github.com/user-attachments/assets/f88ece39-9761-4b90-ba23-97030678fb37" />
> <img width="1097" height="514" alt="22" src="https://github.com/user-attachments/assets/40f9a370-a87d-4f29-a385-b19d4e1dab04" />

> Moving on to the final set of questions for this room, I investigated IDS log events using Splunk to determine which port was used for lateral SMB attempts. To do this, I
entered index="network_logs" sourcetype=ids_logs into the Splunk search field. I then navigated to the left panel, selected dst_port, and chose 445. Next, I reviewed an event
associated with port 445 in the center panel and observed that it was classified as Suspicious Activity, indicating lateral SMB attempts.
>
> <img width="619" height="291" alt="23" src="https://github.com/user-attachments/assets/1d47a48f-7b1b-46d7-b295-b3694103887b" />
> <img width="847" height="527" alt="24" src="https://github.com/user-attachments/assets/ac4ff3d8-e93a-400d-b9fa-8c31715aa46f" />
> <img width="747" height="482" alt="25" src="https://github.com/user-attachments/assets/6bb8f276-98ee-4017-b867-482367bc503c" />

> For the next question regarding the IDS logs, I had to determine which host was beaconing to the command-and-control (C2) server. To do this, I navigated to the Splunk search
field and entered index="network_logs" sourcetype=ids_logs. I then identified an event with the alert ET TROJAN Possible C2 Beaconing, expanded the event details, and observed
that the host involved was the IP address 10.0.0.60.
>
> <img width="493" height="236" alt="26" src="https://github.com/user-attachments/assets/f2b258b7-b6a3-45ed-a50c-65f98c88f9c5" />
> <img width="801" height="383" alt="27" src="https://github.com/user-attachments/assets/6b20e8e1-f262-4fd4-af02-ef0b23509b9e" />

> Moving on to the final two questions, I had to determine which IP address was associated with command-and-control (C2) activity and which host exhibited exfiltration attempts.
To do this, I navigated to the left panel in Splunk, selected the classification filter, and then expanded a relevant event in the center panel. This analysis revealed that the IP
address associated with C2 activity was 198.51.100.77, and the host that showed exfiltration attempts was 10.0.0.51.
>
> <img width="918" height="574" alt="28" src="https://github.com/user-attachments/assets/6cfbf141-9bde-4951-b5f3-2937b90f8a48" />
> <img width="789" height="385" alt="29" src="https://github.com/user-attachments/assets/2bfd5b6c-56ef-4034-ba10-c4e254912dd9" />

---

## Reflection

> This lab strengthened my understanding of network security fundamentals, including monitoring techniques and defenses against adversarial activity.
