# [Cyber Threat Intelligence]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Yara]  
**Date Completed**: [10//2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding 

---

## 🎯 Objectives
- [ ] Learn about 

---

## 🧰 Tools Used
- THM AttackBox
- 
  
---

## 📊 Analysis & Screenshots

*** Using LOKI and its Yara rule set ***

> After reading the sections within Yara THM room i was given my first task within the "Using LOKI and its Yara rule set" section. For my first question i had to play the role of a security analyst for a
mid-size law firm and scan suspicious files on a web server within my organization. I had to first scan "file1" which was located within the "suspicious-files" directory, i had to figure out if Loki
detected the file as suspicious/malicious or benign. To do this i first launched the Yara VM and waited for it to load up. After the VM loaded i then navigated to the "suspicious-files" directory by
inputting the command "cd suspicious-files," then "enter," then "cd file1," then "enter." To run the scan i inputted the command sythax of "python ../../tools/Loki/loki.py -p ." then "enter."
>
> <img width="974" height="135" alt="yara1" src="https://github.com/user-attachments/assets/c27a5cce-085e-4a00-8940-ee60beb2c69d" />

> After running the scan the results from Loki retrieved the file to be suspicious
>
> <img width="794" height="93" alt="yara6" src="https://github.com/user-attachments/assets/7cc8a997-a48d-4bac-ac14-cc9a77c0a566" />

> I then had to figure out the Yara rule that the file matched on. To figure this out i just naviagated through the scan results and saw that it was matched on "webshell_metaslsoft."
>
> <img width="620" height="26" alt="yara8" src="https://github.com/user-attachments/assets/8504fc61-694a-43b2-b1d5-7ce56c1118af" />

> I then had to figure out the classification of the file by Loki. To figure this out i simply navigated through the scan results and saw that it was classified as "Web Shell."
>
> <img width="578" height="25" alt="yara7" src="https://github.com/user-attachments/assets/1e3a1135-ce15-4dd0-8ea0-a36a63ae2a71" />

> Next i had to figure out what string within he Yara rule did the output match on. To figure this out i just look through the scanned output and saw that the string was "Str1."
>
> <img width="912" height="30" alt="yara9" src="https://github.com/user-attachments/assets/6da04ed7-3162-42cb-afb5-8971ffac03cc" />

> I then had to figure the name and version of the hack tool. To figure this out i simply looked through the scanned output and saw that the name and version was "b374k 2.2" which was stored within
"FIRST_BYTES."
>
> <img width="807" height="30" alt="yara10" src="https://github.com/user-attachments/assets/f46af42a-83aa-4932-a356-ded37211e9c8" />

> I then had to inspect the actual Yara file that flagged file 1 and figure out how many strings were there to flag the file. After viewing the yara file i discovered that there was 1 string to flag
file 1.

> Following, i had to scan file 2 which was within the same "suspicious-files" directory and determine whether Loki detected the file as suspicious/malicious or benign. To figure this out i simply
inputted the command "cd files2," then "enter," then "python ../../tools/Loki/loki.py -p ." then "enter."
>
> <img width="875" height="137" alt="yara11" src="https://github.com/user-attachments/assets/3f7b1ba6-8302-4f18-a573-fa9f0c56d070" />

> After initiating the scan and completing it the results showed that the file was OK.
>
> <img width="813" height="105" alt="yara12" src="https://github.com/user-attachments/assets/10b24d90-f3e9-41f1-aa49-6cc7765cc2ce" />

> For the last question of this practical i had to inspect "file2" and figure out the name and version of the web shell. To go about this i first inputted the command "cat 1ndex.php," then "enter,"
then "more cat 1ndex.php," then "enter." This then returned the name and version of the webshell to be "b374k 3.2.3."
>
> <img width="1098" height="329" alt="yara5" src="https://github.com/user-attachments/assets/a8faa245-9ac6-438a-a78a-fdcc352846b5" />

*** Creating Yara rules with yarGen *** 




---

## Reflection

> This lab provided me with knowledge about 
