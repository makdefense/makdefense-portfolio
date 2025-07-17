# [Active Directory]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Active Diretory Basics]  
**Date Completed**: [07//2025]

---

## 🧠 Summary

> In this lab, 


## 🎯 Objectives
- [ ] Launch THM AttackBox
- [ ] Learn about Windows Domains
- [ ] Learn about Active Directory
- [ ] Learn how to manage users in AD

---

## 🧰 Tools Used
- THM AttackBox
- Windows
- Powershell

---

## 📸 Screenshots

> [Delegating "phillip" to sales folder] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20delegating%20phillip%20to%20sales%20folder.png)
> [Delegating "phillip" to reset users in sales folder passwords] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20delegating%20phillip%20to%20reset%20users%20passwords.png)
> ["phillip" user sign on] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20phillip%20sign%20on.png)
> [powershell "phillip" resetting "sophie" password] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/powershell%20resetting%20sophie%20password.png)
> ["sophie" sign on] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20sohpie%20signon.png)
> ["sophie" captured flag] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20sophie%20flag.png)
> [Creating OUs] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20creating%20OUs.png)
> [Creating "Workstations" OU] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20workstation%20OU.png)
> [Organizing Workstations] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20organizing%20workstations.png)
> ["Workstations" OU] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20workstations%20list.png)
> ["Servers" OU] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20servers%20list.png)
> []

---

## 📊 Analysis

> After launching THM AttackBox, I then launched "Active Directory Users and Computers" right clicked on the "Sales" folder and clicked "Delegate Control" which launched the Wizard.
After clicking "Next," i searched "phillip" as the delegated user and selected him to manage the password reset to any user in the sales department. I then opened "Remote Desktop" App
to then signed in as "phillip" by clicking the drop down "show options" and inputted the computer as "10.10.89.79" and the user name "phillip" and clicked the "connect" button. I was then
signed in to the user "phillip" and launched "powershell" app, i then inputted the code "Set-ADAccountPassowrd sophie -Reset -Newpassword (ReadHost -AsSecureString -Prompt 'NewPassword')
-Verbose" press "enter and was prompted to create a new password to sophie. After changing the password for the user "sophie" i then logged into the user and captured the Flag that was on the
desktop, which was "THM{thanks_for_contacting_support}."
> 
> Next, i created an organizational unit called "Workstations" and clicked the folder "Computers" and selected the computers of: LPT-PHILLIP, LPT-SOPHIE, LPT-THOMAS, PC-CLAIRE, PC-DANIEL,
PC-MARK, and PC-MARY, then dragged them to the folder titled "Workstations." After creating an organizational unit called "Servers" I then selected the computers of: SRV-DB01, SRV-DB02,
and SVR-WEB01 and dragged them into that unit.
> 
> After launching the "Group Policy Management" application i then implemented a policy where all users had to have a password with the minimum length of 10 characters. I did this by
right-clicking on "default domain policy" then selecting "edit" option, then clicked the dropdown of the folder titled "Policies" under "Computer Configuration" then the dropdown of the
folder "Windows Settings" then the dropdown of utility "Security Settings," then "Account Policies," then finally selected "Password Policy" and selected "Minimum password length" and changed
the value from 7 to 10.

---

## Reflection

> This lab provided me 
