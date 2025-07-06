# [How Website Work]

**TryHackMe Path**: [Pre-Security]  
**Lab Topic**: [JavaScript]  
**Date Completed**: [07/04/2025]

---

## 🧠 Summary

> In this lab, I used the TryHackMe JavaScript Editor to modify the rendered HTML code to "Hack The Planet" and added a "Click Me" button to the HTML page. The importance of my doing so was to learn the DevTool
JavaScript Editor and be able to inspect, test, and manipulate how a webpage behaves in real-time.

---

## 🎯 Objectives
- [ ] Change demo element's content
- [ ] Add Click Me button to HTML page
      

---

## 🧰 Tools Used
- THM Javascript editor

---

## 📸 Screenshots

> [Demo Element Change] 1. (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Javascript%20not%20added.png)
2. (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Javascript%20added.png)
> [Click Me button added] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Javascript%20added%20for%20Button%20clicked.png)

---

## 📊 Analysis

> To change the rendered HTML code to "Hack The Planet," I first added the JavaScript to the document.getElementById("demo").innerHTML = "Hack the Planet"; in line 9 then clicked
Render HTML and JavaScript code to display "Hack The Planet" and add the "Click Me" button to the HTML page. I added "<button onclick='document.getElementById("demo").innerHTML = "Hack the Planet";'>Click Me!</button>"
between lines 7 and 8.

---

## Reflection

> This lab taught me how to add changes to a demo's element using javascript code and how to also add "onclick" events to execute javascript when the event occurs.
