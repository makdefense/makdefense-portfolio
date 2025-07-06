# [How Website Work]

**TryHackMe Path**: [Pre-Security]  
**Lab Topic**: [HTML Injection]  
**Date Completed**: [07/04/2025]

---

## 🧠 Summary

> In this lab, I used TryHackMe to implement HTML injection on a mock website. The importance of my implementing HTML injection was to learn how attacks can exploit web vulnerabilities, basically, and
how to defend against them.

---

## 🎯 Objectives
- [ ] Create HTML link
- [ ] Implement HTML Injection
      

---

## 🧰 Tools Used
- THM 

---

## 📸 Screenshots

> [HTML injection] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/html%20injection.png)

---

## 📊 Analysis

> To implement the injection, first I had to create an HTML link for http://hacker.com, so the code I used to create it was "<a href="http://hacker.com">Visit hacker.com</a>,"
Afterwards, I took that same line of code and input it into the "What's my name" field, clicked the "say hi" button to display "Welcome Visit hacker.com," and was able to implement the HTML
injection.

---

## Reflection

> This lab taught me how to implement HTML injection on a mock website's input field using an HTML link.
