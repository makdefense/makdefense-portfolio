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

> [Launching Remmina] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/launching%20remmina.png)
> [Signing in using SSH credentials] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/remmina%20ssh%20credentials%20sign%20in.png)
> [Launching PowerShell] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/command%20line%20powershell%20launch.png)
> [Retrieving list of "Remove" commands] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/powershell%20list%20of%20%22Remove%22%20commands.png)
> [Retrieving list of all aliases] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/example%20usage%20for%20the%20cmdlet%20New-LocalUser.png)
> [Finding alias with counterpart "echo"] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/powershell%20echo%20and%20its%20command.png)
> [Retrieving example usage for cmdlet "New-LocalUser"] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/powershell%20example%20usage%20for%20cmdlet.png)
> [Display the contents of "C:\Users" directory] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/powershell%20using%20command%20to%20display%20contents.png)
> [Display the contents of "captain"] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/powrshell%20listing%20all%20child%20directories.png)
> [Selecting "Documents" directory] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/powrshell%20listing%20all%20child%20directories.png)
> [Creating new item (directory)] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/powershell%20creating%20new%20item.png)
> [Creating new file in item (directory)] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/powershell%20creating%20new%20file%20in%20new%20item.png)
> [Selecting "captain-cabin" directory] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/selecting%20captain-cabin%20directory.png)
> [Retrieving contents of "captain-hat.txt" file] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/getting%20contents%20of%20file.png)
> 

---

## 📊 Analysis

> After launching AttackBox, i connected to the VM via SSH using the Remmina client by entering the IP address "10.10.8.156" into the bar at the top of the Remmina client then clicking enter. Next
i signed into the client with the creditianls of "captain" for the username and "JollyR0ger#" for the password. I then launched PowerShell by using the target VM's command prompt by typing "powershell"
and clicking enter. Next i figured out how to retrieve a list of commands that start with the verb "Remove" by inputting the commmand "Get-Command -Name "Remove*"" into PowerShell. I then inputted the
command "Get-Alias" to list all aliases available to find the alias with the counterpart of "echo" which was the command "Write-Output." Following i then figured out the command to retrieve some example usage
for the cmdlet "New-LocalUser" by using the "Get-Help" command which provides detailed information about cmdlets. The entire command i inputted to display it was "Get-Help New-LocalUser -examples."
> Next i practiced navigating through the system with powershell using command "Get-ChildItem," i specifically used that command to display the contents of the "C:\Users" directory by inputting "Get-ChildItem
-Path C:\Users" and clicking enter. What was displayed was 4 users for that specific directory. I then learned how to work with files, specifically i selected the user "captain" by typing "Get-ChildItem, which listed
all the folders for that user. I then selected the specific file titled "Documents" by typing "Set-Location -Path ".\Documents"." I then created a new item (directory) called "captain-wardrobe in the document folder by typing
"New-Item -Path ".\captain-cabin\captain-wardrobe" -ItemType "Directory"." Next i created a file within that directory called "captain-boots.txt" by typing
"New-Item -Path ".\captain-cabin\captain-wardrobe\captain-boots.txt" -ItemType "File"." I then copied one directory and moved it to another directory by typing
"Copy-Item -Path .\captain-cabin\captain-hat.txt -Destination .\captain-cabin\captain-hat2.txt and clicking enter. Followed by typing "Get-ChildItem -Path ".captain-cabin\"." To display what was moved to that directory.
Next i then selected that directory by typing "Set-Location -Path .\captain-cabin" then clicked enter, followed by typing Get-Content -Path ".\captain-hat.txt" to display the contents of the .txt file.
> Next i practiced piping, filtering, and sorting data within specific child directories. 


---

## Reflection

> This lab provided me with knowledge about 
