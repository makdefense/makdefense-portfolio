# [How Website Work]

**TryHackMe Path**: [Pre-Security]  
**Lab Topic**: [JavaScript]  
**Date Completed**: [07/04/2025]

---

## 🧠 Summary

> In this lab, I used TryHackMe JavaScript Editor to change the rendered html code to "Hack The Planet" and added a click me button to the HTML page.
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

> To Change the rendered html code to "Hack The Planet" i first added the javascript of document.getElementById("demo").innerHTML = "Hack the Planet"; in line 9 then clicked
render HTML and javascript code to display "Hack The Planet" and to add the click me button to the HTML page i added <button onclick='document.getElementById("demo").innerHTML = "Hack the Planet";'>Click Me!</button>
between lines 7 and 8.
---

## Reflection

> This lab taught me how to add changes to a demo's element using javascript code and how to also add "onclick" events to execute javascript when the event occurs.
