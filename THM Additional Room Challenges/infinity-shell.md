# [THM Additional Room Challenges]

**TryHackMe Path**: [Learn]  
**Lab Topic**: [Infinity Shell]  
**Date Completed**: [07/05/2026]

**Lab Link**: [https://tryhackme.com/room/hfb1infinityshell]

---

## 🧠 Summary

> In this lab, I investigated and analyzed the traces of an attack involving an implanted web shell. The investigation focused on identifying how the attacker used the web shell
to interact with the compromised system, execute commands, and move through the environment.

I reviewed evidence related to the attacker’s activity, including command execution, suspicious web requests, file access, and potential post-exploitation behavior. By analyzing 
these traces, I was able to better understand how the attacker maintained access, what actions were performed after the web shell was implanted, and what impact the compromise 
may have had on the system.

Overall, this lab helped strengthen my ability to investigate web shell activity, follow an attacker’s actions through logs, and recognize indicators of compromise related to web-
based attacks.


---

## 🎯 Objectives
- [ ] Complete "Infinity Shell" Challenge
      
---

## 🧰 Tools Used
- THM AttackBox
- Terminal
- CyberChef

---

## 📊 Analysis & Screenshots

*** Inifnity Shell ***

> In this section, I was tasked with investigating and analyzing the traces of an attack from an implanted web shell to retrieve a flag. I first launched the machine attached to
the room. Then, I opened the terminal and navigated to the "CMSsite-master" directory. After listing all files within that directory, I navigated to the "img" directory and
listed all files to verify that the "images.php" file was there.
I then navigated to the "apache2" directory, which was located in the "/var" main directory. After confirming that the "other_vhosts_access.log.1" file was there, I entered the
following command:
cat other_vhosts_access.log.1 | grep 'images.php'
This allowed me to retrieve the Base64 input, which I then decoded in CyberChef. After decoding the Base64 string, I was able to retrieve the hidden flag:
THM{sup3r_34sy_w3bsh3ll}
>
> <img width="742" height="592" alt="1" src="https://github.com/user-attachments/assets/f042fbc3-3a30-42c6-9bba-9598dc632a07" />
> <img width="1040" height="806" alt="2" src="https://github.com/user-attachments/assets/566379f0-a181-4126-a573-000195d33faf" />
> <img width="948" height="120" alt="3" src="https://github.com/user-attachments/assets/1159b9e4-6e46-44f2-8f28-b001bde05994" />
> <img width="882" height="305" alt="4" src="https://github.com/user-attachments/assets/744f733e-ac56-46b5-b568-d6c34628e6f0" />
> <img width="1503" height="816" alt="5" src="https://github.com/user-attachments/assets/78cfff58-b861-4e2d-ac5f-bde9f3ab1578" />
> <img width="1754" height="715" alt="6" src="https://github.com/user-attachments/assets/8bcb2fb8-7fb4-4f85-90be-f5db09f02c11" />

--- 

## Reflection

> This lab strengthened my ability to investigate web shell activity by analyzing the traces left behind after a system was compromised. I practiced identifying suspicious web
requests, command execution, file access, and other post-exploitation behavior that helped reveal how the attacker interacted with the target environment.

The lab also helped me better understand how attackers use implanted web shells to maintain access, execute commands, and perform further actions on a compromised server. By 
reviewing the available evidence, I was able to follow the attacker’s activity and connect different events to build a clearer attack timeline.

Overall, this lab improved my ability to recognize indicators of compromise, analyze web-based attack activity, and explain how a web shell can be used during an intrusion. It 
also reinforced the importance of strong web server security, proper file upload controls, log monitoring, and quick detection of suspicious behavior.
