# [Web Hacking]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Web Application Basics]  
**Date Completed**: [09/08/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding the basics of HTTP, which is that it is the "language of the web." It underpins nearly every web app, is the basis of web attacks and defenses, and is
critical for troubleshooting and career advancement in cybersecurity. Next, I learned about the importance of understanding the basics of URLs, which are the backbone of web navigation, a common
vector for attacks, and a vital troubleshooting tool. They're also your first line of defense against phishing and other social engineering threats. I then learned about the importance of understanding the different
HTTP request methods, which control the core actions of the web, form the basis of web vulnerabilities, help in debugging and testing, and are essential for both offensive and defensive security work.
Fourthly, I learned about the importance of understanding response codes, which is that they tell you exactly how a server handled your request, help reveal vulnerabilities, make troubleshooting faster, and are
essential for both attackers and defenders in cybersecurity. Lastly, I learn about the importance of understanding headers, which are the control signals of the web. They enable functionality, reveal
vulnerabilities, help with troubleshooting, secure applications, and form the basis of API and web testing.

---

## 🎯 Objectives
- [ ] Learn the basics of HTTP
- [ ] Learn the basics of URLs
- [ ] Learn about request methods
- [ ] Learn about response codes
- [ ] Learn about headers
      
---

## 🧰 Tools Used
- THM Static Site

---

## 📊 Analysis & Screenshots

*** Practical Task: Making HTTP Requests ***

> After launching the THM Static Site, I was given a practical to make HTTP requests. For the first question, I had to find a flag by making a GET request to the website "http://tryhackme.com/api/users." To do this,
I just input "http://tryhackme.com/api/users" in the Static Site's browser and selected "GET," then clicked "Go." This returned the flag of "THM{YOU_HAVE_JUST_FOUND_THE_USER_LIST}."

> <img width="1103" height="1123" alt="web1" src="https://github.com/user-attachments/assets/55846b47-f278-4081-b850-4515d63dc7af" />

> For the next question, I had to find another flag by making a POST request to the website "http://tryhackme.com/api/user/2," along with updating the country of Bob from the UK to the US. To do this, all I did was
input the website "http://tryhackme.com/api/user/2" within the Static Site's browser, selected POST, then changed the parameters to key: country and value: US, then clicked Go. This returned the flag of
"THM{YOU_HAVE_MODIFIED_THE_USER_DATA}."

> <img width="584" height="341" alt="web3" src="https://github.com/user-attachments/assets/3a8cd24d-146b-4262-885a-ef172c5f4bf0" />
> <img width="1092" height="873" alt="web2" src="https://github.com/user-attachments/assets/d060b86d-f942-4605-832a-43edf71ffbf7" />

> For the last question, I had to find a flag by deleting a user by making a DELETE request to the website "http://tryhackme.com/api/user/1." To do this, all I did was input the website
"http://tryhackme.com/api/user/1" in the Static Site's browser, and selected "DELETE," then clicked "Go." This returned the flag of "THM{YOU_HAVE_JUST_DELETED_A_USER}."

> <img width="1101" height="1117" alt="web4" src="https://github.com/user-attachments/assets/8266a4d9-24ea-481e-b867-9375e1e0fd68" />

---

## Reflection

> This lab provided me with knowledge about HTTP and its request methods, response codes, and headers. It also gave insight into URLs. Provided me with hands-on experience of making HTTP requests within a Static
Site.
