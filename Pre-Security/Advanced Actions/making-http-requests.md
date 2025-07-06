# [HTTP In Detail]

**TryHackMe Path**: [Pre-Security]  
**Lab Topic**: [Making HTTP Requests]  
**Date Completed**: [07/04/2025]

---

## 🧠 Summary

> In this lab, I used the TryHackMe browser to make different HTTP requests to various website paths and manage URL and body parameters. The importance of my doing this
was to discover hidden or sensitive content. Also, Modifying URL and body parameters helps me to test for input vulnerabilities and logic flaws.

---

## 🎯 Objectives
- [ ] Make GET, DELETE, POST, and PUT requests
- [ ] Manage URl and body parameters
- [ ] Add different key values to customize requests

---

## 🧰 Tools Used
- THM Browser

---

## 📸 Screenshots

> [Changing Parameters For HTTP Request] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/http%20requests.png)

---

## 📊 Analysis

> After making a GET request to http://tryhackme.com/room, I was successfully directed to that room. When making another GET request to the "/blog" page, I then set
the parameter to 1, and it took me to the specific blog page. I then made a DELETE request to the "/user/1" page, and it deleted the user.
Afterwards, I made a PUT request to the "/user/2" page with the KEY set to 'username' and the parameter set to 'admin', and it updated the user. Finally, I then made a
POST request to /login page with the KEY parameter set to 'thm' and the VALUE parameter set to 'letmein', and it logged me in
