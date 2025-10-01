# [Defensive Security Tooling]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [CyberChef: The Basics]  
**Date Completed**: [09/30/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding what CyberChef is, which is that it is a fast, practical Swiss-army knife for decoding, transforming, and analyzing data - invaluable for
forensics, incident response, threat intel, CTFs, and everyday triage work. Next, I learned about the importance of understanding how to navigate the interface, which is that it turns raw capability into
real work. Fast navigation saves time, reduces mistakes, and makes your investigations and responses far more effective. I then learned about the importance of understanding everyday operations, which are
the repeatable tasks you do every day in security. Knowing them matters because they turn theory into reliable action. Finally, I learned the importance of understanding how to create recipes and process
the data within CyberChef which is that the application lets you rapidly transform, decode, parse, and extract intelligence from messy or obfuscated data - so you can triage faster, reporduce work, hand
clean data to other tool (SIEM/EDR/YARA), and teach others exactly what you did.

---

## 🎯 Objectives
- [ ] Learn about what CyberChef is
- [ ] Learn how to navigate the interface
- [ ] Learn about common operations
- [ ] Learn how to create recipes and process the data

---

## 🧰 Tools Used
- THM CyberChef
  
---

## 📊 Analysis & Screenshots

*** Practice, Practice, Practice ***

> After reading the sections within CyberChef: The Basics, I was given a practice lab to complete using the CyberChef program. I first had to download the "Extractor-1725699521639.txt" file onto my system.
Next, I was given a question to determine the hidden email address within the text file. To do so, I first went to the CyberChef program, then clicked "Open file as input," then selected
"Extractor-1725699521639.txt" file.

> <img width="465" height="668" alt="cc1" src="https://github.com/user-attachments/assets/8fbcda2c-28d0-4e88-bf39-91991578d69c" />

> Next, I navigated to the left side of the application and selected "Extractors" from the "Operations" menu, then double-clicked "Extract email address," which added the operation to the recipe.
The hidden email that returned within the output field was "hidden@hotmail.com".

> <img width="838" height="332" alt="cc2" src="https://github.com/user-attachments/assets/439f8b89-288c-474c-b691-4f7ca6f35bb9" />
> <img width="541" height="227" alt="cc3" src="https://github.com/user-attachments/assets/a9c2a39b-c2c0-4001-83c9-18390fcdb9b8" />

> For the next question, I had to figure out the hidden IP address that ended in ".232." So to figure this out, I deleted the "Extract email address" from the recipe field and double-clicked on
"Extract IP address" and returned the IP of "102.20.11.232" within the output field.

> <img width="818" height="209" alt="cc4" src="https://github.com/user-attachments/assets/2d55cd48-cf1b-4f00-9883-71b3447afd2f" />
> <img width="564" height="304" alt="cc5" src="https://github.com/user-attachments/assets/559567a1-7abb-47d2-a397-48fb60e03cd7" />

> For the last question, I had to figure out which domain address started with the letter "T". To figure this out, I cleared out the "recipe" field within the application and navigated to the left side and
double-clicked "Extract domains," which then returned the domain "TryHackMe.com" within the output field.

> <img width="750" height="245" alt="cc6" src="https://github.com/user-attachments/assets/367b80d4-9503-47a2-94b9-21df4761d954" />
> <img width="364" height="196" alt="cc7" src="https://github.com/user-attachments/assets/1fd26c98-4c9a-49d8-939d-2f1cf9d261d5" />


*** Your First Official Cook ***

> For my next practical exercise, I had to use the same "Extractor-1725699521639.txt" file. However, for the first question, I had to figure out the IP that starts and ends with "10". To figure this out,
I navigated to the left side of the application and double-clicked on the "Extractor" "Extract IP addresses" which returned the IP address of "10.10.2.10" within the output field.

> <img width="869" height="252" alt="cc8" src="https://github.com/user-attachments/assets/3007baae-e842-414c-8eaf-84e40d033bce" />
> <img width="548" height="345" alt="cc9" src="https://github.com/user-attachments/assets/8a17dafa-cd74-47a5-8f9b-1b6d2d654e55" />

> Moving on to the next question, I had to determine the base64-encoded value of the string "Nice Room!" To figure this out, I first copied and pasted "Nice Room!" within the input field,
deleted whatever was in the "recipe" field, navigated to the left side of the application, and double-clicked on "To Base64," which retrieved the output of "TmljZSBSb29tIQ=="

> <img width="708" height="357" alt="cc10" src="https://github.com/user-attachments/assets/aca49b28-90a8-4ec2-9ce0-9ad3e63a1de5" />
> <img width="417" height="231" alt="cc11" src="https://github.com/user-attachments/assets/d3049c40-dc52-4619-ad1e-8624612b97db" />

> Next, I had to figure out the URL-decoded value for "https%3A%2F%2Ftryhackme%2Ecom%2Fr%2Froom%2Fcyberchefbasics". To figure this out, I cleared out the "recipe" field, copied and pasted the URL into the
input field, hovered over to the left side of the app, double-clicked on "URL decode", which retrieved the output "https://tryhackme.com/r/room/cyberchefbasics".

> <img width="776" height="277" alt="cc12" src="https://github.com/user-attachments/assets/adf4c4ef-62f0-42df-b0da-c803a8801ab3" />
> <img width="566" height="247" alt="cc13" src="https://github.com/user-attachments/assets/5de0600f-6765-426e-b17f-867a39cf2c06" />

> Next question: I was tasked with finding the datetime string for the Unix timestamp "1725151258". To figure this out, I cleared the "recipe" field, copied and pasted "1725151258" into the input field,
navigated to the left of the application, double-clicked on "From UNIX Timestamp," and retrieved the output "Sun 1 September 2024 00:40:58 UTC".

> <img width="794" height="452" alt="cc14" src="https://github.com/user-attachments/assets/ed21eb7a-a3ae-4f70-8cb8-b7d35640d76d" />
> <img width="603" height="328" alt="cc15" src="https://github.com/user-attachments/assets/fd3b97cb-63d3-4c88-a037-0748477da9b5" />

> Finally, my last task was to determine the Base85-decoded string of the value "<+oue+DGm>Ap%u7". To figure this out, I cleared the "recipe" field for the final time, copied and pasted "<+oue+DGm>Ap%u7"
into the input field, hovered over to the left side of the application, double-clicked on "To Base85" that was under "Date format," and retrieved the output of "This is fun!"

> <img width="802" height="569" alt="cc16" src="https://github.com/user-attachments/assets/36087b3a-18dc-48fc-b15a-a0908e5669f6" />
> <img width="353" height="253" alt="cc17" src="https://github.com/user-attachments/assets/6d4cde91-7f3c-4b7e-a774-ad9a8d0d8d17" />

---

## Reflection

> This lab provided me with knowledge about CyberChef and how to operate the application.

