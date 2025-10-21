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

> For my next task in first had to generate a rule for "file2" that was in the "suspicious-files" directory. To do so i had to first navigate to the directory "/tools/yarGen," then input the command
"python3_yarGen.py -m /home/cmnatic/suspicious-files/file2 --excludegood -o /home/cmnatic/suspicious-files/file2.yar," then "enter." 
>
> <img width="1108" height="51" alt="yara13" src="https://github.com/user-attachments/assets/f25bdade-d703-4223-95a0-502fa0724cd5" />

> This then created the rule for "file2."
>
> <img width="743" height="69" alt="yara14" src="https://github.com/user-attachments/assets/9dcae51f-52da-4452-9de7-0e092fa0f146" />

> Moving on to the first question of this practical i had to figure out what command i would use to test Yara and my rule against file 2 from within the root of the suspicious files directory.
To carry out the test i had to first navigate to the "suspicious-files" directory, then input the command syntax
"yara file2.yar file2/1ndex.php home_cmnatic_suspicious_files_file2_1ndex file2/1ndex. php," then "enter."
>
> <img width="778" height="65" alt="yara15" src="https://github.com/user-attachments/assets/03327b6c-04d7-46ef-ac59-c117736992ad" />

> I then had to copy the rule i created into the Loki signatures directory. To do so i navigated back to the main root directory then inputted the command
"mv /home/cmnatic/suspicious-files/files2.yar /home/cmnatic/tools/Loki/signature-base/yara/," then "enter."
>
> <img width="1213" height="62" alt="yara16" src="https://github.com/user-attachments/assets/31017356-ca74-413b-864f-1ce2ab1c225e" />

> I then had to test the rule with Loki to see if it flags file 2. After running the test it was confirmed that it does flag file 2.
>
> <img width="1110" height="189" alt="yara17" src="https://github.com/user-attachments/assets/b5d0e2ef-0c17-46ba-8dcd-654dde1c86c1" />

> For the next question i had to figure out the name of the variable for the string that it matched on. To figure this out i simply scrolled down to the scan results and saw that the variable name
was "Zepto."
>
> <img width="895" height="179" alt="yara18" src="https://github.com/user-attachments/assets/5b08ea06-763d-4c11-b0ee-8b12c76e7e8c" />

> I then had to figure out how many strings were generated. To figure this out i exited the Loki scan, then navigated to the directory "signature-base" that was in the "tools" directory, inputted the
command "nano file2.yar," then "enter."
>
> <img width="786" height="38" alt="yara19" src="https://github.com/user-attachments/assets/9c22d080-e40a-42b8-bccc-9075c64cf3ed" />

> After entering the nano editor for "file2.yar" it was discovered that they were a total of 20 strings.
>
> <img width="288" height="125" alt="yara20" src="https://github.com/user-attachments/assets/bc452d82-80c6-4d2f-9343-51146f9d4e5c" />

> For the final question of this practical i had to figure out one of the conditions to match on the Yara rule which was specifically a the file size. After scrolling through the nano editor for
"file2.yar" it was discovered that the file has to be less that 700KB to match on the yara rule.
>
> <img width="519" height="70" alt="yara21" src="https://github.com/user-attachments/assets/219a7dac-5dab-409b-bfec-9e3a9f768ca3" />

*** Valhalla *** 

> 

---

## Reflection

> This lab provided me with knowledge about 
