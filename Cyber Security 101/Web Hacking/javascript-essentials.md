# [Web Hacking]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [JavaScript Essentials]  
**Date Completed**: [09//2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding 
---

## 🎯 Objectives
- [ ] Learn
      
---

## 🧰 Tools Used
- THM Machine
- THM Google Chrome
- THM Pulma

---

## 📊 Analysis & Screenshots

*** JavaScript Overview ***

> After launching the THM Machine i then was given a small practical to create a program in JS within the Google Chrome application console. I had to figure out the value of two added numbers by using a specific code
that was provided. To do this i launched the Google Chrome application, then right-clicked and selected "inspect."

> <img width="856" height="846" alt="java1" src="https://github.com/user-attachments/assets/a45d731a-e79f-4830-b837-dea0c0fa0992" />

> I then selected the "console" tab, copied the code that was provided and pasted it within the console then clicked enter. I got the result of "15."

> <img width="763" height="787" alt="java2" src="https://github.com/user-attachments/assets/62149e59-859d-496f-bc2b-d08fa88eda6e" />

> I then had to change the value of x to 10 to figure out the new result. After copy and pasting the same code within the console i changed the value of x to 10, then clicked enter and got the result of 20.

> <img width="769" height="799" alt="java3" src="https://github.com/user-attachments/assets/648581cf-01e6-4452-aee8-864acad721f9" />

*** Integrating JavaScript in HTML ***

> I was then given an exercise to create an HTML document with internal JS. To do this i right-clicked on the desktop, then selected "Create Document," then "Empty File."

> <img width="619" height="406" alt="java4" src="https://github.com/user-attachments/assets/04353a5e-415c-43a1-a551-02b1d1c190f5" />

> I then renmaed the created document to "internal.html."

> <img width="404" height="485" alt="java5" src="https://github.com/user-attachments/assets/aca563b7-ee4b-4358-b037-e8b43beb2a5e" />

> I then had to add some code to the "internal.html" file by opening it with Pulma, then copying and pasting the code into the text editor.

> <img width="482" height="554" alt="java6" src="https://github.com/user-attachments/assets/58e43ca5-c363-449b-bbcb-6497874ee9a0" />
> <img width="971" height="635" alt="java7" src="https://github.com/user-attachments/assets/c12810c6-57ba-4c98-bb63-7e11d76f816e" />

> I then saved the code within within the "internal.html" file, closed the text editor then double clicked on the file to open it up in Google Chrome. Opening the file within Google Chrome gave me the result of
the task i was looking to perform. Which was to add (x and y) and then display the results on the web page. The result was "15."

> <img width="945" height="651" alt="java8" src="https://github.com/user-attachments/assets/42c562dc-48fb-4e68-b70f-ea21e7e140dd" />
> <img width="772" height="515" alt="java9" src="https://github.com/user-attachments/assets/04ddbcaf-d889-4dba-98bc-0e58804cf7f2" />

> For my next task i had to perform external JS. To do this i had to first create a separate .js file and store JS code within the file. So after creating the .js file on the desktop and renaming the file to
"script.js" i then added the code for the same task i did within the "internal.html" to the "script.js" file, saved it, and closed the text editor.

> <img width="278" height="203" alt="java10" src="https://github.com/user-attachments/assets/07463728-3a5e-40d8-8972-c0d82bd807df" />
> <img width="778" height="626" alt="java11" src="https://github.com/user-attachments/assets/9678ddd7-87c3-4617-a7b7-32538927a4a6" />

> I then had to create another "html" file on the desktop. After renaming the file to "external.html," i opened it with Pulma and added the same code from the "internal.html" file, saved it and closed the text
editor.

> <img width="297" height="198" alt="java12" src="https://github.com/user-attachments/assets/d1e1d9db-74fc-4d78-9ac8-11c1c1bfcc79" />
> <img width="806" height="628" alt="java13" src="https://github.com/user-attachments/assets/c54b1704-7fdd-4340-94c2-e962b4c99f2d" />

> After double clicking on the "external.html" file and opening it in Google Chrome i got the same result as the "internal.html" file which was "15."

> <img width="1017" height="446" alt="java17" src="https://github.com/user-attachments/assets/b557f0bc-025c-47b4-9a8d-2eb8d48f2d9d" />

> I then was given another exercise on how to verify whether a website uses internal or external JS. I was given an "external_test.html" file within the "exercise" folder on the Desktop.

> <img width="554" height="299" alt="java14" src="https://github.com/user-attachments/assets/191e051e-fe7a-4779-b2c1-4e1e525d2162" />

> To check whether this html file used internal or external JS i had to double click on the file to open it in Google Chrome, then right-click, select "View page source," and this presented that the website
used external JS.

> <img width="1089" height="889" alt="java15" src="https://github.com/user-attachments/assets/4954dca7-cdd2-46b9-8009-ad985a4dc35b" />
> <img width="785" height="592" alt="java16" src="https://github.com/user-attachments/assets/e514baf7-d59c-4bfa-918d-c77bf99a3bea" />

*** Abusing Dialouge Functions ***

> I was then given a few exercises within the Abusing Dialouge Functions section. My first task was to get Google Chrome to display the alert "Hello THM." To do this i first launched Google Chrome, then opened
the console tab and inputted the code "alert("Hello THM")," then pressed "enter."

> <img width="1045" height="619" alt="java18" src="https://github.com/user-attachments/assets/c063a345-df70-4023-9b40-02ca916e96fc" />
> <img width="1085" height="549" alt="java19" src="https://github.com/user-attachments/assets/f414a839-e8ae-458f-88d9-70bae923da43" />

> For the next exercise i had to get Google Chrome to display the prompt "What is your name?" To do this i first lauched Google Chrome, then opened the console tab and inputted the code
"name = prompt("What is your name?");," followed by " alert("Hello " + name);," then pressed "enter."

> <img width="1081" height="774" alt="java20" src="https://github.com/user-attachments/assets/76811a8f-a5b1-48d1-a9c1-1e9851165f20" />

> After entering my name within the prompt i pressed the "ok" button and got the alert "Hello Makonenn."

> <img width="979" height="395" alt="java21" src="https://github.com/user-attachments/assets/c5af8b0d-11bd-484f-94fb-01c08509bfee" />

> For the next exercise i had to get Google Chrome to display the confirm dialouge "Do you want to proceed?" To do this i inputted the code "confirm("Do you want to proceed?")," then pressed "enter."

> <img width="1010" height="657" alt="java22" src="https://github.com/user-attachments/assets/829f7f20-a5b9-474c-9ccd-fd658a3fe00a" />

> After pressing the "ok" button on the confirm dialouge i got the message "true."

> <img width="291" height="251" alt="java23" src="https://github.com/user-attachments/assets/5311175a-82a5-44e3-960c-bd8bf080de90" />

> I then did an exercise where i had to exploit the functionality so that when a user used Google Chrome JS disrupts their browsing experience. I had to get an html file to prompt the alert "hacked" three
times when a user would open the file. To go about this i first created a file called "invoice.html" on the desktop.

> <img width="341" height="221" alt="java24" src="https://github.com/user-attachments/assets/6836bd2b-8246-419c-88c0-ce2570da38e4" />

> I then right-clicked on the "invoice.html" file and selected open with "Pluma" and inputted specific code that included the hacked alert to be displayed three times when a user would open it.

> <img width="886" height="614" alt="java25" src="https://github.com/user-attachments/assets/6a036f5c-fa2b-4f61-833e-062faf37a6b9" />

*** Bypassing Control Flow Statements ***

> For this section i was given an exercise to figure out what message was displayed after entering an age that was less than 18 within a conditional statement prompt. So firstly i had to create a file on the Desktop and
titled it "age.html."

> <img width="432" height="238" alt="java26" src="https://github.com/user-attachments/assets/aaaed8c0-e455-4aa7-bb1e-3bbec8ecd1cd" />

> Next i had to input specific if-else code statements that would allow me to execute different blocks of code depending on whether a condition evaluates to true or false. So all i did was opened the "age.html" file
with "Pluma" and copied and pasted the code within the text editor and saved it.

> <img width="867" height="607" alt="java27" src="https://github.com/user-attachments/assets/e2c1fa6e-5e88-4520-9e7b-690e2a750d19" />

> Then i double-clicked on the file to open it with Google Chrome. After opening it with Chrome i inputted the age of 17 within the prompt and got the message "You are a minor."

> <img width="619" height="383" alt="java30" src="https://github.com/user-attachments/assets/c2b01f50-ed93-416c-8faa-125eaee731e7" />

> For my next exercise i had to figure out the password of the user admin. To do this i first had to locate a file called "login.html" within the "exercise" folder on the Desktop. After locating it i right-clicked the
file and selected "open with Pluma." This then displayed the password "ComplexPassword" within the code for the username "admin."

> <img width="854" height="636" alt="java31" src="https://github.com/user-attachments/assets/98dba5f7-4b83-4067-a5f2-cecc0639fc8b" />

*** Exploring Minified Files ***

> For my next exercise i had to implement Obfuscation within an html file. I first had to create a file called "hello.html" and save it on the Desktop.

> <img width="501" height="155" alt="java34" src="https://github.com/user-attachments/assets/97973fe7-9eff-40d2-826c-c76b0ef08ed4" />

> I then had to right-click on the "hello.html" file and select "open with Pluma," then copy and paste the obfuscated code within the text editor area and save it.

> <img width="727" height="484" alt="java35" src="https://github.com/user-attachments/assets/0446d543-38a0-4e2b-8497-255c1d197f63" />

> I then had to create and save another file on the Desktop titled "hello.js"

> <img width="389" height="135" alt="java36" src="https://github.com/user-attachments/assets/226ac80d-2ea9-4093-8770-1e376355c2a7" />

> After saving the file i had to right-click on the file and select "open with Pluma," then copy and paste "function" code within the text editor area and save it.

> <img width="458" height="177" alt="java37" src="https://github.com/user-attachments/assets/16bc5915-7fa7-4c12-b11b-61f8dd37f87a" />

> After closing Pluma i went back and double-clicked on the "hello.html" file that was saved on the Desktop to open it with Google Chrome and was prompted with the alert "Welcome to THM."

> <img width="1055" height="397" alt="java38" src="https://github.com/user-attachments/assets/b75a6f61-2a29-4d9d-bed2-a65a9e1597f9" />

> After clicking "OK" to close out the message i right-clicked on the page and selected "insepct," then clicked on "sources" tab, then to obfuscate the code i just selected all the code within the text area, copied it
and pasted it within the text field of the "https://codebeautify.org/javascript-obfuscator" website and clicked "JS Obfuscator" to retrieve the obfuscated code.

> <img width="619" height="423" alt="java39" src="https://github.com/user-attachments/assets/17df80e8-0cff-4371-aff9-d93ae019d610" />
> <img width="1203" height="692" alt="java40" src="https://github.com/user-attachments/assets/dd305231-24fe-43d1-8f4d-aa7cb8e3e46a" />

> For my next exercise i had to deobfuscate the following obfuscated code snippet "age=0x1*0x247e+0x35*-0x2e+-0x1ae3;" using the website "https://obf-io.deobfuscate.io/." After opening the website, copying and pasting
the obfuscated code within the text field i clicked deobfuscate and got the age value of "21."

> <img width="1464" height="161" alt="java41" src="https://github.com/user-attachments/assets/9efbef82-122f-4df5-85db-544ce15c92fa" />
---

## Reflection

> This lab provided me with knowledge about 
