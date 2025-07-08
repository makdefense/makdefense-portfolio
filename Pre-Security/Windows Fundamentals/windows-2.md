# [Windows Fundamentals]

**TryHackMe Path**: [Pre-Security]  
**Lab Topic**: [Interacting With Windows-2]  
**Date Completed**: [07/08/2025]

---

## 🧠 Summary

> In this lab, I learned how to 

---

## 🎯 Objectives
- [ ] Launch Windows
- [ ] Navigate through System Configuration
      
---

## 🧰 Tools Used
- THM AttackTheBox
- Windows

---

## 📸 Screenshots

> [Windows how to launch system config] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Windows%20system%20config.png)
> [Windows "PsShutdown" Manufacturer] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20PsShutdown%20manufacturer.png)
> [Windows User License] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20registered%20licensee.png)
> [Windows Troubleshooting command] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20trouble%20shooting%20command.png)
> [Windows to open "Control Panel"] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20command%20for%20control%20panel.png)

---

## 📊 Analysis

> After launching Windows for the second time i start the system configuration by clicking the "start" button then the "search" icon and searched for
"MSconfig" and clicked it to launch the system configuration app. Afterwards i searched through the different services to figure out with manufacture was for the
service titled "PsShutdown" which was manufactured by System Internals. I then navigated to find who the windows license was registered to by clicking the tab
titled "Tools" then selecting "About Windows" then clicked launch which showed it licensed under "Windows User." I then figured out the command for Windows
Troubleshooting which was "C:\Windows\System32\control.exe /name Microsoft.Troubleshooting" by clicking "Windows Troubleshooting" in the "Tools" tab. I then figured
out the command that would open the "Control Panel" by clicking on the "Tools" tab and clicking on "System Properties" what was displayed was "control.exe."

---

## Reflection

> This lab provided 
