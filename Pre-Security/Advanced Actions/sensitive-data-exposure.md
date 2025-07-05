# [How Website Work]

**TryHackMe Path**: [Pre-Security]  
**Lab Topic**: [Sensitive Data Exposure]  
**Date Completed**: [07/04/2025]

---

## 🧠 Summary

> In this lab, I found a hidden password within the source code of a website on THM. The importance of doing this lab was to be able to learn to think like a hacker because hackers like to inspect the page source code, looking for
Hardcoded credentials, API keys, hidden input fields, Commented-out sensitive information, and misconfigured JavaScript. As a cybersecurity professional, I must be able to find and report these mistakes developers sometimes make because in
In secure environments, passwords shouldn't be in a page's source code.

---

## 🎯 Objectives
- [ ] Find hidden password within source code
      
---

## 🧰 Tools Used
- THM 

---

## 📸 Screenshots

> [Hidden Password Within Page Source Code] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Hidden%20Password.png)


---

## 📊 Analysis

> To find the hidden Password within the source code of https://static-labs.tryhackme.cloud/sites/howwebsiteswork/html_data_exposure/, I first click on the website, then right
clicked on the general page and clicked on View Page Source, where I then was able to find the Password hidden in the code, which was Password: testpasswd

---

## Reflection

> This lab taught me how to find hidden messages within a website using their source code.
