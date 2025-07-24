# [Command Line]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Windows Command Line]  
**Date Completed**: [07//2025]

---

## 🧠 Summary

> In this lab, I learned about the importance



## 🎯 Objectives
- [ ] Launch THM AttackBox
- [ ] Learn Basic System Information
- [ ] Learn about Network Troubleshooting by using different commands
- [ ] 


---

## 🧰 Tools Used
- THM AttackBox
- 


---

## 📸 Screenshots

> 


---

## 📊 Analysis

> After launching AttackBox, i established an SSH connection with the IP "10.10.93.24," by logging in with the SSH client "user" and with the password "Tryhackme123!". Next i went ahead
and checked the OS version by inputting the command "ver," which then displayed "Microsoft Windows [Version 10.0.20348.2655]."
> I then proceeded to check more in-depth information about the system by inputting the command "systeminfo." Next i inputted "cls" to clear everything up and then inputted "ipconfig" to
figure out the subnet mask which was "255.255.0.0." Then to figure out the MAC address i inputted "ipcong /all" which displayed physical address as "02-14-A0-37-BC-B3." Moved on to figuring
out the name of the process listening on port 3389 by inputting "netstat -abon", which displayed "TermService".
> Next i wanted to find the contents in "C:\Treasure\Hunt" so in order to do that i inputted "cls" to clear all inputs then i typed "cd .." then enter twice to go back twice then typed "dir"
to view all child directories and located the cd called "Treasure." Next i inputted "cd Treasure" then typed enter after locating the Treasure directory. Next i inputted "dir" to view what was
in the "Treasure's" directory, the child directory "Hunt" popped up so i then inputted "cd Hunt" then "dir" to view what flag was in the directory and saw "18 flag.txt" pop up. So to display the
flag i typed "type flag.txt" which displayed the flag details "THM{CLI_POWER}."



---

## Reflection

> This lab provided me with knowledge about 
