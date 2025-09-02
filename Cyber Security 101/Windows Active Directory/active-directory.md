# [Active Directory]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Active Diretory Basics]  
**Date Completed**: [07/21/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of Windows Domains, which is that most businesses, government agencies, and organizations use Windows Domains to manage computers, users, and
resources centrally through Active Directory (AD). Understanding domains means understanding how most corporate networks function.
> I also learned about the importance of Active Directory, which is that it helps to manage users, devices, and resources, detect and prevent identity-based attacks, understand how to simulate
real-world attacks, and, finally, it is required for most IT/cyber jobs that require AD knowledge.
> I then learned about the importance of Group Policy, which was that it helps to enforce password, lockout, and device polices accross the organization, set up hundreds of systems from one
central location, understand what settings were pushed and when, limit who can do what on which machines, and finally reduce manual misconfiguration or policy drift.
Next, I learned about the importance of Authentication Methods, which help protect accounts and systems from unauthorized access. Almost all IT and cyber roles require it daily,
and can spot unusual login activity or abuse of auth tokens.
> Finally, I learned about the importance of trees, forests, and trusts, which is that trees organize domains with a shared namespace, forests define security boundaries, and trusts allow cross
-domain or cross forest access (can be exploited if misconfigured).


## 🎯 Objectives
- [ ] Launch THM AttackBox
- [ ] Learn about Windows Domains
- [ ] Learn about Active Directory
- [ ] Learn how to manage users in AD
- [ ] Learn how to manage computers in AD
- [ ] Learn about Group Policies
- [ ] Learn about Authentication Methods
- [ ] Learn about Trees, Forests, and Trusts

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
> ["Group Policy Management launch"] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20GPM%20launch.png)
> ["Default Domain Policy"] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20default%20domain%20policy.png)
> ["Password length change"] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20password%20length%20change.png)
> ["Restrict Control Panel Access" created] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/window%20New%20GPO.png)
> ["GPM Editor for GPO created] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20gpm%20editor%20launch.png)
> [Search for policy to apply to created GPO] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20search%20for%20policy%20for%20gpo.png)
> [Enabling policy to GPO] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20enabling%20policy%20to%20GPO.png)
> [Applying GPO to departments] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20applying%20GPO%20to%20departments.png)


---

## 📊 Analysis

> After launching THM AttackBox, I then launched "Active Directory Users and Computers," right-clicked on the "Sales" folder, and clicked "Delegate Control," which launched the Wizard.
After clicking "Next," I searched for "Phillip" as the delegated user and selected him to manage the password reset for any user in the sales department. I then opened the "Remote Desktop" App
and signed in as "Phillip" by clicking the drop-down "show options" and inputting the computer as "10.10.89.79" and the user name "Phillip" and clicked the "connect" button. I was then
signed in to the user "phillip" and launched the "PowerShell" app I then inputted the code "Set-ADAccountPassword sophie -Reset -Newpassword (ReadHost -AsSecureString -Prompt 'NewPassword')
-Verbose" press "enter and was prompted to create a new password for Sophie. After changing the password for the user "Sophie," I then logged into the user and captured the Flag that was on the
desktop, which was "THM{thanks_for_contacting_support}."
> 
> Next, I created an organizational unit called "Workstations" and clicked the folder "Computers" and selected the computers of: LPT-PHILLIP, LPT-SOPHIE, LPT-THOMAS, PC-CLAIRE, PC-DANIEL,
PC-MARK and PC-MARY then dragged them to the folder titled "Workstations." After creating an organizational unit called "Servers," I then selected the computers of SRV-DB01, SRV-DB02,
and SRV-WEB01 and dragged them into that unit.
> 
After launching the "Group Policy Management" application, I implemented a policy that required all users to have a password with a minimum length of 10 characters. I did this by
right-clicking on "default domain policy" then selecting "edit" option, then clicked the dropdown of the folder titled "Policies" under "Computer Configuration", then the dropdown of the
folder "Windows Settings" then the dropdown of utility "Security Settings," then "Account Policies," then finally selected "Password Policy" and selected "Minimum password length" and changed
The value from 7 to 10.
>
After launching "Group Policy Management," I created a new policy called "Restrict Control Panel Access" because I wanted to restrict access to the control panel across all
machines to only users part of the IT department. I did this by right-clicking "Group Policy Object" and selecting "New." I then clicked on the new policy that was created, right-clicked
on it, clicked "edit," to open the Group Policy Management Editor, then navigated to "Policies," then clicked the drop-down menu to open "Administrative Templates" under the "Policies"
folder. Then clicked on "Control Panel," then right clicked on "Prohibit Access to Control Panel and PC Settings," clicked on "edit," then "enabled," then "apply," then "ok" to save the GPO's
settings. After closing the "Group Policy Management Editor," I then dragged the "Restrict Control Panel Access" to "Management," "Marketing," and "Sales" to restrict access to the control
panel to only the IT department.
>

---

## Reflection

> This lab provided me with knowledge about Windows Domains, Active Directory, how to manage users and computers in AD, about Group Policies and how to create them, and about Authentication
Methods, and about Trees, Forests, and Trusts.

