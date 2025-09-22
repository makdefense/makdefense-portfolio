# [Offensive Security Tooling]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Gobuster: The Basics]  
**Date Completed**: [09/22/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding basic enumeration, which is where recon becomes usable intelligence - it turns vague targets into a concrete map of services, users, and
misconfigurations you can test or defend. Next, I learned about the importance of understanding how to use Gobuster to enumerate web directories and files, which is that it turns blind web recon into
fast, actionable results - it quickly finds hidden directories, files, and virtual hosts that reveal attack paths, sensitive files, or low-hanging misconfigurations. Also, it makes your web-app recon
far more effective, and teaches you how defenders can spot automated discovery. I then learned about the importance of understanding how to use Gobuster to enumerate subdomains, which is that it lets you
quickly find forgotten apps, admin panels, API endpoints, and staging instances that attackers love. Following, I learned the importance of understanding how to use Gobuster to enumerate virtual hosts,
which is that many apps, admin panels, APIs, or staging sites live under different hostnames on the same IP. Knowing the vhost mode lets you discover those hidden hosts quickly, turning invisible attack
surface into actionable findings. Finally, I learned the importance of understanding how to use a wordlist, which is that they are the fuel for much of practical recon, brute-forcing, and discovery -
learningto pick, build, order, and tune them makes your attacks (in labs) and defenses (in production) far more effective and efficient.
 
---

## 🎯 Objectives
- [ ] Learn about basic enumeration
- [ ] Learn how to use Gobuster to enumerate web directories and files
- [ ] Learn how to use Gobuster to enumerate subdomains
- [ ] Learn how to use Gobuster to enumerate virtual hosts
- [ ] Learn how to use a wordlist
      
---

## 🧰 Tools Used
- THM Machine
- THM Gobuster

---

## 📊 Analysis & Screenshots

*** Setting Up Envioronment ***

> After launching the THM Machine, I first had to ensure I could resolve domains used throughout the room, so I had to change the "/etc/resolv-dnsmasq" file. To do so, I first had to enter the
type "sudo nano /etc/resolv-dnsmasq" and press "enter" to start editing the file with nano.

> <img width="633" height="52" alt="gb0" src="https://github.com/user-attachments/assets/5e7031cd-9b76-401a-ab1a-0185c7eb1396" />

> When I got into nano mode, I input the first line as "nameserver 10.201.52.205," pressed "^+O" to save the input, then pressed "enter," then "^+X" to close nano.

> <img width="497" height="96" alt="gb1" src="https://github.com/user-attachments/assets/840a491e-e072-45c4-9da7-deb6b49b2972" />
> <img width="693" height="61" alt="gb2" src="https://github.com/user-attachments/assets/f1f801a5-a746-488c-9f6c-22140f675266" />

> I then had to restart the DNSMAQ service so the changes could take effect. I did so by inputting the command "/etc/init.d/dnsmasq restart," then "enter."

> <img width="578" height="63" alt="gb3" src="https://github.com/user-attachments/assets/e1b24920-f575-48c8-90a6-ef79b7f3b70a" />

*** Use Case: Directory and File Enumeration ***

> After reading the "Use Case: Directory and File Enumeration" section, I was tasked with finding a directory within the website "www.offensivetools.thm" that stands out. To do so, I input the
command "gobuster dir -u "www.offensivetools.thm" -w /usr/share/wordlists/dirbuster/directory-1-list-2.3-medium.txt," then "enter." This started the enumeration for the website
"www.offensivetools.thm." After going through the enumeration, the directory that stood out to me was "/secret"

> <img width="1095" height="577" alt="gb4" src="https://github.com/user-attachments/assets/ebeccc42-9b3e-4af5-8b77-5725068bbe76" />

> Next, I had to retrieve a flag from a ".js" file called "flag.js." To do that, I continued the enumeration by inputting the command
"gobuster dir -u 'http://www.offensivetools.thm/secret' -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x .js," then "enter" to basically single out all .js files within the directory
"/secret."

> <img width="1425" height="438" alt="gb5" src="https://github.com/user-attachments/assets/3ab43689-4a7a-4751-9947-28d3acab7135" />

> After spotting the "flag.js" within the enumeration, I then canceled the enumeration by inputting "^+C," then "curl www.offensivetools.thm/secret/flag.js," then "enter," and retrieved the flag
THM{ReconWasASuccess}."

> <img width="676" height="54" alt="gb6" src="https://github.com/user-attachments/assets/224ab14a-5719-46e5-89ab-94c046ea69b1" />

*** Use Case: Subdomain Enumeration ***

> After reading the "Use Case: Subdomain Enumeration" section, I was given a practical to figure out how many subdomains were configured for the offensivetools.thm domain. To go about this, all I did was
input the command syntax "gobuster dns -d offensivetools.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt," then "enter," and saw that there were four subdomains
configured.

> <img width="1283" height="470" alt="gb7" src="https://github.com/user-attachments/assets/93feeb43-1e49-4c4b-8bce-d7b8e269815e" />

*** Use Case: Vhost Enumeration ***

> After reading the "Use Case: Vhost Enumeration" section, I was given a practical to figure out how many vhosts are on the offensivetools. The domain replies with a status code 200. To go about this, I
input the command syntax "gobust vhost -http://10.201.62.214" --domain offensivetools.thm -w /usr/share/wordlists/Seclists/Discovery/DNS/subdomains-topmillion-5000.txt --append-domain --exclude-length 250-
320," then "enter," which then retrieved a total of 4 vhosts for the domain "offensive.thm"

> <img width="2042" height="497" alt="gb8" src="https://github.com/user-attachments/assets/a03e7713-954d-4624-8293-d38e3511d148" />

---

## Reflection

> This lab provided me with knowledge about Gobuster and how to use it for enumeration.
