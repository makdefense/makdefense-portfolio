# [Phishing Analysis]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Phishing Analysis Fundamentals]  
**Date Completed**: [12//142025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding all the components that make up an email, which is that each part-headers, body, metadata, attachments, links,
and sender information-contains critical clues that help analysts identify phishing, spoofing, malware, social engineering, and policy violations. Email is the #1 attack vector,
and knowing its components allows you to accurately analyze threats, validate authenticity, and protect the organization.

---

## 🎯 Objectives
- [ ] Learn all the components that make up an email

---

## 🧰 Tools Used
- THM AttackBox
  
---

## 📊 Analysis & Screenshots

*** Email Body ***

> For this room, I had to first find a flag within the file "email2.txt". To figure this out, I first launched the attached virtual machine, then double-clicked on the folder
titled "Email Samples" to discover the "email2.txt" file.

> <img width="636" height="416" alt="email1" src="https://github.com/user-attachments/assets/ee270c52-5d47-4497-b1ee-f96e4a877032" />

> I then double-clicked on the "email2.txt" file to retrieve the base64 data.

> <img width="647" height="518" alt="email2" src="https://github.com/user-attachments/assets/e1116b5b-9916-4f1b-b33a-a525609e6c60" />

> I then opened Google Chrome on my machine, launched CyberChef, copied and pasted the base64 data, and dragged "from base64" into the recipe field. This then generated the data i
into the output field.

> <img width="1633" height="1095" alt="email3" src="https://github.com/user-attachments/assets/6b8371be-1cc0-41e8-88c3-c9757e21302f" />

> I then clicked "Save output to file," which then retrieved the flag "THM{BENIGN_PDF_ATTACHMENT}."

> <img width="321" height="204" alt="email4" src="https://github.com/user-attachments/assets/6bbf201c-4e35-4f62-8b5a-308b372f69d1" />
> <img width="417" height="260" alt="email5" src="https://github.com/user-attachments/assets/8253f6c8-bece-4ca2-a4ef-f0e193de6973" />

*** Types of Phishing ***

> For my next exercise, I had to analyze a file titled "email3.eml" within the virtual machine and answer a few questions. So I first discovered the "email3.eml" file within the
"Email Samples" folder and double-clicked it.

> <img width="641" height="502" alt="email6" src="https://github.com/user-attachments/assets/bc41e0b7-b115-4346-b297-c7cc8c61d3ef" />

> For the first set of questions in this exercise, I had to figure out the trusted entity the email was masquerading as, the sender's email address, and the subject line. After
opening the "email3.eml" file, I discovered that the trusted entity was "Home Depot," the sender's email was "support@teckbe.com," and the subject line was
"Order Placed : Your Order ID OD2321657089291 Placed Successfully."

> <img width="799" height="527" alt="email7" src="https://github.com/user-attachments/assets/a1bcc308-7ed7-44b3-9113-3ab3cb78d746" />

> For the last question, I had to figure out the defanged format of the website for the "CLICK HERE" URL. To figure this out, I first clicked on the "CLICK HERE" to launch the
website. After launching the website, I copied and pasted it into CyberChef, dragged "Defang URL" into the recipe, and retrieved the Defanged URL of "hxxp[://]t[.]teckbe[.]com."

> <img width="1371" height="741" alt="email8" src="https://github.com/user-attachments/assets/0a27f734-8e4c-46bc-94a8-d5d991e22994" />
---

## Reflection

> This lab provided me with knowledge about all the components that make up an email.
