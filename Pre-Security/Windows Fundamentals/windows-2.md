# [Windows Fundamentals]

**TryHackMe Path**: [Pre-Security]  
**Lab Topic**: [Interacting With Windows-2]  
**Date Completed**: [07/08/2025]

---

## 🧠 Summary

> In this lab, I learned about the System Configuration, the importance of which was to be able to grasp user and resource management, performance optimization, troubleshooting,
problem solving, system security, and just foundational tech skills. Additionally, learn about adjusting the UAC setting. The importance of this is to know about controlling access, preventing
threats, and protecting the system. Learned about the Windows Registry, the importance being that it will help me to control how Windows behaves, secures itself, or fails. Lastly,
I learned about Resource Monitoring. This is important because it will help me to secure and optimize my system.
---

## 🎯 Objectives
- [ ] Launch Windows
- [ ] Navigate through "System Configuration"
- [ ] Learn How To Change UAC settings
- [ ] Navigate through the "Computer Management" App
- [ ] Navigate through "System Information"
- [ ] Navigate through "Resource Monitor"
- [ ] Navigate through "Command Prompt"
- [ ] Navigate through "Registry Editor"
      
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
> [Windows change UAC settings] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20change%20uac%20settings.png)
> [Windows Launch "compmgmt" app] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20compmgmt%20app.png)
> [Windows "GoogleUpdateTaskMachineUA" time] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20googleupdate%20task%20time.png)
> [Windows hidden shared folder location] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20hidden%20shared%20folder.png)
> [Windows Launch "System Information"] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20launch%20system%20information.png)
> [Windows "System Name"] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20system%20name.png)
> [Windows "Compsec" variable value] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20compsec%20value.png)
> [Windows Launch "Resource Monitor"] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20launch%20resmon.png)
> [Windows Launch "cmd"] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20launch%20cmd.png)
> [Windows "ipconfig" command] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20ipconfig%20cmd.png)
> [Windows "ipconfig" full info] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20ipconfig%20info.png)
> [Windows Launch "Registry Editor"] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20registry%20editor%20app.png)
> [Windows "Registry Editor" command] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/windows%20registry%20editor%20command.png)

---

## 📊 Analysis

> After launching Windows for the second time, I started the system configuration by clicking the "start" button, then the "search" icon, and searched for
I clicked "MSConfig" to launch the System Configuration app. Afterwards, I searched through the different services to figure out which manufacturer was for the
service titled "PsShutdown," which was manufactured by System Internals. I then navigated to find who the Windows license was registered to by clicking the tab
titled "Tools," then selecting "About Windows," then clicking Launch, which showed it was licensed under "Windows User." I then figured out the command for Windows
Troubleshooting, which was "C:\Windows\System32\control.exe /name Microsoft.Troubleshooting" by clicking "Windows Troubleshooting" in the "Tools" tab. I then figured
out the command that would open the "Control Panel" by clicking on the "Tools" tab and clicking on "System Properties." What was displayed was "control.exe." After navigating
through the system configurations, I learned the command to change the "UAC Settings" by clicking the "Tools" tab. Next, figured out the command to open "Computer Management"
which was "compmgmt" by inputting it into the search bar and clicking the "Start" button. I then checked what time the "GoogleUpdateTaskMachineUA" task was configured to run every day
by loading up the Computer Management App and clicking the "Task Scheduler" Tab. I scrolled through the different task names and found that it updates at 6:15 am every day. Following, I discovered
the name of a hidden folder that is shared, which was called "sh4redF0Ld3r" by clicking the "Shared Folders" tab, then the sub-tab titled "Shares." After launching the "System Information" app
by searching for the command "msinfo32" in the search bar after clicking the "Start" button, I checked to see what was listed under "System Name," which was "THM-WINFUN2" by navigating to the
"System Summary" tab. From there, I then figured out the value for "CompSec," which was located under "Environment Variables" and was set to "SystemRoot%\system32\cmd.exe." Then I launched
"Resource Monitor" by searching for the command "resmon" in the search bar after clicking the "Start" button. After launching the "Command Prompt" with the command "cmd" i displayed detail
information by inputting the command of "ipconfig /all," then to figure out the full command for the Internet Protocol Configuration" i searched "System Configuration" in the search
bar and selected the "Tools" tab and scrolled then selected "Internet Protocol Configuration," the command was "C:\Windows\System32\cmd.exe /k %windir%\system32\ipconfig.exe." Finally,
I figured out the command to launch the "Registry Editor" by searching "msconfig" in the search bar, launching the "System Configuration" app, selecting the "Tools" tab, and navigating to
"Registry Editor," the command was "C:\Windows\System32\regedt32.exe."

---



## Reflection

> This lab provided knowledge on System Configuration, Adjustment of UAC settings, Computer Management, System Information, Resource Monitoring, the Command Prompt, and the Registry Editor.
