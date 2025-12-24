# [Phishing Analysis]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Snapped Phish-ing Line-CTF]  
**Date Completed**: [12/23/2025]

---

## 🧠 Summary

> In this lab, I learned how to probe malicious emails and URLS, exposing a vast campaign.

---

## 🎯 Objectives
- [ ] Commplete "Snapped Phish-ing Line" Room

---

## 🧰 Tools Used
- THM AttackBox
- THM ThunderBird
- THM Mozilla FireFox
- Google Chrome
- VirusTotal
- dcode.fr (Ciper Identifier)
- CyberChef

---

## 📊 Analysis & Screenshots

*** Challenge Scenario ***

> For this room, I had to complete several tasks related to an unusual email received by employees across different departments. Those tasks included analyzing email samples
provided by my colleagues, analyzing phishing URL(s) by browsing them using Firefox, retrieving the phishing kit used by the adversary, using CTI-related tooling to gather more
information about the adversary, and analyzing the phishing kit to gather more information about the adversary.

> Moving on to the first two questions, I had to figure out who the individual was to receive an email attachment containing a PDF and what email address was used by the
adversary to send phishing emails. To figure this out, I first had to launch the attached virtual machine, then open the folder "phish-emails" on the Desktop, then open the
".eml" file "Quote for Services Rendered." After doing this, it retrieved the individual's name to be "William McClean" and the adversary's email address to be
"Accounts.Payable@groupmarketingonline.icu."

> <img width="434" height="582" alt="1" src="https://github.com/user-attachments/assets/9b1af625-11e7-4fda-9be4-25f3ddf62b66" />
> <img width="578" height="504" alt="2" src="https://github.com/user-attachments/assets/4472415b-394c-4b96-ad3b-d360bff49ae8" />
> <img width="859" height="296" alt="3" src="https://github.com/user-attachments/assets/309141c2-1a92-4634-a33c-78f958513a58" />

> Moving on to the next question, I had to figure out the redirection URL to the phishing page for the individual Zoe Duncan, in defanged format. To figure this out, I navigated
back to the ".eml" file within the "phish-emails" folder that contained "zoe duncan," then navigated to the attached "html," downloaded it onto the Desktop, opened it with
the Text Editor application, retrieved the URL, and then ran it through CyberChef. After doing all of this, I retrieved the defanged URL to be
"hxxp[://]kennaroads[.]buzz/data/Update365/office365/40e7baa2f826a57fcf04e5202526f8bd/?email=zoe[.]duncan@swiftspend[.]finance&error."

> <img width="677" height="547" alt="4" src="https://github.com/user-attachments/assets/d02ce056-690e-4657-9cd3-1d17cf25581a" />
> <img width="1433" height="125" alt="5" src="https://github.com/user-attachments/assets/2ef1dcb4-644d-4947-b97b-e856c9da552a" />
> <img width="541" height="252" alt="6" src="https://github.com/user-attachments/assets/cf22ddaa-4418-4c39-bf08-12bde2f84c73" />
> <img width="836" height="347" alt="7" src="https://github.com/user-attachments/assets/e3d57b00-d198-496b-bd5f-cf0d8e3e8aae" />
> <img width="704" height="340" alt="8" src="https://github.com/user-attachments/assets/17036f29-85d3-44bb-8d1d-92e501df7407" />
> <img width="1021" height="272" alt="9" src="https://github.com/user-attachments/assets/269cfe7b-7ee6-480d-bc1e-c5f15c6b1bec" />
> <img width="1405" height="749" alt="10" src="https://github.com/user-attachments/assets/ac9c615b-4644-417b-a092-9c48a9373b3c" />

> Moving on to the next question, I had to figure out the URL to the .zip archive of the phishing kit in defanged format. To figure this out, I navigated to Mozilla Firefox,
inputted "kennaroads.buzz/data" into the input field, launched the website, then copied the link to the "Update365.zip" file and pasted the link into CyberChef to defang it. After
doing all of this, I retrieved the URL of "hxxp[://]kennaroads[.]buzz/data/Update365[.]zip."

> <img width="646" height="233" alt="11" src="https://github.com/user-attachments/assets/a08fa364-95a2-4d75-aa2b-511e0aacd6a3" />
> <img width="596" height="558" alt="12" src="https://github.com/user-attachments/assets/df3de7ec-8f06-4e06-bf27-1df5f2741805" />

> Moving on to the next question, I had to figure out the SHA-256 hash of the phishing kit archive. To figure this out, I navigated to the same link I defanged in the previous
task,downloaded the "Update365.zip" file, then launched the Terminal application on the machine, then inputted "ls," then "enter," then "cd Downloads," then "enter," then "ls,"
then "enter." After doing all of this, this returned the "Update365.zip" file from the "Downloads" directory. I then input the command "sha256sum Update365.zip," then "enter" to
retrieve the SHA256 of "ba3c15267393419eb08c7b2652b8b6b39b406ef300ae8a18fee4d16b19ac9686.

> <img width="754" height="344" alt="13" src="https://github.com/user-attachments/assets/073d6f45-8de9-48cb-90ee-e57295bd1bd8" />
> <img width="835" height="571" alt="14" src="https://github.com/user-attachments/assets/ca4fc8da-233e-4c51-befc-151924004ad7" />

> Moving on to the next question, I had to figure out when the phishing kit archive file was submitted. To figure this out, I had to navigate to "VirusTotal" on Google Chrome,
then I copied & pasted the SHA256 I retrieved for the "Update365.zip" file into the "search" input field, and I then navigated to the details tab and saw that the submission date
of the was "2020-04-08 21:55:50 UTC."

> <img width="851" height="826" alt="15" src="https://github.com/user-attachments/assets/120de2a9-3464-4429-bfb1-0db4b4e1550d" />
> <img width="662" height="901" alt="16" src="https://github.com/user-attachments/assets/71e88fdd-47dc-460d-b968-8adefbecbef9" />

> For the next question, I had to figure out when the SSL certificate the phishing domain used to host the phishing kit archive was first logged. Since the SSL Certificate was no
longer available on the VirusTotal results, I clicked the hint icon and retrieved the answer "2020-06-25."

> <img width="508" height="120" alt="17" src="https://github.com/user-attachments/assets/cab16dc5-a580-4838-9e6f-95c579168db2" />

> Moving on to the next question, I had to figure out the user's email address who submitted their password twice. To figure this out, I navigated back to the URL
"hxxp[://]kennaroads[.]buzz/data/" undefanged, then navigated to the "Update365" folder, I then saw the email address of the user to be "michael.ascot@swiftspend.finance"
that submitted their password twice through the Microsoft Login.

> <img width="482" height="554" alt="18" src="https://github.com/user-attachments/assets/cd86ed32-89d6-4e57-a3d2-d5f6a64c5ad2" />
> <img width="443" height="898" alt="19" src="https://github.com/user-attachments/assets/8f69607c-6a82-4741-ab30-e6507bb2bf30" />

> Moving on to the next question, I had to figure out the email address the adversary used to collect compromised credentials. To figure this out, I navigated to the "Update365"
zip file onto the attached VM, unzipped it, double-clicked it, navigated to the "Validation" folder, then to the "submit.php" file, scrolled down, and saw the adversary's email
address was "m3npat@yandex.com."

> <img width="412" height="322" alt="20" src="https://github.com/user-attachments/assets/05291364-c259-48b1-98d7-29d94147c3cd" />
> <img width="743" height="376" alt="21" src="https://github.com/user-attachments/assets/3769a689-f54f-4ec9-af0f-16da395e1dcb" />
> <img width="718" height="572" alt="22" src="https://github.com/user-attachments/assets/c4b5ce5b-62c3-446d-80a3-0c79d642fe5a" />
> <img width="438" height="461" alt="23" src="https://github.com/user-attachments/assets/a120d405-6def-40de-97b8-3a0a9236a899" />

> Moving on to the second-to-last question, I had to figure out the other email address that the adversary used, but for this specific email, it ended with "@gmail.com." To
figure this out within the "Validation" folder, I navigated to the "update" file categorized as "unknown," scrolled further down into the script, and saw the email to be
"jamestanner2299@gmail.com."

> <img width="682" height="478" alt="24" src="https://github.com/user-attachments/assets/349d4976-786c-4951-8465-2d1393d03de3" />
> <img width="747" height="624" alt="25" src="https://github.com/user-attachments/assets/bc123f4d-f99b-47fe-8892-07dac334c024" />

> Moving on to the last question, I had to find the hidden flag. To retrieve the hidden flag, I navigated back to Firefox, then entered within the input field
"kennaroads.buzz/data/Update365/office365/flag.txt," which then returned the secret I had to decode. After retrieving the secret, I navigated to a cipher identifier on my
machine and saw that the secret decoded to base64. After figuring out the category of the secret to be Base64, I ran it through CyberChef with "From Base64" and "Reverse" recipes
to retrieve the hidden flag "THM{pL4y_w1Th_tH3_URL}."

> <img width="912" height="284" alt="26" src="https://github.com/user-attachments/assets/451875a4-9f1d-4801-8edb-e18d36e602c5" />
> <img width="630" height="353" alt="27" src="https://github.com/user-attachments/assets/61dfe437-83fb-456c-8d80-43dd5cc2ae45" />
> <img width="687" height="320" alt="28" src="https://github.com/user-attachments/assets/07927fea-c2f2-43c5-ad24-c82401c1be8b" />
> <img width="983" height="755" alt="29" src="https://github.com/user-attachments/assets/14f4b9b2-1a59-4aec-90bf-08cb823afae1" />
---

## Reflection

> This lab provided me with knowledge about analyzing malicious emails and URLs.
