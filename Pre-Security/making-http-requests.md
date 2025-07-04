# [HTTP In Detail]

**TryHackMe Path**: [Pre-Security]  
**Lab Topic**: [Making HTTP Requests]  
**Date Completed**: [07/04/2025]

---

## 🧠 Summary

> In this lab, I used TryHackMe browser to make different HTTP requests to different website paths, and managed URl and body parameters.

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

> After making a GET request to http://tryhackme.com/room page it successfully took me to that room, when making another GET request to /blog page I then set
the parameter to 1 and it took me to the specific blog page, I then made a DELETE request to /user/1 page and it deleted the user,
afterwards I made a PUT request to /user/2 page with the KEY set to 'username' and the parameter set to 'admin' and it updated the user, finally I then made a
POST request to /login page with the KEY parameter set to 'thm' and VALUE parameter set to 'letmein' and it logged me in
