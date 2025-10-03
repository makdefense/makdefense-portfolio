# [Defensive Security Tooling]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [REMnux: Getting Started]  
**Date Completed**: [10/03/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding the tools inside the REMnux VM, which bundles a practical toolset you'll use to analyze malware and suspicious artifacts safely.
Knowing those tools turns noisy samples into actionable intelligence, documents for investigations, and repeatable workflows that you can showcase on your resume. Next, I learned the importance of
understanding the tools used to analyze memory images, which is that tools that analyze memory images let you find and prove active compromises that disk forensics alone
will miss. They are essential for incident response, threat hunting, and gathering real forensic evidence. I then learned about the importance of understanding how to simulate a fake network to aid in the
analysis, which is that a fake (isolated) network lets you safely observe real malware/attack behavior. force network interactions (C2, DNS, HTTP), collect high-fidelity telemetry (pacaps, logs, process+
net timelines), test detections, and build repeatable evidence - all without risking your home/office/production network. Finally, I learned about the importance of understanding the tools used to analyze
potentially malicious documents effectively, which is that knowing the right tools and workflows turns a scary, unknown file into actionable intelligence - you can identify C2/network callbacks, extract
IOCs, prove compromise, tune detections, and contain incidents quickly.

---

## 🎯 Objectives
- [ ] Learn about the tools inside the REMnux VM
- [ ] Learn how to use tools to analyze potentially malicious documents effectively
- [ ] Learn how to simulate a fake network to aid in the analysis
- [ ] Learn about the tools used to analyse memory images

---

## 🧰 Tools Used
- THM AttackBox
- THM REMnux VM
  
---

## 📊 Analysis & Screenshots

*** File Analysis ***

> After reading the sections within REMnux: Getting Started, I was assigned a task in the file analysis section to determine which Python tool analyzes OLE2 files. To figure this out, I tested the command
I ran "oledump.py" on the document "agenttesla.xlsm" and saw that it basically analyzed the file by extracting 6 data streams.

> <img width="749" height="308" alt="rn1" src="https://github.com/user-attachments/assets/ab2793f9-c1d4-4eaa-9e4d-6a8ae7bef1ac" />

> Next, I had to determine which tool parameter allows you to select a specific data stream from the file you are using. To figure this out, I input the command "oledump.py agenttesla.xlsm -s 4,"
then "enter," which basically dumped the entire stream of data within A4.

> <img width="796" height="794" alt="rn2" src="https://github.com/user-attachments/assets/7855a065-d59f-45fa-84a4-3a2c67a3fc9c" />

> I then had to continue to use the tool to scan another file named "possible_malicious.docx" which was in the "/home/ubuntu/Desktop/tasks/agenttesla/" directory and figure out how many data streams were
presented for the file. To figure this out, I first input the command "cd /Desktop/tasks/agenttesla," then "enter" to get to that directory, then input the command "oledump.py
possible_malicious.docx," then "enter." This then retrieved 16 data streams.

> <img width="791" height="333" alt="rn3" src="https://github.com/user-attachments/assets/abaf3978-cb87-4146-8c30-9d134730902c" />

> I then had to figure out which data stream number indicated that a macro was present. To figure this out, I just looked at all 16 of the data streams and located the data stream that began with a capital
"M," and saw that it was data stream number 8.

> <img width="477" height="195" alt="rn4" src="https://github.com/user-attachments/assets/b5ce94a0-775b-4476-b2b0-8d1918e18f16" />

*** Fake Network to Aid Analysis ***

> For my next task, I had to download and scan the file named "flag.txt" to retrieve a flag. To go about this, I first had to change the inetsim configuration by running the command
"sudo nano /etc/inetsim/inetsim.conf," then "enter."

> <img width="610" height="85" alt="rn5" src="https://github.com/user-attachments/assets/c7211ac6-bd56-4c96-bd81-e16241920bea" />

> I then had to change dns_default_ip to "10.201.74.165," then "^+X" to save and close the nano editor.

> <img width="433" height="297" alt="rn6" src="https://github.com/user-attachments/assets/39530699-2e03-4661-95b7-b2b43848edb4" />
> <img width="607" height="337" alt="rn7" src="https://github.com/user-attachments/assets/b257a31a-5161-4106-97c7-bf3c841ab1b2" />

> To make sure the dns_default_ip was set, I input the command "cat /etc/inetsim/inetsim.conf | grep dns_default_ip," then "enter," and saw that the dns_default_ip was set to "10.201.74.165".

> <img width="733" height="104" alt="rn8" src="https://github.com/user-attachments/assets/4955fa3e-f9e6-4e31-af25-104f18913198" />

> I then ran the command "sudo inetsim," then "enter" to start the tool.

> <img width="625" height="233" alt="rn9" src="https://github.com/user-attachments/assets/07e403da-c2bf-4040-ba15-e5a143e8284a" />

> After starting the tool, I entered the command "sudo wget https://10.201.74.165/flag.txt --no-check-certificate" and then pressed "Enter" to download the "flag.txt" file.

> <img width="1113" height="275" alt="rn10" src="https://github.com/user-attachments/assets/ef808d8e-88d4-461f-95cc-31edc117936b" />

> After downloading the file, I went to the "Desktop" and double-clicked on the "root home" folder, then double-clicked on the "flag.txt" file to retrieve the flag "Tryhackme{remnux_edition}."

> <img width="970" height="620" alt="rn11" src="https://github.com/user-attachments/assets/1663538f-1815-463e-92ee-892fa1a21945" />

> Then I had to figure out the URL method used to download the "flag.txt" file. To figure this out, I had to stop the "inetsim" tool to get the generated report, which was "report.2112.txt"

> <img width="698" height="214" alt="rn12" src="https://github.com/user-attachments/assets/6975de1a-25c7-4c17-99d2-fc9c13d61f5e" />

> I then had to input the command "sudo cat /var/log/inetsim/report/report.2112.txt," then "enter," which retrieved the HTTPS connection method as "GET"

> <img width="1442" height="302" alt="rn13" src="https://github.com/user-attachments/assets/a076a045-26d5-47bc-b56d-230cd67c5f76" />

*** Method Investigation: Evidence Preprocessing ***

> For my next task, I had to preprocess the evidence using various commands. For the first question, I had to figure out the plugin that lists processes in a tree based on their parent process ID. To
figure this out, I first had to get to the root directory by inputting the command "sudo su," then "enter." I then input the command "cd home/ubuntu/Desktop/tasks/Wcry_memory_image/," then "enter" to get
to that directory.

> <img width="811" height="44" alt="rn13" src="https://github.com/user-attachments/assets/b9cd9f59-69c6-4187-bd48-50981ce7040c" />

> I then input the command "vol3 -f wcry.mem windows.pstree.PsTree," followed by "enter," which led me to discover that the "PsTree" plugin lists processes in a tree based on their parent process ID.

> <img width="1217" height="476" alt="rn14" src="https://github.com/user-attachments/assets/882eea90-3678-4b2f-9b1e-2b35bf19f6c3" />

> Next, I had to determine the plugin used to list all currently active processes on the machine. To figure this out, I just input the command "vol3 -f wcry.mem windows.pslist.PsList," then "enter"
which led me to figure out that the "PsList" plugin lists all currently active processes in the machine.

> <img width="1293" height="452" alt="rn15" src="https://github.com/user-attachments/assets/070094c2-ca99-4fe1-92a0-cf4977742874" />

> I then had to determine the first process identified as suspected of having injected code. To figure this out, I had to run vol3 with the Malfind parameter. So I input the command
"vol3 -f wcry.mem windows.Malfind," then "enter," and saw that the first process was "csrss.exe."
> I then had to determine the second process that was identified as potentially having injected code. To figure this out, I just scrolled down to the second process, the "exe" process, and saw that it was
"winlogon.exe."

> <img width="1156" height="335" alt="rn16" src="https://github.com/user-attachments/assets/7cef1258-4a3b-4557-8fe1-7f2844ebd41c" />

> Finally, I had to determine the path of the binary file "@WanaDecryptor@.exe." To figure this out, I had to run the command "vol3 -f wcry.mem windows.dlllist.DllList," then "enter," which retrieved the
path "C:\Intel\ivecuqmanpnirkt615".

> <img width="1126" height="117" alt="rn17" src="https://github.com/user-attachments/assets/ef94f2ac-4db7-4f93-b391-f2b4aa618874" />
> <img width="958" height="135" alt="rn18" src="https://github.com/user-attachments/assets/8c4c13c4-657a-4181-b43c-aa21000effc0" />

---

## Reflection

> This lab provided me with knowledge about using the tools inside the REMnux VM.

