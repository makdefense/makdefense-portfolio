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

---

## 📊 Analysis

> After launching THM AttackBox, I then launched "Active Directory Users and Computers" right clicked on the "Sales" folder and clicked "Delegate Control" which launched the Wizard.
After clicking "Next," i searched "phillip" as the delegated user and selected him to manage the password reset to any user in the sales department. I then opened "Remote Desktop" App
to then signed in as "phillip" by clicking the drop down "show options" and inputted the computer as "10.10.89.79" and the user name "phillip" and clicked the "connect" button. I was then
signed in to the user "phillip" and launched "powershell" app, i then inputted the code "Set-ADAccountPassowrd sophie -Reset -Newpassword (ReadHost -AsSecureString -Prompt 'NewPassword')
-Verbose" press "enter and was prompted to create a new password to sophie. After changing the password for the user "sophie" i then logged into the user and captured the Flag that was on the
desktop, which was "THM{thanks_for_contacting_support}"
---

## Reflection

> This lab provided me 
