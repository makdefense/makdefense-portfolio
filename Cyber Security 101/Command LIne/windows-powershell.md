# [Command Line]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Windows PowerShell]  
**Date Completed**: [07//2025]

---

## 🧠 Summary

> In this lab, I learned about 


---

## 🎯 Objectives
- [ ] Launch THM AttackBox
- [ ] Learn PowerShell Basics
- [ ] Learn to Navigate the File System and Work with Files
- [ ] Learn about Piping, Filtering, and Sorting Data

---

## 🧰 Tools Used
- THM AttackBox
- Windows PowerShell
  
---

## 📸 Screenshots

> [] 

---

## 📊 Analysis

> After launching AttackBox, i connected to the VM via SSH using the Remmina client by entering the IP address "10.10.8.156" into the bar at the top of the Remmina client then clicking enter. Next
i signed into the client with the creditianls of "captain" for the username and "JollyR0ger#" for the password. I then launched PowerShell by using the target VM's command prompt by typing "powershell"
and clicking enter. Next i figured out how to retrieve a list of commands that start with the verb "Remove" by inputting the commmand "Get-Command -Name "Remove*"" into PowerShell. I then inputted the
command "Get-Alias" to list all aliases available to find the alias with the counterpart of "echo" which was the command "Write-Output." Following i then figured out the command to retrieve some example usage
for the cmdlet "New-LocalUser" by using the "Get-Help" command which provides detailed information about cmdlets. The entire command i inputted to display it was "Get-Help New-LocalUser -examples."
> Next i practiced navigating through the system with powershell using command "Get-ChildItem," i specifically used that command to display the content of the "C:\Users" directory by inputting "Get-ChildItem
-Path C:\Users" and clicking enter. What was displayed was 4 items for that specific directory.
> 

---

## Reflection

> This lab provided me with knowledge about 
