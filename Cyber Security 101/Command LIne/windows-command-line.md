# [Command Line]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Windows Command Line]  
**Date Completed**: [07/26/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of learning basic system information, which is that it helps to fix problems faster, detect threats and protect the system, prevent crashes
and errors, improve performance and efficiency, build skills employers expect, and speak the language of IT. Next i learned about the importance of network troubleshooting by using different
commands, which is that it helps to diagnose problems fast by fixing connection and DNS issues in minutes, it is required for IT, security, and SOC roles, boost security awareness by spotting
suspicious activity and weak configs, helps to understand network architecture by learning how systems communicate at all levels, and save time with quick commandline tools. Following, I learned
the importance of file and disk management, which is that it prevents data loss by backing up and restoring files with confidence, boosts system performance by keeping drives clean and fast, enhances
security by detecting shady files or access permissions issues, enables automation by scripting tasks to save time, and improves organization. Finally, I learned about the importance of task and
process management, which is that it helps with troubleshooting by fixing crashes, freezes, and slowness, helps with cybersecurity by detecting unauthorized or malicious activity, and helps with performance optimization by closing resource hogs and speeding up your system.


---

## 🎯 Objectives
- [ ] Launch THM AttackBox
- [ ] Learn Basic System Information
- [ ] Learn about Network Troubleshooting by using different commands
- [ ] Learn about File and Disk Management
- [ ] Learn about Task and Process Management

---

## 🧰 Tools Used
- THM AttackBox
- Windows CommandLine

  
---

## 📸 Screenshots

> [Windows version] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20command%20line%20OS%20version.png)
> [Windows System Info] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20command%20line%20sysinfo.png)
> [Windows Subnet Mask] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20command%20line%20subnet%20mask.png)
> [Windows MAC address] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20command%20MAC%20addy.png)
> [Windows directories] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20command%20all%20cds.png)
> [Windows process listening on port 3389] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20name%20of%20process%20listening.png)
> [Windows Treasure directory] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20Treasure%20directory.png)
> [Windows Flag] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20command%20line%20flag.png)

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

> This lab provided me with knowledge about Basic System Information, network troubleshooting using different commands, File and Disk Management, and Task and Process Management.
