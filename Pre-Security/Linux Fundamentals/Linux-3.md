# [Linux Fundamentals]

**TryHackMe Path**: [Pre-Security]  
**Lab Topic**: [Interacting With Linux-3]  
**Date Completed**: [07/05/2025]

---

## 🧠 Summary

> In this lab, I used TryHackMe to launch Ubuntu Linux to implement the Nano command. The importance of my using the Nano command was because I'm still learning Lunix and Nano isnt as
complicated as VIM, and it was ideal for my situation since I signed in using SSH. I also implemented the Wget command to download files from the internet; the importance of me doing this
was just being able to learn the concept of getting files from an HTTP web server. Secondly, I located a few processes in Linux, the importance of me doing so was to learn how to detect hidden/
malicious processes. I then implemented the cron command, the significance of this was to automate my tasks and to also do a log check on a website, and see which specific user accessed the log
and what specific files they accessed.

---

## 🎯 Objectives
- [ ] Use Nano command in Linux
- [ ] Use Wget command to download files
- [ ] Locate processes in Linux
- [ ] Use cron command in Linux
- [ ] Locate logs in Linux
- [ ] Locate who accessed logs and what did they access
       
---

## 🧰 Tools Used
- THM AttackTheBox
- Ubuntu Linux

---

## 📸 Screenshots

> [Linux created file using nano] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20created%20file%20using%20nano.png)
> [Linux edited task3 file to capture flag] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20editted%20task3%20file%20and%20cap%20flag.png)
> [Linux started web server using Python3] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20started%20web%20server%20using%20Python3.png)
> [Linux downloaded file] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20downloaded%20.flag.txt%20file.png)
> [Linux displayed file contents] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20displayed%20file%20content.png)
> [Linux locate process running on IP] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20locate%20process%20and%20cap%20flag.png)
> [Linux crontab will run at reboot] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20crontab%20reboot.png)
> [Linux located apache2 logs] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20located%20apache2%20logs.png)
> [Linux IP and file user accessed] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20IP%20address%20and%20file%20access.png)

---

## 📊 Analysis

> Deployed Linux Machine, signed in using SSH, credentials were "tryhackme@10.10.196.156." After logging in, I created a file called "myfile" using the Nano command. I then edited a file called.
"task3" in "tryhackme"'s home directory using Nano by inputting "nano task3" and captured a flag called THM{TEXT_EDITORS}. I then used Python 3's "HTTPServer" module to start a web server in the
home directory of the "tryhackme" user by inputting "python3 -m http.server." I then downloaded the file "http://10.10.196.156:8000/.flag.txt" from the web onto the TryHackMe AttackBox
in a new terminal and then used the "cat" command to display its contents. I then located the process running on "10.10.196.156" by entering "ps aux | less" and captured the flag {THM}PROCESSES. To figure
out when a crontab will run exactly when deployed on instance (10.10.198.134), I input "crontab -e," scrolled down, and saw the crontab will run @reboot. I then located the Apache2 logs on the
On a Linux machine, by inputting "cd /var/log/apache2" and pressing "enter", then input "ls" in the following line to display the logs. Then, to check the IP address of the user who visited the site, "access.log.1"
I inputted "less access.log.1" and pressed Enter, and it displayed the IP address "10.9.232.111" and showed that the user accessed "catsanddogs.jpg."

---

## Reflection

> This lab taught me several actions in Linux, such as using the nano command to create files, using the Wget command to download files from the internet, finding processes in a Linux machine, using the cron
command to check logs, and figured out who access them and what files they accessed within that log. Handwritten notes were taken to review and memorize the commands.
