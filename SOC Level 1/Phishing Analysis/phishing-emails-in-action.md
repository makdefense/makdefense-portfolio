# [Phishing Analysis]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Phishing Emails in Action]  
**Date Completed**: [12/19/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding why we should look at tools that will aid us in examining email header information, which is a tool that helps
examine email header information because headers contain complex technical data that can be difficult ot interpret manually. Tools make it easier to identify spoofing, routing
anomalies, authentication failures, and potential indicators of phishing or compromise. They improve accuracy, speed, and consistency in email investigation, critical for SOC
efficiency and threat detection. Next, I learned about the importance of understanding techniques to obtain hyperlinks in emails, and expand the URLS if they're URL s
shortened, which is that attackers often hide or disguise malicious URLs using obfuscation and URL shorteners. Expanding these links safely allows analysts to uncover the proper
destination, detect phishing sites, identify malware delivery infrastructure, and assess risk without accidentally visiting malicious content. This is a core skill in email
threat analysis. Following, I learned about the importance of understanding tools to give us information about potentially malicious links without directly interacting with a
malicious link, which is that clicking or opening a suspicious URL can lead to malware infection, credential theft, network compromise, or triggering attacker-controlled actions.
Safe analysis tools allow analysts to inspect, expand, and evaluate URLs in a controlled, isolated way-protecting both the analyst and the organization while still providing
critical intelligence about the threat. Finally, I learned about the importance of understanding techniques to obtain malicious attachments from phishing emails and using malware
sandboxes to detonate the attachments to understand further what the attachment was designed to do, which is that this process reveals the proper behavior, payload, and intent of
the attacker. Sandboxing helps analysts understand what the malware is designed to do, such as credential theft, persistence, data exfiltration, or lateral movement, without
risking infection of real systems. This knowledge improves incident response, threat intelligence, and detection engineering.

---

## 🎯 Objectives
- [ ] Look at tools that will aid us in examining email header information.
- [ ] Cover techniques to obtain hyperlinks in emails, expand the URLs if they're URL shortened.
- [ ] Look into tools to give us information about potentially malicious links without directly interacting with a malicious link.
- [ ] Cover techniques to obtain malicious attachments from phishing emails and use malware sandboxes to detonate the attachments to understand further what the attachment was
      designed to do.
      
---

## 🧰 Tools Used
- THM AttackBox
- THM AnyRun
- THM ThunderBird
  
---

## 📊 Analysis & Screenshots

*** Phishing Case 1 ***

> For this room, I had to obtain details from several suspicious emails and implement appropriate rules to prevent my colleagues from receiving additional spam/phishing emails
as a Level 1 SOC analyst. For the first case, I had to deploy the attached virtual machine to analyze the first suspicious email.

> <img width="487" height="688" alt="pc1" src="https://github.com/user-attachments/assets/970406fd-2bba-4038-8766-b0eccac2a0da" />

> After launching the virtual machine and launching the "Phish3Case1-.eml" file. My first set of questions was to figure out the brand the email was tailored to impersonate and
the From email address. To figure this out, I navigated to the top of the page of the email and saw that the brand it was tailored to impersonate was "Netflix," and the From
email address was "NetfIix<JGQ47wazXe1xYVBrkeDg-JOg7ODDQwWdR@JOg7ODDQwWdR-yVkCaBkTNp.gogolecloud.com>."

> <img width="899" height="928" alt="pc2" src="https://github.com/user-attachments/assets/a32d26d4-16ce-49ab-b124-c0788d8c0b7a" />

> Moving on to the next question, I had to figure out the originating IP address and then defang it. To figure this out, I navigated to the top right of the email
page, clicked the "more" drop-down menu, then clicked "view page source," which then retrieved the originating IP address to be "209.85.167.226." After running it through
CyberChef, the Defanged IP address was "209[.]85[.]167[.]226."

> <img width="603" height="455" alt="pc3" src="https://github.com/user-attachments/assets/c3a76962-ec86-4a45-bfad-0e585f9b336d" />
> <img width="719" height="539" alt="pc4" src="https://github.com/user-attachments/assets/29acd157-47e3-48d0-824f-8369317510b7" />

> After the analysis so far, I was asked to determine the domain of interest and Defang it. To figure this out, I navigated through the "view page source" page
and saw that the domain of interest was "etekno.xyz." After running it through CyberChef, the Defanged domain was "etekno[.]xyz."

> <img width="624" height="388" alt="pc5" src="https://github.com/user-attachments/assets/6d1ab63a-463e-4613-a5d6-9f46d924da7d" />
> <img width="1016" height="702" alt="pc6" src="https://github.com/user-attachments/assets/a03ad11e-f6bd-4fc1-8d77-894b6bf364d5" />

*** Phishing Case 2 *** 

> Moving on to the following case, I had to investigate an email sent through the web application "AnyRun." After clicking the link
"https://app.any.run/tasks/8bfd4c58-ec0d-4371-bfeb-52a334b69f59" I retrieved the email to investigate.

> <img width="293" height="213" alt="pc7" src="https://github.com/user-attachments/assets/3b894332-f139-431b-a81a-010fbc2841b7" />

> For the first question, I had to figure out the classification AnyRun assigned to the email and the name of the "PDF file." To figure this out, I navigated to the top right of
the AnyRun application and clicked "Text Report." After clicking that, I retrieved both the PDF file name of "Payment-updateid.pdf" and the classification verdict to be
"Suspicious activity."

> <img width="768" height="304" alt="pc8" src="https://github.com/user-attachments/assets/e8eaa30b-bca5-462b-8a21-528007b241fd" />

> For the next question, I had to compute the SHA-256 hash of the PDF file. To figure this out, I navigated further down and saw that the SHA-256 hash was
"cc6f1a04b10bcb168aeec8d870b97bd7c20fc161e8310b5bce1af8ed420e2c24."
>
> <img width="798" height="541" alt="pc11" src="https://github.com/user-attachments/assets/492e74e7-1a09-41b8-b079-474a2825c6a1" />

> For the next question, I had to identify two IP addresses classified as malicious and defang them. To figure this out, I simply navigated down to the
"Connections" section and saw that the two IP addresses were "2.16.107.24, and 2.16.107.83." 

> <img width="1191" height="252" alt="pc12" src="https://github.com/user-attachments/assets/cf2fd0b7-f191-46d7-a93c-7cbb5ea0e500" />
> <img width="1108" height="451" alt="pc13" src="https://github.com/user-attachments/assets/d7dc8f94-dc10-4d5c-80f1-eb76780243b7" />

> After running both IP addresses through CyberChef to Defang them, the Defanged IP addresses were "2[.]16[.]107[.]24, and 2[.]16[.]107[.]83"

> <img width="1035" height="726" alt="pc14" src="https://github.com/user-attachments/assets/37e9fee8-de10-43dc-aad5-d6a37c04fe6d" />
> <img width="986" height="690" alt="pc15" src="https://github.com/user-attachments/assets/57fa1e37-57cd-458d-a981-797bf34d7ebb" />

> For the last question in this case, I had to figure out which Windows process was flagged as potentially bad traffic. To figure this out, I navigated further down the text
report, and under the "Threats" heading, I retrieved the "potentially bad traffic" process of "svchost.exe."

> <img width="1166" height="177" alt="pc16" src="https://github.com/user-attachments/assets/9347e997-a661-4ad4-90fb-75e07b82aa79" />

*** Phishing Case 3 ***

> Moving on to the following case, I had to investigate an email that was sent again through the web application "AnyRun." After clicking the link
"https://app.any.run/tasks/82d8adc9-38a0-4f0e-a160-48a5e09a6e83" I retrieved the email to investigate.

> <img width="419" height="206" alt="pc17" src="https://github.com/user-attachments/assets/ef276a2d-83d7-46a7-b9b0-08d7f4821a52" />

> For the first question, I had to figure out the classification. AnyRun classified the email as the name of the "Excel file." To figure this out, I navigated to the top right
of the AnyRun application and clicked "Text Report." After clicking that, I retrieved both the Excel file name of "CBJ200620039539.xlsx" and the classification verdict to be
"Malicious activity."

> <img width="723" height="279" alt="pc18" src="https://github.com/user-attachments/assets/1a1f98d4-b8c2-4f51-ac20-4afac5b33318" />

> For the next question, I had to determine the SHA-256 hash of the Excel file. To figure this out, I simply navigated further down and saw that the SHA-256 was
"5f94a66e0ce78d17afc2dd27fc17b44b3ffc13ac5f42d3ad6a5dcfb36715f3eb."

> <img width="831" height="626" alt="pc20" src="https://github.com/user-attachments/assets/33afbd8f-5be0-4302-bbd2-e84620d95758" />

> For the next question, I had to figure out which domains and IP addresses were listed as malicious and defang them. To figure this out, I navigated further down to
"DNS requests," retrieved the malicious domains: "biz9holdings.com, findresults.site, ww38.findresults.site" and the malicious IP addresses:
"75.2.11.242, 103.224.182.251, 204.11.56.48"

> <img width="606" height="245" alt="pc21" src="https://github.com/user-attachments/assets/10e54a7b-189f-4e82-a74a-2afb9d0a9c60" />

> After running both the malicious domains and IP addresses in CyberChef to Defang them. The results for the domains were
"biz9holdings[.]com,findresults[.]site,ww38[.]findresults[.]site" and for the IP addresses the results were "75[.]2[.]11[.]242,103[.]224[.]182[.]251,204[.]11[.]56[.]48."

> <img width="861" height="695" alt="pc22" src="https://github.com/user-attachments/assets/b2bbde0a-ab03-4120-bc19-c88e141525e7" />
> <img width="849" height="708" alt="pc23" src="https://github.com/user-attachments/assets/045f9051-4fef-4ed6-897b-04b78bafb82b" />
> <img width="894" height="664" alt="pc24" src="https://github.com/user-attachments/assets/1b5c9202-4a5f-4978-8e5b-359111ed2daa" />
> <img width="814" height="687" alt="pc25" src="https://github.com/user-attachments/assets/5edcef83-517f-46f2-8f07-c3a42710b600" />
> <img width="874" height="675" alt="pc26" src="https://github.com/user-attachments/assets/3ee2c1eb-8a9e-4797-916a-6031ecba561a" />
> <img width="828" height="670" alt="pc27" src="https://github.com/user-attachments/assets/4e5b90e1-ce9f-456e-84ab-7458636775fb" />

> For the last question in this case, I had to figure out which vulnerability the malicious attachment attempts to exploit. To figure this out, I navigated back up to the top of the "Text Report" and saw, within the "Tags" section, that the vulnerability was "CVE-2017-11882."

> <img width="621" height="479" alt="pc28" src="https://github.com/user-attachments/assets/e7d88217-a5e3-43b5-8e26-45fbfbf432a9" />

---

## Reflection

> This lab provided me with knowledge about the tools used to aid an analyst to investigate suspicious emails.
