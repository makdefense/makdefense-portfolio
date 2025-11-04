# [Network Security and Traffic Analysis]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Traffic Analysis Essentials]  
**Date Completed**: [11/04/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding network security operations, which is the front line that keeps your organization online, resilient, and secure - they detect and stop attacks,
limit damage, restore services quickly, and turn telemetry into decisions. Knowing it gives you skills that directly reduce risk and make you valuable in any security team. I then learned about the
importance of understanding network traffic analysis, which is the single best way to see what's actually happening on your network - attackers, data flows, lateral movement, exfiltration, and stealthy
command-and-control all leave network traces. Knowing NTA gives you detection, hunting, and forensic skills that turn raw packets into actionable evidence.

---

## 🎯 Objectives
- [ ] Learn about Network Security Operations
- [ ] Learn about Network Traffic Analysis

---

## 🧰 Tools Used
- THM Static Site
  
---

## 📊 Analysis & Screenshots

*** Traffic Analysis ***

> For this room, I had to simulate a traffic analysis operation and find flags. For the first question, I had to simulate identifying and filtering malicious IP addresses. So the first thing I did was
launch the Static Site. I then had to click the "Start Network Traffic" button.

> <img width="885" height="646" alt="tae1" src="https://github.com/user-attachments/assets/cbbc5c40-8702-4668-b27e-dfe323d1055f" />

> After clicking that button, I had to click the "Restore the network and record the traffic for further investigation" button.

> <img width="798" height="598" alt="tae2" src="https://github.com/user-attachments/assets/ebd9bd8f-eb7b-4d21-be54-eca392a50d05" />

> I then had to select 2 IP addresses to filter from the network. The two IP addresses I selected were "10.10.99.99" and "10.10.99.62." After choosing the two IP addresses, I then had to click the
"Restart Network Traffic" button. This then retrieved the first flag "THM{PACKET_MASTER}."

> <img width="806" height="598" alt="tae3" src="https://github.com/user-attachments/assets/d9acc780-97ed-4cad-b1ff-fa0d85e677f2" />
> <img width="852" height="519" alt="tae4" src="https://github.com/user-attachments/assets/4f1ff801-0e3c-4d8d-a12c-b2b03957c026" />

> Moving on to the second question, I had to simulate the identification and filter malicious IP and Port addresses. To carry this out, I clicked the "Next Level" button. Then selected the three ports
"4444," "7777," and "2222." After selecting the three IP and Port addresses, I then had to click the "Restart Network Traffic" button.

> <img width="844" height="592" alt="tae5" src="https://github.com/user-attachments/assets/0f38a431-002f-4fc5-956b-4bc00e89bf70" />

> After clicking that button, it then retrieved the second and final flag, "THM{DECTECTION_MASTER}."

> <img width="848" height="599" alt="tae6" src="https://github.com/user-attachments/assets/ecfea5d5-bb69-486a-a09a-377391133321" />

---

## Reflection

> This lab provided me with knowledge of Network Security and Traffic Analysis foundations and hands-on experience probing for network anomalies.
