# [Cyber Defence Frameworks]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Pyramid Of Pain]  
**Date Completed**: [10//2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding 

---

## 🎯 Objectives
- [ ] Learn about the Pyramid of Pain

---

## 🧰 Tools Used
- THM Static Site
  
---

## 📊 Analysis & Screenshots

*** Hash Values ***

> After reading the sections within the Pyramid of Pain, i was given my first question under the topic "Hash Values (Trivial)." Which was to analyze the report associated with the hash
"b8ef959a9176aef07fdca8705254a163b50b49a17217a4ff0107487f59d4a35d" to figure out the file name. So to answer this question i clicked the given linked where the report was and navigated around and saw that
the file name was "Sales_Receipt 5606.xls" under the hash value of "b8ef959a9176aef07fdca8705254a163b50b49a17217a4ff0107487f59d4a35d."
>
> <img width="1364" height="564" alt="pop1" src="https://github.com/user-attachments/assets/9f2bb184-5a47-4502-bfed-e6bea482da1e" />

*** IP Address ***

> Next i was given my second question under the topic "IP Address (Easy)" which was to read a report to figure out both the first IP address and domain name the malicious process (PID 1632) attempted to
communicate with. To fiugre this out i just clicked the link where the report was and navigated through the pages of the report and saw that under "Network Activity" the first IP address was
"50.87.136.52" and the first domain was "craftingalegacy.com."
>
> <img width="797" height="498" alt="pop2" src="https://github.com/user-attachments/assets/653f8fd6-4909-4961-bf5a-433b3b4185a9" />

*** Domain Names (Simple) ***

> I then was given my third question under the topic "Domain Names (Simple)" which was to providde the redirected website for the shortened URL using a preview: "https://tinyurl.com/bw7t8p4u."
To provide this i just went to "Google Chrome" copied and pasted "https://tinyurl.com/bw7t8p4u" into the search field and added a "+" sign at the end this provided me with the URL "https://tryhackme.com/."
>
> <img width="411" height="195" alt="pop3 1" src="https://github.com/user-attachments/assets/7b87c3bb-3ce1-440a-b811-b455a7a378ba" />
> <img width="1288" height="532" alt="pop3" src="https://github.com/user-attachments/assets/3caec0e1-bef5-4e07-90bd-e5205b7ed481" />

*** Host Artifacts ***

> Following i was given my next question from within the topic "Host Artifacts (Annoying)" which was to figure out the IP address of a process that makes POST request to an IP address based in the United
States on port 8080. To figure this out i had to click on a link with a report then scroll all the way the page 50 where i discovered that the POST request was made to IP "96.126.101.6."
>
> <img width="460" height="154" alt="pop4" src="https://github.com/user-attachments/assets/6c7c4c45-1f5f-4254-9513-7da73fc45294" />

> I then had to figure out the name of a malicious executable (EXE) that the actor dropped. To figure this out i just navigated through the report and saw that executable was "G_jugk.exe" under the PID
1640.
>
> <img width="414" height="211" alt="pop5" src="https://github.com/user-attachments/assets/668e8c9d-4eb5-4414-b897-cbfd2fb05062" />

> I then had to determine how many vendows thought the host was malicious by looking at a report by Virustotal. To figure this out i just clicked on the link which kept the report and saw that a total
of 9 vendors determined the host to be malicious.
>
> <img width="471" height="169" alt="pop6" src="https://github.com/user-attachments/assets/8f915931-5aa4-45a8-825d-a64f42e0c39b" />

*** Tools ***

> Moving on to this section i had to answer a question that wanted me to provide the alternate name for fuzzy hashes without the abbreviation. To figure this out i went to the "SSDeep" official webpage,
navigated around and saw the alternate name to be "context triggered piecewise hashes."
>
> <img width="733" height="329" alt="pop7" src="https://github.com/user-attachments/assets/224db1b1-7fd0-4401-b0f9-5b45d297efc5" />

*** TTPs ***

> I then had to answer a few questions within this section. The first one i had to figure out how many techniques fall under he Exfiltration category. To figure this out i had to navigate to the
ATT&CK Matrix webpage, scroll around, and i discovered that there were a total of 9 techniques under the Exfiltration category.
>
> <img width="152" height="571" alt="pop8" src="https://github.com/user-attachments/assets/5452c3df-567e-4490-ac74-ae5865ceb709" />

> For the last question i had to figure out the name of the commercial, remote access tool Chimera used for C2 beacons and data exfiltration. To figure this out i navigated to the website
"MITRE ATT&CK Matrix," scrolled around and saw that the Chimera used "Cobalt Strike" as the remote access tool.
>
> <img width="1416" height="351" alt="pop9" src="https://github.com/user-attachments/assets/97a267cf-a1bd-40a2-87b9-e212fadc3252" />

---

## Reflection

> This lab provided me with knowledge about the pyramid of pain and how to utilize this model to determine the level of difficulty it will cause for an adversary to change the indicators associated with
them, and their campaign.

